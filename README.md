# Strat: Deterministic Structural Definition System
**Structure that means the same thing everywhere**

[![Status](https://img.shields.io/badge/status-active%20research%20and%20development-blue)](#project-status--roadmap) [![Spec](https://img.shields.io/badge/spec-0.1.0--draft-informational)](#versioning) [![Docs: CC BY-NC-SA 4.0](https://img.shields.io/badge/docs-CC%20BY--NC--SA%204.0-blue)](https://creativecommons.org/licenses/by-nc-sa/4.0/) [![Code: BSL 1.1 → Apache-2.0 (2028-11-03)](https://img.shields.io/badge/code-BSL%201.1%20%E2%86%92%20Apache--2.0%20(2028--11--03)-orange)](./LICENSE.BSL)

> **Note:** Strat is an active research project. This document describes its current intent and design direction. As the project evolves, details may change — but the goal remains constant: to make structure itself an immutable truth.

## Overview

Every compiler, language, and platform interprets structure slightly differently. A schema that looks identical in C might not line up in Rust or Zig. Even when the code compiles, its binary layout can subtly diverge.

**Strat** defines structure, instances, and function signatures as immutable truths — declarative facts about how data is represented, not how it behaves. There is no implementation logic, no control flow, and no compiler interpretation. Once defined, a Strat schema means exactly the same thing everywhere — in bytes, in memory, and in proof.

## What It Does

Strat is a deterministic, declarative system for describing typed schemas and function signatures that remain identical across compilers, languages, and architectures. It makes data representation verifiable and permanent so every structure and instance carries the same meaning by definition—not by convention.

**Properties & enforcement in practice**

* **Immutable schemas** that stay stable across time, systems, and toolchains.
* **Verifiable equivalence** via 256-bit BLAKE3 fingerprints computed over canonicalized bytes.
* **Zero-copy compatibility** directly usable by C, Rust (repr(C)), and Zig (extern struct), plus C headers.
* **No hidden semantics**—only structure, never behavior.
* **Canonical grammar** where document order defines layout with no implicit reordering or sugar.
* **ABI precision** using fixed-width primitives (u8, i32, f64) with explicit padding, alignment, and endianness.
* **Canonical serialization** in declaration order with a fixed binary format.
* **Cross-language consistency** without translation layers, reflection, or generators.
* **Verification integration** providing a structural foundation for formal proof.

*In short: define once, and it stays true everywhere.*

## Status & Roadmap

- Stage: active research / early.
- Near-term plan: core prototypes (parser, canonical grammar checks, serializer, tooling, etc.) will be implemented in **Zig** first, with emitters/interop for C and Rust (`repr(C)` / `extern struct`).

## License

**Documentation, specifications, and diagrams:** [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)

**Code and grammars:** Business Source License 1.1 (BSL 1.1) — changes to Apache-2.0 on **2028-11-03**. See [LICENSE.BSL](./LICENSE.BSL) for terms and change parameters, and [LICENSE-APACHE](./LICENSE-APACHE) for the future license text.

**Scope:** Only materials explicitly published in this repository are covered by these licenses. Unpublished or private works remain proprietary unless otherwise indicated.

**Contact:** Lloyd (nklzero) — [lloyd@nukli.zone](mailto:lloyd@nukli.zone)
