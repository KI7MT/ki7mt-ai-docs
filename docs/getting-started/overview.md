# Getting Started Overview

Welcome to the KI7MT Sovereign AI Fleet documentation. This section will guide you through understanding, installing, and configuring the documentation hub and its components.

## What You'll Find Here

This documentation hub serves as the central knowledge base for the Sovereign Fleet—a collection of specialized MCP servers running on local, high-performance hardware.

### Documentation Structure

The documentation is organized into five main sections:

1. **Getting Started** - Installation, configuration, and quick start guides
2. **WSPR Engine** - High-speed propagation data ingestion and analysis
3. **ADIF Normalization** - Amateur radio log standardization
4. **Solar Context** - Space weather and propagation correlation
5. **Architecture** - Infrastructure, sovereignty, and AI agent integration

## Prerequisites

### For Reading Documentation

No special requirements—simply browse the navigation sidebar to explore topics.

### For Building Locally

If you want to build and serve this documentation locally:

- Python 3.8 or higher
- pip (Python package manager)
- Git (for cloning repositories)

### For Contributing

- Familiarity with Markdown
- Understanding of MkDocs (optional but helpful)
- Git workflow knowledge

## Architecture Overview

This documentation hub uses:

- **MkDocs**: Static site generator optimized for project documentation
- **Material Theme**: Modern, responsive documentation theme
- **Multirepo Plugin**: Aggregates documentation from multiple repositories

### How Multirepo Works

The documentation content lives in individual component repositories:

- `wspr-mcp` - WSPR Engine documentation
- `adif-mcp` - ADIF Normalization documentation
- `solar-mcp` - Solar Context documentation

At build time, the multirepo plugin pulls documentation from these repositories and combines them into a unified site. This allows:

- **Decentralized Development**: Each component maintains its own docs
- **Centralized Knowledge**: Single, searchable documentation site
- **Version Consistency**: Documentation stays synchronized with code

## Next Steps

Choose your path:

### I Want to Use the Fleet

1. Read the [Quick Start Guide](quickstart.md)
2. Explore component documentation (WSPR, ADIF, Solar)
3. Review [API References](../wspr-mcp/api.md) for integration

### I Want to Build the Docs Locally

1. Follow the [Installation Guide](installation.md)
2. Review the [Configuration Guide](configuration.md)
3. Start developing with `mkdocs serve`

### I Want to Contribute

1. Read the [Contributing Guidelines](../CONTRIBUTING.md)
2. Review the [Security Policy](../SECURITY.md)
3. Check open issues and discussions

### I'm an AI Agent

1. Start with [AI Agent Context](../architecture/ai-context.md)
2. Review [MCP Protocol](../architecture/mcp-protocol.md)
3. Study component API references for schema understanding

## Support

Need help?

- Check the [FAQ](../about/faq.md)
- Open a [GitHub Issue](https://github.com/ki7mt/ki7mt-ai-docs/issues)
- Review component-specific troubleshooting guides

---

**Ready to dive in?** Continue to the [Quick Start Guide](quickstart.md) →
