# Application Guide

## Scan workflow

After signing in, the user can scan a QR code with the camera or type a web address. The application checks the input, gathers available security information, saves the scan, and displays the result.

The result can include a risk score, classification, confidence value, URL details, redirects, SSL status, phishing signs, manipulation tactics, detected threats, and a recommendation. These details help the user make a decision, but they do not prove that a website is safe or dangerous.

## Splash and Home

The Splash page introduces the application and then opens Home. Home shows the account, recent scan totals, scanning options, shortcuts, and any tools available to the user.

## Scanner and Manual Scan

Scanner uses the device camera through `html5-qrcode`. It can control the flashlight on supported devices. Manual Scan accepts a web address without using the camera. Both options follow the same documented analysis process.

## Results

Results shows the saved assessment. From this page, the user can copy the address, submit a report, send an alert, start another scan, or return home. The application asks for clear confirmation before opening a risky address. Even a safe result can become outdated if the destination changes later.

## Dashboard and History

Dashboard summarizes scan totals, risk levels, trends, and threat categories. History lets users search, filter, sort, and review previous scans.

## Community Reports

Users can report a threat or say that an earlier result was incorrect. A report records the address, category, description, supporting evidence, votes, and review status.

Some project files say that five votes change the status automatically. Other files say that an analyst must approve the report. The source code is needed to settle this difference.

Verified threat reports can help with later scans of the same address. The Base44 project history also records a September 2026 change meant to include confirmed incorrect results. This behavior still needs a practical test.

## Threat Hunting

Analysts and administrators can filter scans by date, classification, threat type, score, or search text. They can open a scan, add notes, create an investigation, and manage watchlists.

## Incident Response

Automation Settings contains rules for suspicious or malicious results. A rule can trigger a Slack or email notification. Older project files call this feature Playbooks. The Playbooks page was later removed, while Automation Settings remains in the current project.

## Account and User Management

Account shows profile and preference information. User Management is available to administrators for finding users, sending invitations, and changing roles.

## Access by role

| Capability | User | Analyst | Admin |
| --- | :---: | :---: | :---: |
| Scan QR codes and URLs | Yes | Yes | Yes |
| View personal history and dashboard | Yes | Yes | Yes |
| Submit community reports | Yes | Yes | Yes |
| Review and vote on reports | Needs confirmation | Yes | Yes |
| Use threat hunting and investigations | No | Yes | Yes |
| Change incident response settings | No | Yes | Yes |
| Manage users | No | No | Yes |

The backend must check these permissions whenever someone reads or changes data. Hiding a page link does not protect the underlying information.
