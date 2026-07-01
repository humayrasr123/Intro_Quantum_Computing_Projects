# Intro to Quantum Computing Projects

**Course:** CS 4540 — Introduction to Quantum Computing
**Author:** Humayra Rashid

## 📖 Overview

This repository contains a collection of projects completed for my Introduction to Quantum Computing course, built using **Qiskit** and executed on both local simulators and real **IBM Quantum hardware**. Each project builds on core quantum computing concepts — starting from a simple two-qubit entangled state, scaling up to a 100-qubit entangled system on real hardware, and finally implementing a foundational quantum algorithm that demonstrates provable speedup over classical computation.

Together, these projects reflect a progression through the fundamentals of quantum circuits, entanglement, hardware execution, noise, and quantum algorithms.

## 🗂️ Projects

### [Project 1 — Bell State Entanglement](./Project_1)
A "Hello World" introduction to Qiskit: building a 2-qubit circuit to generate a **Bell state** and measuring expectation values across a set of Pauli operators to confirm entanglement.

### [Project 2 — n-Qubit GHZ State on IBM Hardware](./Project_2)
Extending the Bell state idea to a **100-qubit GHZ (Greenberger–Horne–Zeilinger) state**, transpiled and executed on two real IBM Quantum backends (`ibm_torino` and `ibm_marrakesh`), comparing how correlation decays with qubit distance due to hardware noise.

### [Project 3 — The Deutsch–Jozsa Algorithm](./Project_3)
Implementing the **Deutsch–Jozsa algorithm**, one of the first quantum algorithms to show exponential speedup over classical computation. Includes oracle construction, simulation, and execution on real IBM hardware (`ibm_fez`), comparing simulator vs. hardware results.

## 🛠️ Tech Stack

- **Qiskit** & **Qiskit Aer** — circuit construction and simulation
- **IBM Quantum** — real hardware execution (`ibm_torino`, `ibm_marrakesh`, `ibm_fez`)
- **Python** (Jupyter Notebooks)
- **Matplotlib** — result visualization

## 🧠 What This Repo Demonstrates

- Building and visualizing quantum circuits from the ground up
- Understanding and generating multi-qubit entanglement (Bell and GHZ states)
- Working with quantum primitives (`Estimator`) to compute expectation values
- Transpiling circuits for specific quantum hardware
- Running circuits on real IBM Quantum backends and comparing them to ideal simulation
- Understanding the real-world impact of noise, decoherence, and gate errors on quantum results
- Implementing a foundational quantum algorithm (Deutsch–Jozsa) and analyzing its theoretical vs. real-world performance

## 📁 Structure

```
Intro_Quantum_Computing_Projects/
├── README.md                 ← you are here
├── Project_1/
│   ├── README.md
│   └── proj1_summary_Humayra_Rashid.{ipynb, pdf}
├── Project_2/
│   ├── README.md
│   └── proj2_hello_GHZ_Rashid.ipynb, proj2_summary_Rashid.pdf
└── Project_3/
    ├── README.md
    └── project3-deutsch-jozsa-algorithm.ipynb, proj3_report_Rashid.pdf
```
