# Architecture

## Current Base44 application

The supplied technical report describes this stack:

| Layer | Documented technology |
| --- | --- |
| Frontend | React 18, Tailwind CSS, Framer Motion |
| Components | shadcn/ui and Radix UI |
| Data fetching | TanStack Query v5 |
| Routing | React Router v6 |
| Platform | Base44 entities, authentication, integrations, and functions |
| AI analysis | Base44 `InvokeLLM`, documented as GPT-4o-mini based |
| QR decoding | `html5-qrcode` |
| Alerts | Slack OAuth connector |

## Documented data model

- `ScanHistory` stores the submitted content, scan type, assessment, evidence, and result details.
- `ThreatReport` stores community threat or false-positive reports and moderation data.
- `Investigation` groups related scans into a case.
- `Watchlist` stores domains, URL patterns, keywords, or threat types to monitor.
- `AutomationRule` defines incident-response triggers and actions.
- `ScanAnnotation` attaches analyst notes and findings to a scan.
- `UserPreferences` stores dashboard and display preferences.

Older materials also mention `Playbook` and `PlaybookLog`. The Base44 activity record says Playbook references were later removed from routing and the results flow. These entities may still exist for compatibility and need source verification.

## Trust boundaries

The browser handles authentication, camera input, display, and user actions. Potentially dangerous URL inspection should occur in server-side functions. Base44 stores entity records and applies access rules. External integrations receive only the information required for the requested alert.

## Redirect handling

Presentation materials describe a server-side function that follows up to ten redirects with HTTP header requests and reports domain changes. This design reduces direct client exposure during analysis, but it does not create absolute isolation: the server still contacts attacker-controlled infrastructure, HEAD may behave differently from GET, DNS can change, and redirects can target private network addresses unless the function blocks them. Production code should enforce protocol allowlists, DNS and IP checks on every hop, timeouts, response-size limits, and outbound-network restrictions.

## Authorization requirements

Frontend role checks improve navigation but do not protect data. Every function and entity operation should authenticate the caller and authorize access to the specific record. Service-role access should be narrow and explicitly scoped.

The September 2026 Base44 security review identified four functions that lacked caller verification: `autoSlackThreatAlert`, `handleThreatDetection`, `postMalwareToAlerts`, and `syncSlackResults`. The plan did not allow those backend functions to be modified. Treat this as an open release blocker until the functions verify either an authenticated, authorized user or a signed internal automation request.

