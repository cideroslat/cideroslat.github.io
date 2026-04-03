## MODIFIED Requirements

### Requirement: Landing page displays a hero section
The landing page (`index.md`) SHALL render a full-width hero section. The hero headline, sub-headline, and CTA label SHALL be sourced from `site.data.translations[page.lang]` rather than being hardcoded in the Markdown file. Both the English (`/`) and Spanish (`/es/`) home pages SHALL use the same `home` layout, with language determined by the `lang` front matter key.

#### Scenario: Hero section is visible above the fold on English page
- **WHEN** a visitor lands on `/`
- **THEN** the hero headline, sub-headline, and CTA button are visible without scrolling, in English

#### Scenario: Hero section is visible above the fold on Spanish page
- **WHEN** a visitor lands on `/es/`
- **THEN** the hero headline, sub-headline, and CTA button are visible without scrolling, in Spanish

#### Scenario: CTA button navigates to contact or services in both languages
- **WHEN** a visitor clicks the primary CTA on the English home page
- **THEN** they navigate to `/services/`

#### Scenario: CTA button navigates to Spanish services from Spanish home
- **WHEN** a visitor clicks the primary CTA on the Spanish home page
- **THEN** they navigate to `/es/services/`

### Requirement: Landing page includes a services preview
The landing page SHALL include a services preview section. When rendered in English, it SHALL display services from the `_services/` collection. When rendered in Spanish, it SHALL display services from the `_services_es/` collection.

#### Scenario: English home shows English services preview
- **WHEN** the English home page is rendered
- **THEN** the services preview section displays English service titles and excerpts

#### Scenario: Spanish home shows Spanish services preview
- **WHEN** the Spanish home page is rendered
- **THEN** the services preview section displays Spanish service titles and excerpts
