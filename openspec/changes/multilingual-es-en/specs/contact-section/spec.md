## MODIFIED Requirements

### Requirement: Contact page provides a way for visitors to reach the business
The Contact page SHALL exist in both English (`/contact/`) and Spanish (`/es/contact/`). Form field labels, placeholder text, submit button label, and the page introduction SHALL be translated and sourced from `site.data.translations[page.lang]`. Both pages SHALL submit to the same Formspree endpoint.

#### Scenario: English contact page renders English labels
- **WHEN** a visitor navigates to `/contact/`
- **THEN** form fields show English labels: "Name", "Email", "Message", and "Send Message"

#### Scenario: Spanish contact page renders Spanish labels
- **WHEN** a visitor navigates to `/es/contact/`
- **THEN** form fields show Spanish labels: "Nombre", "Correo electrónico", "Mensaje", and "Enviar mensaje"

### Requirement: Contact form submits to Formspree endpoint from both language versions
Both the English and Spanish contact forms SHALL submit to the same Formspree endpoint configured in `_config.yml`. The hidden `_subject` field SHALL reflect the language of the form submission.

#### Scenario: Spanish contact form submission is identifiable
- **WHEN** a visitor submits the contact form from `/es/contact/`
- **THEN** the Formspree submission subject line identifies it as originating from the Spanish version of the site

### Requirement: Contact page is linked from main navigation in both languages
The Contact page SHALL be accessible via the navigation header in both language versions.

#### Scenario: English Contact navigation link
- **WHEN** a visitor clicks "Contact" in the English navigation
- **THEN** the browser navigates to `/contact/`

#### Scenario: Spanish Contact navigation link
- **WHEN** a visitor clicks the contact link in the Spanish navigation
- **THEN** the browser navigates to `/es/contact/`
