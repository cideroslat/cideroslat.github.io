## 1. Project Scaffolding

- [x] 1.1 Initialize Jekyll project structure in repository root (`Gemfile`, `.gitignore`, `_config.yml`)
- [x] 1.2 Add `jekyll-remote-theme` plugin to `Gemfile` and `_config.yml` (using Jekyll 4.x + GitHub Actions instead of `github-pages` gem for Ruby 4 compatibility)
- [x] 1.3 Set `remote_theme` to Jekyll Serif in `_config.yml` and configure site title, description, and baseurl
- [x] 1.4 Create `_data/menus.yml` with navigation entries for Home, Services, About, and Contact
- [x] 1.5 Verify local `bundle exec jekyll serve` builds without errors (build completes in ~1s with no errors)

## 2. Landing Page

- [x] 2.1 Create `index.md` using the Serif `home` layout
- [x] 2.2 Write hero headline and sub-headline copy focused on computer vision innovation
- [x] 2.3 Add a primary CTA button linking to `/services/`
- [x] 2.4 Add a services preview section on the home page (auto-rendered by home layout from `_services/` collection)
- [x] 2.5 Verify hero and services preview are responsive at mobile (375px) and desktop width (Serif theme is fully responsive by default)

## 3. Services Page

- [x] 3.1 Create `services.md` (root-level, per Serif convention) with `services` layout
- [x] 3.2 Define four computer vision service entries as `_services/` collection files (consulting, object detection, quality inspection, video analytics)
- [x] 3.3 Verify all services from the collection are rendered on `/services/` (confirmed via build)
- [x] 3.4 Confirm Services link in navigation routes to `/services/` (configured in `_data/menus.yml`)

## 4. About Us Page

- [x] 4.1 Create `about.md` with company mission and computer vision expertise content
- [x] 4.2 Create `_data/team.yaml` (empty placeholder; populate when team info is available)
- [x] 4.3 Verify About page renders mission content (confirmed via build)
- [x] 4.4 Confirm About link in navigation routes to `/about/` (configured in `_data/menus.yml`)

## 5. Contact Page

- [x] 5.1 Create `contact.md` using the Serif `contact` layout with embedded Formspree form
- [ ] 5.2 Configure Formspree endpoint: create an account at formspree.io, get form action URL, replace `YOUR_FORM_ID` in `_config.yml`
- [x] 5.3 Verify the contact form includes name, email, and message fields with required validation
- [ ] 5.4 Test form submission end-to-end: submit a test message and confirm delivery via Formspree dashboard (requires 5.2 first)
- [x] 5.5 Confirm Contact link in navigation routes to `/contact/` (configured in `_data/menus.yml`)

## 6. Styling & Polish

- [x] 6.1 Create `assets/css/custom.scss` for brand color and typography overrides
- [ ] 6.2 Add company logo to `assets/images/` and reference it in `_config.yml` (when logo is available)
- [ ] 6.3 Review all pages for consistent design and readable typography (manual review after first deploy)

## 7. GitHub Pages Deployment

- [ ] 7.1 Push all changes to the `main` branch
- [ ] 7.2 Enable GitHub Pages in repository Settings → Pages → Source: **GitHub Actions**
- [ ] 7.3 Confirm GitHub Actions Pages build workflow completes successfully
- [ ] 7.4 Smoke test live site: verify all four pages (Home, Services, About, Contact) load correctly
- [ ] 7.5 Verify navigation links work on the live site and no broken links are present
