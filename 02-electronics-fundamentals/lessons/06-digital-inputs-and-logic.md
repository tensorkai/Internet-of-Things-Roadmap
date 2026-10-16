# 06 · Digital inputs and logic

[Previous](05-measurement-and-troubleshooting.md) · [Module home](../README.md) · **Lesson 6 of 9** · [Next](07-power-and-decoupling.md)

**Goal:** give an input a defined state and establish whether two devices can communicate electrically.

## A digital signal is still a voltage

An input interprets voltage ranges as LOW or HIGH. Its datasheet specifies `VIL(max)`, the highest guaranteed LOW voltage, and `VIH(min)`, the lowest guaranteed HIGH voltage. Between them, interpretation is not guaranteed. Separately check allowed input voltages: a signal can be recognized as HIGH and still exceed a damage limit.

For an illustrative input with `VIL(max) = 0.3 × VDD` and `VIH(min) = 0.7 × VDD` at 3.3 V, LOW is guaranteed at or below 0.99 V and HIGH at or above 2.31 V, within permitted input limits. These ratios are examples, not universal MCU specifications.

Compare the source's guaranteed `VOH(min)` with the receiver's `VIH(min)`, and `VOL(max)` with `VIL(max)`, at the actual load and supply. A 3.3 V output may not meet a 5 V receiver's HIGH requirement. A 5 V output may damage a 3.3 V input unless that exact pin is explicitly tolerant under the relevant conditions, including power-off.

## Wire a button with a pull-up

```text
+3.3 V ---- Rpull 10 kohm ----+---- input / meter
                             |
                            switch
                             |
                            GND
```

| Switch | Input voltage, approximately | Logical meaning |
| --- | --- | --- |
| Open | 3.3 V | HIGH / not pressed |
| Closed | 0 V | LOW / pressed |

This is an active-low button. When pressed, the resistor limits current to `3.3 / 10000 = 0.33 mA`. Without the pull-up, an open input floats and may respond to noise. A pull-down reverses the arrangement: resistor to ground and switch to the logic supply. Internal pull resistors can be useful, but their values, availability, and startup configuration depend on the controller.

Four-leg tactile switches commonly have internally joined pin pairs. Map those pairs with continuity before wiring; otherwise the input may appear permanently pressed.

## Level shifting and debounce

A resistor divider can reduce a slow, unidirectional signal into a high-impedance input when loading, thresholds, tolerance, and timing are checked. It cannot raise voltage and is not a general bidirectional bus translator. Use a translator appropriate to push-pull or open-drain signaling and the required speed. An open-drain line needs a pull-up to a voltage permitted by every attached device.

Mechanical contacts bounce: one press can produce several transitions. One software approach samples every millisecond and accepts a new state after 20 consecutive equal samples. That 20 ms interval is a starting example; verify actual behavior. An RC network feeding a suitable Schmitt-trigger input is a hardware option. An RC ramp into an ordinary input can violate input transition-time requirements, so check the receiver's guidance.

## Try it yourself

A source guarantees HIGH at 2.4 V; a receiver needs at least 2.31 V. What is nominal guaranteed HIGH margin, before other effects? Does this prove complete compatibility?

<details><summary>Check your reasoning</summary>

Margin is 0.09 V. Also check LOW levels, current, noise/ground offsets, timing, input limits, and power sequencing. A positive HIGH margin alone is insufficient.

</details>

**Keep:** lab 2 button table and voltage-compatibility notes. References: [SparkFun: Pull-up Resistors](https://learn.sparkfun.com/tutorials/pull-up-resistors), [TI: Logic Datasheets](https://www.ti.com/lit/an/szza036b/szza036b.pdf).

[Next: Reliable power](07-power-and-decoupling.md)
