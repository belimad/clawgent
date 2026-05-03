<p align="center">
  <img width="160" alt="Regent Logo" src="https://raw.githubusercontent.com/kalshi-labs/regent/main/assets/regent_glyph.png">
</p>

<h1 align="center">✨ Regent-Core v2.1: The Probabilistic Logic Layer</h1>
<p align="center"><strong>Formal Entropy Reduction for Regulated Prediction Markets.</strong></p>

---

## 🤖 The "AGI" Body

Regent-Core is a deterministic truth-synthesis engine disguised as a general intelligence. It maps raw data into formal logic proofs ($P \to \{0, 1\}$), treating the real world as a noisy signal waiting to be compressed into a binary market settlement.

### 1. Updating
Instead of crude binary scraping, Regent maintains a continuous belief state. It continuously refines its confidence in an outcome ($H$) as evidence ($E$) arrives:

$$P(H|E) = \frac{P(E|H) \cdot P(H)}{P(E)}$$

### 2. Integrity
To ensure strict regulatory compliance, price action is modeled as a discrete-time Martingale. Settlement invariants are strictly preserved:

$$\mathbb{E}[X_{n+1} \mid X_1, \dots, X_n] = X_n$$

If an unauthorized drift is detected without a high-confidence data signal, the engine halts state transitions immediately.

### 3. Entropy 
To resolve discrepancies between sources, Regent calculates the Kullback–Leibler (KL) Divergence across data providers. High divergence triggers recursive validation; low divergence triggers sub-millisecond settlement.

---

## 🧬 Core Architecture

| Framework | Implementation | Purpose |
| :--- | :--- | :--- |
| **Measure Theory** | Lebesgue Integration | Resolving continuous outcome spaces. |
| **Stochastic Calculus** | Ito's Lemma | Modeling volatility decay in long-tail event contracts. |
| **Concentration Bounds** | Chernoff/Hoeffding | Quantifying risk of concurrent source failure. |
| **Algorithmic Prob.** | Kolmogorov Complexity | Minimizing evidence payloads for ZK-proofs. |

---

## 🛠️ Technical Arrangement

* **Z3 SMT Solver:** Formal verification of probabilistic logic chains.
* **Rust (Rayon & Tokio):** Parallelizing measure-concentration algorithms.
* **NATS JetStream:** Low-latency (<5ms) Markov state propagation.
* **gRPC / Protobuf:** Strictly typed schemas for all random variables.

---

## 📲 Integration

### Bayesian Execution Loop

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
