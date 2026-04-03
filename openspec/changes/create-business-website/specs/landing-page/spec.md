## ADDED Requirements

### Requirement: Landing page displays a hero section
The landing page (`index.md` or `index.html`) SHALL render a full-width hero section as the first visible element. The hero SHALL include: a headline communicating the computer vision innovation message, a supporting sub-headline, and a primary call-to-action button.

#### Scenario: Hero section is visible above the fold
- **WHEN** a visitor lands on the home page
- **THEN** the hero headline, sub-headline, and CTA button are visible without scrolling

#### Scenario: CTA button navigates to contact or services
- **WHEN** a visitor clicks the primary call-to-action button
- **THEN** they are taken to the Contact page or Services section

### Requirement: Landing page includes a services preview
The landing page SHALL include a brief preview section that highlights the top services with short descriptions and links to the full Services page.

#### Scenario: Services preview section is rendered on home page
- **WHEN** a visitor scrolls past the hero
- **THEN** a services preview section is visible with at least three service cards or items

#### Scenario: Each service card links to the full services page
- **WHEN** a visitor clicks a service card on the home page
- **THEN** they are navigated to the Services page

### Requirement: Landing page is responsive
The landing page SHALL render correctly on mobile, tablet, and desktop screen sizes.

#### Scenario: Hero section is readable on mobile
- **WHEN** the page is loaded on a viewport width of 375px
- **THEN** the hero headline text is fully visible and not clipped or overflowing
