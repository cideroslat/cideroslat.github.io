## MODIFIED Requirements

### Requirement: About Us page describes the company mission and expertise
The About Us page SHALL exist in both English (`/about/`) and Spanish (`/es/about/`). Body content (mission statement, expertise description, values) SHALL be sourced from `_data/translations[page.lang]` or from language-specific Markdown content. The Spanish version SHALL use manually authored text.

#### Scenario: English about page renders English content
- **WHEN** a visitor navigates to `/about/`
- **THEN** the page displays English mission and expertise content

#### Scenario: Spanish about page renders Spanish content
- **WHEN** a visitor navigates to `/es/about/`
- **THEN** the page displays Spanish mission and expertise content

### Requirement: About page is linked from main navigation in both languages
The About page SHALL be accessible via the navigation header in both the English and Spanish versions of the site.

#### Scenario: English About navigation link
- **WHEN** a visitor clicks "About" in the English navigation
- **THEN** the browser navigates to `/about/`

#### Scenario: Spanish About navigation link
- **WHEN** a visitor clicks the about link in the Spanish navigation
- **THEN** the browser navigates to `/es/about/`
