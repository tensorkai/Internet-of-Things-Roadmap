# 02 · Circuit calculations

[Previous](01-electricity-and-safe-setup.md) · [Module home](../README.md) · **Lesson 2 of 9** · [Next](03-components-and-datasheets.md)

**Goal:** solve simple networks and account for component tolerances.

## Series, parallel, and Kirchhoff's laws

Series components share branch current; their resistances add. Two 1 kohm resistors in series across 3.3 V give 2 kohm, 1.65 mA, and a 1.65 V drop across each resistor.

Parallel components share both nodes and therefore voltage. `1/Rtotal = 1/R1 + 1/R2`; for two resistors, `Rtotal = R1 × R2 / (R1 + R2)`. Two 1 kohm resistors in parallel give 500 ohm. Each draws 3.3 mA; total current is 6.6 mA.

**Kirchhoff's current law:** total incoming current equals total outgoing current at a node. **Kirchhoff's voltage law:** signed rises and drops sum to zero around a loop. A 3.3 V source cannot support two steady 2 V drops in its only passive series loop: check the assumptions or measurements.

## A voltage divider

```text
+3.3 V ---- R1 10 kohm ----+---- R2 10 kohm ---- GND
                          |
                         Vout
```

With negligible output loading, `Vout = Vin × R2 / (R1 + R2) = 1.65 V`. R2 connects the output to ground. A divider can produce a sensor signal; it is not a regulated power supply.

Connect a 10 kohm load from Vout to ground. The lower effective resistance becomes `10 kohm || 10 kohm = 5 kohm`, so `Vout = 3.3 × 5 / 15 = 1.10 V`. The output changed because the load changed the circuit. Even a meter loads the circuit; check its input resistance.

## Worst-case bounds

A 10 kohm ±5% resistor can be 9.5–10.5 kohm. For the unloaded equal divider and an exact 3.3 V supply:

```text
Vout minimum = 3.3 × 9.5 / (10.5 + 9.5) = 1.5675 V
Vout maximum = 3.3 × 10.5 / (9.5 + 10.5) = 1.7325 V
```

If the supply varies, use its minimum for minimum output and maximum for maximum output. Include loading and instrument uncertainty before calling a measurement wrong. Typical values are not guaranteed limits.

## Try it yourself

For a 3.3 V unloaded divider with 1 kohm above 2 kohm, calculate output voltage, current, and power in the upper resistor.

<details><summary>Check your reasoning</summary>

`Vout = 2.2 V`; `I = 1.1 mA`; `Pupper = 0.0011² × 1000 = 1.21 mW`. A load to ground reduces the effective lower resistance and the output voltage.

</details>

**Keep:** nominal and worst-case calculations. Reference: [SparkFun: Voltage Dividers](https://learn.sparkfun.com/tutorials/voltage-dividers).

[Next: Components and datasheets](03-components-and-datasheets.md)
