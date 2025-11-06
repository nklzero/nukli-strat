# Strat

**Structure that means the same thing everywhere**

![Image](strat_logo.png)


[![Status](https://img.shields.io/badge/status-active%20research%20and%20development-blue)](#project-status--roadmap)
[![Spec](https://img.shields.io/badge/spec-0.1.0--draft-informational)](#versioning)
[![Docs: CC BY-NC-SA 4.0](https://img.shields.io/badge/docs-CC%20BY--NC--SA%204.0-blue)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
[![Code: BSL 1.1 → Apache-2.0 (2028-11-03)](https://img.shields.io/badge/code-BSL%201.1%20%E2%86%92%20Apache--2.0%20(2028--11--03)-orange)](./LICENSE.BSL)

**Strat** is a *verifiable, deterministic, and language-agnostic ABI system* designed to define, link, and execute data and function signatures across languages and platforms. It aims for **C ABI compatibility**, **zero-copy semantics**, and **bit-for-bit reproducibility**.

## Overview

- **Declarative language** for defining data and function signatures.
- **Canonical binary representation** equal to memory layout.
- **Portable runtime and SDK** enforcing ABI invariants.
- **Cryptographic verifiability** for reproducible builds.

> **Note:** Strat is an active research project. This document describes its current intent and design direction. As the project evolves, details may change — but the goal remains constant: to make structure itself an immutable truth.

## Prototype

The current stage is a **Zig-based prototype**, validating Strat’s architecture and ABI model.  
Future milestones will expand toward the complete Strat SDK, binary format, and cross-language bindings.

## Philosophy

Strat is built for **predictability**, **portability**, and **reproducibility**.  
It defines how computation and data coexist in a verifiable, durable form — with a **minimal runtime**, not a virtual machine.

## License

**Documentation, specifications, and diagrams:** [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)

**Code and grammars:** Business Source License 1.1 (BSL 1.1) — changes to Apache-2.0 on **2028-11-03**. See [LICENSE-code.txt](LICENSE-code.txt) for terms and change parameters.

**Scope:** Only materials explicitly published in this repository are covered by these licenses. Unpublished or private works remain proprietary unless otherwise indicated.

**Contact:** Lloyd (nklzero) — [lloyd@nukli.zone](mailto:lloyd@nukli.zone)

---

> Strat is a *verifiable systems architecture and ABI specification* unifying the ideas of Cap’n Proto, FlatBuffers, LLVM, and WebAssembly into one portable, auditable foundation for interoperable and long-lived computation.