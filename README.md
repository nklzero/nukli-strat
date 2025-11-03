# Nukli Strat

**Strat** is a **declarative specification language (DSL)** and **interface definition language (IDL)** for describing *verifiable*, *deterministic*, and *interoperable* software interfaces.

It is part of the broader **Nukli** project, focused on building a meta-architecture for **verified systems** and **reproducible software artifacts**.

Strat defines software structures, functions, and ABIs using a clear, minimal syntax:

```strat
@structure Point {
  x: f32,
  y: f32,
}
```

## Highlights

* **Declarative:** Specify what an interface *is*, not how it’s implemented.
* **Deterministic:** One source → one canonical binary and schema layout.
* **Verifiable:** Designed for formal checks and reproducible build artifacts.
* **Interoperable:** Maps cleanly to C, JSON, and future Nukli IR formats.

---

## Status and Research Focus

Strat is an **active research project** in its early **experimental** phase.
Its current focus areas include:

* Developing a formal grammar and type system for **verifiable interface definitions**
* Experimenting with **deterministic serialization** and **ABI-level reproducibility**
* Exploring **meta-language design** for composable software specifications
* Integrating Strat with the **Nukli Core** runtime for validation and testing

The grammar, semantics, and ABI model are evolving and **not yet stable**.
Feedback, peer review, and experimental contributions are highly encouraged.

---

## Use Cases

* Define cross-language **ABIs** and **serialization schemas**
* Generate **C headers**, **JSON schemas**, or **verifiable binary layouts**
* Serve as a **formal spec layer** for deterministic builds
* Extend with templates, attributes, and metadata for domain-specific specs

---

## License

- Documentation, specifications, and diagrams: [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)
- Code and grammars: [Business Source License 1.1](https://mariadb.com/bsl11/)
  *(Changes to Apache 2.0 on 2028-11-03)*

Only materials explicitly published in this repository are covered by these
licenses. Unpublished or private works remain proprietary unless otherwise
indicated.

**Contact:** Lloyd (`nklzero`) — <lloyd@nukli.zone>.

---

**GitHub Topics:** `language-design`, `dsl`, `idl`, `compiler`, `meta-programming`, `abi`, `serialization`, `formal-spec`, `nukli`