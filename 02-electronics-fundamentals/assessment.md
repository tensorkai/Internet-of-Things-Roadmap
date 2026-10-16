# Electronics fundamentals assessment

[Module home](README.md) · [Workbook](workbook.md)

Answer before opening the key. Calculations may use a calculator; explain the connection or assumption as well as the number.

1. A 1 kohm resistor is connected across 3.3 V. Find current and power.
2. Two 1 kohm resistors are in parallel across 3.3 V. Find equivalent resistance and source current.
3. A 10 kohm / 10 kohm divider outputs 1.65 V unloaded. What happens when a 10 kohm load is connected from its output to ground?
4. Select a standard resistor near the calculated value for a 2.0 V LED at about 4 mA from 3.3 V. Explain why you also calculate worst-case current.
5. Why can a breadboard circuit fail even when the component positions resemble a photograph?
6. How do voltage and current meter connections differ? What must be checked before using continuity mode?
7. Explain the two states of a 10 kohm pull-up button circuit. Calculate current when pressed at 3.3 V.
8. A 5 V output drives a 3.3 V input. Is a readable HIGH enough to establish compatibility?
9. A 100 uF ideal capacitor supplies 20 mA for 100 microseconds. Find its voltage drop. Name two effects the calculation ignores.
10. Find ideal code width for a 12-bit, 3.3 V ADC. Explain why this does not establish accuracy.
11. A 3.3 V PWM output has 25% duty. Find its average voltage and its HIGH voltage.
12. Describe flyback diode orientation for a low-side N-MOSFET motor switch. Why are gate threshold and normal running current insufficient selection criteria?

<details><summary>Answer key</summary>

1. 3.3 mA; 10.89 mW.
2. 500 ohm; 6.6 mA total.
3. Lower effective resistance becomes 5 kohm, so output becomes 1.10 V.
4. Calculated 325 ohm; choose 330 ohm. Supply, LED drop, and resistor tolerance change current; confirm component ratings at the worst case.
5. Electrical nodes matter: rail splits, internally connected groups, reversed polarity, and package pinouts can differ.
6. Voltage is measured across nodes; current in series using the correct fused socket/range. Continuity requires power removed and capacitors discharged.
7. Released HIGH, pressed LOW; about 0.33 mA through the pull-up when pressed.
8. No. Verify allowed input voltage, guaranteed HIGH/LOW levels, loading, timing, and power-off conditions. Use appropriate translation where necessary.
9. 0.020 V; ESR, inductance, and supply response are omitted.
10. About 0.806 mV. Reference error, noise, offset, gain, and nonlinearity can dominate.
11. Average 0.825 V; HIGH remains 3.3 V.
12. Cathode to positive motor supply, anode to drain/motor-low node. Threshold does not establish low on-resistance; startup/stall current can exceed normal current. Check thermal and switching limits too.

</details>

## Practical review

| Competency | Evidence required |
| --- | --- |
| Predict | LED and divider calculations, units, tolerances |
| Build | Reproducible schematic, parts list, your own wiring photo |
| Measure | Lab tables with real readings and instrument details |
| Diagnose | Fault hypothesis, test, repair, and retest |
| Explain limits | Logic/ADC compatibility, power transients, driver protection |

Revisit incorrect answers and repeat any failed practical check. Do not mark the hardware work complete using only calculated or simulated values. Optional sensor, firmware, scope, and motor extensions can remain pending if clearly identified.

[Return to the workbook](workbook.md) · [Continue to mathematical foundations](../03-mathematical-foundations/README.md)
