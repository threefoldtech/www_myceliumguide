# GitHub Pages Setup Guide

This guide will help you enable GitHub Pages for your Mycelium User Guide documentation.

## Quick Setup (Using GitHub UI)

1. **Push your changes to GitHub:**
   ```bash
   git add .
   git commit -m "Add GitHub Pages documentation"
   git push origin main
   ```

2. **Enable GitHub Pages:**
   - Go to your repository on GitHub
   - Click on **Settings** (top right)
   - Scroll down to **Pages** in the left sidebar
   - Under **Source**:
     - Select branch: `main`
     - Select folder: `/docs`
   - Click **Save**

3. **Wait for deployment:**
   - GitHub will automatically build and deploy your site
   - This usually takes 1-2 minutes
   - You'll see a green checkmark when it's ready

4. **Visit your site:**
   - Your documentation will be available at:
   - `https://threefoldtech.github.io/www_myceliumguide/`

## Alternative: Using GitHub Actions (Recommended)

The repository includes a GitHub Actions workflow (`.github/workflows/pages.yml`) that automatically deploys your documentation.

To use it:

1. **Enable GitHub Actions for Pages:**
   - Go to **Settings** > **Pages**
   - Under **Source**, select: `GitHub Actions`

2. **Push your changes:**
   ```bash
   git add .
   git commit -m "Add GitHub Pages documentation with Actions"
   git push origin main
   ```

3. **Monitor deployment:**
   - Go to the **Actions** tab in your repository
   - Watch the deployment progress
   - Once complete, your site will be live

## Local Development

To preview the documentation locally before pushing:

1. **Install Jekyll:**
   ```bash
   # macOS
   gem install bundler jekyll
   
   # Ubuntu/Debian
   sudo apt-get install ruby-full build-essential
   gem install bundler jekyll
   ```

2. **Install dependencies:**
   ```bash
   cd docs
   bundle install
   ```

3. **Serve locally:**
   ```bash
   bundle exec jekyll serve
   ```

4. **View in browser:**
   - Open `http://localhost:4000/www_myceliumguide/`

## Customization

### Change Theme

Edit `docs/_config.yml` and change the `theme` line:

```yaml
theme: jekyll-theme-minimal  # or any other supported theme
```

Supported themes:
- `jekyll-theme-cayman` (current)
- `jekyll-theme-minimal`
- `jekyll-theme-slate`
- `jekyll-theme-architect`
- `jekyll-theme-hacker`
- `jekyll-theme-leap-day`
- `jekyll-theme-merlot`
- `jekyll-theme-midnight`
- `jekyll-theme-modernist`
- `jekyll-theme-tactile`
- `jekyll-theme-time-machine`

### Update Base URL

If your repository name is different, update `docs/_config.yml`:

```yaml
baseurl: "/your-repo-name"
url: "https://your-username.github.io"
```

### Add Custom Domain

1. Create a file `docs/CNAME` with your domain:
   ```
   docs.mycelium.example.com
   ```

2. Configure DNS:
   - Add a CNAME record pointing to `threefoldtech.github.io`

3. Enable HTTPS in repository settings

## Troubleshooting

### Site not loading

- Check that GitHub Pages is enabled in Settings > Pages
- Verify the branch and folder are correct (`main` and `/docs`)
- Wait a few minutes for the initial build

### 404 errors on navigation

- Ensure `baseurl` in `_config.yml` matches your repository name
- Links should use relative paths without `.md` extension

### Local preview not working

```bash
# Install missing dependencies
cd docs
bundle install

# Clear cache and rebuild
bundle exec jekyll clean
bundle exec jekyll serve
```

## Next Steps

After setup:

1. ✅ Verify all pages load correctly
2. ✅ Test navigation between pages
3. ✅ Check mobile responsiveness
4. ✅ Share the documentation URL with users
5. ✅ Keep content updated as Mycelium evolves

## Support

For issues with:
- **GitHub Pages setup**: Check [GitHub Pages documentation](https://docs.github.com/en/pages)
- **Jekyll**: See [Jekyll documentation](https://jekyllrb.com/docs/)
- **Content**: Open an issue in this repository
