## ADDED Requirements

### Requirement: About Us page describes the company mission and expertise
The site SHALL include an `/about/` page that communicates the company's mission, focus on computer vision, and team expertise. The page SHALL include at minimum: a company description paragraph and a statement of core expertise.

#### Scenario: About page is rendered with company information
- **WHEN** a visitor navigates to `/about/`
- **THEN** a page is displayed with the company description and expertise statement

### Requirement: About page team section (optional, expandable)
The about page SHALL support an optional team section populated from `_data/team.yaml`. If the YAML file is empty or absent, the team section SHALL not be rendered.

#### Scenario: Team members are displayed when data file is populated
- **WHEN** `_data/team.yaml` contains one or more entries and the site is built
- **THEN** team member names and titles appear in the team section of the About page

#### Scenario: Team section is hidden when data file is empty
- **WHEN** `_data/team.yaml` is empty or absent
- **THEN** no team section is rendered on the About page

### Requirement: About page is linked from main navigation
The About page SHALL be accessible via the main navigation header on all pages.

#### Scenario: About link in navigation opens the about page
- **WHEN** a visitor clicks "About" in the navigation menu
- **THEN** the browser navigates to `/about/`
