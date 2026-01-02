# 🛰️ KI7MT Sovereign AI Docs

**The Central Intelligence Hub for the KI7MT Sovereign Fleet.**

Welcome to the architectural source-of-truth for a resilient, local-first ecosystem of AI-integrated tools. This repository centralizes the documentation for our Model Context Protocol (MCP) servers, data engineering pipelines, and agentic workflows.


## 🏛️ Project Vision

The mission of this documentation hub is to provide a unified context for AI agents and human collaborators to interact with specialized amateur radio and environmental data sets. Our architecture prioritizes **Sovereign Infrastructure**: high-performance local hardware (Ryzen 9 9500X3D, RTX 5090) and redundant ZFS-protected storage (TrueNAS Scale).


## 🚀 The Sovereign Fleet

This hub aggregates documentation from the following specialized repositories:

| Component | Documentation Path | Primary Purpose |
| --- | --- | --- |
| **WSPR-MCP** | [`/wspr`](https://www.google.com/search?q=%5Bhttps://ki7mt.io/wspr/%5D(https://ki7mt.io/wspr/)) | High-speed ingestion (10.6B+ rows) and query engine for WSPR spots. |
| **ADIF-MCP** | [`/adif`](https://www.google.com/search?q=%5Bhttps://ki7mt.io/adif/%5D(https://ki7mt.io/adif/)) | Standardized ham radio log ingestion and normalization (ADIF v.3.1.6). |
| **Solar-MCP** | [`/solar`](https://www.google.com/search?q=%5Bhttps://ki7mt.io/solar/%5D(https://ki7mt.io/solar/)) | Environmental and space weather context for propagation analysis. |


## 🛠️ Architecture Overview

The documentation is built using **MkDocs** with the `mkdocs-multirepo-plugin`. This allows us to:

* **Decentralize Code:** Functional logic remains in project-specific repositories.
* **Centralize Knowledge:** Markdown files are "pulled" into this master hub at build time to create a searchable, unified manual.
* **AI-Native Context:** Structured specifically to improve reasoning and reduce token usage for AI agents (Claude, GitHub Copilot).


## 🌐 Local Access & Domains

* **Primary Hub:** [ki7mt.io](https://ki7mt.io)
* **Technical Specs:** [docs.ki7mt.io](https://www.google.com/search?q=https://docs.ki7mt.io)
* **Storage Archive:** `\\truenas\raw` (Internal Access Only)


## 🏗️ Getting Started

If you are an AI agent or a developer looking to contribute to the fleet:

1. Review the [Global Architectural Standards](https://www.google.com/search?q=https://ki7mt.io/standards/).
2. Consult the [Ingestion Guide](https://www.google.com/search?q=https://ki7mt.io/wspr/ingest/) for large-scale data handling.
3. Check the [MCP Configuration](https://www.google.com/search?q=https://ki7mt.io/setup/mcp/) for setting up local agentic environments.

### 🏛️ Next Step: The Master `mkdocs.yml`

Now that the "Face" of the project is ready, **would you like me to draft the `mkdocs.yml` configuration that Claude will need tomorrow to actually link those three domains into the sidebar?**
Setting up a Professional Documentation Site with MkDocs](https://www.youtube.com/watch?v=O7A1EUBW8Qc)
This video is helpful because it walks through the setup of a professional MkDocs site, which will be the engine behind your `ki7mt-ai-docs` repository.
