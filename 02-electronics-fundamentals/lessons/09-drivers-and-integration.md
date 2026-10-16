# 09 · Drivers and integration

[Previous](08-analog-adc-and-pwm.md) · [Module home](../README.md) · **Lesson 9 of 9** · [Workbook](../workbook.md)

**Goal:** separate control signals from load power and explain inductive-load protection.

A GPIO can drive only limited current, with per-pin and device-wide limits. A small LED may fit those limits with a calculated resistor. Motors, relay coils, and many buzzers require a driver. Never power a motor directly from a GPIO.

## A low-side MOSFET switch

The following is a topology for review, not a universal parts recipe:

```text
+Vload ---- motor ----+---- drain of N-channel MOSFET
                     |
             flyback diode anode

flyback diode cathode ---- +Vload
MOSFET source ------------ GND
GPIO ---- gate resistor -- gate
gate ---- pull-down ------ GND
controller GND ----------- GND
```

The flyback diode is across the motor, with **cathode at positive supply and anode at the switched drain node**. It is reverse biased during normal operation. When the switch opens, motor inductance keeps current flowing through the diode loop, limiting the voltage excursion. Reversing that diode can short the supply when the MOSFET turns on.

Select a logic-level MOSFET with on-resistance specified at the actual available gate voltage. Gate threshold voltage describes the beginning of conduction, not full enhancement. Check drain voltage, startup/stall current, safe operating area, thermal conditions, and switching losses. For example, 0.2 A through 0.1 ohm produces `I²R = 4 mW` of conduction loss; a 1 A stall produces 100 mW. That does not include switching loss or establish package temperature.

A gate pull-down keeps the driver off while the GPIO is high impedance. A series gate resistor controls charging current and ringing; choose it with switching speed and the controller's drive limits in mind. Select the diode for current, reverse voltage, pulse energy, and switching frequency. A documented motor-driver module can provide an easier starting point, but verify its ratings and included protection.

## Different loads need different handling

| Load | Key design decision |
| --- | --- |
| LED | Current-limiting resistor and GPIO current budget |
| Active buzzer | Rated supply/current; switch on/off as required |
| Passive piezo | Requires an alternating drive waveform; not the same as a magnetic coil |
| Magnetic buzzer / relay / DC motor | Inductive energy and appropriate clamp protection |
| Reversible DC motor | H-bridge with specified recirculation paths; a single diode across the motor is not a general solution |

Motor startup can disturb supply and ground. Keep the load current loop compact and follow the driver layout guidance. Use a load supply appropriate for the motor; share the intended signal reference without tying unrelated positive supplies together.

## Try it yourself

Why can a MOSFET with a 1 V threshold perform poorly when driven by 3.3 V? Why is motor running current insufficient for driver selection?

<details><summary>Check your reasoning</summary>

Threshold does not guarantee low on-resistance at 3.3 V. Check a guaranteed on-resistance specification at an appropriate gate voltage. Starting or stalled current can greatly exceed running current and determine electrical and thermal stress.

</details>

## Finish the module

Complete the three [workbook labs](../workbook.md), then the [assessment](../assessment.md). Submit the schematic, bill of materials, your wiring photograph, calculations, readings, and a fault diagnosis. A motor build is optional; the reviewed topology and component-selection reasoning are required.

References: [Adafruit: DC Motor Transistors](https://learn.adafruit.com/adafruit-arduino-lesson-13-dc-motors/transistors), [Adafruit: MOSFET Driver](https://learn.adafruit.com/adafruit-mosfet-driver?view=all).

[Next category: Mathematical Foundations](../../03-mathematical-foundations/README.md)
