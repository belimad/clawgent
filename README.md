<p align="center">
  <img width="208" alt="Lyra Logo" src="https://raw.githubusercontent.com/kalshi-labs/lyra/main/assets/lyra_glyph.png">
</p>

<h1 align="center">✨ Lyra-Core v2.1</h1>
<p align="center"><strong>High-throughput deterministic truth synthesis for Kalshi.</strong></p>

<p align="center">
  A distributed, low-latency execution layer for autonomous event-settlement and Bayesian truth-verification in regulated prediction markets.
</p>

---

## Overview

**Lyra** is a specialized, local-first settlement engine designed for the **Kalshi** ecosystem. It is engineered for developers who require sub-millisecond data triangulation and deterministic market resolution without the overhead of centralized oracular consensus.

Instead of relying on singular, fallible API endpoints, Lyra utilizes a **State-Space Search** model to map real-world entropy into binary finality ($S \to \{0, 1\}$). It collapses the infrastructure burden of event verification into a lightweight, high-performance runtime optimized for cold-start investigation and zero-trust auditability.

It is intended for environments where you want:

- **Autonomous Settlement** without manual intervention or human-in-the-loop latency.
- **Multi-Vector Triangulation** across disjoint datasets (IoT, SEC, NOAA, Web).
- **Sub-500ms Resolution** from event expiry to capital liberation.
- **Formal Verification** of settlement logic against contract specifications.

---

## System Overview

Lyra acts as a compact, concurrent runtime for truth-seeking agents. It reduces the operational complexity of the broader oracle stack by condensing investigation, synthesis, and cryptographic signing into a single, performance-tuned environment.

The project emphasizes:

- **Non-Blocking I/O** utilizing `io_uring` for massive parallel data ingestion.
- **Bayesian Updating** for generating high-confidence settlement scores.
- **LLM-Augmented Reasoning** for parsing complex legislative or regulatory text.
- **Minimal Operational Footprint** compared to full cloud-based oracle networks.

This makes it indispensable for high-frequency prediction trading, automated market making, and developers building the next generation of regulated risk-management tools.

---

## Key Features

- **Deterministic Logic Engine** Uses Z3 SMT solvers to ensure settlement decisions strictly adhere to contract invariants.

- **Recursive Source Validation (RSV)** Eliminates single-point-of-failure by cross-referencing $N$ independent data streams.

- **High-Concurrency Ingress** Optimized Rust-based ingestors for real-time WebSocket and gRPC feed processing.

- **Explainable Evidence Bundles** Generates immutable, cryptographically signed snapshots of the data state at $t_0$.

- **Zero-Trust Finality** Built-in support for ZK-proofs to verify data retrieval without compromising source integrity.

---

## Technology Stack

- **Rust** Core runtime implemented for memory safety, SIMD-accelerated parsing, and zero-cost abstractions.

- **vLLM / TensorRT** Local inference engine for high-speed contextual reasoning on unstructured data.

- **NATS JetStream** Lightweight, distributed messaging for ultra-low latency inter-agent communication.

- **DragonflyDB** Multi-threaded, in-memory state storage for real-time market-state tracking.

---

## Use Cases

Lyra is a good fit for:

- Local development of proprietary settlement bots.
- Automated liquidity provision in "long-tail" or niche markets.
- Real-time hedging of physical-world risks (weather, policy, economics).
- High-frequency arbitrage between disjoint prediction venues.
- Research into automated regulatory compliance and CFTC-grade auditing.

---

## Quick Start

### 1. Clone the repository

```bash
git clone [https://github.com/kalshi-labs/lyra.git](https://github.com/kalshi-labs/lyra.git)
cd lyra
