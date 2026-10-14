# IoT Messaging and Application Protocols

[Back to roadmap](../README.md)

## Prerequisites

Categories 04, 06, and 07; apply category 11 while connecting devices.

## Topics to learn

- [ ] Use MQTT brokers, publish/subscribe, topic hierarchy, subscriptions, wildcard scope, and per-device topic permissions.
- [ ] Compare MQTT QoS 0/1/2, retained messages, last wills, keepalive, persistent sessions, and message/session expiry where supported. Broker delivery guarantees do not make a database write or actuator action exactly once.
- [ ] Use HTTP methods, headers, status codes, timeouts, authentication, pagination, caching, and idempotent resource operations. Understand TLS and certificate verification.
- [ ] Compare CoAP resource access and confirmable messaging with HTTP; identify constrained-network tradeoffs. Use WebSockets when a persistent bidirectional application channel is useful.
- [ ] Design JSON and compact binary payloads; compare readability, schema tooling, bandwidth, parsing cost, and compatibility. Bound payload length before parsing.
- [ ] Include device identity, schema version, units, sample/event time, ingestion time where relevant, sequence number, and data-quality flags. State how identity is authenticated rather than trusting a payload field.
- [ ] Separate telemetry, events, commands, configuration, desired state, and reported state. Define accepted, executed, failed, and expired command outcomes.
- [ ] Handle duplicates, retries, reordering, stale retained values, interrupted sessions, and backpressure. Use unique command identifiers and a persistent deduplication strategy when needed.
- [ ] Specify command expiry and reboot behavior. Prefer explicit set-state commands to non-idempotent toggles; physical feedback is required to confirm physical results.

## Hands-on work

1. Publish measurements and status; verify QoS, retained messages, last wills, and reconnect behavior with a second client.
2. Write a versioned telemetry schema and reject oversized, malformed, and unsupported payloads.
3. Send the same command twice, deliver an expired command, and restart the device between receipt and completion; record the defined outcome.

## Completion evidence

- [ ] Provide a topic/API contract, payload examples, authorization rules, and command state diagram.
- [ ] Show that retries cannot silently repeat a hazardous or unintended action.
- [ ] Document the actual broker/client protocol version and supported features.

## Primary reference

[OASIS MQTT 5.0 specification](https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html)

