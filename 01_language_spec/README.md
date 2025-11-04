# Strat — Language Specification

Documentation and reference material for the Strat language live in this folder. It contains the primary grammar [strat_core_grammar.md](01_language_spec/strat_core_grammar.md) (former `core_grammar.ebnf` which will be reintroduced upon grammar stability and feature lock) and will contain supporting language-design material: examples, notes, and any validator/formatting guidance.

> **Provenance:** examples were initially produced with AI assistance and **human-reviewed** to match the current grammar.

---

## Core grammar examples

The examples below are short, focused, and grouped by concept. Each example is in its own code block for easy copy/paste into files or test cases.

### Template

```text
@template Vec2 {
  x: i32,
  y: i32,
}
```

### Structure with attributes and `@extends`

```text
@structure Point {
  @attributes{ packed = true, align = 4 },
  @extends Vec2,
  id: u64,
  name: str,           # C string pointer (char const *)
}
```

### Fixed-size array and variable pool

```text
@structure Matrix {
  rows: u32,
  cols: u32,
  data: array[f32, 16],        # fixed-size array of 16 f32 values
  pool: slice[i32],            # variable-length pool: use slice or pointer+len
  # Alternative explicit form:
  # pool_ptr: pointer[i32],
  # pool_len: size,
}
```

### Pointer, Reference, and Slice examples

```text
@structure BufferView {
  ptr: pointer[u8],       # raw pointer (T*)
  len: size,              # size_t
  cap: size,
  const_ref: reference[i32],
  window: slice[u8],      # { T*, size_t } view
}
```

### Union (layout-affecting attributes)

```text
@union Variant {
  @attributes{ packed = false, align = 8 },
  as_u64: u64,
  as_f64: f64,
  bytes: array[u8, 8],
}
```

### Enumeration with explicit values

```text
@enumeration Color {
  @attributes{ deprecated = false },
  Red = 0,
  Green = 1,
  Blue = 2,
  Alpha = 255,
}
```

### Function signatures (declarations)

```text
@function add(a: i32, b: i32) -> i32
@function create_point(x: i32, y: i32) -> Point
@function parse_name(bytes: slice[u8]) -> i32
```

### Metadata and escaped strings

```text
@metadata{
  build = "2025-11-02",
  notes = {
    author = "nklzero",
    comment = "Uses C-style escapes: \"newline\\n tab\\t unicode: \\u2603\"",
  },
}
```

### Combined template + structure example

```text
@template Header {
  magic: array[u8, 4],
  version: u32,
}

@structure FileRecord {
  @attributes{ align = 8 },
  @extends Header,
  timestamp: u64,
  payload: slice[u8],
  checksum: u32,
}
```

---

## Quick semantics

* **Primitives**

  * `i8, i16, i32, i64`, `u8, u16, u32, u64`, `f32, f64`, `bool` — fixed-width numeric primitives.
  * `size` — maps to the platform `size_t` (use when storing lengths/capacity).
  * `str` — C NUL-terminated string (alias-like semantics; treated as `pointer[u8]` at the ABI level).

* **Compound types**

  * `array[T, N]` — fixed-size array of `N` elements.
  * `slice[T]` — a *memory view* `{ T*, size_t }` (non-owning, variable length).
  * `pointer[T]` — raw pointer to `T` (nullable by convention).
  * `reference[T]` — non-owning reference (non-null by convention).

* **Ownership & nullability**

  * `pointer[T]` is allowed to be nullable.
  * `reference[T]` is intended to be non-null and not owning.
  * `slice[T]` is a non-owning view; if ownership is required use `pointer+len` conventions or a separate owning container.

* **Attributes & ordering**

  * `@attributes{ ... }` may appear at the top of composite blocks.
  * `@extends` (if present) **must** come after `@attributes` and before the field list (this ordering is required by the memory-layout rules in the grammar).

* **Functions**

  * `@function name(args...) -> Type` are declarations (no body in the EBNF examples). Function names use plain identifiers to match the current grammar.

* **Formatting**

  * Trailing commas in lists/blocks are allowed and supported in the examples for ergonomics.
  * Comments use `#` for end-of-line comments, and string escapes support C-style escapes like `\n`, `\t`, `\"`, and `\uXXXX`.

---

© 2025 Lloyd (nklzero) — Andorra  
This documentation, including embedded grammar and code examples,  
is licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).

Example grammar excerpts are illustrative and provided for educational,
non-commercial use. Full grammar source files are licensed separately
under the [Business Source License 1.1](LICENSE-code.txt).
