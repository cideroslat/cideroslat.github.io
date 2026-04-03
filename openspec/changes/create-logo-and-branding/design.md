## Context

The Jekyll Serif theme is already installed and running. The `_config.yml` already defines logo path references at `images/logo/logo.svg` (desktop, 140×32px) and `images/logo/logo-mobile.svg` (mobile, 32×32px), and `header.html` consumes those paths automatically. The current `custom.scss` uses a single hardcoded accent blue (`#0d9cdb`) with no design tokens. There is no logo file on disk yet — the header renders a broken image.

**Constraints:**
- Static site hosted on GitHub Pages (no build server — must use Google Fonts CDN or web-safe font stack)
- Jekyll Serif base theme styles must be overridden, not replaced
- Both EN and ES site versions share the same stylesheet and layout

## Goals / Non-Goals

**Goals:**
- Design an SVG logo for CIDEROS (wordmark + icon variant) that communicates precision and computer vision
- Define a complete brand color palette as CSS custom properties in `custom.scss`
- Define a typographic scale and font pairing as CSS custom properties
- Integrate the logo into the existing `header.html` via `_config.yml` logo paths
- Ensure the brand applies consistently across all pages (EN and ES)

**Non-Goals:**
- Animated or interactive logo variations
- Print/PDF brand guidelines document
- Social media asset generation (avatars, banners) — those are created separately
- Replacing or forking the Jekyll Serif theme

## Decisions

### 1. Logo Concept: Geometric Eye + Wordmark

**Decision:** The CIDEROS logo uses a minimalist SVG combining a geometric eye/lens shape (representing computer vision) with a clean wordmark. The icon is a stylized hexagonal "aperture" or "iris" made of thin strokes — suggestive of a camera sensor or detection bounding box.

**Rationale:** An abstract lens/eye icon is universally understood as "vision" while remaining simple at small sizes. A pure wordmark was considered but rejected because it lacks visual distinctiveness at favicon/avatar sizes. A photorealistic camera was considered but rejected as clichéd and too complex for SVG.

**Variants delivered:**
- `logo.svg` — horizontal: icon (32px) + CIDEROS wordmark, 140×32px container
- `logo-mobile.svg` — icon mark only, 32×32px (matches `_config.yml` mobile dimensions)

### 2. Color Palette: Deep Teal + Electric Cyan

**Decision:** Use a dark deep-teal primary with an electric cyan accent. Full palette defined as CSS custom properties.

```
--color-primary:     #0B2D3E   /* Deep ocean teal — headers, hero bg */
--color-secondary:   #0F4C5C   /* Mid teal — card backgrounds, section dividers */
--color-accent:      #00D4FF   /* Electric cyan — CTAs, hover states, highlights */
--color-accent-dark: #00A8CC   /* Darker cyan — pressed/active states */
--color-text:        #1A1A2E   /* Near-black with blue undertone — body text */
--color-text-muted:  #5A6B77   /* Muted steel — secondary text, captions */
--color-bg:          #FFFFFF   /* Page background */
--color-bg-alt:      #F4F7F9   /* Light grey-blue — alternating sections */
--color-border:      #D8E4EA   /* Subtle border */
```

**Rationale:** Tech/AI companies (including antac.ai) use dark blues/teals to signal trust, precision, and innovation. The electric cyan accent creates high contrast for CTAs without feeling garish. The palette works in both light-mode (current site) and could later support dark mode.

**Alternatives considered:** Purple/violet (too associated with AI hype), black + neon green (too "hacker"), cobalt blue + orange (too generic analytics).

### 3. Typography: Inter (headings) + Inter (body)

**Decision:** Use a single typeface — **Inter** — across all weights. Headings use Inter 700 (Bold), body uses Inter 400 (Regular), UI labels use Inter 500 (Medium).

**Rationale:** Inter is purpose-built for screen readability, has a clean geometric character well-suited to tech/AI branding, and loads from Google Fonts CDN with a single `@import`. A two-font system (e.g., Sora + Inter) was considered but adds CDN overhead and complexity without sufficient differentiation on a Jekyll theme.

**CSS type scale:**
```
--font-family:       'Inter', system-ui, sans-serif
--font-size-xs:      0.75rem
--font-size-sm:      0.875rem
--font-size-base:    1rem
--font-size-lg:      1.125rem
--font-size-xl:      1.375rem
--font-size-2xl:     1.75rem
--font-size-3xl:     2.25rem
--font-size-4xl:     3rem
```

### 4. CSS Architecture: Custom Properties in custom.scss

**Decision:** Define all brand tokens as `:root` CSS custom properties at the top of `custom.scss`. Theme overrides then reference those variables.

**Rationale:** Jekyll Serif uses plain CSS classes — there is no Sass variable inheritance to hook into cleanly. CSS custom properties work at the cascade level and are accessible to any stylesheet, including the theme's own compiled CSS. This allows all brand values to be changed in one place and propagates everywhere.

### 5. Logo File Format: Inline SVG Code

**Decision:** Create hand-authored, minimal SVG files for the logo (not embedded raster images). Store at `assets/images/logo/logo.svg` and `assets/images/logo/logo-mobile.svg`.

**Note:** The `_config.yml` references paths under `images/logo/` (without the `assets/` prefix) — the Jekyll Serif theme resolves these relative to the `assets/` folder via `relative_url`. Files must be placed at `assets/images/logo/`.

## Risks / Trade-offs

| Risk | Mitigation |
|------|-----------|
| Google Fonts CDN unavailable in some regions | CSS `@import` includes `system-ui, sans-serif` fallback stack |
| Logo SVG renders poorly at 32px mobile size | Mobile variant uses icon-only mark (no wordmark text at small sizes) |
| Jekyll Serif theme update overwrites theme CSS | All overrides live in `custom.scss` which is never touched by the theme |
| Brand colors may not match Jekyll Serif's dark/light mode if added later | Variables are named semantically (not `--blue-500`) so they can be remapped |
| `_config.yml` logo path (`images/logo/logo.svg`) does not include `assets/` prefix | Confirmed theme uses `relative_url` filter — files go in `assets/images/logo/` |
