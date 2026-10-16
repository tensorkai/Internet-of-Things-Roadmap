# 07 · Reliable power

[Previous](06-digital-inputs-and-logic.md) · [Module home](../README.md) · **Lesson 7 of 9** · [Next](08-analog-adc-and-pwm.md)

**Goal:** explain why a correct schematic can still reset or produce noisy readings.

Wires and breadboard contacts have resistance and inductance. A sudden load increase can make the local supply dip even when the supply display seems normal. Motors, radios, and switching outputs can also disturb shared ground connections.

## Two capacitor jobs

**Decoupling capacitors** provide a short local path for fast transient currents. A 100 nF ceramic near an IC supply pin is a common starting example, but follow that IC's required values and layout. Keep the loop from power pin through capacitor to ground short.

**Bulk capacitors** provide additional charge for slower changes. Put them near the load or supply entry as appropriate. A large capacitor elsewhere does not replace local decoupling. Check voltage rating, polarity, effective capacitance under bias, ESR, and the regulator's stability requirements.

![Capacitor package reference](../assets/capacitors.jpg)

The photograph illustrates several packages; choose actual parts from specifications, not visual resemblance. SparkFun Electronics, CC BY-SA 4.0; [credit](../assets/README.md).

## Estimate a transient

If a capacitor alone supplies an extra current `I` for time `dt`, its ideal voltage change is `dV = I × dt / C`. An extra 20 mA for 100 microseconds from 100 uF gives:

```text
dV = 0.020 × 0.000100 / 0.000100 = 0.020 V
```

This simplified estimate omits ESR, inductance, and the supply's response. It explains a trend; it is not proof that a chosen capacitor fixes a real circuit.

## Regulator headroom and heat

A linear regulator needs sufficient input above its output: verify dropout at your current and temperature. A hypothetical regulator with 0.3 V dropout needs at least about 3.6 V input for 3.3 V output, plus design margin. Its approximate dissipation from 5 V to 3.3 V at 100 mA is `(5 - 3.3) × 0.1 = 0.17 W`. Check thermal resistance and allowable temperature, not just its advertised current rating.

Switching regulators can improve efficiency, but require suitable inductors, capacitors, and layout, and can introduce ripple. A regulator module's label does not establish board-level current capability.

Budget peak currents as well as averages. Route load current so it does not share a long, resistive return with a sensitive sensor. Keep board-level signal grounds connected as intended; arbitrary separation can destroy the common reference.

## Try it yourself

How much does an ideal 100 uF capacitor drop while supplying 10 mA for 1 ms? Can a steady meter reading rule out a brief reset-causing dip?

<details><summary>Check your reasoning</summary>

`dV = 0.010 × 0.001 / 0.000100 = 0.1 V`. A meter may miss a short transient. Use a suitably triggered oscilloscope when available; otherwise label transient behavior unverified.

</details>

**Keep:** workbook lab 3 observations. Reference: [SparkFun: Capacitors](https://learn.sparkfun.com/tutorials/capacitors). Consult the actual regulator datasheet for capacitor and layout requirements.

[Next: Analog, ADCs, and PWM](08-analog-adc-and-pwm.md)
