# 08 · Analog signals, ADCs, and PWM

[Previous](07-power-and-decoupling.md) · [Module home](../README.md) · **Lesson 8 of 9** · [Next](09-drivers-and-integration.md)

**Goal:** relate an analog voltage to a digital code and explain what PWM actually outputs.

## ADC resolution is not accuracy

An analog-to-digital converter maps an input range to codes. An ideal unipolar N-bit ADC spanning 0 to Vref has `2^N` codes, from 0 to `2^N - 1`, with an ideal code width of `Vref / 2^N`.

For 12 bits and a 3.3 V reference, the code width is `3.3 / 4096 = 0.806 mV`. An ideal 1.65 V input is around midscale, code 2048. A useful approximate reconstruction is `Vin ≈ code × Vref / 4096`. Real converters differ in transition conventions, offset, gain, attenuation, and full-scale behavior; use the actual transfer function. Do not confuse endpoint display scaling by 4095 with the 4096 quantization intervals.

Noise, reference error, nonlinearity, and sensor error can exceed one code width. A 12-bit result does not guarantee 12-bit measurement accuracy. The ADC's reference and accepted input range may differ from the board supply. Never assume a “3.3 V board” accepts the full 0–3.3 V range on every analog input.

## Make an adjustable input

Connect the outer terminals of a 10 kohm potentiometer to 3.3 V and ground; measure its wiper relative to ground. Confirm terminal identities first. Check low, middle, and high positions with a meter before attaching an ADC. If the ADC permits less than that range, change the source range or conditioning circuit first.

For a real analog sensor, document supply range, output range, units, and transfer function. A hypothetical sensor with `Vout = 0.5 V + 0.010 V/°C × T` gives 25 °C at 0.75 V. That equation applies only to the hypothetical sensor; do not use it for an unspecified part.

## PWM and an RC filter

PWM repeatedly switches between LOW and HIGH. Duty cycle is `Ton / period`; frequency is `1 / period`. Ideal 0–3.3 V PWM at 25% duty has a time-average of 0.825 V, but the pin still reaches 3.3 V. It is not a steady 0.825 V supply.

```text
PWM ---- R 10 kohm ----+---- filtered output (high-impedance load)
                       |
                     C 100 nF
                       |
                      GND
```

`tau = R × C = 1 ms`; `fc = 1 / (2πRC) ≈ 159 Hz`. A 10 kHz PWM signal is substantially above this cutoff and is smoothed, with residual ripple. Larger RC reduces ripple but slows response; a step takes about five time constants to settle near its final value. Output loading changes the filter. Low-pass filtering before ADC sampling also helps reduce aliasing; software averaging cannot undo all aliasing after sampling.

An op-amp voltage follower can buffer a weak signal: output feeds the inverting input and the signal feeds the non-inverting input. Choose a unity-gain-stable part with suitable input common-mode range, output swing, supply voltage, bandwidth, and load capability. “Rail-to-rail” still requires reading the specified limits. ADC acquisition time and source impedance also matter because its sampling capacitor needs time to charge.

## Try it yourself

Find the code width of a 10-bit ADC with 3.3 V reference, and the ideal average of 60% duty 3.3 V PWM.

<details><summary>Check your reasoning</summary>

`3.3 / 1024 = 3.22 mV` per code; PWM average is `0.60 × 3.3 = 1.98 V`. The instantaneous HIGH voltage remains 3.3 V.

</details>

**Keep:** workbook lab 2 analog table. References: [Microchip: ADC Code Width](https://developerhelp.microchip.com/xwiki/bin/view/products/data-converters/adc-specs/code-width/), [SparkFun: PWM](https://learn.sparkfun.com/tutorials/pulse-width-modulation).

[Next: Drivers and integration](09-drivers-and-integration.md)
