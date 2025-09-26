# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an academic personal homepage built with Jekyll and hosted on GitHub Pages. It features automatic Google Scholar citation updates, responsive design, and academic portfolio showcase.

## Development Commands

### Local Development
- **Start development server**: `bash run_server.sh` or `bundle exec jekyll liveserve`
- **Install dependencies**: `bundle install`
- **Update gems**: `bundle update`

### Prerequisites
- Ruby, RubyGems, GCC, and Make (follow [Jekyll installation guide](https://jekyllrb.com/docs/installation/#requirements))
- Bundler gem: `gem install bundler`

## Architecture

### Core Structure
- **Jekyll Static Site**: Uses GitHub Pages compatible Jekyll with kramdown markdown processor
- **Google Scholar Integration**: Automated citation data crawling via GitHub Actions
- **Responsive Design**: Based on Minimal Mistakes theme with academic customizations

### Key Components

#### Configuration (`_config.yml`)
- Site metadata, author information, and Jekyll settings
- Google Analytics and SEO configurations
- Plugin definitions (jekyll-feed, jekyll-sitemap, hawkins)

#### Content Structure
- `_pages/about.md`: Main homepage content with academic profile
- `_data/navigation.yml`: Site navigation menu structure
- `_layouts/`: Jekyll layout templates
- `_includes/`: Reusable Jekyll components
- `_sass/`: Styling and CSS files
- `assets/`: Static assets and compiled resources

#### Google Scholar Automation
- `google_scholar_crawler/main.py`: Python script for fetching citation data
- `requirements.txt`: Python dependencies (jsonpickle, scholarly)
- `.github/workflows/google_scholar_crawler.yaml`: Daily automated citation updates
- Outputs to `google-scholar-stats` branch as JSON files

### Citation Display System
The homepage automatically displays citation metrics using:
- Dynamic citation badges from `gs_data_shieldsio.json`
- Paper-specific citation counts via `<span class='show_paper_citations' data='SCHOLAR_ID'></span>`
- CDN or direct GitHub raw file serving based on `google_scholar_stats_use_cdn` setting

### Content Management
- Academic content in Jekyll/Liquid templates with HTML+Markdown syntax
- Section-based navigation (About Me, News, Publications, etc.)
- Automatic paper citation integration from Google Scholar data

## Environment Setup

### Google Scholar Configuration
1. Set `GOOGLE_SCHOLAR_ID` repository secret with your Scholar ID
2. Enable GitHub Actions workflows
3. Citations update automatically at 08:00 UTC daily and on pushes

### Local Testing
1. Clone repository
2. Run `bundle install` to install Jekyll dependencies
3. Use `bash run_server.sh` for live reload development
4. Access at http://127.0.0.1:4000

## File Hierarchy

```
├── _config.yml              # Jekyll configuration
├── _pages/about.md          # Main homepage content
├── _data/navigation.yml     # Site navigation
├── _layouts/                # Jekyll layouts
├── _includes/               # Reusable components
├── _sass/                   # Styling files
├── assets/                  # Static assets
├── google_scholar_crawler/  # Citation automation
├── images/                  # Image assets
└── run_server.sh            # Development server script
```

This is a Jekyll-based academic website optimized for showcasing research publications with automated citation tracking.