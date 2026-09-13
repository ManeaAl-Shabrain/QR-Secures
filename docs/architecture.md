# Architecture

## Application technology

The technical report lists the following technology for the current Base44 application.

| Part | Technology described in the report |
| --- | --- |
| Interface | React 18, Tailwind CSS, and Framer Motion |
| Components | shadcn/ui and Radix UI |
| Data requests | TanStack Query version 5 |
| Page routing | React Router version 6 |
| Platform | Base44 authentication, data entities, integrations, and functions |
| Threat analysis | Base44 InvokeLLM, described as using GPT 4o mini |
| QR scanning | html5 qrcode |
| Alerts | Slack through OAuth |

## Stored information

`ScanHistory` stores the scanned content and its result. `ThreatReport` stores reports from users, including reports of incorrect classifications. `Investigation` groups related scans into a case. `Watchlist` stores domains, patterns, keywords, or threat types that analysts want to monitor. `AutomationRule` stores the conditions and actions used for incident response. `ScanAnnotation` stores analyst notes. `UserPreferences` stores display and dashboard choices.

Older files also mention `Playbook` and `PlaybookLog`. The Base44 activity history says that Playbook links and result page references were later removed. The entities may still exist for compatibility, but the application source is needed to confirm that.

## Security boundaries

The browser handles sign in, camera access, display, and user actions. Checks involving a suspicious address should run in a protected backend function. Base44 stores the records and applies access rules. Slack should receive only the information required for an alert.

## Redirect checks

The presentation describes a backend function that follows as many as ten redirects and reports when the destination domain changes. This can reduce exposure on the user's device, but the server still contacts a system controlled by someone else. An HTTP HEAD request can also behave differently from a normal page request.

A production version should allow only HTTP and HTTPS, reject private and reserved network addresses at every redirect, set strict time limits, restrict response sizes, and limit outbound network access. These controls help prevent the redirect checker from being used to reach internal systems.

## Access control

Hiding a menu item does not protect data. Every backend request must identify the caller and confirm that the caller can access the requested record. Any use of the Base44 service role should be limited to the exact records and actions needed.

The September 2026 Base44 security review found four functions without caller verification: `autoSlackThreatAlert`, `handleThreatDetection`, `postMalwareToAlerts`, and `syncSlackResults`. The current Base44 plan did not allow those backend functions to be changed. These functions should be treated as an open security issue until they accept only an authorized user or a verified internal automation request.
