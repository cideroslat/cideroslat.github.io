## ADDED Requirements

### Requirement: Logo image displayed in site header
The system SHALL display the CIDEROS logo in the site header on all pages by configuring the `logo` block in `_config.yml` to point to the correct asset paths.

#### Scenario: Desktop header shows horizontal logo
- **WHEN** any page is loaded on a viewport wider than 768px
- **THEN** the header SHALL render the CIDEROS desktop wordmark logo (`assets/images/logo/logo.svg`)

#### Scenario: Mobile header shows icon-only logo
- **WHEN** any page is loaded on a viewport ≤ 768px wide
- **THEN** the header SHALL render the CIDEROS mobile icon logo (`assets/images/logo/logo-mobile.svg`)

### Requirement: Logo links to the site homepage
The logo image in the header SHALL be wrapped in an anchor tag that links to the site root (`/`).

#### Scenario: Clicking the logo navigates to homepage
- **WHEN** a user clicks the logo in the header
- **THEN** the browser SHALL navigate to the site homepage (`/`)

### Requirement: Brand styles apply to both EN and ES versions
The brand color system and typography specs SHALL be applied identically on all pages under `/` (English) and `/es/` (Spanish).

#### Scenario: Spanish pages use the same brand palette
- **WHEN** a user navigates to any page under `/es/`
- **THEN** the header background, accent colors, and typography SHALL match the English site exactly

### Requirement: _config.yml logo paths correctly reference asset files
The `_config.yml` `logo` configuration SHALL reference paths that resolve correctly when processed by Jekyll's `relative_url` filter from the `assets/` base.

#### Scenario: Built site contains logo image files
- **WHEN** `jekyll build` is run
- **THEN** the `_site/assets/images/logo/logo.svg` and `_site/assets/images/logo/logo-mobile.svg` files SHALL exist in the build output
