# 01 · Electricity and a safe setup

[Module home](../README.md) · **Lesson 1 of 9** · [Next](02-circuit-calculations.md)

**Goal:** explain voltage and current, then predict a resistor circuit's behavior.

## Four quantities

| Quantity | Meaning | Unit | Use |
| --- | --- | --- | --- |
| Voltage, V | Potential difference between two points | volt, V | Measure across two nodes |
| Current, I | Rate of charge flow through a branch | ampere, A | Measure in series |
| Resistance, R | Opposition to current in a resistive element | ohm | For an ohmic resistor, R = V / I |
| Power, P | Rate of energy transfer | watt, W | P = V × I |

Voltage is relative: “3.3 V” normally means 3.3 V relative to circuit ground. **Ground is a reference and return connection, not automatically protective earth.** Current needs a closed path. An open switch interrupts it; a short creates an unintended low-resistance path. Conventional current flows from positive through the load toward the return. A resistor transfers energy as heat; it does not consume current.

## Worked example

```text
+3.3 V ---- R1 1 kohm ---- GND

I = V / R = 3.3 / 1000 = 0.0033 A = 3.3 mA
P = V × I = 3.3 × 0.0033 = 10.89 mW
```

A 1/4 W resistor is rated for 250 mW under specified conditions, well above this prediction. Temperature and mounting can reduce allowed dissipation. For resistors, `P = I²R = V²/R`. LEDs and motors do not behave as simple fixed resistances.

Convert units before calculating: `1 kohm = 1000 ohm`, `1 mA = 0.001 A`, and `100 nF = 0.1 uF`. A mA/A mix-up changes the result by 1000.

## Prepare the bench

1. With no circuit attached, set the regulated supply to 3.3 V and verify its output with the meter.
2. For the first LED or resistor circuit, set a current limit around 20 mA. This is a ceiling, not a forced operating current.
3. Turn the output off. Check polarity, resistor value, rail connections, and loose wires.
4. Connect and energize briefly. If current limiting occurs unexpectedly, turn off and inspect the circuit.
5. Disconnect power before changing wiring. Do not handle hot or damaged parts.

![Voltage measurement across an AA battery](../assets/battery-voltage.jpg)

**Look for:** probes across opposite source terminals. This is a voltage measurement, not a current measurement. The battery reading is not the 3.3 V used in our lab. Photo: SparkFun Electronics, CC BY-SA 4.0; [credit](../assets/README.md).

## Try it yourself

Find current and power for 3.3 V across 330 ohm. Is a 1/4 W resistor sufficient at nominal conditions?

<details><summary>Check your reasoning</summary>

`I = 10 mA`; `P = 33 mW`, below 250 mW. Adding an LED changes the voltage across the resistor and therefore the current.

</details>

**Keep:** calculations in workbook section A. Further reading: [SparkFun: Ohm's Law](https://learn.sparkfun.com/tutorials/voltage-current-resistance-and-ohms-law).

[Next: Circuit calculations](02-circuit-calculations.md)
