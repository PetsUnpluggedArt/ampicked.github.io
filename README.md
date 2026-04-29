# Ampicked - Expert WordPress Hosting Reviews

This is the Jekyll-powered source code for [ampicked.com](https://ampicked.com), a site dedicated to honest, data-driven WordPress hosting reviews and comparisons.

## Quick Start

### Local Development

If you want to develop locally, you'll need Jekyll installed:

```bash
# Install Ruby and Bundler first
gem install bundler jekyll

# Clone this repo
cd ampicked.github.io

# Install dependencies
bundle install

# Serve locally
bundle exec jekyll serve
```

Then visit `http://localhost:4000` to see your site.

### Building

To build the static site:

```bash
bundle exec jekyll build
```

The compiled site will be in the `_site/` directory.

## Site Structure

```
ampicked.github.io/
├── _config.yml              # Jekyll configuration
├── _layouts/
│   ├── default.html         # Base template for all pages
│   └── post.html            # Blog post template
├── _includes/
│   ├── nav.html             # Navigation bar (shared)
│   └── footer.html          # Footer (shared)
├── _posts/                  # Blog articles (Markdown)
│   ├── 2026-04-27-wordpress-hosting-mistakes.md
│   ├── 2026-04-27-cheap-hosting-costs.md
│   └── 2026-04-27-choose-hosting.md
├── index.md                 # Homepage
├── about.md                 # About page
└── README.md                # This file
```

## Pages

### Homepage (`index.md`)
Main entry point with sections for:
- Choose Your Path (4 main navigation options)
- Why Ampicked (6 key features)
- Learn From Our Blog (featured blog posts)
- Individual Host Reviews

### About (`about.md`)
- Mission statement
- Tony Jackson's background
- Why trust Ampicked
- Contact information

### Blog Posts
Located in `_posts/` folder, using Jekyll's standard date-prefixed naming convention.

## Customization

### Editing Navigation
Edit `_includes/nav.html` to add/modify navigation links. The change will appear on all pages automatically.

### Editing Footer
Edit `_includes/footer.html` to update footer content. Changes appear on all pages.

### Editing Styles
All CSS is in `_layouts/default.html` within the `<style>` tag. Modify there to change the site's appearance.

### Adding Blog Posts
Create a new Markdown file in `_posts/` with the format `YYYY-MM-DD-slug.md` and include front matter:

```yaml
---
layout: post
title: Article Title
description: Brief description for meta tags
keywords: keyword1, keyword2
date: 2026-04-27
permalink: /article-slug/
---
```

### Adding Pages
Create a new Markdown file in the root directory with front matter:

```yaml
---
layout: default
title: Page Title
description: Meta description
permalink: /page-slug/
---
```

## Deployment

This site is hosted on GitHub Pages and automatically deployed when you push to the main branch.

### Push to GitHub

```bash
git add -A
git commit -m "Description of changes"
git push origin main
```

GitHub Pages will automatically build the Jekyll site and deploy it within 1-2 minutes.

## SEO

- All meta tags (title, description, keywords) are automatically handled via `jekyll-seo-tag` plugin
- Sitemap is automatically generated daily via `jekyll-sitemap` plugin
- Google Analytics tracking ID is configured in `_config.yml`

## Analytics

Google Analytics 4 tracking code is in `_layouts/default.html`. Update the `G-QKR6GF3W3X` ID if needed.

## Performance

The site is built as static HTML for maximum performance:
- No database queries
- No server-side processing
- CDN-ready (GitHub Pages serves from a global CDN)
- ~90+ Lighthouse score out of the box

## Support

For questions about this site structure or content, contact hello@ampicked.com

## License

Content © 2026 Ampicked. All rights reserved.
