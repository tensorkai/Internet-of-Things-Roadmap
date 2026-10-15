# 02 · A reading's journey

[← Things and systems](01-things-and-systems.md) · **Lesson 2 of 6** · [Next: Connections and failure →](03-architecture-and-failure.md)

> **Learning goal:** distinguish message types and explain what a message can—and cannot—prove.

## Give the number context

Imagine receiving `26.4`. Is it degrees Celsius? Which room? Was it measured now? Did the sensor report a fault?

A **message contract** is the agreement between a sender and receiver about fields, meanings, and behavior. The following is our example contract, not a required IoT standard:

```json
{
  "schema_version": 1,
  "device_id": "room-01",
  "boot_id": "boot-7",
  "sequence": 42,
  "sampled_at": "2026-10-14T08:00:00Z",
  "temperature_c": 26.4,
  "quality": "valid"
}
```

Read it as a sentence: room-01 produced sample 42 during boot-7 at the stated UTC time; the measured quantity is temperature in Celsius, and the device currently marks the sample valid.

The receiver records its own `received_at` time. Measurement time and reception time are different: an offline device may upload a reading much later. If the device clock is not synchronized, label the timestamp uncertainty rather than pretending it is exact. A validity label describes device checks; it is not proof of calibration.

For this exercise, the combination of device ID, a boot ID that changes on each reboot, and sequence number identifies a reading. A production implementation must ensure the boot ID is not accidentally reused.

## Separate the conversations

| Message type | Meaning | Example |
| --- | --- | --- |
| Telemetry | A measurement or observation | Temperature is 26.4 °C |
| Event | Something happened | Sensor became unavailable |
| Command | A request for an action | Set the indicator LED on |
| Configuration | A setting governing future behavior | Sample every 10 seconds |
| Desired state | A requested target | Indicator should be on |
| Reported state | What the device says is currently true | Indicator output is off |

A command asks for a change. Desired state can persist as a target to reconcile. Reported state can disagree with that target while work is pending or has failed.

## Trace one command

Suppose the dashboard requests `set_led(on)` with command ID `c17` and a 30-second expiry.

| Step | What you know | What you do not yet know |
| --- | --- | --- |
| Application sends c17 | A request left the application | Whether the device received it |
| Device accepts c17 | The device recognized and allowed it | Whether the output changed |
| Device reports “on” | Its firmware reports the output state | Whether the LED physically emitted light |
| Independent observation confirms light | The observed physical effect occurred | Whether it will remain correct indefinitely |

A broker acknowledgement belongs to the messaging exchange. It is not a physical-action receipt. MQTT defines delivery qualities and acknowledgement exchanges, including a mode where duplicate delivery can occur ([Banks et al., 2019](../references.md#ref-mqtt)). Design the application outcome separately.

For our exercise, repeating `set_led(on)` leaves the same desired result. Repeating `toggle_led()` may reverse it. This is why “set the state” is easier to reason about than “change the state” when a request can be repeated. The device must still define expiry, authorization, and behavior after restart.

## Distinguish fresh, stale, and invalid

Use this teaching policy: sample every 10 seconds and mark a valid reading **stale when its age exceeds 30 seconds**. An explicit sensor fault is **invalid immediately**, even if the last good value is recent. Show the old value only as history with its timestamp.

| Time | Observation | Correct display |
| --- | --- | --- |
| 08:00:00 | Valid sample: 26.4 °C | 26.4 °C, valid |
| 08:00:20 | No newer sample | Last value, age 20 s |
| 08:00:31 | Still no newer sample | Stale; last measured at 08:00:00 |
| 08:00:35 | Sensor-fault event arrives | Invalid / sensor unavailable |

A zero temperature is a possible measurement, so do not use zero as the only error signal.

## Try it yourself

In workbook section B, define your telemetry fields and their units. Add a rule for duplicate readings, uncertain time, and invalid measurements. Then classify these messages: “sample interval = 60 s,” “door opened,” “set LED off,” and “LED is off.”

## Check your reasoning

<details>
<summary>Reveal the classification and a duplicate-message example</summary>

The four messages are configuration, event, command, and reported state.

If the receiver sees room-01 / boot-7 / sequence 42 twice, it can store one reading under this contract. It must not discard all readings with sequence 42 forever: a later boot has a different boot ID.

A delayed old reading can fill a historical gap without replacing the current value as “live.”

</details>

**Keep:** your contract and a timeline containing a delayed sample and a repeated command.  
[Next: Connections and failure →](03-architecture-and-failure.md)
