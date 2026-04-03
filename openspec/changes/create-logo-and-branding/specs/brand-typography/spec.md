## ADDED Requirements

### Requirement: Inter font imported from Google Fonts CDN
The system SHALL import the Inter typeface (weights 400, 500, 700) from Google Fonts CDN via a `@import` statement at the top of `assets/css/custom.scss`.

#### Scenario: Inter font loads on supported browsers
- **WHEN** a page is loaded in a modern browser with internet access
- **THEN** all text SHALL render in Inter; fallback to `system-ui, sans-serif` if the CDN is unreachable

### Requirement: Typography scale defined as CSS custom properties
The system SHALL define the following CSS custom properties on the `:root` selector:

| Token | Value |
|-------|-------|
| `--font-family` | `'Inter', system-ui, sans-serif` |
| `--font-size-xs` | `0.75rem` |
| `--font-size-sm` | `0.875rem` |
| `--font-size-base` | `1rem` |
| `--font-size-lg` | `1.125rem` |
| `--font-size-xl` | `1.375rem` |
| `--font-size-2xl` | `1.75rem` |
| `--font-size-3xl` | `2.25rem` |
| `--font-size-4xl` | `3rem` |

#### Scenario: Typography tokens resolve globally
- **WHEN** any CSS rule references `var(--font-family)`
- **THEN** the value SHALL resolve to `'Inter', system-ui, sans-serif`

### Requirement: Base body font applied site-wide
The system SHALL set the `body` font-family to `var(--font-family)` overriding the Jekyll Serif theme default.

#### Scenario: Body text renders in Inter
- **WHEN** any page is loaded
- **THEN** all body text (paragraphs, lists, table cells) SHALL render in the Inter typeface

### Requirement: Heading styles use brand weight and sizing
The system SHALL set `h1`–`h4` to use Inter weight 700 and sizes aligned to the type scale tokens.

#### Scenario: Page title heading uses largest type scale
- **WHEN** a page with an `h1` is loaded
- **THEN** the `h1` SHALL render at `var(--font-size-4xl)` (3rem) in weight 700
