# 04 · Requirements and tradeoffs

[← Connections and failure](03-architecture-and-failure.md) · **Lesson 4 of 6** · [Next: Trust and lifecycle →](05-security-privacy-and-lifecycle.md)

> **Learning goal:** replace vague goals with measurable requirements and compare designs against them.

## Turn an intention into a test

“The monitor should be fast” leaves too much room for disagreement. Fast at sampling? Uploading? Refreshing the screen? Under which network conditions?

A useful requirement names the behavior, a limit, the conditions, and how to check it. Systems engineering separates stakeholder expectations from technical requirements and uses verification to check implementation against requirements ([National Aeronautics and Space Administration, 2016](../references.md#ref-systems), Chapters 4–5).

For this course, use this pattern:

**Under [conditions], the system shall [behavior] within [measurable limit], verified by [method].**

“Shall” expresses a requirement in the design document. It is not a claim that you have implemented or passed it.

## Work through five example requirements

These numerical values are sample learning targets. Choose and justify your own.

| ID | Example requirement | Proposed verification |
| --- | --- | --- |
| R1 | While powered, acquire one temperature sample every 10 s, with successive intervals between 9 and 11 s during a 30-minute run | Inspect timestamped device logs |
| R2 | On the defined test network, at least 95 of 100 valid readings appear within 5 s of acquisition | Compare acquisition and display timestamps using synchronized clocks |
| R3 | Mark the last valid reading stale when its age exceeds 30 s; update the display within the next 1 s refresh interval | Stop delivery and observe the status transition |
| R4 | During a 10-minute network outage, continue local sampling within R1's interval limits and never exceed 60 queued readings | Disconnect the network and inspect sample and queue logs |
| R5 | Retain telemetry for 7 days; a daily cleanup removes older records within the next 24 hours | Seed dated test records and execute the cleanup |

R4 deliberately permits queue overflow if timing produces more than 60 readings. The overflow policy must explain what gets discarded. If your requirement is “lose no readings,” capacity needs margin and a more precise timing model.

## Distinguish accuracy, resolution, and freshness

A screen showing 26.40 °C has a fine display increment. That does not establish that the measurement is within 0.01 °C of the actual temperature. Measurement uncertainty must be evaluated, rather than inferred from the number of displayed digits ([Joint Committee for Guides in Metrology, 2008](../references.md#ref-gum)).

For an introductory design, write a candidate accuracy target and the comparison method you would use. Record the reference instrument's uncertainty and test conditions. Mark the target **unverified** until measurements exist.

Freshness is a different question: a highly accurate reading from yesterday may not answer what the room is like now.

## Estimate the data volume

Assume:

- one reading every 10 seconds;
- 120 bytes of application payload per reading;
- seven days of retention.

Then:

```text
Readings per day = 86,400 seconds / 10 seconds = 8,640
Payload per day = 8,640 × 120 bytes = 1,036,800 bytes
Seven-day payload = 7 × 1,036,800 = 7,257,600 bytes
```

That is about **7.26 MB in decimal units**, for payload only. Network framing, encryption, retries, database indexes, backups, and logs add overhead. If your real message is larger than 120 bytes, replace the assumption and recalculate.

Do not estimate battery life from this calculation. Power requires a duty-cycle model and later current measurements; the [power module](../../15-power-and-energy-engineering/README.md) develops that work.

## Compare alternatives fairly

| Criterion | Direct-to-backend example | Gateway example |
| --- | --- | --- |
| Additional hardware | No dedicated gateway | Gateway and power supply |
| Local aggregation | Must run on device or another local service | Can run on gateway |
| Device maintenance | Device and backend | Device, gateway, and backend |
| Upstream outage | Depends on device's local design | Gateway may buffer, but devices still need a policy |
| Compatibility | Device must support its backend connection | Gateway can bridge selected interfaces |

First check mandatory requirements. A low-cost design that fails a required local behavior is not rescued by a high score elsewhere. After that, weigh preferences such as installation effort or flexibility.

## Try it yourself

Complete workbook section D with five requirements. Include conditions and a verification method for each. Estimate daily payload volume, then compare two architectures against the same requirements.

Add explicit assumptions for measurement accuracy, battery or power source, installation cost, availability, retention, and support lifetime. “Unknown—measure later” is more useful than an unsupported number.

## Check your reasoning

**Question:** You increase the sampling interval from 10 s to 60 s. What changes?

<details>
<summary>Reveal the explanation</summary>

At the same payload size, scheduled readings and payload volume fall to one sixth. Fast changes may become less visible. A 30-second stale threshold would now label normal operation stale between readings, so it must be reconsidered.

Battery life does not necessarily improve sixfold: sleep consumption, wake-up costs, sensing, and radio behavior also matter.

</details>

**Keep:** five requirements, a budget calculation, assumptions, and a decision rationale.  
[Next: Trust and lifecycle →](05-security-privacy-and-lifecycle.md)
