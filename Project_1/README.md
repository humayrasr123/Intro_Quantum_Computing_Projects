# Project 1 — Bell State Entanglement with Qiskit

**Course:** CS 4540 — Introduction to Quantum Computing
**Author:** Humayra Rashid

## 📝 Summary

A "Hello World" style project in Qiskit demonstrating the creation and analysis of the 2-qubit **Bell state**. The goal was to build a simple circuit that generates quantum entanglement and measure expectation values for a set of Pauli operators.

## ⚙️ Environment

```
python:      3.12.4 (Anaconda)
qiskit:      2.2.1
qiskit_aer:  0.17.2
```

## 🔧 Procedure

1. **Setup** — Imported Qiskit and Qiskit Aer, and printed library versions to confirm the environment.
2. **Circuit construction** — Built a 2-qubit circuit: a Hadamard gate (`H`) on qubit 0, followed by a CNOT gate (`0 → 1`), and visualized the circuit diagram.
3. **Expectation values** — Defined six Pauli observables (`ZZ`, `ZI`, `IZ`, `XX`, `XI`, `IX`) and used Qiskit Aer's `Estimator` primitive to compute their expectation values on the resulting state.
4. **Visualization** — Plotted the expectation values across all six observables to visually confirm entanglement.

## 📊 Results

| Observable | Expected | Observed |
|---|---|---|
| ZZ | 1 | 1.000 |
| XX | 1 | 1.000 |
| ZI | 0 | 0.021 |
| IZ | 0 | 0.021 |
| XI | 0 | -0.033 |
| IX | 0 | -0.033 |

The observed values closely matched the expected values (`ZZ ≈ 1`, `XX ≈ 1`, all others ≈ 0), confirming successful entanglement between the two qubits.

## 📁 Files

- `proj1_summary_Humayra_Rashid.ipynb` — Jupyter notebook with the full implementation and outputs
- `proj1_summary_Humayra_Rashid.pdf` — Written summary and results write-up

## 🧠 Key Concepts Learned

- **Bell state** — A two-qubit entangled state where the measurement outcome of one qubit is directly correlated with the other; created via a Hadamard gate followed by a CNOT gate.
- **Hadamard gate (H)** — Single-qubit gate that creates superposition by mapping basis states to equal superpositions.
- **CNOT gate** — Two-qubit gate that creates entanglement by flipping the target qubit when the control qubit is `|1⟩`; the quantum analog of a classical XOR.
- **Pauli gates** — Single-qubit operations (`X`, `Y`, `Z`) that form the basis for defining observables.
- **Primitives** — Standardized, pre-built Qiskit functions (like `Estimator`) that simplify and standardize common quantum computing tasks.
- **Observables** — Quantities (like `ZZ`, `XX`, etc.) measured to characterize a quantum state's behavior.
- **Estimator** — Runs a circuit, measures a given observable across many simulations, and returns its expectation value.
- **Qiskit Aer vs. QPU** — Aer simulates quantum circuits on classical hardware (fast, noise-free); a QPU is a real quantum processor (introduces real-world noise and decoherence, but reflects true quantum hardware behavior).
