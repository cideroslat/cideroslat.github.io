## ADDED Requirements

### Requirement: Language selector is displayed in the site header
The site header SHALL display a language selector on every page that allows the visitor to switch between English and Spanish. The selector SHALL visually indicate the currently active language. The selector SHALL be composed of plain HTML links — no JavaScript required.

#### Scenario: Visitor sees language selector on home page
- **WHEN** a visitor loads any page on the site
- **THEN** the header displays two language options: "EN" and "ES"

#### Scenario: Active language is visually distinguished
- **WHEN** a visitor is on an English page
- **THEN** the "EN" option in the language selector appears active (e.g., bold or underlined) and "ES" is a plain link

#### Scenario: Active language is visually distinguished on Spanish page
- **WHEN** a visitor is on a Spanish page under `/es/`
- **THEN** the "ES" option in the language selector appears active and "EN" is a plain link

### Requirement: Language selector navigates to the equivalent page in the other language
The language selector links SHALL navigate to the equivalent page in the other language (e.g., from `/about/` to `/es/about/`, not to the home page). When an equivalent Spanish URL cannot be determined, the link SHALL fall back to `/es/`.

#### Scenario: Switching from English About to Spanish About
- **WHEN** a visitor clicks "ES" while on `/about/`
- **THEN** the browser navigates to `/es/about/`

#### Scenario: Switching from Spanish Services to English Services
- **WHEN** a visitor clicks "EN" while on `/es/services/`
- **THEN** the browser navigates to `/services/`
