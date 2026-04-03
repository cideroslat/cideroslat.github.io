## Why

The current website is English-only, which excludes Spanish-speaking prospects and limits the business's reach. Adding a Spanish version — with manually curated translations for key messaging — allows the business to serve both audiences effectively and communicate its value proposition in culturally appropriate terms for each.

## What Changes

- Add a Jekyll multilingual structure using the `jekyll-multiple-languages-plugin` (or equivalent `_i18n` + data-file approach compatible with GitHub Pages)
- Extract all user-visible text into language data files (`_data/translations/en.yml` and `_data/translations/es.yml`)
- Create Spanish-language versions of all content pages: Home (hero), Services, About Us, and Contact
- Add a language selector component (flag/label toggle) displayed prominently in the site header
- Ensure navigation labels, footer, and call-box text are translated in both languages
- Keep design, layout, and theme identical across both language versions — only content changes
- **BREAKING**: URL structure changes — English content moves to `/en/` prefix (or English remains at root and Spanish at `/es/`) — existing URLs must redirect or be updated

## Capabilities

### New Capabilities

- `language-selector`: A header UI element allowing visitors to switch between English and Spanish with a single click, persisting the selected language across pages
- `i18n-content-structure`: The data file and directory structure (`_data/translations/`) that holds all translatable strings, page content, and manually authored translations for both languages
- `spanish-pages`: Spanish-translated versions of all site pages (Home, Services, About, Contact) using the same Serif layouts with Spanish content

### Modified Capabilities

- `landing-page`: Hero headline, sub-headline, CTA label, and features text must be sourced from i18n data files instead of being hardcoded in `index.md`
- `services-section`: Service titles and descriptions must be sourced from i18n data files or language-specific `_services/` collection variants
- `about-us-section`: Company mission and expertise content must support both languages via data files
- `contact-section`: Contact form labels and page intro must be translated

## Impact

- All existing page content files (`index.md`, `about.md`, `services.md`, `contact.md`) are modified to use Liquid i18n tags or data-variable references instead of hardcoded text
- All `_services/*.md` files either duplicated per language or refactored to pull titles/descriptions from `_data/translations/`
- `_data/menus.yml` navigation labels sourced from translation files or duplicated per language
- New dependency: a Jekyll i18n plugin or a custom Liquid-based translation helper (must be GitHub Pages-compatible — `jekyll-multiple-languages-plugin` is NOT on the GitHub Pages whitelist; a no-plugin approach using `_data/` files and Liquid will be used instead)
- GitHub Actions workflow may need to pass `JEKYLL_ENV` or additional build flags
- No database or backend changes — purely static file additions and template modifications
