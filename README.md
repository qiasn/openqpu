# OpenQPU

## An Open Architecture for Quantum Processing

**OpenQPU is an open quantum-processing architecture inspired by the role that RISC-V plays in classical computing.**

Rather than defining one particular quantum processor, OpenQPU seeks to define open abstractions, interfaces, logical models, control semantics, and implementation profiles through which multiple quantum technologies can coexist and evolve.

The goal is simple:

> **Open architecture. Multiple physical implementations. No required dependence on a single QPU technology or vendor.**

OpenQPU is licensed under the **Apache License 2.0**.

---

## Why OpenQPU?

Quantum processors are being developed using very different physical technologies, including superconducting circuits, silicon spins, quantum defects, trapped ions, photonics, and other emerging approaches.

These technologies differ substantially in:

* physical qubits and qudits;
* operating temperature;
* control mechanisms;
* initialization and readout;
* coherence;
* coupling;
* fabrication;
* error management; and
* scaling strategy.

OpenQPU attempts to place an open architectural boundary above these differences.

Conceptually:

```text
             Applications
                  |
                  v
        +-------------------+
        |      OpenQPU      |
        | Logical Model     |
        | ISA / QIR         |
        | Control Semantics |
        | Mapping           |
        | Interfaces        |
        +---------+---------+
                  |
        Open Physical Interface
                  |
       +----------+----------+----------+
       |          |          |          |
       v          v          v          v
    Defect     Silicon    Quadrupolar  Future
     QPU        Spin         QPU        QPU
       |          |          |          |
       +----------+----------+----------+
                  |
             Physical
          Qubits / Qudits
```

The architecture should remain useful even as the underlying quantum technology changes.

---

## Logical and Physical Quantum Resources

OpenQPU explicitly separates **logical quantum resources** from their physical realization.

At the architecture level, OpenQPU may describe:

* logical qubits;
* logical qudits;
* quantum operations;
* measurement;
* logical-to-physical mapping;
* error-management abstractions;
* scheduling; and
* control interfaces.

At the implementation level, a particular QPU determines how those abstractions are realized using physical states and devices.

This allows, for example, the same logical operation to be mapped onto very different physical technologies.

OpenQPU is also intentionally **qudit-aware**. Physical systems providing more than two useful quantum states need not automatically be reduced to a two-state qubit abstraction.

---

## Reference Physical Implementations

OpenQPU encourages multiple independent implementations.

A reference implementation demonstrates the architecture; it does **not** define the architecture.

### Open Defect-Qudit (ODQ)

The first OpenQPU reference research direction is **Open Defect-Qudit (ODQ)**.

ODQ investigates solid-state quantum defects as a path toward small, high-temperature, and potentially edge-deployable quantum processors.

The initial roadmap includes:

**ODQ-0 — Diamond NV**

A reference profile based on nitrogen-vacancy centers in diamond and publicly demonstrated room-temperature defect-spin quantum technology.

**ODQ-1 — Silicon-Carbide Defects**

Exploration of semiconductor-compatible quantum defects, including multi-level spin systems potentially suitable for physical qudits.

**ODQ-2 — Engineered Quantum Defects**

Longer-term investigation of computationally and AI-assisted design of quantum defects optimized for temperature, coherence, controllability, manufacturability, and specialized quantum workloads.

See:

`implementations/odq-reference/README.md`

and

`implementations/odq-reference/whitepaper.md`

for the ODQ reference architecture and research roadmap.

---

## Other Implementations

OpenQPU is not restricted to ODQ.

Potential implementation families include:

```text
implementations/
|
+-- odq-reference/
|   +-- diamond-nv/
|   +-- silicon-carbide/
|
+-- silicon-spin/
|
+-- diamond-quadrupolar/
|
+-- experimental/
```

Additional physical implementations are encouraged.

A physical implementation may be fully open, partially contributed, independently developed, commercially supplied, or subject to separate intellectual-property rights, provided that its relationship to OpenQPU is clearly documented.

---

## What Does "Open" Mean?

**OpenQPU refers to the openness of the OpenQPU architecture and materials actually contributed under the project's open-source license.**

