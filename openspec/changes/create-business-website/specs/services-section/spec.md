## ADDED Requirements

### Requirement: Services page lists all offered computer vision services
The site SHALL include a `/services/` page that lists each service with a name, icon or image, and description. Services SHALL be defined in `_data/services.yaml` so they can be updated without modifying HTML templates.

#### Scenario: Services page displays all entries from data file
- **WHEN** a visitor navigates to `/services/`
- **THEN** all services defined in `_data/services.yaml` are rendered on the page

#### Scenario: Each service entry includes a name and description
- **WHEN** the services page is rendered
- **THEN** each service card shows at minimum: a service name and a short description

### Requirement: Services content is data-driven
Service entries SHALL be managed via `_data/services.yaml`. Adding a new service entry to that file SHALL automatically include it on the rendered page without further template changes.

#### Scenario: Adding a new service to YAML file includes it on the page
- **WHEN** a new entry is added to `_data/services.yaml` and the site is rebuilt
- **THEN** the new service appears on the Services page

### Requirement: Services page is linked from main navigation
The Services page SHALL be accessible via the main navigation header on all pages.

#### Scenario: Services link in navigation opens the services page
- **WHEN** a visitor clicks "Services" in the navigation menu
- **THEN** the browser navigates to `/services/`
