## 1. Logo Asset Creation

- [x] 1.1 Create the directory `assets/images/logo/` in the repository
- [x] 1.2 Author `assets/images/logo/logo.svg` — horizontal wordmark (geometric aperture/iris icon + "CIDEROS" text), sized to 140×32px viewBox, using brand colors (`#0B2D3E`, `#00D4FF`, `#FFFFFF`)
- [x] 1.3 Author `assets/images/logo/logo-mobile.svg` — icon mark only (no wordmark), sized to 32×32px viewBox, using brand colors
- [x] 1.4 Verify both SVG files are under 5KB and render correctly at 1×, 2×, and 3× scales in a browser

## 2. Brand Color System

- [x] 2.1 Add Google Fonts `@import` for Inter (weights 400, 500, 700) at the top of `assets/css/custom.scss`
- [x] 2.2 Add `:root` CSS custom property block to `assets/css/custom.scss` defining all nine color tokens (`--color-primary`, `--color-secondary`, `--color-accent`, `--color-accent-dark`, `--color-text`, `--color-text-muted`, `--color-bg`, `--color-bg-alt`, `--color-border`)
- [x] 2.3 Update the existing hardcoded `#0d9cdb` accent color in `custom.scss` contact-form rules to use `var(--color-accent)` instead
- [x] 2.4 Add header background override rule in `custom.scss` to apply `var(--color-primary)` to the `.header` element

## 3. Brand Typography

- [x] 3.1 Add `:root` CSS custom property block for typography tokens (`--font-family`, `--font-size-xs` through `--font-size-4xl`) to `assets/css/custom.scss`
- [x] 3.2 Add `body` font-family override rule in `custom.scss` using `var(--font-family)` to replace the Jekyll Serif theme default
- [x] 3.3 Add heading (`h1`–`h4`) overrides in `custom.scss` setting weight 700 and sizes from the type scale tokens

## 4. Brand Integration

- [x] 4.1 Verify that `_config.yml` logo paths (`images/logo/logo.svg` and `images/logo/logo-mobile.svg`) correctly resolve to the files created in step 1 when Jekyll processes `relative_url`
- [x] 4.2 Run `bundle exec jekyll build` and confirm `_site/assets/images/logo/logo.svg` and `_site/assets/images/logo/logo-mobile.svg` exist in the build output
- [x] 4.3 Open the local site in a browser and verify the desktop header displays the CIDEROS horizontal logo
- [x] 4.4 Open the local site in a browser at mobile viewport (≤768px) and verify the icon-only logo is displayed
- [x] 4.5 Navigate to `/es/` (Spanish version) and verify the logo and brand colors match the English version exactly
- [x] 4.6 Verify clicking the logo navigates to the site homepage (`/`)
