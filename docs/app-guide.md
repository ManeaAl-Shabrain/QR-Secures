# Application Guide

## Scan workflow

Users sign in, select the camera scanner or manual URL check, and submit content for analysis. The application validates the input, gathers security signals, stores the result in scan history, and opens a detailed results page.

The results page may show a risk score, classification, confidence, URL details, redirect information, SSL status, phishing indicators, social-engineering indicators, detected threat types, and a recommended action. Treat these fields as decision support rather than a definitive verdict.

## Pages

### Splash and Home

The splash screen introduces the product and routes to Home. Home shows the signed-in account, recent scan statistics, scan entry points, protection indicators, quick links, and role-specific tools.

### Scanner and Manual Scan

Scanner uses the device camera through `html5-qrcode` and offers a torch control when supported. Manual Scan accepts a URL without camera access. Both paths feed the same documented application analysis flow.

### Results

Results displays the stored assessment and offers copy, report, alert, rescan, and navigation actions. Opening a risky destination should require clear user intent. A safe classification cannot guarantee that the destination remains safe.

### Dashboard and History

Dashboard summarizes scan volume, risk distribution, trends, and threat categories. History supports search, filters, sorting, and detailed review of past scans.

### Community Reports

Users can report a threat or a false positive. Reports include the URL, category, description, evidence, vote counts, voters, and review status. Current materials describe threshold-based status changes and analyst review differently, so the exact moderation rule requires source verification.

Verified threat evidence can inform later scans. The application conversation records a September 2026 change intended to include verified false-positive evidence too, but this should be tested in the deployed app.

### Threat Hunting

Analysts and administrators can filter scans by time, classification, threat type, score, and text. The page also provides scan details, annotations, investigations, and watchlists.

### Incident Response

Automation settings configure rules for suspicious or malicious results and actions such as Slack or email notification. Earlier Playbook UI references were removed, while the Automation Settings page remains visible in the live project. Documentation therefore uses the current page name.

### Account and User Management

Account displays profile and preference information. User Management is restricted to administrators and supports user lookup, invitations, and role changes.

## Roles

| Capability | User | Analyst | Admin |
| --- | :---: | :---: | :---: |
| Scan QR codes and URLs | Yes | Yes | Yes |
| View personal history and dashboard | Yes | Yes | Yes |
| Submit community reports | Yes | Yes | Yes |
| Review and vote on reports | Verify in app | Yes | Yes |
| Threat hunting and investigations | No | Yes | Yes |
| Incident-response settings | No | Yes | Yes |
| User management | No | No | Yes |

Access must be enforced by backend authorization and row-level rules, not only by hidden navigation links.

