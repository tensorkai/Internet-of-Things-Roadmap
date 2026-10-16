# Electronics lab workbook

[Module home](README.md) · [Lessons](README.md#your-learning-path) · [Assessment](assessment.md)

Copy this workbook into your notes and fill the blanks. **Example predictions are not measured results.** Label each result calculated, simulated, or measured. If equipment is unavailable, leave the measurement blank and state what remains unverified.

## A · Predictions and setup

- Name / date:
- Supply model, set voltage, and current limit:
- Meter model, sockets, selected mode/range, accuracy specification:
- Breadboard continuity map, including any split rails:
- 3.3 V across 1 kohm: current ___; resistor power ___.
- 3.3 V across 330 ohm: current ___; resistor power ___.
- Two 1 kohm resistors: series equivalent ___; parallel equivalent ___.
- Equal 10 kohm divider: nominal output ___; bounds with ±5% resistors ___ to ___.

## B · Bill of materials and compatibility

| Reference | Exact part / value | Relevant rating or pinout | Datasheet or manual link |
| --- | --- | --- | --- |
| Supply | | | |
| R1, LED resistor | 330 ohm nominal | Tolerance and power: | |
| D1, red LED | | Anode/cathode, forward drop, current: | |
| Rpull | 10 kohm nominal | | |
| SW1 | Momentary button | Internally connected pairs: | |
| RV1 | 10 kohm potentiometer | Wiper and outer terminals: | |
| Optional sensor | | Supply, output range, transfer function: | |
| Optional controller | | GPIO limits, ADC range/reference: | |

Record source `VOH(min)` / `VOL(max)` and receiver `VIH(min)` / `VIL(max)` before connecting a digital signal. Check input voltage limits separately, including powered-off behavior.

## Lab 1 · Calculate, build, and measure an LED

**Purpose:** connect Ohm's law, polarity, tolerance, and measurement.

1. Read lessons 01–05. Confirm that your LED's documented ratings suit the calculated current.
2. Predict current with `I = (Vsupply - Vforward) / R`; calculate resistor dissipation and worst-case bounds.
3. With power off, measure the isolated resistor. Wire `3.3 V → 330 ohm → LED anode → LED cathode → GND` using separate nodes. Lesson 04 provides example coordinates.
4. Inspect polarity and connections. Use about a 20 mA current limit for this small circuit. Turn on and measure local supply, LED voltage, and resistor voltage.
5. Infer current from measured resistor voltage divided by measured resistance. Check that the resistor and LED drops approximately sum to the supply.
6. Power off, replace R1 with 1 kohm, and repeat. Restore the original value afterward if desired.

| Quantity | Calculated prediction | Measured result | Instrument / uncertainty notes |
| --- | --- | --- | --- |
| Actual R1 resistance, unpowered | 330 ohm ± its tolerance | | |
| Local supply | 3.3 V nominal | | |
| LED forward voltage | 2.0 V example only | | |
| R1 voltage | 1.3 V example only | | |
| Current inferred from R1 | 3.94 mA example only | | |
| Resistor dissipation | 5.12 mW example only | | |
| Current with 1 kohm | 1.3 mA example only | | |

**Explain:** do measured values fit your actual part tolerances and meter uncertainty? Why is LED voltage not precisely constant?

Attach your schematic and a clear photograph of your own wiring. The module's reference photographs are not substitutes for build evidence.

## Lab 2 · Button and analog input

**Purpose:** establish defined logic states and measure a sensor-like voltage before connecting a controller.

### Button

1. Map the button's contacts with continuity while unpowered.
2. Connect 10 kohm from 3.3 V to a signal node, and the button from that node to ground.
3. Measure the node relative to ground with the button released and pressed.
4. If adding a controller, verify its logic compatibility, select an input pin, and connect the common reference. Record physical pin and software name separately.
5. Optional firmware exercise: compare raw transition counts with a debounce rule, such as accepting a state after 20 consecutive 1 ms samples. Record actual behavior rather than assuming every switch needs 20 ms.

| State | Expected voltage | Measured voltage | Logical state |
| --- | --- | --- | --- |
| Released | Near 3.3 V | | |
| Pressed | Near 0 V | | |

### Analog input

Connect the potentiometer's outer terminals to 3.3 V and ground; measure the wiper. Confirm wiper identity before wiring. A potentiometer is a sensor-voltage substitute, not a calibrated environmental sensor.

| Wiper position | Measured voltage | Optional ADC code | Reconstructed voltage / difference |
| --- | --- | --- | --- |
| Near ground | | | |
| Near middle | | | |
| Near supply | | | |

Before adding an ADC, check its permitted range, reference, attenuation, and acquisition requirements. Reduce the source range if necessary. Never connect an out-of-range wiper merely because the controller's supply is 3.3 V.

If you have a documented analog sensor, replace the potentiometer only after checking its supply, pinout, output range, and transfer equation. Record its raw voltage and calculated physical quantity. If unavailable, mark **sensor hardware extension pending**.

### Diagnose a disconnected pull-up

Power off, disconnect only the pull-up, then observe the released input with power restored. A floating voltage may be unstable or appear steady because the meter and leakage affect it. Do not require a particular random reading as proof. Power off and use continuity to establish the missing resistor connection, restore it, and remeasure both states.

## Lab 3 · Observe a small supply load change

**Purpose:** distinguish steady measurements from transient evidence without requiring a motor.

Build this separate resistor-only circuit with power off:

```text
+3.3 V ---- Rbase 1 kohm ---------------- GND
     |
     +---- switch ---- Rload 330 ohm ---- GND
```

The base current is 3.3 mA. Closing the switch adds 10 mA, for 13.3 mA nominal total. Rload dissipates 33 mW, within a 1/4 W rating under normal lab conditions. Verify actual ratings and set a suitable current limit, such as 20 mA for this resistor-only setup. If adding other circuitry, recalculate the budget.

1. Measure the local supply before and during the added load. Record whether the supply enters current limiting.
2. Optional: use a correctly connected oscilloscope to trigger on the load change and capture the minimum supply voltage. Record probe reference, timebase, bandwidth, and trigger setting.
3. Power off. If allowed by your supply's documentation, add a suitably rated 100 nF ceramic and 10–100 uF electrolytic across the local supply, with correct polarity. Recheck the wiring and repeat. Discharge capacitors appropriately before rewiring; do not short them with a tool.
4. Compare results. A small, well-regulated circuit may show no meaningful steady change. Do not invent a transient improvement if your instrument cannot establish one.

| Condition | Meter voltage, load off | Meter voltage, load on | Scope minimum, if available | Observation |
| --- | --- | --- | --- | --- |
| Without added capacitors | | | | |
| With permitted capacitors | | | | |

**Explain:** a meter's stable display cannot rule out a short dip. If there is no scope, state “transient behavior not measured.” Identify wiring resistance, supply response, current limit, and probe setup as possible influences before changing parts.

## C · Fault log and final evidence

| Symptom | Prediction / hypothesis | Measurement | Change | Retest result |
| --- | --- | --- | --- | --- |
| | | | | |

- [ ] Schematic includes values, node labels, polarity, and exact pin names.
- [ ] Your own photograph clearly shows the assembled connections.
- [ ] Parts and ratings match the actual build.
- [ ] Calculations include units and tolerance bounds.
- [ ] Readings identify the instrument and measurement conditions.
- [ ] At least one fault is diagnosed with evidence.
- [ ] Unperformed extensions and unknowns remain explicitly labeled.

[Take the assessment](assessment.md)
