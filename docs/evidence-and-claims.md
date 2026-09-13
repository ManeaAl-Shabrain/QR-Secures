# Evidence and Claim Status

This register prevents results from different project phases from being mixed together.

| Claim | Source in supplied material | Status for public use |
| --- | --- | --- |
| Practicum dataset contained about 150,000 labeled URLs with a 70/15/15 split | Final practicum report | Reported academic result; underlying dataset split and training artifacts are not in this repository |
| CNN achieved 0.982 accuracy and 0.995 ROC-AUC | Final practicum report | Reported academic result; reproducibility package is unavailable |
| Hybrid engine classified 48 of 50 challenge URLs correctly | Final practicum report | Reported academic result; test cases are unavailable |
| Current app uses Base44 `InvokeLLM` and community context | Base44 technical report and live project history | Documented implementation; source export unavailable |
| Current app resolves redirect chains server-side up to ten hops | Presentation and Base44 project history | Documented behavior; source and controlled test evidence unavailable |
| Current app detected 100% of 50 redirect attacks | Presentation/script only | Unverified; omit from headline claims |
| Current app achieved 94% phishing accuracy versus 68% for legacy databases | Presentation/script only | Unverified comparison; omit from headline claims |
| Worst-case latency improved from 8 seconds to 3.2 seconds | Presentation/script only | Unverified benchmark; omit from headline claims |
| Community intelligence improves accuracy by 26 percentage points | User narrative and presentation | Unverified and appears derived from the 94% versus 68% comparison |
| Automated response completed more than 28 executions across five scenarios | User narrative | Unverified; execution logs unavailable |
| All scan data has effective row-level protection | Base44 security activity says rules were added for eight entities | Needs regression and authorization testing |

## Important distinctions

The CNN metrics belong to the Fall 2025 practicum detector. The present Base44 application is documented as using LLM-assisted analysis. Without the application source and deployment configuration, the repository does not claim that the current app runs the CNN model.

The supplied app reports describe community moderation in two ways: automatic verification or rejection at five votes, and a combined voting plus analyst-approval process. The public documentation describes both as an unresolved implementation detail.

The reports also vary on whether Community Reports is available to all users or only analyst roles. The live project history supports submission by all users and analyst/admin review, but the deployed authorization should be tested.

## Reproducibility needed

To convert reported results into verified results, add a versioned dataset manifest, preprocessing code, fixed train/test identifiers, model configuration, saved model hash, evaluation script, challenge URL set, expected outputs, environment lockfile, and dated benchmark logs. Sensitive or live malicious URLs should be replaced with safe fixtures or hashes where appropriate.

