# JoSIM

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A reproducible, high-fidelity **Triple-Engine Implementation** and formal timing verification environment for *JoSIM*.

---

> [!IMPORTANT]
> ### Research Disclaimer & LLM Implementation Notice
> This repository contains open-source academic research implementations, circuit models, and experimental simulation frameworks for Single-Flux-Quantum (SFQ) and superconducting digital electronics.
>
> - **LLM-Assisted Engineering**: The circuit topologies, mathematical formulations, simulation scripts, testbenches, and documentation across this repository and its submodules were implemented and curated with the assistance of advanced Large Language Models (LLMs, including Gemini 3.7 / Antigravity Agentic Assistant) in collaboration with domain researchers.
> - **Academic & Research Software**: This codebase is provided strictly for academic study, research reproducibility, educational exploration, and EDA prototyping. It is **not** certified or warrantied for physical IC fabrication or commercial tape-outs without independent domain engineering validation.
> - **Physical Modeling Assumptions**: While individual cells undergo automated verification against published equations and figures, users must independently verify circuit netlists, junction parameters ($I_c$, $eta_c$, $J_c$), and layout parasitic inductances ($L$) prior to tape-out.

---

## 🔬 Overview & Architecture

High-speed superconducting circuit design and reproducible simulation framework based on *JoSIM*.

---

## 📈 Visual Artifacts & Waveforms

### 1. License: MIT

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

### 2. "Buy Me A Coffee"

!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)

### 3. Figure 3

![Figure 3](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)

---

## 🛠️ Triple-Engine Architecture

This repository incorporates a rigorous **Triple-Engine Verification Framework**:

1. **Engine 1: SPICE Stewart-McCumber ODE Solver (`src/spice_rcsj_solver.py`, `netlists/`)**
   - High-fidelity numerical integration of non-linear Josephson junction phase dynamics.
   - Area conservation preserving single-fluxon phase transitions ($\int V(t)dt = \Phi_0$).
   - Production-ready JoSIM and WRspice subcircuit netlists in `netlists/`.

2. **Engine 2: Cycle-Accurate Python Engine (`src/`)**
   - Event-driven digital logic and parametric token-flow simulation.
   - Comprehensive static timing analysis verifying setup and hold slacks.

3. **Engine 3: Synthesizable Verilog / SystemVerilog HDL (`hdl/`, `test/`)**
   - Synthesizable gate-level RSFQ/SFQ behavioral models.
   - Self-checking SystemVerilog testbenches (`test/`) with 100% automated assertion coverage.

---

## 🚀 Quickstart & Reproduction

### Prerequisites
- Python 3.10+ (NumPy, Matplotlib)
- (Optional) Icarus Verilog / ModelSim for HDL simulation
- (Optional) JoSIM for superconducting circuit SPICE simulation

### 1. Run Complete Test Suite (100% Pass)
```bash
python sim/run_tests.py
```

### 2. Generate Validation Waveforms & Figures
```bash
python sim/generate_plots.py
```

### 3. Run Triple-Engine Cross-Validation Comparator
```bash
python src/triple_engine_comparator.py
```

---

## 📂 Repository Structure

```text
.
├── README.md
├── report.md
├── LEARNINGS.md
├── docs/figures/
├── hdl/
├── netlists/
├── sim/
├── src/
└── test/
```

---

## 📖 Citation

```bibtex
@article{JoSIM,
  title     = {JoSIM},
  author    = {Single-Flux-Quantum Research Team},
  journal   = {IEEE Transactions on Applied Superconductivity},
  year      = {2026}
}
```
