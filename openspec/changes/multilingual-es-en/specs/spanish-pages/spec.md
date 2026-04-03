## ADDED Requirements

### Requirement: Spanish versions of all site pages exist under /es/
The site SHALL provide Spanish-language versions of all four main pages at the following URLs: `/es/` (home), `/es/services/`, `/es/about/`, `/es/contact/`. Each Spanish page SHALL use the same Serif layout as its English counterpart and SHALL render content from `_data/translations/es.yml`.

#### Scenario: Spanish home page is accessible
- **WHEN** a visitor navigates to `/es/`
- **THEN** the home page is rendered with Spanish content including the hero headline, sub-headline, and CTA label

#### Scenario: Spanish services page is accessible
- **WHEN** a visitor navigates to `/es/services/`
- **THEN** the services page renders with Spanish service titles and descriptions from the `_services_es/` collection

#### Scenario: Spanish about page is accessible
- **WHEN** a visitor navigates to `/es/about/`
- **THEN** the about page renders with Spanish mission and expertise text

#### Scenario: Spanish contact page is accessible
- **WHEN** a visitor navigates to `/es/contact/`
- **THEN** the contact page renders with Spanish form labels and page introduction

### Requirement: Spanish pages use manually authored translations
Spanish page content SHALL be authored manually — not auto-translated. The content of `_data/translations/es.yml` and `_services_es/` collection files SHALL contain human-written Spanish text that is culturally appropriate and accurately conveys the business's value proposition.

#### Scenario: Spanish hero headline is distinct from English auto-translation
- **WHEN** the Spanish home page hero headline is reviewed
- **THEN** the text is idiomatic Spanish and not a word-for-word machine translation of the English

### Requirement: Spanish pages are responsive
Spanish pages SHALL render correctly on mobile, tablet, and desktop viewports, inheriting all responsive styles from the Serif theme.

#### Scenario: Spanish home page renders on mobile
- **WHEN** the Spanish home page is loaded at 375px viewport width
- **THEN** the hero headline and CTA button are fully visible without horizontal scrolling
