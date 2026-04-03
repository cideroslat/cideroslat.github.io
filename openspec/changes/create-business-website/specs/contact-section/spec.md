## ADDED Requirements

### Requirement: Contact page provides a way for visitors to reach the business
The site SHALL include a `/contact/` page with either a contact form (via Formspree) or a clearly displayed email address. The page SHALL also display any relevant business location or social links.

#### Scenario: Contact page renders a form or email address
- **WHEN** a visitor navigates to `/contact/`
- **THEN** either a contact form or a visible email address is displayed

### Requirement: Contact form submits to Formspree endpoint
If a contact form is used, it SHALL submit to a Formspree endpoint URL configured in `_config.yml`. On successful submission, the visitor SHALL be shown a confirmation message or redirected to a thank-you page.

#### Scenario: Visitor submits the contact form with valid input
- **WHEN** a visitor fills in name, email, and message fields and clicks Submit
- **THEN** the form data is sent to the Formspree endpoint and the visitor sees a success confirmation

#### Scenario: Form does not submit with missing required fields
- **WHEN** a visitor attempts to submit the form without filling in required fields
- **THEN** the browser prevents submission and highlights the missing fields

### Requirement: Contact page is linked from main navigation
The Contact page SHALL be accessible via the main navigation header on all pages.

#### Scenario: Contact link in navigation opens the contact page
- **WHEN** a visitor clicks "Contact" in the navigation menu
- **THEN** the browser navigates to `/contact/`
