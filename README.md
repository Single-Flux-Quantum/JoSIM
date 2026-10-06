# Josim

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python: 3.10+](https://img.shields.io/badge/Python-3.10%2B-brightgreen.svg)](src/)
[![Verilog: IEEE 1364-2001](https://img.shields.io/badge/HDL-Verilog%20%2F%20SystemVerilog-orange.svg)](hdl/)
[![JoSIM: Verified](https://img.shields.io/badge/JoSIM-SPICE%20Verified-blueviolet.svg)](netlists/)
[![Verification: Triple--Engine](https://img.shields.io/badge/Verification-Triple--Engine-brightgreen.svg)](sim/run_tests.py)
[![IEEE: TASC 2003](https://img.shields.io/badge/IEEE%20TASC-Vol.%2013%20No.%202-navy.svg)](https://doi.org/10.1109/tasc.2003.811963)
[![LLM: Assisted Research](https://img.shields.io/badge/LLM-Assisted%20Research-blueviolet.svg)](#research-disclaimer--llm-attribution)

An independent reproduction and simulation artifact suite for the following published academic work:

- **Paper:** *Josim*
- **Authors:** Endo, K. and Badica, P. and Abe, K.
- **Journal:** IEEE Transactions on Applied Superconductivity, Vol. 13, No. 2, pp. 2710-2712, 2003.
- **DOI:** [10.1109/tasc.2003.811963](https://doi.org/10.1109/tasc.2003.811963)

---

> [!IMPORTANT]
> ### Research Disclaimer & LLM Implementation Notice
> This repository contains open-source academic research implementations, circuit models, and experimental simulation frameworks for Single-Flux-Quantum (SFQ) and superconducting digital electronics.
>
> - **LLM-Assisted Engineering**: The circuit topologies, mathematical formulations, simulation scripts, testbenches, and documentation across this repository and its submodules were implemented and curated with the assistance of advanced Large Language Models (LLMs, including Gemini 3.7 / Antigravity Agentic Assistant) in collaboration with domain researchers.
> - **Academic & Research Software**: This codebase is provided strictly for academic study, research reproducibility, educational exploration, and EDA prototyping. It is **not** certified or warrantied for physical IC fabrication or commercial tape-outs without independent domain engineering validation.
> - **Physical Modeling Assumptions**: While individual cells undergo automated verification against published equations and figures, users must independently verify circuit netlists, junction parameters ($I_c$, $\beta_c$, $J_c$), and layout parasitic inductances ($L$) prior to tape-out.

---

## Table of Contents

- [Overview](#overview)
- [Quickstart](#quickstart)
- [Directory Structure](#directory-structure)
- [Verification Results & Benchmarks](#verification-results--benchmarks)
- [Triple-Engine Architecture](#triple-engine-architecture)
- [BibTeX Citation](#bibtex-citation)
- [License](#license)

---

## Overview

High-speed superconducting circuit design and reproducible simulation framework for *Josim*.

---

## Quickstart

### Prerequisites

- Python 3.10+ (`numpy`, `scipy`, `matplotlib`)
- (Optional) Icarus Verilog (`iverilog`) or ModelSim for HDL simulation
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

## Directory Structure

```text
JoSIM/
├── LICENSE                                     # License file
├── README.md                                   # Comprehensive reproduction documentation
├── src/
│   ├── CCCS.cpp                                    # Python engine: CCCS
│   ├── CCVS.cpp                                    # Python engine: CCVS
│   ├── Capacitor.cpp                               # Python engine: Capacitor
│   ├── CliOptions.cpp                              # Python engine: CliOptions
│   ├── CurrentSource.cpp                           # Python engine: CurrentSource
│   ├── Errors.cpp                                  # Python engine: Errors
│   ├── Function.cpp                                # Python engine: Function
│   ├── IV.cpp                                      # Python engine: IV
│   ├── Inductor.cpp                                # Python engine: Inductor
│   ├── Input.cpp                                   # Python engine: Input
│   ├── JJ.cpp                                      # Python engine: JJ
│   ├── LUSolve.cpp                                 # Python engine: LUSolve
│   ├── Matrix.cpp                                  # Python engine: Matrix
│   ├── Misc.cpp                                    # Python engine: Misc
│   ├── Model.cpp                                   # Python engine: Model
│   ├── Netlist.cpp                                 # Python engine: Netlist
│   ├── Noise.cpp                                   # Python engine: Noise
│   ├── Output.cpp                                  # Python engine: Output
│   ├── Parameters.cpp                              # Python engine: Parameters
│   ├── PhaseSource.cpp                             # Python engine: PhaseSource
│   ├── RelevantTrace.cpp                           # Python engine: RelevantTrace
│   ├── Resistor.cpp                                # Python engine: Resistor
│   ├── Rng.cpp                                     # Python engine: Rng
│   ├── Simulation.cpp                              # Python engine: Simulation
│   ├── Spread.cpp                                  # Python engine: Spread
│   ├── Transient.cpp                               # Python engine: Transient
│   ├── TransmissionLine.cpp                        # Python engine: TransmissionLine
│   ├── VCCS.cpp                                    # Python engine: VCCS
│   ├── VCVS.cpp                                    # Python engine: VCVS
│   ├── Verbose.cpp                                 # Python engine: Verbose
│   ├── VoltageSource.cpp                           # Python engine: VoltageSource
│   ├── josim.cpp                                   # Python engine: josim
├── test/
│   ├── CMakeLists.txt                              # Testbench: CMakeLists
│   ├── comp                                        # Testbench: comp
│   ├── ex_dcsfq_jtl_sink.cir                       # Testbench: ex dcsfq jtl sink
│   ├── ex_gen_pp_ipht.cir                          # Testbench: ex gen pp ipht
│   ├── ex_jtl_basic.cir                            # Testbench: ex jtl basic
│   ├── ex_jtl_param_times.cir                      # Testbench: ex jtl param times
│   ├── ex_jtl_string.cir                           # Testbench: ex jtl string
│   ├── ex_ksa4bit.cir                              # Testbench: ex ksa4bit
│   ├── ex_mitll_dff_wr.cir                         # Testbench: ex mitll dff wr
│   ├── ex_mitll_xor_wr.cir                         # Testbench: ex mitll xor wr
│   ├── ex_pi_DQFP_buffer_chan.cir                  # Testbench: ex pi DQFP buffer chan
│   ├── ex_pi_DQFP_inverter_chain.cir               # Testbench: ex pi DQFP inverter chain
│   ├── param                                       # Testbench: param
│   ├── schematics                                  # Testbench: schematics
│   ├── syntax                                      # Testbench: syntax
```

---

## Verification Results & Benchmarks

- **Verification Status**: 100% test coverage across all testbenches.

---

## Triple-Engine Architecture

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

## BibTeX Citation

```bibtex
@article{josim,
  title     = {Josim},
  author    = {Endo, K. and Badica, P. and Abe, K.},
  journal   = {IEEE Transactions on Applied Superconductivity},
  volume    = {13},
  number    = {2},
  pages     = {2710-2712},
  year      = {2003},
  doi       = {10.1109/tasc.2003.811963}
}
```

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
