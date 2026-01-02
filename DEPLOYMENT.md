# Deployment Guide

This guide explains how to deploy the KI7MT Sovereign AI Fleet documentation to GitHub Pages using the automated GitHub Actions workflow.

## Overview

The documentation is automatically built and deployed to GitHub Pages whenever changes are pushed to the `main` branch. The deployment process:

1. Checks out the repository
2. Sets up Python environment
3. Installs MkDocs and required plugins
4. Builds the documentation site
5. Deploys to the `gh-pages` branch
6. GitHub Pages serves the site from the `gh-pages` branch

## Initial Setup

### 1. Enable GitHub Pages

To enable GitHub Pages for your repository:

1. Go to your repository on GitHub
2. Navigate to **Settings** → **Pages**
3. Under **Source**, select:
   - **Branch**: `gh-pages`
   - **Folder**: `/ (root)`
4. Click **Save**

The site will be available at: `https://ki7mt.github.io/ki7mt-ai-docs/`

### 2. Configure Repository Permissions

The workflow requires write permissions to deploy:

1. Go to **Settings** → **Actions** → **General**
2. Scroll to **Workflow permissions**
3. Select **Read and write permissions**
4. Check **Allow GitHub Actions to create and approve pull requests**
5. Click **Save**

### 3. Verify Workflow

After the first push to `main`:

1. Go to **Actions** tab in your repository
2. Click on the latest workflow run
3. Verify all steps completed successfully
4. Check the deployment summary for the site URL

## Automatic Deployment

### Trigger Deployment

The workflow automatically runs when:

- Changes are pushed to the `main` branch
- Manually triggered from the Actions tab

To trigger a manual deployment:

1. Go to **Actions** tab
2. Select **Deploy MkDocs to GitHub Pages**
3. Click **Run workflow**
4. Select the `main` branch
5. Click **Run workflow**

### Deployment Process

The workflow performs these steps:

```yaml
1. Checkout repository (with full git history)
2. Set up Python 3.11
3. Install dependencies:
   - mkdocs
   - mkdocs-material
   - mkdocs-multirepo-plugin
4. Configure Git user for deployment
5. Build and deploy with mkdocs gh-deploy
6. Display deployment summary
```

### Expected Duration

Typical deployment takes **2-4 minutes**:

- Checkout and setup: ~30 seconds
- Dependency installation: ~1 minute
- Site build: ~1-2 minutes (longer on first build due to multirepo fetching)
- Deployment: ~30 seconds

## Deployment Workflow Details

### Workflow File

Location: `.github/workflows/deploy.yml`

### Key Features

- **Automatic deployment** on push to `main`
- **Manual deployment** via workflow_dispatch
- **Concurrency control** prevents multiple simultaneous deployments
- **Clean deployment** removes old files before deploying
- **Verbose logging** for troubleshooting
- **Deployment summary** shows site URL

### Dependencies

The workflow installs:

```bash
pip install mkdocs
pip install mkdocs-material
pip install mkdocs-multirepo-plugin
```

To add additional dependencies:

1. Edit `.github/workflows/deploy.yml`
2. Add `pip install package-name` to the install step
3. Commit and push changes

Or use `requirements.txt`:

```yaml
- name: Install dependencies
  run: |
    pip install --upgrade pip
    pip install -r requirements.txt
```

## Troubleshooting

### Common Issues

#### Workflow Fails with Permission Error

**Error**: `Permission denied` or `403 Forbidden`

**Solution**:
1. Check repository settings (see Initial Setup above)
2. Ensure workflow has write permissions
3. Verify GITHUB_TOKEN has correct permissions

#### Site Shows 404 Error

**Error**: Site loads but shows 404 page

**Solution**:
1. Check GitHub Pages settings (Settings → Pages)
2. Verify `gh-pages` branch exists
3. Ensure source is set to `gh-pages` branch, `/ (root)` folder
4. Wait a few minutes for GitHub Pages to update

#### Multirepo Plugin Fails

**Error**: `Failed to fetch repository` or timeout

**Solution**:
1. Verify repository URLs in `mkdocs.yml`
2. Check if remote repositories are accessible
3. Ensure branch names are correct
4. For private repos, add authentication token

