# Security and Privacy

[Back to roadmap](../README.md)

## Prerequisites

Start with 01 and revisit during 05–13; networking details require 07–08.

## Topics to learn

- [ ] Model assets, actors, physical access, trust boundaries, attack surfaces, and abuse cases. Include device controls as well as confidentiality.
- [ ] Assign distinct device identities; plan authenticated provisioning, least privilege, ownership transfer, credential rotation, revocation, and recovery.
- [ ] Separate authentication and authorization for devices, users, services, and administrators. Restrict broker topics, APIs, network exposure, and maintenance interfaces.
- [ ] Use established TLS libraries with hostname and chain validation. Address time bootstrap, expired certificates, trust-store updates, and credential compromise without disabling verification.
- [ ] Store secrets outside repositories and logs; assess secure storage or secure elements on the chosen hardware. Use appropriate randomness and established cryptography.
- [ ] Distinguish secure boot, signed updates, encryption, and anti-rollback. Define key custody and recovery before enabling irreversible production settings.
- [ ] Validate lengths, ranges, schemas, and command permissions; rate-limit expensive operations. Disable unnecessary services and restrict production debug access.
- [ ] Collect only necessary personal data; define purpose, access, retention, deletion, ownership transfer, and audit events. Confirm jurisdiction-specific obligations before real deployment.
- [ ] Track third-party dependencies and an inventory/SBOM, monitor advisories, triage vulnerabilities, and document a patch/support process and end-of-support policy.
- [ ] Map controls to device identification, configuration, data protection, interface access, software update, and security-state reporting. Supplement device controls with documentation and support processes.

## Hands-on work

1. Create a threat model with ranked risks and map each control to a test.
2. Attempt access using another device's identity, a revoked credential, an invalid certificate, and malformed commands in your own test environment.
3. Rotate a credential, simulate certificate expiry, and demonstrate a documented recovery path.
4. Verify that firmware, repository history used for release, logs, and example configuration contain no real secrets.

## Completion evidence

- [ ] Submit an identity lifecycle diagram, access matrix, security tests, data retention policy, and support plan.
- [ ] Explain residual risks and show that compromised-device access can be revoked independently.

## Primary reference

[NIST IoT device cybersecurity baseline](https://csrc.nist.gov/pubs/ir/8259/a/final) and [NIST 8259 series](https://www.nist.gov/itl/applied-cybersecurity/nist-cybersecurity-iot-program/nistir-8259-series)

