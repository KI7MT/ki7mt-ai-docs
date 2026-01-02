# Contributing to ki7mt-ai-docs

Thank you for your interest in contributing to the Sovereign AI Fleet documentation hub!

## About This Repository

This repository serves as a **central documentation aggregation hub** for the Sovereign AI Fleet project. We use [MkDocs](https://www.mkdocs.org/) with the [mkdocs-multirepo-plugin](https://github.com/jdoiro3/mkdocs-multirepo-plugin) to combine documentation from multiple MCP (Model Context Protocol) server repositories into a unified documentation site.

### Current MCP Repositories

- **wspr-mcp** - WSPR (Weak Signal Propagation Reporter) MCP server
- **adif-mcp** - ADIF (Amateur Data Interchange Format) MCP server
- **solar-mcp** - Solar data and analytics MCP server

## How This Works

This repository does not contain the actual documentation content for each MCP server. Instead, it:

1. References documentation from individual MCP repositories
2. Aggregates them using mkdocs-multirepo-plugin
3. Builds a unified documentation site that combines all project docs

## Adding New Documentation Sections

To add documentation for a new MCP server or project component:

1. **Prepare your repository**
   - Ensure your repository has a `docs/` directory with MkDocs-compatible markdown files
   - Include a `mkdocs.yml` configuration file in your repository

2. **Update the main mkdocs.yml**
   - Add your repository to the `plugins.multirepo.repos` section
   - Specify the navigation structure for your documentation section

3. **Example configuration**
   ```yaml
   plugins:
     - multirepo:
         repos:
           - name: your-mcp
             import_url: 'https://github.com/ki7mt/your-mcp?branch=main'
             section: YourMCP Documentation
   ```

4. **Submit a pull request**
   - Fork this repository
   - Add your configuration changes
   - Submit a PR with a clear description of the documentation section you're adding

## Documentation Standards

- Use clear, concise markdown
- Include code examples where appropriate
- Follow the existing navigation structure
- Ensure all links are relative and will work in the aggregated site
- Test locally before submitting (see below)

## Testing Locally

To test the documentation site locally:

```bash
# Install MkDocs and the multirepo plugin
pip install mkdocs mkdocs-multirepo-plugin

# Serve the documentation
mkdocs serve

# Build the site
mkdocs build
```

## Questions or Issues?

If you have questions about contributing or run into issues:

- Open an issue in this repository
- Check existing issues for similar questions
- Review the [MkDocs documentation](https://www.mkdocs.org/)
- Review the [mkdocs-multirepo-plugin documentation](https://github.com/jdoiro3/mkdocs-multirepo-plugin)

## License

All contributions to this repository are subject to the [MIT License](LICENSE).
