# Project 3 — The Deutsch–Jozsa Algorithm

**Course:** CS 4540 — Introduction to Quantum Computing
**Author:** Humayra Rashid

## 🎯 Introduction

The **Deutsch–Jozsa algorithm** is one of the first quantum algorithms to demonstrate a provable **exponential speedup** over classical computation. Given a function

```
f: {0,1}ⁿ → {0,1}
```

promised to be either **constant** (same output for every input) or **balanced** (outputs 0 and 1 equally often), the goal is to determine which type it is.

- **Classically**, this requires up to `2^(n-1) + 1` evaluations in the worst case.
- **Quantumly**, the Deutsch–Jozsa algorithm solves it in a **single evaluation** using superposition, quantum parallelism, and interference.

## 🔧 What We Did

- Constructed a quantum oracle for a randomly chosen constant or balanced function
- Implemented the Deutsch–Jozsa algorithm in Qiskit
- Simulated the circuit using Qiskit Aer
- Executed the same circuit on a real IBM Quantum backend (`ibm_fez`)
- Compared simulator vs. hardware results
- Analyzed discrepancies caused by quantum noise

## ⚙️ Oracle Construction

The oracle was generated via `dj_query(num_qubits)`, producing either a constant or balanced function by:
1. Selecting exactly half of the possible input bitstrings
2. "Marking" each selected state by temporarily X-flipping its qubits
3. Applying a multi-controlled X gate targeting the output qubit
4. Uncomputing the X flips to restore the original state
5. Adding barriers for clarity in circuit visualization

## 🔧 Circuit Implementation

Built via `compile_circuit(function)`:
1. Initialize all input qubits to `|0⟩` and the output qubit to `|1⟩` (via an X gate)
2. Apply Hadamard gates to all qubits — placing inputs into uniform superposition and the output qubit into the `|0⟩ − |1⟩` phase state needed for interference
3. Compose the oracle directly into this superposition
4. Apply a final round of Hadamard gates to the input qubits, converting oracle-induced phase differences into measurable basis states
5. Measure the input qubits

**Expected outputs:**
- All-zero output (`000...0`) → function is **constant**
- Any other output → function is **balanced**

## 📊 Results

**Simulator (Qiskit Aer, n = 3):** Result `010` → classified **balanced**, matching the ideal noise-free expectation.

**Hardware (`ibm_fez`, n = 3):** Result `110` → classified **balanced**.

| Backend | Output | Result |
|---|---|---|
| Simulator | 010 | Balanced |
| ibm_fez (hardware) | 110 | Balanced |

## 🔍 Quantum Noise & Discrepancies

Although the exact measured bitstrings differ between the simulator (`010`) and hardware (`110`), the **classification matches perfectly** — both correctly identify the function as balanced. The differing bit values are attributed to real-hardware effects such as gate errors, decoherence, and measurement errors.

## 🧾 Conclusion

This experiment confirms the core insight of the Deutsch–Jozsa algorithm: even in the presence of hardware noise, the quantum circuit preserves the essential information needed to distinguish constant from balanced functions. The theoretical exponential speedup holds, and while noise affects the specific measurement outcome, it does not affect the final classification.

## 📁 Files

- `project3-deutsch-jozsa-algorithm.ipynb` — Jupyter notebook with oracle construction, circuit implementation, simulation, and hardware execution
- `proj3_report_Rashid.pdf` — Written report and results write-up

## 🧠 Key Concepts Learned

- **Deutsch–Jozsa problem** — Determining whether a black-box function is constant or balanced, solvable in one query quantumly vs. exponentially many classically.
- **Quantum oracle** — A black-box circuit encoding a function's behavior as a phase or bit-flip operation on qubits.
- **Superposition & interference** — Hadamard gates place qubits into superposition; interference after the oracle converts hidden phase information into a measurable outcome.
- **Transpilation & hardware execution** — Running circuits on real backends (like `ibm_fez`) introduces gate errors, decoherence, and measurement noise not present in ideal simulation.
