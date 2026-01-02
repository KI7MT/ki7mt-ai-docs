# KI7MT Sovereign AI Fleet Documentation

[![Deploy MkDocs](https://github.com/ki7mt/ki7mt-ai-docs/actions/workflows/deploy.yml/badge.svg)](https://github.com/ki7mt/ki7mt-ai-docs/actions/workflows/deploy.yml)
[![Validate Documentation](https://github.com/ki7mt/ki7mt-ai-docs/actions/workflows/validate.yml/badge.svg)](https://github.com/ki7mt/ki7mt-ai-docs/actions/workflows/validate.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**The Central Intelligence Hub for Local-First, Agentic Workflows**

Welcome to the architectural source-of-truth for the KI7MT Sovereign Fleet—a resilient, privacy-first ecosystem of AI-integrated tools built on sovereign infrastructure. This repository centralizes documentation for our Model Context Protocol (MCP) servers, data engineering pipelines, and agentic workflows.

**📖 Live Documentation**: [https://ki7mt.github.io/ki7mt-ai-docs/](https://ki7mt.github.io/ki7mt-ai-docs/)

---

## Mission Statement

The KI7MT Sovereign Fleet embodies a fundamental commitment to **data sovereignty** and **local-first architecture**. In an era of cloud dependency and centralized AI services, we maintain complete control over our computational infrastructure, data, and AI workflows.

Our mission is to demonstrate that **agentic AI systems** can operate at scale on sovereign hardware without sacrificing performance, privacy, or capability. We believe in:

- **Data Sovereignty**: Your data stays on your hardware, under your control
- **Local-First Computing**: High-performance local infrastructure over cloud dependency
- **Agentic Workflows**: AI agents with deep context and specialized domain knowledge
- **Open Architecture**: Transparent, documented systems that empower both humans and AI
- **Resilient Infrastructure**: ZFS-protected storage and enterprise-grade hardware

This documentation hub serves as the unified context source that enables AI agents and human collaborators to interact effectively with specialized amateur radio, environmental, and propagation datasets—all while maintaining complete data sovereignty.

---

## Fleet Overview

The Sovereign Fleet consists of specialized MCP servers, each providing deep domain expertise through structured data access and analysis capabilities:

| Component | Documentation Path | Primary Purpose |
|-----------|-------------------|-----------------|
| **wspr-mcp** | `/wspr` | High-speed ingestion and query engine for 10.6B+ WSPR propagation spots |
| **adif-mcp** | `/adif` | Standardized amateur radio log ingestion and normalization (ADIF v3.1.6) |
| **solar-mcp** | `/solar` | Environmental and space weather context for propagation analysis |

Each component operates independently while contributing to a unified knowledge graph accessible to AI agents through the Model Context Protocol.

---

## Hardware Stack

The Sovereign Fleet runs on purpose-built, high-performance local infrastructure:

### Compute Platform
- **CPU**: AMD Ryzen 9 9950X3D (16 cores, 32 threads)
- **GPU**: NVIDIA GeForce RTX 5090 (AI acceleration, CUDA compute)
- **Memory**: High-bandwidth DDR5 RAM
- **Storage**: TrueNAS Scale with ZFS redundancy

### Storage Architecture
- **Primary**: NVMe SSD arrays for high-speed data ingestion
- **Archive**: TrueNAS ZFS pools with snapshot protection
- **Capacity**: Multi-terabyte resilient storage for 10B+ row datasets

This hardware configuration enables:
- Real-time ingestion of millions of records per day
- Sub-second query response on billion-row datasets
- Local LLM inference and AI agent operations
- Zero cloud dependencies for core operations

---

## Context Source for AI Agents

This documentation hub is specifically designed as a **Context Source** for AI agents operating within the Sovereign Fleet ecosystem.

### Why This Matters

Traditional documentation is written for human readers. This hub is architected for both:

1. **Human Developers**: Clear, navigable reference documentation
2. **AI Agents**: Structured, parseable context that reduces token usage and improves reasoning

### How AI Agents Use This Hub

AI agents (Claude, custom MCP clients, etc.) leverage this documentation to:

- **Understand Schema**: Access data structure and API specifications
- **Execute Queries**: Learn correct query patterns and optimization strategies
- **Reason About Data**: Understand domain context (propagation, solar cycles, ADIF standards)
- **Generate Code**: Reference working examples and integration patterns
- **Maintain Consistency**: Follow established architectural standards

### Structured for AI Consumption

The documentation uses:

- **Consistent Markdown Structure**: Predictable heading hierarchy and organization
- **Code Examples**: Working samples that agents can adapt
- **API Specifications**: Clear parameter and return type documentation
- **Domain Glossaries**: Specialized terminology definitions
- **Cross-References**: Linked concepts for contextual reasoning

By providing this structured context, we enable AI agents to operate with deep domain knowledge while minimizing hallucination and maximizing accuracy.

---

## Architecture Overview

The documentation is built using **MkDocs** with the **mkdocs-multirepo-plugin**, enabling:

### Decentralized Development
- Functional code remains in project-specific repositories
- Each MCP server maintains its own documentation
- Independent versioning and release cycles

### Centralized Knowledge
- Documentation is aggregated at build time
- Single, searchable documentation site
- Unified navigation across all fleet components

### AI-Native Design
- Optimized for AI agent comprehension
- Reduced token usage through efficient structure
- Clear separation of concepts and implementation details

---

## Deployment

This documentation is automatically built and deployed to GitHub Pages on every push to the `main` branch.

### Automated Deployment

- **Trigger**: Automatic on push to `main`, manual via Actions tab
- **Build Time**: ~2-4 minutes
- **Deployment Target**: GitHub Pages (`gh-pages` branch)
- **Live Site**: [https://ki7mt.github.io/ki7mt-ai-docs/](https://ki7mt.github.io/ki7mt-ai-docs/)

### Documentation Updates

Documentation is pulled from three MCP server repositories at build time:
- `wspr-mcp` - WSPR Engine documentation
- `adif-mcp` - ADIF Normalization documentation
- `solar-mcp` - Solar Context documentation

Changes to these repositories are reflected in the next deployment after pushing to `main`.

For deployment setup and troubleshooting, see the [Deployment Guide](DEPLOYMENT.md).

---

## Getting Started

### For Developers

1. Review the [Contributing Guidelines](CONTRIBUTING.md)
2. Check the [Security Policy](SECURITY.md) for vulnerability reporting
3. Explore individual MCP server documentation

### For AI Agents

1. Start with the Fleet Overview table to identify relevant data sources
2. Navigate to component-specific documentation for API details
3. Reference code examples and query patterns
4. Follow architectural standards for consistency

### Building Locally

```bash
# Install dependencies
pip install -r requirements.txt

# Serve documentation locally (with live reload)
mkdocs serve

# Build static site
mkdocs build

# Build with strict mode (catches warnings)
mkdocs build --strict
```

See the [Installation Guide](docs/getting-started/installation.md) for detailed setup instructions.

---

## Project Status

This documentation hub is actively maintained and continuously updated as the Sovereign Fleet evolves. Each MCP server is in active development with regular data ingestion and capability expansion.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## Contact

- **Maintainer**: KI7MT (Greg Beam)
- **Security**: See [SECURITY.md](SECURITY.md) for vulnerability reporting
- **Issues**: Use the [GitHub issue tracker](.github/ISSUE_TEMPLATE/bug_report.md)

---

**Sovereign Infrastructure. Agentic Intelligence. Data Freedom.**
