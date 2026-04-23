<p align="center">
  <img width="208" alt="Regent Logo" src="https://raw.githubusercontent.com/kalshi-labs/regent/main/assets/regent_glyph.png">
</p>

<h1 align="center">✨ Regent-Core v2.1: Probabilistic Logic Layer</h1>
<p align="center"><strong>Formal Entropy Reduction for Regulated Prediction Markets.</strong></p>

---

## 🏗️ Theoretical Architecture

Regent-Core doesn't just "fetch data"; it builds a formal proof of reality. The system operates at the intersection of **Measure Theory** and **Bayesian Inference**, treating every data point as a signal meant to collapse a probability distribution into a binary settlement.

### 1. Bayesian Truth Synthesis
Instead of binary "True/False" ingestion, Regent maintains a continuous belief state. It utilizes **Bayesian Updating** to refine market outcomes as evidence ($E$) arrives from disjoint sources.

$$P(H|E) = \frac{P(E|H) \cdot P(H)}{P(E)}$$

- **P(H):** The prior probability (the market price at $t_{-1}$).
- **P(E|H):** The likelihood of seeing this specific data if the event is true.
- **P(H|E):** The posterior probability—Regent's updated confidence score.

### 2. Martingales & Market Integrity
To maintain Kalshi's regulatory standards, the engine models price action as a **Martingale**. The system assumes that in an efficient market, the conditional expectation of the next value, given all prior observations, is equal to the current value.

> **Invariant:** $E[X_{n+1} \mid X_1, \dots, X_n] = X_n$

If the settlement engine detects a "Non-Martingale" jump that isn't backed by high-confidence data ingestion, Regent triggers a **State-Space Guardrail** to prevent flash-settlement errors.

### 3. Shannon Entropy & Divergence
Regent measures the "cleanliness" of truth through **Information Theory**. When cross-referencing multiple $N$ sources, it calculates the **Kullback–Leibler (KL) Divergence** to quantify disagreement.

- **Low Divergence:** Sources agree; Regent proceeds to high-speed settlement.
- **High Divergence:** Sources conflict; Regent escalates to a **Recursive Source Validation (RSV)** loop to find the "Information Bottleneck."

---

## 🧬 Probability Tooling

| Framework | Implementation | Purpose |
| :--- | :--- | :--- |
| **Measure Theory** | Lebesgue Integration | Handling continuous outcome spaces ($S \in \mathbb{R}$). |
| **Stochastic Calculus** | Ito's Lemma | Modeling volatility decay in long-tail event contracts. |
| **Concentration Bounds** | Chernoff/Hoeffding | Quantifying "Tail Risk" of simultaneous source failure. |
| **Algorithmic Prob.** | Kolmogorov Complexity | Minimizing the "Evidence Bundle" size for ZK-proofs. |

---

## 🛠️ Technical Stack

- **Z3 SMT Solver:** For mapping probabilistic outcomes into **Formal Logic** ($P \to \{0, 1\}$).
- **Rust (Rayon/Tokio):** Parallelizing **Measure-Concentration** calculations across multi-node clusters.
- **NATS JetStream:** Propagating **Markov State** changes with <5ms global propagation.
- **gRPC / Protobuf:** Ensuring strictly typed schemas for all random variables.

---

## 📲 Integration

### Bayesian Update Example (Pseudo-Rust)
```rust
let prior = MarketState::fetch(contract_id);
let evidence = RegentIngestor::triangulate(vec![NOAA_API, REUTERS_FEED]);

// Calculate posterior using KL-Divergence guardrails
let posterior = prior.apply_bayes(evidence)
    .verify_logic_invariants() // Z3 Check
    .map_err(|e| RegentError::EntropyTooHigh(e))?;

if posterior.confidence > 0.9999 {
    Regent::settle(contract_id, posterior.outcome);
}
