# Security Policy

## Reporting a vulnerability

Do not publish exploitable details, private URLs, credentials, access tokens, or user data in a public issue. Contact the project owner privately through the GitHub profile associated with this repository and include the affected component, impact, safe reproduction steps, and suggested mitigation.

## Known security work

The current evidence identifies four backend alert or analysis functions that require caller authentication or signed automation verification. Release testing should also confirm row-level entity rules, role authorization, redirect protections against private-network access, secret handling, alert payload minimization, rate limits, and audit logs.

## Safe testing

Use controlled domains and inert QR codes. Do not scan live credentials, private invitation links, password-reset URLs, internal hosts, or customer data. Do not probe systems without authorization.

