## ADDED Requirements

### Requirement: Brand color tokens defined as CSS custom properties
The system SHALL define the following CSS custom properties on the `:root` selector in `assets/css/custom.scss`:

| Token | Value | Usage |
|-------|-------|-------|
| `--color-primary` | `#0B2D3E` | Headers, hero backgrounds |
| `--color-secondary` | `#0F4C5C` | Card backgrounds, section dividers |
| `--color-accent` | `#00D4FF` | CTAs, hover states, links |
| `--color-accent-dark` | `#00A8CC` | Pressed/active CTA states |
| `--color-text` | `#1A1A2E` | Body text |
| `--color-text-muted` | `#5A6B77` | Secondary text, captions |
| `--color-bg` | `#FFFFFF` | Page background |
| `--color-bg-alt` | `#F4F7F9` | Alternating section backgrounds |
| `--color-border` | `#D8E4EA` | Borders and dividers |

#### Scenario: Color tokens are available globally
- **WHEN** any CSS rule on any page references `var(--color-accent)`
- **THEN** the value SHALL resolve to `#00D4FF` without fallback

### Requirement: Accent color applied to interactive elements
The system SHALL override the Jekyll Serif theme's default link and button colors using the brand accent token.

#### Scenario: Link hover uses accent color
- **WHEN** a user hovers over a navigation or inline link
- **THEN** the link color SHALL change to `var(--color-accent)` (`#00D4FF`)

#### Scenario: Contact form focus ring uses accent color
- **WHEN** a user focuses a form input or textarea
- **THEN** the focus outline and border SHALL use `var(--color-accent)` (`#00D4FF`)

### Requirement: Primary color applied to hero and header regions
The system SHALL apply `var(--color-primary)` as the background for the site header and hero sections.

#### Scenario: Header background uses primary brand color
- **WHEN** any page is loaded
- **THEN** the site header background SHALL render as `#0B2D3E`

### Requirement: Alternate background applied to every other section
The system SHALL apply `var(--color-bg-alt)` to alternating content sections so that the page has visual rhythm.

#### Scenario: Alternating section backgrounds
- **WHEN** the homepage is loaded
- **THEN** consecutive content sections SHALL alternate between `var(--color-bg)` and `var(--color-bg-alt)`
