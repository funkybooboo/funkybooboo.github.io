# Detailed Setup Guide

This guide provides more comprehensive instructions for setting up the Portfolio development environment.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

1.  **Ruby**: This project requires Ruby version 3.0 or higher.
    -   Check your version: `ruby -v`
2.  **RubyGems**: The package manager for Ruby.
    -   Check your version: `gem -v`
3.  **GCC and Make**: Required for building native extensions (like `jekyll`).

## Installation

1.  **Clone the repository** (if you haven't already):
    ```bash
    git clone https://github.com/funkybooboo/funkybooboo.github.io.git
    cd funkybooboo.github.io
    ```

2.  **Install Bundler**:
    Bundler manages Ruby gem dependencies.
    ```bash
    gem install bundler
    ```
    *Note: Depending on your system configuration, you might need to use `sudo` or configure a local gem path.*

3.  **Install Project Dependencies**:
    Run the following command in the project root to install all gems defined in the `Gemfile`:
    ```bash
    bundle install
    ```
    This will install `jekyll`, `github-pages`, and other necessary plugins into a local `vendor` directory or your system gems, depending on your configuration.

## Running Locally

To preview your site locally:

```bash
bundle exec jekyll serve
```

-   The site will be hosted at `http://localhost:4000`.
-   Add the `--livereload` flag to automatically refresh the browser when you change files:
    ```bash
    bundle exec jekyll serve --livereload
    ```

## Troubleshooting

### "Command not found: bundle"
If your shell cannot find `bundle`, you may need to add the gem executable path to your `PATH` environment variable.

### "Permission denied"
If you encounter permission errors when installing gems, try configuring bundler to install locally in the project:
```bash
bundle config set --local path 'vendor/bundle'
bundle install
```
