# 01 · Things and systems

[← Module home](../README.md) · **Lesson 1 of 6** · [Next: Data and commands →](02-data-and-commands.md)

> **Learning goal:** identify the physical quantity, the hardware roles, and the human decision in a connected system.

## Start with a useful question

Suppose a room feels warm when you arrive. A single thermometer tells you the temperature now. A connected room monitor could also show when the temperature rose, whether the reading is recent, and whether another room has the same pattern.

The useful outcome is not “send numbers to the internet.” It is “help someone decide when to investigate room conditions.” That difference matters: a device can successfully transmit thousands of readings while giving its user no useful answer.

IoT combines physical things with communication and information services. The ITU reference model distinguishes device, network, service-support, and application roles, with management and security across them ([International Telecommunication Union, 2012](../references.md#ref-itu)). A cloud service is one possible deployment choice; it is not a compulsory box in every learning design.

## Recognize the roles

| Role | What it does | Room-monitor example |
| --- | --- | --- |
| Sensor | Converts a physical quantity into a usable signal | A temperature sensor |
| Signal conditioning | Prepares a signal for measurement | Filtering or amplification; it may be inside the sensor |
| Controller | Runs device logic and coordinates inputs and outputs | A microcontroller executing firmware |
| Network | Carries data between participants | The local network and its access point |
| Gateway | Connects device-side communication to another system | An optional local collection computer |
| Backend | Receives, processes, or stores data | A telemetry receiver and database |
| Application | Helps someone interpret or act on information | A history chart with data age |
| Actuator | Produces a physical effect | An optional indicator LED |

This table is a teaching decomposition of the device-to-application path. Several roles may share one board or process. A digital sensor can contain both sensing and conversion circuitry. A monitoring-only system can omit the actuator. “Gateway,” “router,” and “database” describe different responsibilities even when one computer hosts more than one of them.

## Look at real hardware

<img src="../../assets/iot-esp32.jpg" alt="Real photograph of an ESP32 development board, showing its module, connector, and pin headers." width="560">

*Photograph by Ubahnverleih (2018), CC0. [Source and license](../../assets/VISUALS.md#esp32-development-board).*

Find the metal-covered module, connector, and pin headers in the photograph. You are looking at a development board, not a finished room monitor. The photograph does not establish which pins a particular sensor needs, whether its voltage is compatible, or how the firmware behaves.

The next electronics module teaches you how to answer wiring questions using documentation and measurement. Here, practice separating **what a component is** from **what the full system must accomplish**.

## Follow the physical-to-digital loop

For our example:

1. The room has a temperature.
2. A sensor produces a reading.
3. Firmware attaches units, an identifier, and status.
4. The reading crosses a network.
5. A service stores it.
6. A dashboard shows the value and its age.
7. A person decides whether to investigate.

If we add a remote LED command, the journey also returns from the application to the device. The LED shows that an output changed; it does not prove that the room became cooler.

## Apply the idea elsewhere

These are illustrative design prompts, not claims about specific installed systems.

| Context | Physical observation | Possible decision | Important limitation |
| --- | --- | --- | --- |
| Home automation | Door-open event | Check an unexpected opening | A contact sensor does not identify the person |
| Agriculture | Soil-moisture reading | Inspect whether irrigation is needed | One probe may not represent the whole plot |
| Environmental monitoring | Air-temperature history | Investigate unusual conditions | Placement affects interpretation |
| Industrial monitoring | Machine vibration | Schedule an inspection | A change alone does not diagnose a fault |
| Asset tracking | Position or proximity update | Find an item | Last reported position may be old |
| Wearables | Movement signal | Review activity patterns | A consumer reading is not automatically a diagnosis |

## Try it yourself

In workbook section A, choose one use case. Write: **“For [user], measure [quantity] so they can decide [action].”** Then name the roles in its data path. Mark a gateway and actuator as required, optional, or unnecessary, and explain each choice.

## Check your reasoning

**Question:** A sensor sends a number to a phone, but the phone shows neither units nor the time of measurement. Is the network connection enough to make the information useful?

<details>
<summary>Reveal the explanation</summary>

No. A value such as “29” is ambiguous without its unit, and an old value can be mistaken for a current one. The connection is only part of the system. The application needs enough context to support the intended decision.

</details>

**Keep:** your use-case statement and component map.  
[Next: A reading's journey →](02-data-and-commands.md)
