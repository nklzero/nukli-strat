# Strat

**Structure that means the same thing everywhere**

![Image](assets/strat_logo.png)  

[![Status](https://img.shields.io/badge/status-active%20research%20and%20development-blue)](#project-status--roadmap)  
[![Core ABI](https://img.shields.io/badge/Core_ABI-in_progress-blue?style=flat)](#roadmap) [![Portability](https://img.shields.io/badge/Portability-planned-lightgray)](#roadmap) [![Binary Format](https://img.shields.io/badge/Binary_Format-planned-lightgrey?style=flat)](#roadmap) [![Language Layer](https://img.shields.io/badge/Language_Layer-planned-lightgrey?style=flat)](#roadmap) [![Prototype SDK](https://img.shields.io/badge/Prototype_SDK-planned-lightgrey?style=flat)](#roadmap)  [![Docs: CC BY-NC-SA 4.0](https://img.shields.io/badge/Docs_License-CC%20BY--NC--SA%204.0-purple)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
[![Code: BSL 1.1 → Apache-2.0 (2028-11-03)](https://img.shields.io/badge/Code_License-BSL%201.1%20%E2%86%92%20Apache--2.0%20(2028--11--03)-purple)](./LICENSE.BSL)

**Strat** is a *verifiable, deterministic, and language-agnostic ABI system* designed to declare schemas, data and function signatures across languages and platforms. It aims for **C ABI compatibility**, **zero-copy semantics**, and **bit-for-bit reproducibility**.

## Overview

**Strat** is a _verifiable systems architecture and ABI specification_ — unifying the core ideas of established efforts in the software industry into a single, portable, auditable foundation for interoperable and long-lived computation.
- Declarative language for defining data types and function signatures.  
- Canonical binary representation that mirrors memory layout for portability.
- Portable runtime and SDK built to enforce ABI invariants.
- Built-in cryptographic verifiability, supporting reproducible builds.

_**Strat is in active research and prototyping stage**. As the project evolves, details, [Roadmap](#Roadmap) and other content in this file might change — but the goal remains constant: to make structure itself an immutable truth._

## Philosophy
Strat is built for **predictability**, **portability**, and **reproducibility**.  
It defines how computation and data coexist in a verifiable, durable form — with a **minimal runtime**, not a virtual machine.

## Roadmap

The project is in early prototype stage. My initial focus is on validating the foundational ABI and portability layer, before advancing into higher-level language and runtime components.

**Phase 1 — Core ABI & Portability**
- Define the core ABI rules and portability invariants.
- Establish a deterministic, C-compatible binary layout.
- Publish reference tests validating layout and reproducibility.

**Phase 2 — Binary Representation & Tooling**
- Define the canonical binary format.
- Develop tooling for serialization / deserialization.
- Release reference artifacts and layout validators.

**Phase 3 — Language Layer**
- Introduce the declarative syntax for types and functions.
- Publish the grammar reference and an initial parser prototype. 
	- Draft already present in [Strat Core Grammar](language_specification/strat_core_grammar.md) with some examples in [language_specification](language_specification/README.md)
- Ensure equivalence between text definitions and binary representation.

**Phase 4 — Prototype SDK**
- Provide a minimal SDK exposing the ABI/data model.
- Offer CLI tooling to compile schemas and validate layouts.
- Document external language-binding strategy.

**Phase 5 — Cross-Language Bindings & Verifiability**
- Extend SDK bindings to languages such as C, Rust, Zig.
- Incorporate cryptographic fingerprints and reproducible-build validation.
- Publish a compliance test suite and canonical examples.

## License

**Scope:** Only materials explicitly published in this repository are covered by these licenses. Unpublished or internal works remain proprietary unless otherwise stated.

- **Documentation, specifications & diagrams:** [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)
- **Code & grammars:** Business Source License 1.1 (BSL 1.1) — will convert to Apache 2.0 on **2028-11-03**. _See [LICENSE-code.txt](LICENSE-code.txt) for full terms and change parameters._
- **Contact:** Lloyd (nklzero) — [lloyd@nukli.zone](mailto:lloyd@nukli.zone)
