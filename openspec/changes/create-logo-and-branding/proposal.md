## Why

CIDEROS currently has no visual identity — no logo, defined color palette, or typography system. Without a cohesive brand, the website lacks credibility and fails to differentiate the business in a competitive computer vision consulting market. Establishing branding now ensures all current and future site work is visually consistent and professionally positioned.

## What Changes

- Introduce an SVG logo for CIDEROS (wordmark + icon mark) reflecting computer vision / precision / innovation
- Define a brand color palette (primary, secondary, accent, neutrals)
- Define typography choices (heading font, body font, weights/sizes)
- Create a CSS custom properties system (`_variables`) to apply the brand across the Jekyll site
- Update the site's `custom.scss` to incorporate brand colors and fonts
- Add logo assets to `assets/images/` for use in the header and across the site (both EN and ES versions)
- Provide a simple brand guidelines reference document for internal use

## Capabilities

### New Capabilities

- `logo-asset`: SVG/PNG logo files for CIDEROS (horizontal wordmark, stacked variant, icon-only mark) stored in `assets/images/`
- `brand-color-system`: Defined color palette as CSS custom properties applied site-wide
- `brand-typography`: Font selections and scale defined as CSS custom properties applied site-wide
- `brand-integration`: Header, navigation, and site layout updated to use logo and brand styles consistently across EN and ES pages

### Modified Capabilities

<!-- No existing specs require requirement-level changes -->

## Impact

- `assets/css/custom.scss`: Updated with brand color variables, typography imports, and global style rules
- `_layouts/default.html`: Updated to reference logo image in the header
- `_includes/header.html`: Updated to use logo asset instead of plain text site title
- `assets/images/`: New directory with SVG/PNG logo files
- Both EN (`/`) and ES (`/es/`) versions of the site inherit brand styles via the shared stylesheet
- No breaking changes to existing page content or Jekyll configuration
