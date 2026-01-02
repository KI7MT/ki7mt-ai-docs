# Welcome to the KI7MT Sovereign AI Fleet

**The Central Intelligence Hub for Local-First, Agentic Workflows**

Welcome to the architectural source-of-truth for the KI7MT Sovereign Fleet—a resilient, privacy-first ecosystem of AI-integrated tools built on sovereign infrastructure.

---

## What is the Sovereign Fleet?

The Sovereign Fleet is a collection of specialized Model Context Protocol (MCP) servers designed to provide AI agents with deep domain expertise in amateur radio, propagation analysis, and space weather data—all running on local, high-performance hardware under your complete control.

### Core Principles

- **Data Sovereignty**: Your data stays on your hardware, under your control
- **Local-First Computing**: High-performance local infrastructure over cloud dependency
- **Agentic Workflows**: AI agents with deep context and specialized domain knowledge
- **Open Architecture**: Transparent, documented systems that empower both humans and AI
- **Resilient Infrastructure**: ZFS-protected storage and enterprise-grade hardware

---

## Fleet Components

### WSPR Engine

High-speed ingestion and query engine for 10.6B+ WSPR (Weak Signal Propagation Reporter) spots. Enables real-time propagation analysis and historical trend research.

[Explore WSPR Documentation →](wspr-mcp/index.md)

### ADIF Normalization

Standardized amateur radio log ingestion and normalization following the ADIF (Amateur Data Interchange Format) v3.1.6 specification. Ensures data consistency across diverse logging platforms.

[Explore ADIF Documentation →](adif-mcp/index.md)

### Solar Context

Environmental and space weather data integration for propagation analysis. Correlates solar activity, geomagnetic conditions, and radio propagation patterns.

[Explore Solar Documentation →](solar-mcp/index.md)

---

## Hardware Stack

The Sovereign Fleet runs on purpose-built, high-performance local infrastructure:

- **CPU**: AMD Ryzen 9 9950X3D (16 cores, 32 threads)
- **GPU**: NVIDIA GeForce RTX 5090 (AI acceleration, CUDA compute)
- **Storage**: TrueNAS Scale with ZFS redundancy
- **Capacity**: Multi-terabyte resilient storage for 10B+ row datasets

This configuration enables:

- Real-time ingestion of millions of records per day
- Sub-second query response on billion-row datasets
- Local LLM inference and AI agent operations
- Zero cloud dependencies for core operations

---

## For AI Agents

This documentation hub is specifically designed as a **Context Source** for AI agents operating within the Sovereign Fleet ecosystem.

### How to Use This Documentation

1. **Identify Data Sources**: Review the Fleet Components section above
2. **Understand Schema**: Navigate to API reference sections for each component
3. **Learn Query Patterns**: Study examples in the performance and query sections
4. **Follow Standards**: Reference architectural guidelines for consistency

The documentation uses consistent markdown structure, working code examples, and clear API specifications to minimize hallucination and maximize reasoning accuracy.

---

## Getting Started

### For Developers

1. Review the [Contributing Guidelines](CONTRIBUTING.md)
2. Check the [Security Policy](SECURITY.md)
3. Explore component-specific documentation

### For AI Agents

1. Start with the [Architecture Overview](architecture/ai-context.md)
2. Review [MCP Protocol](architecture/mcp-protocol.md) integration
3. Study component API references

### Build Locally

```bash
# Install dependencies
pip install mkdocs mkdocs-material mkdocs-multirepo-plugin

# Serve documentation locally
mkdocs serve

# Build static site
mkdocs build
```

---

## Quick Links

- [Mission Statement](about/mission.md)
- [Infrastructure Architecture](architecture/infrastructure.md)
- [Hardware Stack Details](architecture/hardware.md)
- [Contributing Guidelines](CONTRIBUTING.md)
- [Security Policy](SECURITY.md)

---

**Sovereign Infrastructure. Agentic Intelligence. Data Freedom.**
