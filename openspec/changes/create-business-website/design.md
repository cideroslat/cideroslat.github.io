## Context

This is a greenfield static website for a computer vision consulting/solutions business, to be hosted on GitHub Pages. The site will use Jekyll with the **Jekyll Serif** theme and serve as the primary public-facing presence for the business. The reference aesthetic is https://www.antac.ai/ — clean, professional, with a strong focus on visual AI/computer vision identity.

There is no existing site; all files will be created from scratch. The repository is already on GitHub (`cideroslat.github.io`), which means GitHub Pages publishing is available via the `main` branch or a `gh-pages` branch.

## Goals / Non-Goals

**Goals:**
- Build and deploy a Jekyll-based static site using the Jekyll Serif theme
- Deliver four content sections: Hero/Landing, Services, About Us, Contact
- Ensure the site is functional on GitHub Pages (no unsupported plugins)
- Keep the design clean and modern with minimal customization of the base theme

**Non-Goals:**
- Backend/server-side functionality (no CMS, databases, or dynamic APIs)
- Custom theme development — Serif is used as-is with content overrides only
- Multi-language support
- Blog or news section
- Authentication or user accounts

## Decisions

### 1. Jekyll Serif via Remote Theme

**Decision**: Use `remote_theme: jekyll/jekyll-serif-theme` in `_config.yml`.

**Rationale**: GitHub Pages natively supports `jekyll-remote-theme`, meaning no local Gem management is required for deployment. This avoids version pinning issues and simplifies the `Gemfile` to just `github-pages` gem.

**Alternative considered**: Forking Serif and modifying it directly — rejected because it adds maintenance overhead and drift risk.

### 2. Content via `_data/` YAML Files

**Decision**: Populate services, team/about content, and navigation via YAML data files in `_data/`.

**Rationale**: Keeps content separate from layout, making future updates easier without touching HTML/Liquid templates. The Serif theme expects this pattern for services and team members.

**Alternative considered**: Hardcoding content directly into page layouts — rejected for maintainability.

### 3. Single-Page vs. Multi-Page Layout

**Decision**: Use a multi-page site with dedicated pages (`/services/`, `/about/`, `/contact/`) linked from the landing page, following Serif's default structure.

**Rationale**: The Serif theme is designed for multi-page sites and ships with route-aware navigation. A single-page approach would require overriding Serif's layout structure significantly.

**Alternative considered**: Single-page scrolling site — rejected to avoid fighting the theme's conventions.

### 4. Contact Form via Formspree

**Decision**: Use [Formspree](https://formspree.io) for the contact form backend.

**Rationale**: GitHub Pages cannot run server-side code. Formspree provides a free, no-backend form endpoint that works with static sites. The Serif theme ships with a contact page template that works with external form endpoints.

**Alternative considered**: Mailto link only — acceptable fallback but less professional for a business site.

### 5. GitHub Pages Deployment Branch

**Decision**: Deploy from the `main` branch, root directory.

**Rationale**: Simplest configuration for a user/organization GitHub Pages repository (`<username>.github.io`). No separate `gh-pages` branch needed.

## Risks / Trade-offs

- **Jekyll Serif theme updates could break layout** → Pin the remote theme to a specific commit SHA once the site is stable.
- **Formspree free tier limits (50 submissions/month)** → Acceptable for early-stage business; can upgrade or swap to Netlify Forms later. No code changes needed.
- **GitHub Pages whitelist plugins only** → Avoid non-whitelisted plugins. All plugins used must appear on the [GitHub Pages supported versions list](https://pages.github.com/versions/).
- **Remote theme load time in local development** → Use `bundle exec jekyll serve` with the `github-pages` gem for accurate local preview; theme is cached after first fetch.

## Migration Plan

1. Add Jekyll project files (`_config.yml`, `Gemfile`, `index.md`, `_pages/`) to the repository root
2. Add content YAML to `_data/` (services, team, navigation)
3. Add any custom CSS overrides to `assets/css/custom.scss` if needed
4. Push to `main` branch
5. Enable GitHub Pages in repository Settings → Pages → Source: `main` / `/(root)`
6. Verify build succeeds in the Actions tab (GitHub Pages build action)

**Rollback**: Remove or revert the Jekyll files; GitHub Pages will simply serve no content (or a bare README).

## Open Questions

- What is the business name and tagline? (Needed for `_config.yml` `title` and hero headline)
- Are there specific services to list (e.g., object detection, quality inspection, video analytics)?
- Is there a logo or brand color to apply via custom CSS?
- Will a Formspree account be created, or is a `mailto:` link preferred initially?
