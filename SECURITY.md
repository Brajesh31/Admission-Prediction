# Security Policy

## Scope

This project is an educational notebook and dataset repository. Security concerns include exposed credentials, malicious notebook content, unsafe dependencies, accidental disclosure of applicant information, and unauthorized changes to project infrastructure.

## Reporting a vulnerability

Please do not disclose exploitable issues in a public issue. Contact the repository maintainers privately through the repository owner or security contact configured in the hosting platform. Include:

- a concise description and affected file or commit;
- reproduction steps or a minimal proof of concept;
- the potential impact;
- any suggested mitigation.

Do not include real personal data in a report.

## Response

Maintainers will acknowledge a report when practicable, investigate privately, and coordinate a fix or mitigation. Once a fix is available, the project may publish a sanitized advisory and credit the reporter if permission is granted.

## Data and notebook safety

Never commit secrets, private applicant records, access tokens, or untrusted notebook outputs. Review notebook cells and outputs before opening a pull request, and inspect dependencies before executing code from an untrusted branch.
