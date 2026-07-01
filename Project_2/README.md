# Project 2 — Extending Hello World to an n-Qubit GHZ State

**Course:** CS 4540 — Introduction to Quantum Computing
**Author:** Humayra Rashid

## 🎯 Project Goal

Prepare and analyze an **n-qubit GHZ (Greenberger–Horne–Zeilinger) state** using Qiskit, then run it on **real IBM Quantum hardware**. GHZ states help demonstrate the limits of quantum entanglement and reveal correlations across qubits that cannot be explained classically.

## 🔧 Approach

1. **Circuit construction** — Built the GHZ circuit by applying a Hadamard gate to the first qubit (creating superposition), followed by a chain of CNOT gates entangling each subsequent qubit with the first. Circuit was scaled to **n = 100 qubits**.
2. **Operator analysis** — Measured `ZZ` correlation operators across qubit pairs to observe how expectation values degrade with increasing noise.
3. **Transpilation** — Adapted the circuit to two real IBM backends:
   - `ibm_torino` — 133 qubits
   - `ibm_marrakesh` — 156 qubits

   Transpilation reshapes a circuit to match a specific device's native gate set and qubit connectivity, reducing gate errors and circuit depth.
4. **Hardware execution** — Checked available backends (`ibm_fez`, `ibm_torino`, `ibm_marrakesh`), then ran the 100-qubit GHZ circuit on each and plotted the resulting ⟨Z₀Zᵢ⟩ correlation values against qubit distance.

## 📊 Expected vs. Observed Results

**Expected:** In an ideal GHZ state, all qubits are fully correlated — the `ZZ` expectation value should stay close to **1** for any qubit pair, regardless of distance.

**Observed:**
- **`ibm_torino`** — Strong short-range correlation near the reference qubit (~1.0), decaying quickly toward 0 as distance increases.
- **`ibm_marrakesh`** — Similar decay pattern, but smoother and with slightly higher correlation retained at longer distances.

| Backend | Qubits | Correlation Behavior |
|---|---|---|
| ibm_torino | 133 | Fast decay, more noise past ~20 qubits |
| ibm_marrakesh | 156 | Smoother decay, better long-range coherence |

## 🧾 Conclusion

Both backends started with ⟨Z₀Zᵢ⟩ values near 1 close to the reference qubit, confirming strong short-range entanglement. As qubit distance grew, correlations decayed toward zero beyond ~20 qubits, driven by hardware noise and decoherence inherent to large-scale quantum systems. `ibm_marrakesh` showed modestly better coherence over longer distances than `ibm_torino`, suggesting more stable qubit coupling, better calibration, and lower error rates.

## 📁 Files

- `proj2_hello_GHZ_Rashid.ipynb` — Jupyter notebook with circuit construction, transpilation, and hardware execution
- `proj2_summary_Rashid.pdf` — Written summary and results write-up

## 🧠 Key Concepts Learned

- **GHZ state** — A maximally entangled multi-qubit state where all qubits share a single joint superposition; used to probe the limits of quantum correlation across a system.
- **Transpilation** — The process of converting a quantum circuit into a hardware-specific form, adapting to the device's native gate set and qubit connectivity to reduce circuit depth, gate errors, and noise.
- **Dynamic decoupling** — A noise-mitigation technique that inserts carefully timed pulse sequences during idle qubit periods to suppress decoherence and phase errors.
- **Qubit connectivity & noise** — Real quantum hardware has limited qubit-to-qubit connections and inherent noise, both of which degrade long-range correlations compared to an ideal simulator.
