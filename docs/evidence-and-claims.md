# Evidence Review

The supplied files describe several versions of QR Secures. This page keeps the results from those versions separate and shows which statements still need proof.

| Statement | Where it appears | How it can be described |
| --- | --- | --- |
| The practicum used about 150,000 labeled URLs with a 70, 15, and 15 percent split | Final practicum report | A result reported by the team. The dataset split and training files are not included |
| The CNN reached 0.982 accuracy and 0.995 ROC AUC | Final practicum report | A result reported by the team. It cannot yet be reproduced from this repository |
| The hybrid detector classified 48 of 50 difficult URLs correctly | Final practicum report | A result reported by the team. The 50 test cases are not included |
| The current application uses Base44 InvokeLLM and community reports | Base44 technical report and project history | A documented feature. Source export is not available |
| Redirects are checked on the server for as many as ten hops | Presentation and Base44 project history | Documented behavior that still needs a source review and a controlled test |
| All 50 redirect attacks were detected | Presentation and speaker script | Not independently supported. It should not appear as a headline result |
| Phishing accuracy was 94 percent compared with 68 percent for older databases | Presentation and speaker script | Not independently supported. The comparison method and test data are missing |
| The longest scan time fell from 8 seconds to 3.2 seconds | Presentation and speaker script | Not independently supported. Benchmark logs are missing |
| Community data improved accuracy by 26 percentage points | Project description and presentation | Not independently supported. It appears to come from the 94 and 68 percent comparison |
| The alert system completed more than 28 runs in five scenarios | Project description | Not independently supported by logs supplied for the repository |
| Row level rules protect all scan data | Base44 security history says rules were added for eight entities | Requires testing after the security changes |

## Differences between project stages

The CNN results belong to the Fall 2025 practicum detector. The current Base44 application is described as using a language model. The available material does not show that the Base44 application runs the CNN, so the repository does not combine their results.

The files also disagree about community moderation. One version says that five votes automatically verify or reject a report. Another version requires an analyst to approve it. The public documentation records this difference instead of choosing one version without proof.

Some files say that Community Reports is open to every user. Others place it behind an analyst role. The project history suggests that all users can submit reports and that analysts or administrators review them. This must be checked in the deployed application.

## What is needed to verify the results

A complete research package would need a dataset manifest, preprocessing code, fixed training and test identifiers, model settings, a saved model hash, an evaluation script, the challenge test set, expected outputs, dependency versions, and dated benchmark logs. Live malicious links should be replaced with safe examples or hashes when possible.
