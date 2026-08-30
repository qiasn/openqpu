# openqpu
A project of open design like RISC-V but for quantum (non-classical) processing unit

📦 Featured Open-Source Projects

1. `SLU-Core-RTL`
> **Status:** *Initial Architecture Specs Live | Code Release Q4 2026*

The reference Register-Transfer Level (RTL) implementation of the hardware Safety Logic Unit. Designed for deployment on FPGAs and custom ASIC interlocks.

* Key Features:
  * Sub-microsecond state-vector hardware checks.
  * Deterministic $J$-space barrier enforcement.
  * Direct SPI/PCIe interface adapters for classical host processors.
* **Tech Stack:** SystemVerilog, Chisel, CocoTB testbenches.

---

2. `MCP-Interlock-SDK`
> **Status:** *In Active Development*

A reference implementation of the Model Context Protocol (MCP) integrated directly with hardware interlock drivers. Enables LLM agents and autonomous tool pipelines to query hardware safety boundaries before executing tool calls.

* Key Features:
  * Real-time safety validation for agentic tool use.
  * Low-latency JSON-RPC over Unix domain sockets or PCIe.
  * Formal verification hooks for state transitions.
* Tech Stack: Rust, Python, TypeScript.

---

3. `OpenQPU-Sim`
> **Status:** *Early Preview*

A specialized software simulator for modeling Electric Field Gradient (EFG) quadrupolar control of nuclear spin qubits in diamond at room temperature (300 K).

* Key Features:
  * Pulse-level simulation of nuclear quadrupolar resonance (I=1, e.g., ¹⁴N ).
  * Decoherence and strain-gradient noise modeling.
  * Gate fidelity estimation for multi-qubit quadrupolar coupling.
* Tech Stack: Python, C++, Julia.

---

🛠️ How to Contribute & Stay Updated

Whether you are a silicon engineer, an AI safety researcher, or a quantum technologist, we welcome community collaboration.

1. Star & Watch the Repositories: Follow our developments directly on GitHub: `https://github.com/qiasn/openqpu` (Link active upon public repository rollout).
2. Access Web Whitepapers: Explore deep-dive architectural articles, 3D heterogeneous packaging schematics, and fab yield models here on (https://www.qiassoc.org/projects/openqpu).
3. Submit Issues & RFCs: Join the ongoing discussions on Request for Comments (RFC) documents covering the MCP interlock specifications and OpenQPU hardware standards.
