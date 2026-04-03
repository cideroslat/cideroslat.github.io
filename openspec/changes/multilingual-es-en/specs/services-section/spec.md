## MODIFIED Requirements

### Requirement: Services page lists all offered computer vision services
The services page SHALL list service entries. The English services page (`/services/`) SHALL render from the `_services/` collection. The Spanish services page (`/es/services/`) SHALL render from the `_services_es/` collection. Service titles and descriptions SHALL be the language-appropriate content from each respective collection.

#### Scenario: English services page displays English entries
- **WHEN** a visitor navigates to `/services/`
- **THEN** all English service entries from `_services/` are rendered with English titles and descriptions

#### Scenario: Spanish services page displays Spanish entries
- **WHEN** a visitor navigates to `/es/services/`
- **THEN** all Spanish service entries from `_services_es/` are rendered with Spanish titles and descriptions

### Requirement: Services content is data-driven per language
Spanish service entries SHALL be managed in the `_services_es/` Jekyll collection. Adding a new Spanish service file to that collection SHALL automatically include it on the Spanish services page without template changes.

#### Scenario: Adding a new Spanish service file includes it on Spanish services page
- **WHEN** a new `.md` file is added to `_services_es/` and the site is rebuilt
- **THEN** the new Spanish service appears on `/es/services/`

### Requirement: Services page is linked from main navigation
Both the English and Spanish navigation menus SHALL include a link to their respective services pages.

#### Scenario: English navigation Services link routes to /services/
- **WHEN** a visitor clicks "Services" in the English navigation
- **THEN** the browser navigates to `/services/`

#### Scenario: Spanish navigation link routes to /es/services/
- **WHEN** a visitor clicks the services link in the Spanish navigation
- **THEN** the browser navigates to `/es/services/`
