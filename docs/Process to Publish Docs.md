---
title: InvokeAI Web Server
---
To serve Markdown documents on a public website using MkDocs and GitHub Pages, follow these steps:

### Steps to Publish MkDocs Site on GitHub Pages

1. **Install MkDocs and MkDocs Material**:
   Make sure MkDocs and any themes (e.g., Material for MkDocs) are installed locally:

   ```sh
   pip install mkdocs mkdocs-material
   ```

2. **Create or Update `mkdocs.yml` Configuration**:
   Ensure you have a `mkdocs.yml` configuration file in your repository. This file configures the MkDocs site.

   Example `mkdocs.yml`:

   ```yaml
   site_name: My Documentation Site
   theme:
     name: material

   nav:
     - Home: index.md
     - About: about.md
     - Documentation:
         - Introduction: docs/introduction.md
         - Usage: docs/usage.md
         - API: docs/api.md
     - Blog: blog.md
     - Contact: contact.md
   ```

3. **Create a `docs` Directory**:
   Ensure you have a `docs` directory in your repository where all your Markdown files are located.

4. **Build the Site Locally**:
   Build the MkDocs site locally to ensure everything is set up correctly:

   ```sh
   mkdocs build
   ```

   This command will generate a `site` directory containing the static files for your MkDocs site.

5. **Deploy to GitHub Pages**:
   You can deploy your MkDocs site to GitHub Pages using the following steps:

   **a. Add a GitHub Actions Workflow**:
   GitHub Actions can automatically build and deploy your site to GitHub Pages. Create a file at `.github/workflows/gh-pages.yml` with the following content:

   ```yaml
   name: Deploy MkDocs site to GitHub Pages

   on:
     push:
       branches:
         - main  # or the branch you want to deploy from

   jobs:
     deploy:
       runs-on: ubuntu-latest

       steps:
         - name: Checkout repository
           uses: actions/checkout@v2

         - name: Set up Python
           uses: actions/setup-python@v2
           with:
             python-version: '3.x'

         - name: Install dependencies
           run: |
             pip install mkdocs mkdocs-material

         - name: Build MkDocs site
           run: |
             mkdocs build

         - name: Deploy to GitHub Pages
           uses: peaceiris/actions-gh-pages@v3
           with:
             github_token: ${{ secrets.GITHUB_TOKEN }}
             publish_dir: ./site
   ```

   **b. Commit and Push the Workflow**:
   Commit and push the workflow file to your repository:

   ```sh
   git add .github/workflows/gh-pages.yml
   git commit -m "Add GitHub Actions workflow for MkDocs"
   git push
   ```

6. **Enable GitHub Pages in Repository Settings**:
   Go to your GitHub repository settings, scroll down to the "GitHub Pages" section, and select the branch and folder (e.g., `gh-pages` or `/root`) where the site will be deployed.

### Summary

By following these steps, you should be able to update Markdown documents in your GitHub repository and have them automatically served as a public website using GitHub Pages and MkDocs. Here’s a quick checklist:

1. Ensure MkDocs and themes are installed.
2. Create or update `mkdocs.yml`.
3. Ensure Markdown files are in the `docs` directory.
4. Build the site locally to verify.
5. Use GitHub Actions to deploy the site to GitHub Pages.
6. Enable GitHub Pages in your repository settings.

If you follow these steps and configure GitHub Actions correctly, your MkDocs site should be automatically built and published to GitHub Pages whenever you push changes to the specified branch.

