# Mycelium User Guide Documentation

This directory contains the GitHub Pages documentation for the Mycelium User Guide.

## Structure

- `index.md` - Homepage
- `installation.md` - Installation guide for all platforms
- `quick-start.md` - Quick start guide with public peers
- `configuration.md` - Configuration options and examples
- `usage.md` - Daily usage patterns and SOCKS5 proxy setup
- `troubleshooting.md` - Common issues and solutions
- `_config.yml` - Jekyll configuration

## Local Development

To preview the documentation locally:

```bash
# Install Jekyll (if not already installed)
gem install bundler jekyll

# Serve the site locally
cd docs
jekyll serve

# Visit http://localhost:4000/www_myceliumguide/
```

## GitHub Pages Setup

1. Go to your repository settings
2. Navigate to "Pages" section
3. Under "Source", select:
   - Branch: `main` (or your default branch)
   - Folder: `/docs`
4. Click "Save"

The site will be available at: `https://threefoldtech.github.io/www_myceliumguide/`

## Theme

This documentation uses the default Jekyll theme `jekyll-theme-cayman`. You can change this in `_config.yml` to any of the [supported GitHub Pages themes](https://pages.github.com/themes/).

## Customization

To customize the documentation:

1. Edit `_config.yml` for site-wide settings
2. Modify individual `.md` files for content
3. Update the front matter in each file to change titles and layouts
