# 🔐 Security Policy

## Scope

Admission-Prediction is a local notebook and dataset repository. Security concerns include malicious notebook cells, exposed credentials, unsafe dependencies, accidental disclosure of applicant information, and unauthorized repository changes.

## Supported project

Security reports should identify the affected branch, commit, notebook cell, dependency, or data artifact where possible. The project does not currently operate a hosted API or production inference service.

## Reporting a vulnerability

Please do not disclose exploitable issues in a public issue. Contact the repository owner privately through the contact or security-reporting controls available on GitHub.

Include:
- A concise description of the issue.
- Affected file, cell, dependency, or commit.
- Reproduction steps or a minimal proof of concept.
- Potential impact.
- Suggested mitigation, where known.

Do not include real applicant records, personal data, access tokens, or passwords in a report.

## Response process

Maintainers will review reports in good faith, investigate privately where practicable, and coordinate a fix or mitigation. A public advisory may be prepared after a remedy is available. Reporter credit will be included only with permission.

## Notebook and dataset safety

- Review notebook cells before executing notebooks from untrusted contributors.
- Do not commit secrets, private applicant information, or local credentials.
- Inspect notebook outputs before publishing changes.
- Keep dependencies updated and investigate security advisories.
- Confirm dataset provenance and redistribution permissions.
- Do not upload sensitive or identifiable data to public issue threads.

## Scope limitations

The repository does not currently have a production service, authentication layer, or cloud deployment. Do not interpret this policy as evidence that such systems exist.
