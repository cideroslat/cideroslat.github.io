## ADDED Requirements

### Requirement: All translatable strings are stored in language data files
The site SHALL store all user-visible text strings in two YAML data files: `_data/translations/en.yml` (English) and `_data/translations/es.yml` (Spanish). Pages SHALL reference strings via `site.data.translations[page.lang].<key>` rather than hardcoding text in Markdown or HTML files.

#### Scenario: Translation key is resolved for English page
- **WHEN** an English page with `lang: en` is rendered
- **THEN** `site.data.translations.en` is used to supply all translatable strings on that page

#### Scenario: Translation key is resolved for Spanish page
- **WHEN** a Spanish page with `lang: es` is rendered
- **THEN** `site.data.translations.es` is used to supply all translatable strings on that page

#### Scenario: Missing translation key falls back to English
- **WHEN** a key exists in `en.yml` but not in `es.yml`
- **THEN** the Spanish page renders the English string as a fallback rather than showing blank content

### Requirement: Each page declares its language in front matter
Every page and collection item SHALL declare a `lang:` front matter key set to either `en` or `es`. Pages without a `lang:` key SHALL default to `en`.

#### Scenario: English page lang front matter
- **WHEN** `index.md` is processed by Jekyll
- **THEN** `page.lang` evaluates to `en`

#### Scenario: Spanish page lang front matter
- **WHEN** `_pages/es/index.md` is processed by Jekyll
- **THEN** `page.lang` evaluates to `es`

### Requirement: hreflang meta tags are present on all pages
Every rendered HTML page SHALL include `<link rel="alternate" hreflang="en">` and `<link rel="alternate" hreflang="es">` tags in the `<head>` pointing to the English and Spanish equivalents of that page respectively, to support correct search engine indexing.

#### Scenario: hreflang tags on English home page
- **WHEN** the English home page is rendered
- **THEN** the HTML `<head>` contains `<link rel="alternate" hreflang="en" href="https://cideroslat.github.io/">` and `<link rel="alternate" hreflang="es" href="https://cideroslat.github.io/es/">`
