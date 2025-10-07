# GitHub Pages Quick Reference

## 📁 Structure Created

```
www_myceliumguide/
├── .github/
│   └── workflows/
│       └── pages.yml          # GitHub Actions workflow for auto-deployment
├── docs/                      # GitHub Pages source directory
│   ├── _config.yml           # Jekyll configuration
│   ├── Gemfile               # Ruby dependencies for local dev
│   ├── index.md              # Homepage
│   ├── installation.md       # Installation guide
│   ├── quick-start.md        # Quick start guide
│   ├── configuration.md      # Configuration guide
│   ├── usage.md              # Usage guide
│   ├── troubleshooting.md    # Troubleshooting guide
│   └── README.md             # Docs directory readme
├── userguide/                # Original content (kept for reference)
├── README.md                 # Project readme
└── SETUP.md                  # Detailed setup instructions
```

## 🚀 Quick Start

### Option 1: Manual Setup (Simplest)

1. Push to GitHub:
   ```bash
   git add .
   git commit -m "Add GitHub Pages documentation"
   git push origin main
   ```

2. Enable in GitHub:
   - Go to **Settings** → **Pages**
   - Source: Branch `main`, Folder `/docs`
   - Click **Save**

3. Visit: `https://threefoldtech.github.io/www_myceliumguide/`

### Option 2: GitHub Actions (Recommended)

1. Push to GitHub (same as above)

2. Enable in GitHub:
   - Go to **Settings** → **Pages**
   - Source: **GitHub Actions**

3. Workflow will auto-deploy on every push

## 🎨 Customization

### Change Theme

Edit `docs/_config.yml`:
```yaml
theme: jekyll-theme-minimal  # Change this line
```

### Update Site Info

Edit `docs/_config.yml`:
```yaml
title: Your Title
description: Your Description
baseurl: "/your-repo-name"
url: "https://your-username.github.io"
```

### Add New Page

1. Create `docs/new-page.md`:
   ```markdown
   ---
   layout: default
   title: New Page
   ---
   
   # Content here
   ```

2. Link from other pages:
   ```markdown
   [Link text](new-page)
   ```

## 🔧 Local Development

```bash
# Install dependencies
cd docs
bundle install

# Run local server
bundle exec jekyll serve

# Visit http://localhost:4000/www_myceliumguide/
```

## 📝 Content Guidelines

### Front Matter (Required)

Every page needs this at the top:
```yaml
---
layout: default
title: Page Title
---
```

### Internal Links

Use relative paths without `.md`:
```markdown
[Installation Guide](installation)
[Quick Start](quick-start)
```

### Anchors/Headings

Link to sections:
```markdown
[SOCKS5 Proxy](usage#socks5-proxy)
```

## 🌐 URLs

- **Production**: `https://threefoldtech.github.io/www_myceliumguide/`
- **Local Dev**: `http://localhost:4000/www_myceliumguide/`

## 📋 Checklist

After setup:
- [ ] Push code to GitHub
- [ ] Enable GitHub Pages in Settings
- [ ] Wait for deployment (1-2 minutes)
- [ ] Test all page links
- [ ] Verify mobile responsiveness
- [ ] Update repository description with docs URL

## 🔍 Troubleshooting

### Site shows 404
- Check Settings → Pages is enabled
- Verify branch is `main` and folder is `/docs`
- Wait a few minutes for build

### Links broken
- Ensure `baseurl` matches repo name
- Use relative links without `.md`
- Check front matter is present

### Local preview fails
```bash
cd docs
bundle install
bundle exec jekyll clean
bundle exec jekyll serve
```

## 📚 Resources

- [GitHub Pages Docs](https://docs.github.com/en/pages)
- [Jekyll Docs](https://jekyllrb.com/docs/)
- [Supported Themes](https://pages.github.com/themes/)
- [Jekyll Theme Cayman](https://github.com/pages-themes/cayman)

## 🎯 Next Steps

1. **Test locally** before pushing
2. **Enable GitHub Pages** in repository settings
3. **Share the URL** with your team
4. **Keep content updated** as project evolves
5. **Monitor** GitHub Actions for deployment status

---

**Need help?** See `SETUP.md` for detailed instructions.
