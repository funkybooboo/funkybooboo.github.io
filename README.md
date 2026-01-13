# FunkyBooBoo Portfolio

My personal portfolio showcase website, built with Jekyll and hosted on GitHub Pages.

## Local Development

To run this site locally, ensure you have Ruby installed.

1. **Install dependencies**:
   ```bash
   # If bundle is not in your path
   /home/nate/.local/share/gem/ruby/3.4.0/bin/bundle install
   ```

2. **Serve the site**:
   ```bash
   /home/nate/.local/share/gem/ruby/3.4.0/bin/bundle exec jekyll serve
   ```
   The site will be available at `http://localhost:4000`.

## Deployment

This site is automatically deployed to GitHub Pages when changes are pushed to the `main` branch.

1. **Commit your changes**:
   ```bash
   git add .
   git commit -m "Update portfolio content"
   ```

2. **Push to GitHub**:
   ```bash
   git push origin main
   ```

## Structure

- `_config.yml`: Jekyll configuration settings.
- `index.md`: The homepage of the site.
- `Gemfile`: Ruby dependencies (GitHub Pages compatible).
- `_site/`: The generated static website (ignored by git).

## Documentation

For more detailed information, please see the following guides in the `docs/` directory:

- [Detailed Setup Guide](docs/setup.md)
- [Customization Guide](docs/customization.md)
- [GitHub Pages Information](docs/github-pages.md)
