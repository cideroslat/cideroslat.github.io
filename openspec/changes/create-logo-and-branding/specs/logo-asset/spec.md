## ADDED Requirements

### Requirement: Desktop logo SVG file exists
The system SHALL provide an SVG file at `assets/images/logo/logo.svg` containing the CIDEROS horizontal wordmark with icon mark, sized to fit a 140×32px container.

#### Scenario: Desktop logo renders in header
- **WHEN** the Jekyll site is built and a page is loaded
- **THEN** the browser SHALL display the desktop logo image in the header without a broken-image icon

#### Scenario: Desktop logo is readable at normal size
- **WHEN** the logo SVG is rendered at 140×32px
- **THEN** the wordmark "CIDEROS" SHALL be legible and the icon mark SHALL be visually distinct

### Requirement: Mobile logo SVG file exists
The system SHALL provide an SVG file at `assets/images/logo/logo-mobile.svg` containing the CIDEROS icon mark only (no wordmark), sized to fit a 32×32px container.

#### Scenario: Mobile logo renders in header on small viewports
- **WHEN** the Jekyll site is loaded on a screen ≤ 768px wide
- **THEN** the browser SHALL display the mobile icon-only logo without a broken-image icon

### Requirement: Logo SVG uses brand colors
The logo SVG files SHALL use only colors from the CIDEROS brand palette (deep teal `#0B2D3E`, electric cyan `#00D4FF`, and white `#FFFFFF` for reversed contexts).

#### Scenario: Logo on white background
- **WHEN** the logo is placed on a white (`#FFFFFF`) background
- **THEN** the icon and wordmark SHALL have sufficient contrast (WCAG AA minimum 4.5:1) against the background

#### Scenario: Logo on dark background
- **WHEN** the logo is placed on the primary dark teal (`#0B2D3E`) background
- **THEN** a reversed (light) version of the logo SHALL remain legible

### Requirement: Logo SVG is scalable and lightweight
The logo SVG files SHALL be hand-authored without embedded raster images or external dependencies, and each file SHALL be under 5KB.

#### Scenario: Logo scales without quality loss
- **WHEN** the logo SVG is displayed at 2× or 3× the intended size (e.g., on HiDPI screens)
- **THEN** the logo MUST render without pixelation or blur
