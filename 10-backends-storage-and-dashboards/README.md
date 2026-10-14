# Backends, Storage, and Dashboards

[Back to roadmap](../README.md)

## Prerequisites

Categories 07–09; programming from 04 and access control from 11.

## Topics to learn

- [ ] Build ingestion from a broker or API; authenticate devices, validate schemas, apply quotas, and isolate malformed events without stopping the pipeline.
- [ ] Compare relational, time-series, and object storage. Learn SQL, keys, indexes, transactions, retention, downsampling, and backup/restore.
- [ ] Version database and telemetry schemas; plan additive changes, mixed firmware versions, historical-data backfills, migration validation, and rollback or forward-recovery procedures.
- [ ] Distinguish event time from ingestion time; handle clock skew, missing timestamps, duplicate IDs, late arrivals, out-of-order data, units, and quality flags.
- [ ] Maintain a device registry with ownership, capabilities, firmware, last seen, desired/reported configuration, and lifecycle status.
- [ ] Design APIs with authorization, pagination, input limits, versioning, rate limits, and clear error responses. Enforce tenant boundaries on every access path.
- [ ] Build dashboards with units, time zones, historical ranges, gaps, stale/offline states, loading/error states, keyboard access, and readable non-color-only status.
- [ ] Create alert rules with hysteresis, persistence windows, cooldown, acknowledgement, escalation, and recovery notifications. Distinguish sensor faults from real threshold crossings.
- [ ] Compare local and cloud hosting; study managed-service responsibilities, secrets, infrastructure configuration, deployment rollback, budget alerts, and capacity planning.
- [ ] Apply backpressure, bounded queues, retry limits, dead-letter handling, and idempotent writes. Measure throughput and end-to-end latency under load.
- [ ] Use logs, metrics, traces or correlation IDs, health checks, retention policies, and tested recovery procedures.

## Hands-on work

1. Store telemetry with a unique event key and build a history chart that visibly represents stale or missing data.
2. Replay duplicate and out-of-order samples and verify the database and chart remain correct.
3. Create a second user/device group and test cross-group access denial.
4. Restore a backup into a fresh instance and compare record counts and selected values.
5. Add a telemetry field and migrate storage while accepting both old and new device payloads. Backfill only values that can be derived correctly, preserve unknown values explicitly, and rehearse recovery from an interrupted migration.

## Completion evidence

- [ ] Provide a schema, API contract, dashboard screenshots, load-test results, and restore evidence.
- [ ] Demonstrate an alert opening and clearing without flooding users.
- [ ] Document hosting cost assumptions and capacity limits.
- [ ] Provide a migration script, mixed-version ingestion results, before/after data checks, and a tested recovery procedure.

