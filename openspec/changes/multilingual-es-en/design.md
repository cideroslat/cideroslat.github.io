## Context

The site is a Jekyll static site using the Jekyll Serif remote theme, hosted on GitHub Pages via a GitHub Actions workflow. All pages are currently English-only with content hardcoded in Markdown files (`index.md`, `about.md`, `services.md`, `contact.md`) and the `_services/` collection. The business wants to add Spanish as a second language, with manually authored translations for all key content — not automatic translation.

The constraint is that GitHub Pages (even via GitHub Actions) only supports a curated set of Jekyll plugins. `jekyll-multiple-languages-plugin` is not whitelisted. The solution must work without non-whitelisted plugins using standard Jekyll features only.

## Goals / Non-Goals

**Goals:**
- Support English (`/`) and Spanish (`/es/`) versions of the site with a no-plugin, data-file approach
- Provide a visible language selector in the header to switch between languages
- Allow manually authored translations for all content — no automatic translation
- Keep the Serif theme layout, design, and navigation structure identical in both languages
- Remain deployable via GitHub Actions on GitHub Pages without any plugin changes

**Non-Goals:**
- Automatic or machine translation of any content
- More than two languages (EN + ES only)
- Browser locale detection / automatic language redirect
- CMS or admin UI for managing translations
- URL path localisation beyond `/` (English root) and `/es/` (Spanish prefix)

## Decisions

### 1. No-Plugin Translation via `_data/` + Liquid

**Decision**: Use two YAML translation data files (`_data/translations/en.yml` and `_data/translations/es.yml`) to hold all translatable strings. Pages use a Liquid variable (`page.lang`) to look up the correct file at render time via `site.data.translations[page.lang]`.

**Rationale**: Works with any Jekyll version and any plugin configuration. No whitelist dependency. No gem changes needed. Content authors only edit YAML files to update translations.

**Alternative considered**: `jekyll-multiple-languages-plugin` — rejected because it is not on the GitHub Pages whitelist and would require a custom build step that adds complexity without benefit.

**Alternative considered**: Separate `_includes/` files per language — rejected because it duplicates layout code and makes design changes harder to maintain.

### 2. URL Structure: English at Root, Spanish under `/es/`

**Decision**: English pages remain at their current URLs (`/`, `/services/`, `/about/`, `/contact/`). Spanish pages live at `/es/`, `/es/services/`, `/es/about/`, `/es/contact/`.

**Rationale**: Preserves existing English URLs (no broken links, no redirects needed). Spanish is an additive path. This is the most common convention for bilingual static sites and is SEO-friendly when combined with `hreflang` meta tags.

**Alternative considered**: Both languages under prefixed paths (`/en/` and `/es/`) — rejected because it breaks current English URLs and requires redirects from `/` to `/en/`.

### 3. Spanish Pages as a Separate `_pages/es/` Directory

**Decision**: Spanish pages live in `_pages/es/` (e.g., `_pages/es/index.md`, `_pages/es/services.md`) with `permalink: /es/`, `lang: es` front matter. English pages remain at the root level.

**Rationale**: Keeps files organised and clearly separated per language. Each Spanish page sets `lang: es` so Liquid templates resolve to `site.data.translations.es`. No custom collection needed.

**Alternative considered**: A single page file with language branching in Liquid — rejected because it makes content editing confusing and mixes two languages in one file.

### 4. Language Selector via Custom `_includes/language-selector.html`

**Decision**: Add a `_includes/language-selector.html` snippet that renders two links: one to the root English URL and one to the `/es/` Spanish URL of the current page. The active language link is styled differently. This include is injected via a layout override that wraps the Serif `header.html`.

**Rationale**: Simple, no JavaScript required, works with any browser, visible on every page. Since Serif uses a `_includes/header.html`, we override it in the site's own `_includes/` directory (which takes precedence over the remote theme).

**Alternative considered**: JavaScript-based language toggle — rejected because it adds JS dependency and complicates static hosting.

### 5. Spanish Services via `_services_es/` Collection

**Decision**: Create a `_services_es/` Jekyll collection for Spanish service content. Entries mirror the English `_services/` collection but with Spanish titles and descriptions. The `services` layout is reused.

**Rationale**: Clean separation of content. Avoids cluttering English service files with bilingual front matter. The Serif home layout's service loop will be overridden per language.

**Alternative considered**: Adding `title_es:` / `description_es:` keys to existing English `_services/*.md` files — rejected because it makes the files messy and couples both languages in one file.

### 6. `hreflang` SEO Tags

**Decision**: Add `<link rel="alternate" hreflang="en">` and `<link rel="alternate" hreflang="es">` meta tags to all pages via a `_includes/hreflang.html` include, referenced in the default layout override.

**Rationale**: Required for correct SEO indexing of multilingual sites. Without it, search engines may treat EN and ES pages as duplicate content.

## Risks / Trade-offs

- **Layout override maintenance** → Overriding `_includes/header.html` means theme updates to the header must be manually merged. Mitigate by keeping overrides minimal (only add language selector, don't restructure).
- **Translation YAML drift** → If a key exists in `en.yml` but not `es.yml`, the Spanish page renders blank for that string. Mitigate by keeping both files in sync and using a fallback: `| default: site.data.translations.en[key]`.
- **Service collection duplication** → Maintaining two collections (`_services/` and `_services_es/`) doubles the content authoring work for services. Acceptable for a small set (4 services); re-evaluate if the catalogue grows.
- **No automatic redirects** → Users who bookmark an English page and want Spanish must use the language selector. Acceptable per Non-Goals (no browser locale detection).

## Migration Plan

1. Create `_data/translations/en.yml` and `_data/translations/es.yml` with all translatable strings
2. Override `_includes/header.html` to include the language selector
3. Add `_includes/language-selector.html` and `_includes/hreflang.html`
4. Refactor English root pages (`index.md`, `about.md`, `services.md`, `contact.md`) to use `lang: en` and Liquid translation lookups
5. Create `_pages/es/` directory with Spanish page files
6. Create `_services_es/` collection with Spanish service content and register it in `_config.yml`
7. Override `_layouts/home.html` and `_layouts/services.html` locally to switch service collection based on `page.lang`
8. Add `hreflang` include to default layout
9. Build and verify locally; push to `main` — GitHub Actions deploys

**Rollback**: Revert all new files and the page front matter changes. English pages return to current state with zero data-file lookups.

## Open Questions

- What Spanish business name / tagline should appear in the hero? (Or is "VisionTech Solutions" kept as-is?)
- Should the contact form show a Spanish success/error message, or is a redirect to a static thank-you page in Spanish preferred?
- Is there a preferred Spanish URL slug (e.g., `/es/servicios/` or keep `/es/services/`)?
