# GitHub Actions Workflows

This directory contains automated workflows for the KI7MT Sovereign AI Fleet documentation hub.

## Workflows

### Deploy to GitHub Pages (`deploy.yml`)

**Trigger**: Push to `main` branch, manual dispatch

**Purpose**: Automatically builds and deploys the MkDocs documentation site to GitHub Pages.

**Steps**:
1. Checkout repository with full git history
2. Set up Python 3.11 environment
3. Install MkDocs and required plugins
4. Configure Git for deployment
5. Build and deploy to `gh-pages` branch
6. Display deployment summary with site URL

**Duration**: ~2-4 minutes

**Deployment URL**: `https://ki7mt.github.io/ki7mt-ai-docs/`

### Validate Documentation (`validate.yml`)

**Trigger**: Pull requests to `main` branch, manual dispatch

**Purpose**: Validates documentation changes before merging to ensure build quality.

**Steps**:
1. Checkout pull request code
2. Set up Python 3.11 environment
3. Install MkDocs and required plugins
4. Validate MkDocs configuration (strict mode)
5. Build documentation to check for errors
6. Report validation results

**Duration**: ~1-2 minutes

**What it checks**:
- MkDocs configuration syntax
- Markdown file syntax
- Build errors and warnings (strict mode)
- Missing files or broken references

## Workflow Permissions

Both workflows require the following repository permissions:

- **Contents**: Write (for deployment workflow)
- **Pages**: Write (for GitHub Pages deployment)
- **Pull Requests**: Read (for validation workflow)

Configure in: **Repository Settings** → **Actions** → **General** → **Workflow permissions**

## Manual Workflow Execution

Both workflows can be manually triggered:

1. Go to **Actions** tab in the repository
2. Select the workflow to run
3. Click **Run workflow**
4. Choose the branch (usually `main`)
5. Click **Run workflow** button

## Workflow Status

View workflow status:

- **Actions tab**: See all workflow runs and their status
- **Pull requests**: Validation checks appear as status checks
- **Main branch**: Deploy workflow runs automatically after merge

## Monitoring

### Status Badges

Add status badges to README.md:

```markdown
[![Deploy MkDocs](https://github.com/ki7mt/ki7mt-ai-docs/actions/workflows/deploy.yml/badge.svg)](https://github.com/ki7mt/ki7mt-ai-docs/actions/workflows/deploy.yml)

[![Validate Documentation](https://github.com/ki7mt/ki7mt-ai-docs/actions/workflows/validate.yml/badge.svg)](https://github.com/ki7mt/ki7mt-ai-docs/actions/workflows/validate.yml)
```

### Notifications

GitHub sends email notifications for:
- Workflow failures
- First-time workflow runs on a branch

Configure in: **User Settings** → **Notifications**

## Troubleshooting

### Deploy Workflow Fails

Common issues:

1. **Permission errors**
   - Check workflow permissions in repository settings
   - Verify `GITHUB_TOKEN` has write access

2. **Build errors**
   - Test locally: `mkdocs build --strict`
   - Check for syntax errors in markdown files
   - Verify multirepo plugin can access remote repositories

3. **Deployment timeout**
   - Check multirepo plugin configuration
   - Verify remote repository URLs are accessible
   - Reduce number of imported repositories if needed

### Validate Workflow Fails

Common issues:

1. **Strict mode errors**
   - Fix all warnings in markdown files
   - Ensure all links are valid
   - Check for missing files

2. **Configuration errors**
   - Validate `mkdocs.yml` syntax
   - Test locally: `mkdocs build --strict --verbose`
   - Check plugin configurations

## Customizing Workflows

### Adding Dependencies

To add Python packages:

```yaml
- name: Install dependencies
  run: |
    pip install --upgrade pip
    pip install mkdocs
    pip install mkdocs-material
    pip install mkdocs-multirepo-plugin
    pip install your-new-package
```

Or use `requirements.txt`:

```yaml
- name: Install dependencies
  run: |
    pip install --upgrade pip
    pip install -r requirements.txt
```

### Changing Triggers

Modify the `on:` section to change when workflows run:

```yaml
# Only run on specific paths
on:
  push:
    branches:
      - main
    paths:
      - 'docs/**'
      - 'mkdocs.yml'

# Run on schedule (cron)
on:
  schedule:
    - cron: '0 0 * * 0'  # Weekly on Sunday at midnight

# Multiple triggers
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
  workflow_dispatch:
```

### Adding Caching

Speed up workflows with caching:

```yaml
- name: Cache pip packages
  uses: actions/cache@v3
  with:
    path: ~/.cache/pip
    key: ${{ runner.os }}-pip-${{ hashFiles('**/requirements.txt') }}
    restore-keys: |
      ${{ runner.os }}-pip-
```

### Adding Notifications

Send Slack/Discord notifications on deployment:

```yaml
- name: Notify deployment
  if: success()
  run: |
    curl -X POST -H 'Content-type: application/json' \
      --data '{"text":"Documentation deployed successfully!"}' \
      ${{ secrets.SLACK_WEBHOOK_URL }}
```

## Best Practices

1. **Test locally first**: Always run `mkdocs build --strict` before pushing
2. **Review logs**: Check workflow logs for warnings even on success
3. **Use validation**: Create pull requests to trigger validation workflow
4. **Monitor failures**: Fix failed workflows promptly to keep deployment pipeline healthy
5. **Keep dependencies updated**: Regularly update Python packages

## Security

### Secrets Management

For private repositories or external integrations:

1. Add secrets in **Repository Settings** → **Secrets** → **Actions**
2. Reference in workflow: `${{ secrets.SECRET_NAME }}`
3. Never commit secrets to the repository

### Token Security

The workflows use `GITHUB_TOKEN` automatically provided by GitHub:
- Scoped to the repository
- Automatically rotated
- Expires after workflow completion
- No manual configuration needed

## Resources

- [GitHub Actions Documentation](https://docs.github.com/actions)
- [Workflow Syntax Reference](https://docs.github.com/actions/reference/workflow-syntax-for-github-actions)
- [MkDocs Deployment Guide](https://www.mkdocs.org/user-guide/deploying-your-docs/)
- [Deployment Guide](../../DEPLOYMENT.md) - Detailed deployment documentation

## Support

For workflow issues:

1. Check workflow logs in the **Actions** tab
2. Review the [Deployment Guide](../../DEPLOYMENT.md)
3. Test builds locally
4. Open an issue with workflow logs attached

---

**Maintained by**: KI7MT (Greg Beam)
**Last Updated**: 2026-01-02
