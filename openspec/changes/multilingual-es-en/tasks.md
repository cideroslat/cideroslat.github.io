## 1. Translation Data Structure

- [x] 1.1 Create `_data/translations/en.yml` with all English translatable strings (nav labels, hero headline, sub-headline, CTA, features, services intro, about intro, contact form labels, footer)
- [x] 1.2 Create `_data/translations/es.yml` with manually authored Spanish translations for all keys in `en.yml`
- [x] 1.3 Add `lang: en` front matter to all existing English root pages (`index.md`, `about.md`, `services.md`, `contact.md`)

## 2. Language Selector & Header Override

- [x] 2.1 Create `_includes/language-selector.html` rendering "EN" and "ES" links, with active-language styling based on `page.lang`
- [x] 2.2 Create a local override of `_includes/header.html` (copying from the remote theme and injecting `{% include language-selector.html %}`)
- [x] 2.3 Create `_includes/hreflang.html` with `<link rel="alternate">` tags for both languages
- [x] 2.4 Create a local override of `_layouts/default.html` (copying from the remote theme) to include `{% include hreflang.html %}` in `<head>`
- [x] 2.5 Verify language selector appears in the header on both English and Spanish pages

## 3. Spanish Services Collection

- [x] 3.1 Register `_services_es` collection in `_config.yml` with `output: true` and `sort_by: weight`
- [x] 3.2 Add collection defaults in `_config.yml` to assign `layout: service` and `lang: es` to all `_services_es` entries
- [x] 3.3 Create `_services_es/consultoria-vision-computacional.md` (Spanish version of computer vision consulting)
- [x] 3.4 Create `_services_es/deteccion-de-objetos.md` (Spanish version of object detection)
- [x] 3.5 Create `_services_es/inspeccion-de-calidad.md` (Spanish version of quality inspection)
- [x] 3.6 Create `_services_es/analitica-de-video.md` (Spanish version of video analytics)

## 4. Layout Overrides for Language-Aware Rendering

- [x] 4.1 Create a local override of `_layouts/home.html` that switches the services loop between `site.services` (English) and `site.services_es` (Spanish) based on `page.lang`
- [x] 4.2 Create a local override of `_layouts/services.html` that renders `site.services_es` when `page.lang == 'es'`
- [x] 4.3 Update `_includes/call.html` override (or use translation lookup) so the "Contact" button label is sourced from `translations[page.lang].contact_button_label`

## 5. Spanish Pages

- [x] 5.1 Create `_pages/es/index.md` — Spanish home page with `lang: es`, `permalink: /es/`, and hero content from `_data/translations/es.yml`
- [x] 5.2 Create `_pages/es/services.md` — Spanish services page with `lang: es` and `permalink: /es/services/`
- [x] 5.3 Create `_pages/es/about.md` — Spanish about page with `lang: es`, `permalink: /es/about/`, and Spanish mission content
- [x] 5.4 Create `_pages/es/contact.md` — Spanish contact page with `lang: es`, `permalink: /es/contact/`, Spanish form labels, and same Formspree endpoint with Spanish `_subject`

## 6. Navigation Localisation

- [x] 6.1 Create `_data/translations/en.yml` nav section: keys for Home, Services, About, Contact labels (merge into task 1.1)
- [x] 6.2 Create a local override of `_includes/main-menu.html` that sources navigation link labels from `site.data.translations[page.lang].nav` and uses language-prefixed URLs when `page.lang == 'es'`
- [x] 6.3 Verify English navigation still links to `/`, `/services/`, `/about/`, `/contact/`
- [x] 6.4 Verify Spanish navigation links to `/es/`, `/es/services/`, `/es/about/`, `/es/contact/`

## 7. Content Refactoring (English Pages)

- [x] 7.1 Update `index.md` hero headline and sub-headline to use `site.data.translations.en.hero_headline` and `site.data.translations.en.hero_subheadline` (or keep as Markdown content with `lang: en` for layout branching)
- [x] 7.2 Update `contact.md` form labels to use translation keys for Name, Email, Message, and Submit fields
- [x] 7.3 Verify English pages still render correctly with no visual regressions

## 8. Build Verification & Deployment

- [x] 8.1 Run `bundle exec jekyll build` locally and confirm no errors
- [ ] 8.2 Run `bundle exec jekyll serve` and manually verify: `/` (EN home), `/es/` (ES home), `/services/`, `/es/services/`, `/about/`, `/es/about/`, `/contact/`, `/es/contact/`
- [ ] 8.3 Verify language selector shows correct active state on each page
- [ ] 8.4 Verify hreflang tags are present in page `<head>` on all pages
- [ ] 8.5 Push to `main` and confirm GitHub Actions build succeeds
- [ ] 8.6 Smoke test all 8 pages on the live `https://cideroslat.github.io` site

