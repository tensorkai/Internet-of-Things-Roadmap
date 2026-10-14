# Gateways and Edge Computing

[Back to roadmap](../README.md)

## Prerequisites

Categories 05, 07, and 08; Linux may be learned here.

## Topics to learn

- [ ] Decide whether a gateway is necessary; identify protocol translation, aggregation, local control, and upstream connectivity responsibilities.
- [ ] Learn Linux files, users, permissions, processes, signals, package management, time synchronization, network diagnosis, and service management.
- [ ] Deploy a service with least privilege, configuration outside code, bounded logs, restart behavior, health checks, and controlled upgrades.
- [ ] Use local filtering, aggregation, rules, and caching with explicit CPU, memory, disk, and latency budgets.
- [ ] Build durable store-and-forward queues; define acknowledgements, write ordering, deduplication, replay rate, retention, and a full-disk policy.
- [ ] Translate device protocols without discarding units, timestamps, quality indicators, identity, or errors.
- [ ] Understand containers, persistent volumes, resource limits, image updates, and the differences between process isolation and device security.
- [ ] Plan disk wear, power loss, backups, local recovery, remote maintenance, credential storage, and physical access.
- [ ] Keep essential local functions independent of cloud availability and test what happens when upstream configuration conflicts with local state.

## Hands-on work

1. Deploy a gateway ingestion service that restarts automatically and reports its health.
2. Disconnect upstream service, retain a bounded backlog, restart the gateway, and replay without duplicate stored events.
3. Fill the queue to its configured limit and demonstrate the documented drop, aggregation, or rejection policy.

## Completion evidence

- [ ] Provide service configuration, storage and resource budgets, installation steps, and recovery instructions.
- [ ] Show that an upstream outage, reboot, and disk-capacity limit produce predictable behavior.

