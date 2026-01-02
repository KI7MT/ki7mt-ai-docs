# Installation Guide

This guide walks you through setting up the KI7MT Sovereign AI Fleet documentation locally.

## Prerequisites

### System Requirements

- **Operating System**: Linux, macOS, or Windows
- **Python**: 3.8 or higher
- **pip**: Python package installer
- **Git**: Version control system

### Hardware Recommendations

For the best experience building and serving the documentation:

- **RAM**: 4GB minimum (8GB recommended)
- **Storage**: 1GB free space for documentation and dependencies
- **Network**: Internet connection for downloading dependencies and remote docs

## Installation Steps

### 1. Clone the Repository

```bash
git clone https://github.com/ki7mt/ki7mt-ai-docs.git
cd ki7mt-ai-docs
```

### 2. Create a Virtual Environment (Recommended)

Using a virtual environment keeps dependencies isolated:

```bash
# Create virtual environment
python3 -m venv venv

# Activate virtual environment
# On Linux/macOS:
source venv/bin/activate

# On Windows:
venv\Scripts\activate
```

### 3. Install Dependencies

Install MkDocs and required plugins:

```bash
pip install mkdocs mkdocs-material mkdocs-multirepo-plugin
```

Or use the requirements file if provided:

```bash
pip install -r requirements.txt
```

### 4. Verify Installation

Check that MkDocs is installed correctly:

```bash
mkdocs --version
```

You should see output similar to:

```
mkdocs, version 1.5.3
```

## Building the Documentation

### Serve Locally (Development)

Start a local development server with live reloading:

```bash
mkdocs serve
```

The documentation will be available at: `http://127.0.0.1:8000`

Any changes you make to the documentation files will automatically reload in your browser.

### Build Static Site

Generate a static site for deployment:

```bash
mkdocs build
```

The built site will be in the `site/` directory.

### Build with Multirepo Content

To include documentation from remote repositories (wspr-mcp, adif-mcp, solar-mcp):

```bash
# The multirepo plugin will automatically fetch remote docs
mkdocs build
```

**Note**: The first build may take longer as it downloads documentation from remote repositories.

## Configuration

### Environment Variables

If your component repositories are private, you may need to configure authentication:

```bash
# Set GitHub token for private repositories
export GITHUB_TOKEN=your_github_token_here
```

### Custom Configuration

To modify the documentation structure or theme:

1. Edit `mkdocs.yml` in the repository root
2. See the [Configuration Guide](configuration.md) for details

## Troubleshooting

### Common Issues

#### Plugin Not Found

**Error**: `Plugin 'multirepo' not found`

**Solution**:
```bash
pip install mkdocs-multirepo-plugin
```

#### Port Already in Use

**Error**: `Address already in use`

**Solution**: Use a different port:
```bash
mkdocs serve -a localhost:8001
```

#### Remote Repository Access

**Error**: `Failed to fetch repository`

**Solution**: Check network connection and repository URLs in `mkdocs.yml`

### Getting Help

If you encounter issues:

1. Check the [MkDocs documentation](https://www.mkdocs.org/)
2. Review [Material theme docs](https://squidfunk.github.io/mkdocs-material/)
3. Check [multirepo plugin docs](https://github.com/jdoiro3/mkdocs-multirepo-plugin)
4. Open an issue on the [ki7mt-ai-docs repository](https://github.com/ki7mt/ki7mt-ai-docs/issues)

## Next Steps

Now that you have the documentation running locally:

1. Review the [Configuration Guide](configuration.md) to customize your setup
2. Read the [Quick Start Guide](quickstart.md) to begin using the Fleet
3. Explore component documentation (WSPR, ADIF, Solar)

---

**Installation complete!** Continue to the [Configuration Guide](configuration.md) →
