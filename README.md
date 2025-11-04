# Nukli Strat — Deterministic Language for Verifiable and Reproducible Software

**The deterministic language of structural truth — for reproducible, verifiable, and cross-language software.**

**Strat** is a **deterministic declarative language** and **cross-language interface definition language (IDL)** for defining **verifiable, portable, and reproducible software interfaces**.
Part of the broader **Nukli meta-architecture**, Strat ensures **C-ABI–compatible layouts**, **hash-stable serialization**, and **provably consistent data structures** across compilers and architectures.

> **Keywords:** deterministic language · cross-language IDL · verifiable schema · C ABI · reproducible builds · formal verification · type system · serialization · interoperability · meta-architecture

## Overview

**Strat** provides a **declarative specification layer** for expressing typed data structures, function contracts, and instances whose memory layouts are **provably identical** across toolchains and operating systems.

Strat eliminates nondeterminism in schema and ABI definition, enabling **verifiable cross-language interoperability** and **reproducible builds** across environments.

## Syntax Examples

### Basic Syntax

```strat
@namespace game::core

@enum EntityKind { Player = 1, NPC = 2, Object = 3 }

@struct Vec2 {
	x: f32,
	y: f32
}

@struct Entity {
	id: u32,
	kind: EntityKind,
	position: Vec2
}


@function move_entity {
	parameters: (e: Entity, delta: Vec2),
	returns: Entity
}


@instance hero: Entity = {
	id = 100,
	kind = EntityKind::Player,
	position = { x = 0.0, y = 0.0 }
}
```

### Advanced Constructs

```strat
@metadata {
    project: "Data Pipeline DAG",
    version: "0.5.0",
    author: "nklzero"
}

@namespace flow::pipeline

@enum NodeKind { Extract = 1, Transform = 2, Load = 3 }

@struct Node {
    id: u32,
    kind: NodeKind,
    name: str,
    depends_on: array[u32, 4]  # IDs of parent nodes
}

@struct DAG {
    id: u32,
    nodes: array[Node, 16],
    edge_count: u8
}

# Function signature defining deterministic node resolution order
@function resolve_node {
	parameters: (dag: DAG, node_id: u32),
	returns: Node
}

# Function signature representing a task operation
@function execute_node {
	parameters: (n: Node),
	returns: bool
}

# Template for a default Transform node
@template default_transform: Node = {
	id = 100,
	kind = NodeKind::Transform,
	name = "default_transform",
	depends_on = { 0, 0, 0, 0 }
}

# DAG instance definition
@instance etl_dag: DAG = {
	id = 1,
	nodes = {
		{ id = 1, kind = NodeKind::Extract, name = "extract_users", depends_on = { 0, 0, 0, 0 } },
		{ id = 2, kind = NodeKind::Transform, name = "normalize_data", depends_on = { 1, 0, 0, 0 } },
		{ id = 3, kind = NodeKind::Load, name = "store_in_db", depends_on = { 2, 0, 0, 0 } }
	},
	edge_count = 3
}
```

## About Strat — Deterministic IDL for Verifiable Software

**Nukli–Strat** is an ongoing research prototype for **verifiable, deterministic, and interoperable computation**.

* **Strat** is a **declarative and deterministic language** for defining **typed data structures**, **function contracts**, and **instances**.
  Each Strat artifact—whether text, binary, or in-memory—has a **canonical C-ABI layout** and a **256-bit reproducible hash**, ensuring **bit-for-bit equivalence** and zero translation loss between languages like **C, Rust, and Zig**.

* **Nukli** is the **truth-preserving meta-architecture** built atop Strat.
  It follows the **S → I → E → V** model (*Specification → Implementation → Execution → Verification*) to guarantee that system behavior remains **causally faithful to its declared intent**.

Together they form a **causal-truth stack** where:

1. Intent (specifications) are deterministic and verifiable.
2. Implementations provably match those specifications.
3. Executions can be verified post-factum or in-line.
4. All transformations remain truth-preserving by design.

**Goal:**

> Replace *trust* with **truth** — making correctness, reproducibility, and interoperability intrinsic properties of software itself.

## What Makes Strat Unique

Unlike conventional schema languages or IDLs such as **Protocol Buffers**, **Thrift**, or **Cap’n Proto**, Strat’s goal is *structural truth*, not just data interchange.

* **Deterministic layouts:** Every field, alignment, and padding byte is fixed and reproducible.
* **C-ABI alignment:** Zero-copy compatibility across C, Rust, Zig, and other languages.
* **Canonical hashing:** Each structure and instance has a verifiable, cryptographically stable identity (BLAKE3-256).
* **Cross-platform reproducibility:** Identical results on all compliant toolchains.
* **Formal verifiability:** Designed to integrate with **formal verification** and **reproducible build systems**.

This makes Strat not just an IDL, but a **truth-preserving schema language** — bridging specification, implementation, and proof.

## Project Status and Research Focus on Deterministic Interoperability

Strat is an **active research project** in its early **experimental** phase.
Current focus areas include:

* Developing a formal grammar and type system for **verifiable interface definitions**
* Experimenting with **deterministic serialization** and **ABI-level reproducibility**
* Exploring **meta-language design** for composable software specifications
* Integrating Strat with the **Nukli Core** runtime for validation and testing

The grammar, semantics, and ABI model are evolving and **not yet stable**.
Feedback, peer review, and experimental contributions are highly encouraged.

## Use Cases — Cross-Language ABIs, Reproducible Schemas, Verified Builds

* Define cross-language **ABIs** and **serialization schemas**
* Generate **C headers**, **JSON schemas**, or **verifiable binary layouts**
* Serve as a **formal specification layer** for deterministic builds and releases
* Extend with templates, attributes, and metadata for domain-specific schemas
* Integrate with **reproducible build** pipelines or **formal proof systems**

---

## License

* **Documentation, specifications, and diagrams:** [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)
* **Code and grammars:** [Business Source License 1.1](https://mariadb.com/bsl11/)
  *(Changes to Apache 2.0 on 2028-11-03)*

Only materials explicitly published in this repository are covered by these licenses.
Unpublished or private works remain proprietary unless otherwise indicated.

**Contact:** Lloyd (`nklzero`) — [lloyd@nukli.zone](mailto:lloyd@nukli.zone)

---

## GitHub Topics

`deterministic-language` · `c-abi` · `reproducible-builds` · `idl` · `schema-language` · `cross-language` · `verification` · `type-system` · `serialization` · `nukli` · `meta-architecture`
