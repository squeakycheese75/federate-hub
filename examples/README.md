# 🧪 Federate CLI Examples

This directory contains runnable examples for using the [`federate`](../README.md) CLI tool with various types of plans and data sources.

Each folder contains:
- A `plan.yaml` file (or `.json`) describing the connectors and datasets
- Optional seed SQL files or CSVs
- Instructions in a local `README.md`

---

## 🔰 Getting Started

Use these to get a feel for how the CLI works.

- [`quickstart/`](./quickstart) – Minimal plan using a local CSV file and SQLite storage

Run with:

```bash
federate run --plan examples/quickstart/plan.yaml