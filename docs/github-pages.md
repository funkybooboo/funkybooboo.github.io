# GitHub Pages Documentation

This site is hosted on [GitHub Pages](https://pages.github.com/).

## How it Works

GitHub Pages looks for a static website in specific branches of your repository. Since this repository is named `funkybooboo.github.io`, it is a **User/Organization Page**.

-   **Source Branch**: Content is served from the `main` branch.
-   **Build Process**: When you push to GitHub, a GitHub Actions workflow (or the legacy Pages builder) automatically builds your Jekyll site and deploys the static files.

## Project Structure for Pages

GitHub Pages automatically builds Jekyll sites. You **do not** need to check in the `_site` directory.

-   **Commit**: `_config.yml`, `index.md`, `Gemfile`, `Gemfile.lock`, and your content (`docs/`, etc.).
-   **Ignore**: The `_site` directory is included in `.gitignore` to prevent generated files from cluttering the repository.

## Custom Domain

If you want to use a custom domain (e.g., `www.funkybooboo.com`) instead of `funkybooboo.github.io`:

1.  Purchase your domain name.
2.  Create a file named `CNAME` in the root of your repository.
3.  Add your domain name to the file (e.g., `funkybooboo.com`).
4.  Configure your DNS records with your domain provider to point to GitHub Pages.
    -   See [GitHub's documentation on managing a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

## Troubleshooting Builds

If your site fails to update on GitHub:

1.  Check the "Actions" tab in your repository to see build logs.
2.  Ensure your `Gemfile.lock` is committed.
3.  Verify that you are not using plugins unsupported by GitHub Pages (unless you are using a custom GitHub Actions workflow).
