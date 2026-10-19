# ADR-001: playwright-core with the system's browser

## Decision

Moved to moodle-driver's ADR-001 (playwright-core with the system's browser) when the Moodle code became that library (ADR-014, 9 October 2026). This server follows it through the driver; what remains here is how its settings reach the driver.

## Motivation

The decision is about working Moodle, which the driver does now; one copy, where the code is.

## Consequences

- Read moodle-driver's ADR-001 for the decision itself.
- Firefox (Playwright's own, `MOODLE_MCP_CHANNEL=firefox`) is never in the default order. It can't use a Chromium-based browser's profile, so the server gives it a data folder of its own, `<data folder>/firefox`: its default profiles and saved sites never mix with Edge's, Chrome's or Chromium's (18 October 2026). A profile folder the person sets is used as given.
