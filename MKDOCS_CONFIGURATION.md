# MkDocs Configuration Reference

This document explains the `mkdocs.yml` configuration for the KI7MT Sovereign AI Fleet documentation hub.

## Overview

The configuration uses:

- **MkDocs**: Static site generator for project documentation
- **Material Theme**: Professional, responsive documentation theme
- **Multirepo Plugin**: Aggregates documentation from multiple repositories

## Key Configuration Sections

### Site Metadata

```yaml
site_name: KI7MT Sovereign AI Fleet
site_description: Central documentation hub for local-first, agentic workflows
site_author: KI7MT (Greg Beam)
site_url: https://ki7mt.io
```

Update these values to match your deployment URL and branding.

### Repository Links

```yaml
repo_name: ki7mt/ki7mt-ai-docs
repo_url: https://github.com/ki7mt/ki7mt-ai-docs
```

These create the GitHub repository link in the top navigation bar.

### Material Theme Configuration

#### Color Palette

The configuration includes both light and dark mode:

```yaml
palette:
  - media: "(prefers-color-scheme: light)"
    scheme: default
    primary: indigo
    accent: deep purple
```

**Available color options:**
- Primary: red, pink, purple, deep purple, indigo, blue, light blue, cyan, teal, green, light green, lime, yellow, amber, orange, deep orange
- Accent: red, pink, purple, deep purple, indigo, blue, light blue, cyan, teal, green, light green, lime, yellow, amber, orange, deep orange

#### Logo and Branding

```yaml
logo: assets/images/sovereign-fleet-logo.png
favicon: assets/images/favicon.ico
```

Place your logo files in `docs/assets/images/`:
- **Logo**: 128x128px or larger, PNG with transparency
- **Favicon**: Multi-resolution ICO file (16x16, 32x32, 48x48)

#### Features

Key features enabled:

- `navigation.instant` - Fast page loading without full reload
- `navigation.tabs` - Top-level navigation as tabs
- `navigation.sections` - Group navigation items into sections
- `search.suggest` - Search autocomplete suggestions
- `content.code.copy` - Copy button for code blocks

### Multirepo Plugin

The multirepo plugin aggregates documentation from component repositories:

```yaml
plugins:
  - multirepo:
      cleanup: true
      repos:
        - name: wspr-mcp
          import_url: 'https://github.com/ki7mt/wspr-mcp?branch=main&docs_dir=docs'
          section: WSPR Engine
```

#### Adding a New Repository

To add a new MCP server or component:

1. Ensure the repository has a `docs/` directory with markdown files
2. Add to the `repos` list in `mkdocs.yml`:

```yaml
- name: your-component
  import_url: 'https://github.com/ki7mt/your-component?branch=main&docs_dir=docs'
  section: Your Component Name
```

3. Add corresponding navigation section (see below)

#### Repository URL Format

```
https://github.com/OWNER/REPO?branch=BRANCH&docs_dir=DOCS_DIR
```

- `OWNER`: GitHub organization or user
- `REPO`: Repository name
- `BRANCH`: Branch to pull from (usually `main` or `master`)
- `DOCS_DIR`: Directory containing markdown files (default: `docs`)

### Navigation Structure

The navigation sidebar is defined in the `nav` section:

```yaml
nav:
  - Home: index.md
  - Getting Started:
      - Overview: getting-started/overview.md
  - WSPR Engine:
      - Overview: wspr-mcp/index.md
```

#### Navigation Best Practices

1. **Group related pages** - Use nested sections for organization
2. **Clear labels** - Use descriptive navigation titles
3. **Consistent structure** - Follow the same pattern across sections
4. **Index pages** - Each section should have an index/overview page

#### Linking to Multirepo Content

Reference pages from imported repositories using their configured name:

```yaml
- WSPR Engine:
    - Overview: wspr-mcp/index.md  # Note: matches 'name' in multirepo config
```

### Markdown Extensions

The configuration enables powerful markdown features:

#### Code Blocks

```yaml
- pymdownx.highlight:
    anchor_linenums: true  # Anchor line numbers
- pymdownx.superfences:
    custom_fences:
      - name: mermaid  # Diagram support
```

#### Admonitions (Callout Boxes)

```yaml
- admonition
- pymdownx.details  # Collapsible admonitions
```

Usage in markdown:
```markdown
!!! note "Optional Title"
    This is a note callout box.

!!! warning
    This is a warning.
```

#### Tables of Contents

```yaml
- toc:
    permalink: true  # Add anchor links to headings
    toc_depth: 3     # Include h1, h2, h3 in TOC
```

### Custom CSS and JavaScript

```yaml
extra_css:
  - assets/css/sovereign-fleet.css
  - assets/css/custom-theme.css

extra_javascript:
  - assets/js/custom.js
```

Place custom files in `docs/assets/`:
- CSS for theming and branding
- JavaScript for interactive features

## Customization Guide

### Changing Colors

Edit the `theme.palette` section in `mkdocs.yml`:

```yaml
palette:
  - scheme: default
    primary: blue      # Change main color
    accent: cyan       # Change accent color
```

### Adding Social Links

Edit the `extra.social` section:

```yaml
extra:
  social:
    - icon: fontawesome/brands/github
      link: https://github.com/ki7mt
      name: KI7MT on GitHub
```

Available icons: [Font Awesome icon search](https://fontawesome.com/icons)

### Enabling Analytics

Uncomment and configure in the `extra.analytics` section:

```yaml
extra:
  analytics:
    provider: google
    property: G-XXXXXXXXXX  # Your Google Analytics ID
```

## Building and Testing

### Local Development

```bash
# Start development server with live reload
mkdocs serve

# Access at http://127.0.0.1:8000
```

### Production Build

```bash
# Build static site
mkdocs build

# Output in site/ directory
```

### Validate Configuration

```bash
# Check for configuration errors
mkdocs build --strict

# Validate links
mkdocs build --strict --verbose
```

## Troubleshooting

### Multirepo Plugin Issues

**Problem**: Remote docs not loading

**Solutions**:
- Check repository URLs in `mkdocs.yml`
- Verify `docs_dir` path exists in remote repository
- Ensure branch name is correct
- Check network connectivity

**Problem**: Navigation links broken

**Solutions**:
- Verify `name` in multirepo config matches navigation paths
- Check file paths in remote repository
- Ensure index files exist

### Theme Issues

**Problem**: Custom CSS not loading

**Solutions**:
- Verify file paths in `extra_css`
- Check file exists in `docs/assets/css/`
- Clear browser cache
- Rebuild with `mkdocs build --clean`

## Resources

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Multirepo Plugin](https://github.com/jdoiro3/mkdocs-multirepo-plugin)
- [Python Markdown Extensions](https://facelessuser.github.io/pymdown-extensions/)

## Support

For configuration help:

1. Check this reference document
2. Review official documentation (links above)
3. Search GitHub issues
4. Open a new issue with configuration details

---

**Last Updated**: 2026-01-02
**Configuration Version**: 1.0.0
