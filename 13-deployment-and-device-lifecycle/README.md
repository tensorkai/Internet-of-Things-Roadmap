# Deployment and Device Lifecycle

[Back to roadmap](../README.md)

## Prerequisites

Categories 06–12; coordinate power and production work with 15 and 17.

## Topics to learn

- [ ] Track development, pilot, production, maintenance, and retirement stages with unique identities and hardware/firmware revision records.
- [ ] Provision network settings and credentials securely; support reset, reprovisioning, ownership transfer, and replacement without shared hard-coded secrets.
- [ ] Package updates with version, target compatibility, integrity/authenticity checks, and a documented signing process.
- [ ] Design OTA with storage/partition limits, resumable download where supported, power-loss recovery, post-boot health checks, rollback, and compatibility of stored data.
- [ ] Separate recovery rollback from security anti-rollback. Plan their interaction so security settings do not remove the only recovery path.
- [ ] Roll out to a small canary group, observe health, expand in stages, and define automatic stop criteria. Track failed and unreachable devices.
- [ ] Monitor firmware versions, connectivity, resets, update status, queue depth, sensor health, and certificate lifetime.
- [ ] Design enclosures, connectors, mounting, service access, environmental protection, and antenna placement; verify the assembled system.
- [ ] Estimate power, bandwidth, cloud/storage cost, maintenance visits, spare units, replacements, and support effort.
- [ ] Document incident response, remote diagnosis, disaster recovery, support lifetime, and vulnerability updates.
- [ ] Retire devices by revoking credentials, removing access, clearing sensitive data, updating inventories, and documenting residual retention.

## Hands-on work

1. Provision multiple test identities and rotate/revoke one without disrupting the others.
2. Perform a valid OTA update, reject an invalid/incompatible image, interrupt download, and test a failed post-boot health check on supported hardware.
3. Run a staged release with a deliberate stop condition and preserve logs of the decision.
4. Retire one device and confirm it can no longer reconnect with its old identity.

## Completion evidence

- [ ] Provide an operating runbook, update state diagram, release manifest, fleet inventory, and recovery results.
- [ ] Demonstrate both unattended operation and a realistic technician recovery procedure.
- [ ] Document hardware-specific limits and any scenarios that remain untested.

## Primary reference

[ESP-IDF OTA guide](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/system/ota.html) provides a concrete implementation example; verify your board and SDK configuration.