#### Build Takes Too Long

**Issue**: Deployment times out or takes >10 minutes

**Solution**:
1. Check multirepo plugin is fetching from correct branches
2. Reduce documentation size or number of repos
3. Add caching for multirepo content (advanced)

### Viewing Workflow Logs

To debug deployment issues:

1. Go to **Actions** tab
2. Click on the failed workflow run
3. Expand each step to view detailed logs
4. Look for error messages in red

Common log locations:
- **Install dependencies**: Check for package installation errors
- **Build and deploy**: Check for MkDocs build errors or missing files
- **Deployment summary**: Verify deployment URL

### Testing Locally Before Deploy

Always test the build locally before pushing:

```bash
# Clean build
mkdocs build --clean --strict

# Serve locally
mkdocs serve

# Test multirepo plugin
mkdocs build --verbose
```

The `--strict` flag treats warnings as errors, catching issues before deployment.

## Custom Domain (Optional)

To use a custom domain (e.g., `docs.ki7mt.io`):

### 1. Add CNAME Record

Create `docs/CNAME` file:

```
docs.ki7mt.io
```

### 2. Configure DNS

Add a CNAME record in your DNS provider:

```
Type: CNAME
Host: docs
Value: ki7mt.github.io
```

### 3. Enable in GitHub Settings

1. Go to **Settings** → **Pages**
2. Enter your custom domain: `docs.ki7mt.io`
3. Check **Enforce HTTPS** (wait for certificate provisioning)

### 4. Update mkdocs.yml

Update the `site_url`:

```yaml
site_url: https://docs.ki7mt.io
```

## Monitoring Deployments

### Deployment Status Badge

Add a status badge to your README.md:

```markdown
[![Deploy MkDocs](https://github.com/ki7mt/ki7mt-ai-docs/actions/workflows/deploy.yml/badge.svg)](https://github.com/ki7mt/ki7mt-ai-docs/actions/workflows/deploy.yml)
```

### Email Notifications

GitHub sends email notifications for:
- Workflow failures
- First-time workflow runs

Configure in: **Settings** → **Notifications**

## Advanced Configuration

### Caching Dependencies

Speed up deployments by caching pip packages:

```yaml
- name: Set up Python
  uses: actions/setup-python@v5
  with:
    python-version: '3.11'
    cache: 'pip'  # Already enabled in workflow
```

### Conditional Deployment

Deploy only when documentation changes:

```yaml
on:
  push:
    branches:
      - main
    paths:
      - 'docs/**'
      - 'mkdocs.yml'
      - 'requirements.txt'
```

### Deployment Environments

Use GitHub Environments for approval workflows:

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
```

## Security Considerations

### Secrets and Tokens

The workflow uses `GITHUB_TOKEN` automatically provided by GitHub Actions. No manual token configuration needed.

For private multirepo sources, add a Personal Access Token:

1. Generate token: **Settings** → **Developer settings** → **Personal access tokens**
2. Add to repository: **Settings** → **Secrets** → **Actions**
3. Use in workflow:

```yaml
env:
  GITHUB_TOKEN: ${{ secrets.PAT_TOKEN }}
```

### Branch Protection

Protect the `gh-pages` branch:

1. Go to **Settings** → **Branches**
2. Add rule for `gh-pages`
3. Enable **Require status checks** (optional)
4. **Do not** enable **Require pull request reviews** (blocks automated deployments)

## Resources

- [GitHub Pages Documentation](https://docs.github.com/pages)
- [GitHub Actions Documentation](https://docs.github.com/actions)
- [MkDocs Deployment Guide](https://www.mkdocs.org/user-guide/deploying-your-docs/)
- [Material for MkDocs Publishing Guide](https://squidfunk.github.io/mkdocs-material/publishing-your-site/)

## Support

For deployment issues:

1. Check workflow logs in the Actions tab
2. Review this troubleshooting guide
3. Test the build locally
4. Open an issue with workflow logs attached

---

**Last Updated**: 2026-01-02
**Workflow Version**: 1.0.0
