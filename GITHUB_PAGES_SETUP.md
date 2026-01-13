# GitHub Pages Setup Instructions

The repository is ready for GitHub Pages deployment, but it needs to be configured in the GitHub repository settings.

## Steps to Enable GitHub Pages:

1. **Go to Repository Settings**
   - Navigate to: https://github.com/dmedina5/prompt-engineering-guide/settings/pages

2. **Configure Source**
   - Under "Build and deployment"
   - Source: Select "Deploy from a branch"
   - Branch: Select "main" branch
   - Folder: Select "/ (root)"

3. **Save Configuration**
   - Click "Save"
   - GitHub will start building and deploying your site

4. **Wait for Deployment**
   - The first deployment takes 1-2 minutes
   - Check deployment status at: https://github.com/dmedina5/prompt-engineering-guide/deployments
   - Once complete, your site will be available at: https://dmedina5.github.io/prompt-engineering-guide/

## Files Already Configured:

✅ `.nojekyll` - Prevents Jekyll processing
✅ `index.html` - Main landing page with authentication
✅ `builder.html` - Prompt builder tool
✅ `guide.html` - Prompt engineering guide
✅ All files have correct permissions (644)

## Alternative: GitHub Actions Deployment

If you prefer automated deployment via GitHub Actions:

1. **Update Personal Access Token**
   - Go to: https://github.com/settings/tokens
   - Create new token with `workflow` scope
   - Update git remote with new token

2. **Create Workflow File**
   - The workflow file is ready to be added (see below)

### Workflow File Content (.github/workflows/deploy.yml):

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Pages
        uses: actions/configure-pages@v4

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'

      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

## Troubleshooting:

- **404 Error**: Make sure GitHub Pages source is set to "main" branch in settings
- **Blank Page**: Check browser console for errors, ensure authentication service is running
- **Authentication Loop**: Clear browser cache and localStorage, try again

## Expected Site URL:
https://dmedina5.github.io/prompt-engineering-guide/
