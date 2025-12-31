# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a multi-site GitHub Pages project for Ludovica Sidoti containing three separate static websites:

1. **Main website** (`ludovicasidoti.com`) - Professional personal website at the root directory
2. **Link list** (`meetlulu.org`) - Simple link aggregation page in `meetlulu/` subdirectory
3. **Travel blog** (`lululabs.org`) - Blog with post grid layout in `lululabs/` subdirectory

Each subdirectory (`lululabs/` and `meetlulu/`) is a separate Git repository with its own GitHub Pages deployment.

## Repository Structure

- Root directory = main website (ludovicasidoti.com)
  - `index.html` - Main site content
  - Hosted at https://davidorban.github.io/ludovicasidoti/
  
- `meetlulu/` = separate Git repository
  - Independent `.git` directory
  - Hosted at https://davidorban.github.io/meetlulu/
  
- `lululabs/` = separate Git repository
  - Independent `.git` directory
  - Hosted at https://davidorban.github.io/lululabs/

## Development Commands

### Viewing Sites Locally
```bash
# All sites are static HTML - just open in browser
open index.html                    # Main site
open meetlulu/index.html          # Link list
open lululabs/index.html          # Travel blog
```

### Deploying Changes

Each site requires separate Git operations because they're independent repositories:

```bash
# Deploy main site (ludovicasidoti.com)
git add .
git commit -m "Update: description"
git push

# Deploy link list (meetlulu.org)
cd meetlulu
git add .
git commit -m "Update: description"
git push
cd ..

# Deploy travel blog (lululabs.org)
cd lululabs
git add .
git commit -m "Update: description"
git push
cd ..
```

GitHub Pages automatically deploys changes within 1-2 minutes after push.

## Important Context

### Git Repository Boundaries
- **Critical**: The subdirectories `meetlulu/` and `lululabs/` each contain their own `.git` directory
- When making changes, always be aware of which repository context you're in
- Running `git status` in root vs. subdirectories will show different repositories
- Each site must be committed and pushed separately from its own directory

### DNS Configuration
All three domains use the same GitHub Pages A records:
- 185.199.108.153
- 185.199.109.153
- 185.199.110.153
- 185.199.111.153

### Static HTML Sites
- No build process, bundlers, or package managers
- Direct HTML/CSS editing
- No testing framework in place
- Changes are immediately visible after file save

### Content Customization
When updating content:
- Email placeholders are `contact@example.com` - should be replaced with real addresses
- Emoji placeholders (🦄, travel emojis) can be replaced with actual images
- Each site has inline CSS in `<style>` tags within `index.html`
- Color gradients use consistent branding: `#ff6ec7` (pink), `#a855f7` (purple), `#7dd3fc` (blue)

### GitHub Pages URLs
- Main: https://davidorban.github.io/ludovicasidoti/ → ludovicasidoti.com
- Meet: https://davidorban.github.io/meetlulu/ → meetlulu.org  
- Labs: https://davidorban.github.io/lululabs/ → lululabs.org

## Common Tasks

### Adding a New Blog Post to lululabs
Edit `lululabs/index.html` and duplicate a `.post-card` section, then deploy from the `lululabs/` directory.

### Updating Links in meetlulu
Edit `meetlulu/index.html` link sections, then deploy from the `meetlulu/` directory.

### Checking Deployment Status
```bash
# Check git status for each site
git status                    # Main site
cd meetlulu && git status     # Link list
cd ../lululabs && git status  # Travel blog
```

### Verifying Current Repository
```bash
# Show which repository you're in
git remote -v
```

## Co-authoring Commits
When making commits, include at the end of commit messages:
```
Co-Authored-By: Warp <agent@warp.dev>
```