It does **not** mean that every physical technology capable of implementing OpenQPU is necessarily free of patents or other third-party intellectual-property rights.

This distinction is intentional.

OpenQPU should be capable of supporting:

* open reference hardware;
* university research implementations;
* patented technologies;
* commercial QPU components;
* proprietary fabrication processes;
* open controllers and RTL;
* commercial development tools; and
* future physical technologies.

Open interfaces allow these technologies to participate without requiring OpenQPU to become dependent upon any one of them.

Contributors should consult the repository's licensing and patent documentation before contributing patent-sensitive technology.

---

## Evidence Matters

OpenQPU distinguishes demonstrated science from engineering proposals and research hypotheses.

Technical material may use the following classifications:

**DEM — Demonstrated**

Supported by published experiments or established technology.

**ENG — Engineering**

An OpenQPU engineering design or integration based upon established principles but not necessarily demonstrated as a complete physical system.

**HYP — Hypothesis**

A proposed technology, mechanism, architecture, or performance objective requiring experimental validation.

This distinction is particularly important for AI-assisted quantum hardware design.

---

## OpenQPU Is Not SLU

OpenQPU and the **Safety Logic Unit (SLU)** are independent projects.

OpenQPU is a general quantum-processing architecture.

SLU is a safety architecture.

A future **QSLU** may use OpenQPU as a quantum accelerator:

```text
        Safety Logic Unit
               |
               v
              QSLU
               |
               v
        OpenQPU Interface
               |
               v
       Compatible QPU
```

However:

> **OpenQPU does not depend on SLU, and SLU does not depend on OpenQPU.**

OpenQPU may support applications in optimization, sensing, simulation, materials, control, safety, and other areas that have no relationship to SLU.

---

## Repository Organization

The intended repository structure separates architecture from implementation:

```text
openqpu/
|
+-- architecture/
|   +-- specification/
|   +-- logical-model/
|   +-- interfaces/
|   +-- isa/
|   +-- qir/
|   +-- control/
|   +-- mapping/
|   +-- error-correction/
|   +-- verification/
|
+-- implementations/
|   +-- odq-reference/
|   +-- silicon-spin/
|   +-- diamond-quadrupolar/
|   +-- experimental/
|
+-- reference-platform/
|
+-- examples/
|
+-- docs/
|
+-- LICENSE
+-- NOTICE
+-- PATENTS.md
+-- README.md
```

The directory structure will evolve as the architecture matures.

---

## Design Principle

The central architectural rule of OpenQPU is:

> **Nothing in the core OpenQPU architecture should require knowledge of whether the physical processor underneath it is implemented using diamond defects, silicon spins, quadrupolar states, superconducting circuits, trapped ions, photons, or a technology that has not yet been invented.**

Physical implementations may evolve rapidly.

The architectural contract should endure longer.

---

## Research Direction

OpenQPU is particularly interested in the engineering question:

> **What is the minimum manufacturable quantum system capable of performing a useful quantum workload reliably at the highest practical operating temperature, lowest practical power, and lowest practical deployment cost?**

This question complements—but is different from—the pursuit of very large general-purpose fault-tolerant quantum computers.

OpenQPU therefore welcomes research into both conventional QPU architectures and smaller specialized quantum accelerators.

---

## Contributing

OpenQPU welcomes participation from:

* quantum physicists;
* semiconductor and device engineers;
* FPGA and RTL developers;
* EDA developers;
* materials researchers;
* quantum algorithm researchers;
* universities and research laboratories;
* QPU and control-hardware vendors;
* open-source developers; and
* researchers exploring new physical implementations.

Contributions should clearly distinguish demonstrated results from proposed engineering and experimental hypotheses.

Alternative implementations are not only permitted—they are a fundamental objective of OpenQPU.

---

## License

OpenQPU is released under the **Apache License, Version 2.0**.

See `LICENSE` for the complete license terms.

Third-party components, compatible commercial technologies, and separately patented implementations may be subject to additional terms as documented by their respective owners.

---

## Project Philosophy

OpenQPU is not an attempt to predict which quantum technology will ultimately win.

It is an attempt to make that prediction unnecessary.

> **Keep the architecture open.
> Let implementations compete.
> Let experimental evidence decide.**
