# Internet of Things Roadmap

The Internet of Things (IoT) connects physical devices to software and networks, allowing them to collect data, exchange information, and respond to the world around them. From home automation to environmental monitoring, IoT brings together electronics, embedded programming, connectivity, and data processing to solve practical problems.

This roadmap provides a structured learning path for beginners who want to understand and build IoT systems. It starts with electronics and mathematical foundations, introduces C and C++, and progresses through embedded systems, networking, data processing, security, and deployment.

Use the topics below as a guide, pairing each concept with hands-on practice. Start with the foundations, build a small device, and then connect it to an application. Revisit more advanced topics as your projects require them; you do not need to master every subject before building something useful.

## Category folders

Each category has its own study guide with prerequisites, detailed topics, practical exercises, and completion evidence. Follow the study phases below to progress from foundations to a tested, maintainable IoT system.

| Category | Guide |
| --- | --- |
| 1. Introduction to IoT | [Open guide](01-introduction-to-iot/README.md) |
| 2. Electronics Fundamentals | [Open guide](02-electronics-fundamentals/README.md) |
| 3. Mathematical Foundations | [Open guide](03-mathematical-foundations/README.md) |
| 4. Programming Foundations: C and C++ | [Open guide](04-programming-foundations/README.md) |
| 5. Development Tools and Workflow | [Open guide](05-development-tools-and-workflow/README.md) |
| 6. Microcontrollers and Embedded Systems | [Open guide](06-microcontrollers-and-embedded-systems/README.md) |
| 7. Networking and Wireless Communication | [Open guide](07-networking-and-wireless-communication/README.md) |
| 8. IoT Messaging and Application Protocols | [Open guide](08-iot-messaging-and-application-protocols/README.md) |
| 9. Gateways and Edge Computing | [Open guide](09-gateways-and-edge-computing/README.md) |
| 10. Backends, Storage, and Dashboards | [Open guide](10-backends-storage-and-dashboards/README.md) |
| 11. Security and Privacy | [Open guide](11-security-and-privacy/README.md) |
| 12. Testing and Troubleshooting | [Open guide](12-testing-and-troubleshooting/README.md) |
| 13. Deployment and Device Lifecycle | [Open guide](13-deployment-and-device-lifecycle/README.md) |
| 14. Optional Specializations | [Open guide](14-optional-specializations/README.md) |
| 15. Power and Energy Engineering | [Open guide](15-power-and-energy-engineering/README.md) |
| 16. Sensing, Signal Processing, and Control | [Open guide](16-sensing-signal-processing-and-control/README.md) |
| 17. Production and System Engineering | [Open guide](17-production-and-system-engineering/README.md) |
| 18. Projects and Assessment | [Open guide](18-projects-and-assessment/README.md) |

## Study order and completion rules

Folder numbers retain the original 14 categories. Categories 15–17 add engineering depth and belong at the stages shown below; category 18 contains the practical assessment path.

1. **Foundations:** study 01, learn 02 and 03 together, then work through 04 and 05. Begin security thinking in 11 and tests in 12 immediately.
2. **A dependable device:** complete 06, then the sensing and control foundations in 16 and power measurements in 15. Complete the local-sensing milestone in 18.
3. **A connected device:** work through 07 and 08 with identity, access control, and secure transport from 11. Complete the connected-device milestone.
4. **An end-to-end system:** study 09 and 10, deepen 11 and 12, and complete the application milestone. A gateway implementation is needed when the architecture calls for one; understand its role even in a direct-to-backend design.
5. **Unattended operation:** complete 13 and the system/production foundations in 17. Revisit 15 and 16 using the assembled system, then finish the fleet capstone in 18.
6. **Specialization:** choose one or more branches from 14 after the core system works. PCB manufacture, advanced control, edge ML, and every wireless protocol are not universal prerequisites.

For each category, complete the topics, perform the hands-on work, and retain the completion evidence. Test assumptions, record measurements, and explain failure behavior. One complete stack is enough for the core path; compare alternatives and implement them when your specialization needs them. There is no fixed completion time: progress depends on demonstrated skills.

The outline below remains a concise reference. The linked category guides are the detailed curriculum, and [Projects and Assessment](18-projects-and-assessment/README.md) defines the milestones.

## Learning Path

### 1. Introduction to IoT

[Detailed guide, exercises, and completion criteria](01-introduction-to-iot/README.md)

Understand how the parts of a connected system work together.

- **System components:** Sensors measure physical conditions, actuators perform actions, and controllers run the device logic.
- **Data flow:** Follow a reading from a sensor through a device, network, backend, and dashboard.
- **System architecture:** Learn device-to-device communication, gateway-based systems, and direct connections to a backend.
- **Use cases:** Explore home automation, agriculture, environmental monitoring, industrial monitoring, and asset tracking.
- **Design constraints:** Consider cost, power consumption, connectivity, reliability, privacy, and maintenance.

### 2. Electronics Fundamentals

[Detailed guide, exercises, and completion criteria](02-electronics-fundamentals/README.md)

Learn to assemble and troubleshoot the circuits your software will control.

- **Electrical quantities:** Voltage, current, resistance, power, Ohm's law, and series and parallel circuits.
- **Components:** Resistors, capacitors, diodes, transistors, switches, and voltage regulators.
- **Circuit reading and assembly:** Schematics, breadboards, polarity, grounding, and basic soldering.
- **Digital and analog signals:** Logic levels, pull-up and pull-down resistors, analog-to-digital conversion, and pulse-width modulation (PWM).
- **Sensors and actuators:** Read temperature, light, or motion sensors; drive LEDs, buzzers, and motors through suitable driver circuits.
- **Measurement and safe handling:** Use a multimeter, check component ratings, and begin with low-voltage circuits.

### 3. Mathematical Foundations

[Detailed guide, exercises, and completion criteria](03-mathematical-foundations/README.md)

Focus on the mathematics needed to interpret measurements and reason about device behavior.

- **Algebra and units:** Rearrange equations, convert units, and use scientific notation.
- **Number systems:** Binary, hexadecimal, signed integers, and representation limits.
- **Boolean logic:** AND, OR, NOT, truth tables, and bit masks.
- **Statistics:** Mean, minimum, maximum, variance, and measurement uncertainty.
- **Sampling and filtering:** Sampling intervals, noise, moving averages, and an introduction to aliasing.
- **Applied calculations:** Scale raw sensor readings, estimate battery life, and calculate storage or transmission needs.

### 4. Programming Foundations: C and C++

[Detailed guide, exercises, and completion criteria](04-programming-foundations/README.md)

Develop the skills needed to write firmware and understand hardware-oriented code.

- **Language basics:** Variables, data types, operators, conditions, loops, and functions.
- **Working with data:** Arrays, strings, structures, enumerations, and constants.
- **Memory concepts:** Pointers, references, stack and heap allocation, object lifetimes, and bounds checking.
- **Bitwise operations:** Set, clear, and test individual bits in configuration values and registers.
- **C++ organization:** Classes, encapsulation, constructors, and resource management.
- **Toolchain basics:** Source files, headers, compilation, linking, compiler warnings, and debugging.
- **Supporting languages:** Use Python for scripts and data inspection; learn JavaScript when building web interfaces.

### 5. Development Tools and Workflow

[Detailed guide, exercises, and completion criteria](05-development-tools-and-workflow/README.md)

Make your projects reproducible and easier to maintain.

- **Version control:** Git repositories, commits, branches, diffs, and meaningful change descriptions.
- **Development environment:** Editors, command-line tools, board support packages, libraries, and dependency management.
- **Reading documentation:** Find pin assignments, electrical limits, timing requirements, and examples in datasheets.
- **Device interaction:** Flash firmware, inspect serial output, and capture useful diagnostic logs.
- **Project documentation:** Record wiring, setup steps, configuration, and known limitations.

### 6. Microcontrollers and Embedded Systems

[Detailed guide, exercises, and completion criteria](06-microcontrollers-and-embedded-systems/README.md)

Connect programming concepts to the hardware running your application.

- **Computing platforms:** Understand the difference between microcontrollers and single-board computers.
- **Microcontroller architecture:** CPU, flash, RAM, registers, clocks, and peripherals.
- **GPIO:** Configure inputs and outputs, read buttons, and debounce mechanical switches.
- **Timing:** Timers, interrupts, nonblocking loops, and finite-state machines.
- **Peripheral interfaces:** Use UART for serial communication and I2C or SPI for peripheral connections.
- **Sensor integration:** Read device registers, check errors, calibrate measurements, and handle missing sensors.
- **Reliability and power:** Watchdog timers, reset causes, sleep modes, and persistent configuration.
- **Real-time operating systems:** Explore tasks, scheduling, queues, mutexes, and concurrency after mastering a basic firmware loop.

### 7. Networking and Wireless Communication

[Detailed guide, exercises, and completion criteria](07-networking-and-wireless-communication/README.md)

Understand how devices exchange information and how connection choices affect a design.

- **Network fundamentals:** IP addresses, ports, subnets, DNS, DHCP, and client-server communication.
- **Transport protocols:** Compare TCP and UDP in terms of delivery behavior, overhead, and application needs.
- **Local connectivity:** Learn the roles of Ethernet, Wi-Fi, and Bluetooth Low Energy (BLE).
- **Mesh and long-range options:** Explore Zigbee, Thread, LoRa/LoRaWAN, and cellular connectivity at a conceptual level.
- **Selection criteria:** Compare range, bandwidth, energy use, infrastructure, and operating cost.
- **Connection failures:** Handle disconnects, timeouts, retries with backoff, and offline buffering.

### 8. IoT Messaging and Application Protocols

[Detailed guide, exercises, and completion criteria](08-iot-messaging-and-application-protocols/README.md)

Learn how to structure communication between devices and services.

- **MQTT:** Brokers, topics, publish/subscribe messaging, quality of service, retained messages, and last-will messages.
- **HTTP and REST:** Requests, methods, status codes, headers, and device-facing APIs.
- **Other communication patterns:** Understand where CoAP and WebSockets may fit.
- **Payload design:** Use JSON or binary formats, include units and timestamps, and plan for schema changes.
- **Telemetry and commands:** Separate measurements, device status, configuration changes, and control requests.
- **Delivery behavior:** Account for duplicate messages, delayed commands, acknowledgements, and idempotent operations.

### 9. Gateways and Edge Computing

[Detailed guide, exercises, and completion criteria](09-gateways-and-edge-computing/README.md)

Decide which work belongs near the device and which belongs on a remote service.

- **Gateway responsibilities:** Collect data, translate protocols, and connect local devices to backend services.
- **Linux basics:** Files, permissions, processes, networking tools, and service management.
- **Local processing:** Filter readings, aggregate measurements, and trigger simple rules.
- **Offline operation:** Store data locally and synchronize after connectivity returns.
- **Edge deployment:** Manage configuration, logs, service restarts, and resource limits.

### 10. Backends, Storage, and Dashboards

[Detailed guide, exercises, and completion criteria](10-backends-storage-and-dashboards/README.md)

Turn device messages into information people can use.

- **Data ingestion:** Receive telemetry through a broker or API and validate incoming payloads.
- **Storage choices:** Understand relational databases, time-series data, retention periods, and indexing basics.
- **Device records:** Track identifiers, capabilities, configuration, and last-seen status.
- **Visualization:** Build charts, device lists, status indicators, and historical views with clear units.
- **Alerts and automation:** Define thresholds, avoid repeated alerts, and distinguish stale readings from healthy devices.
- **Hosting fundamentals:** Compare local and cloud hosting; understand environment configuration, backups, and service monitoring.

### 11. Security and Privacy

[Detailed guide, exercises, and completion criteria](11-security-and-privacy/README.md)

Apply these ideas throughout your projects, beginning with the first connected prototype.

- **Threat modeling:** Identify valuable data, exposed interfaces, and possible misuse of device controls.
- **Device identity:** Give devices distinct credentials and plan for provisioning, rotation, and revocation.
- **Access control:** Separate authentication from authorization and limit device and user permissions.
- **Secure communication:** Understand TLS, certificate validation, and protecting secrets in transit and storage.
- **Firmware protection:** Explore secure boot, signed updates, and restrictions on debug interfaces.
- **Input handling:** Validate messages, constrain commands, and avoid exposing secrets in logs or source control.
- **Privacy:** Collect only needed data and define who can access it and how long it is retained.

### 12. Testing and Troubleshooting

[Detailed guide, exercises, and completion criteria](12-testing-and-troubleshooting/README.md)

Check how the system behaves both normally and when components fail.

- **Firmware tests:** Test calculations, parsing, state transitions, and error handling independently of hardware where practical.
- **Hardware integration:** Verify sensor readings, wiring, interface timing, and actuator behavior on the real device.
- **End-to-end checks:** Trace a measurement from the device to storage and the dashboard.
- **Failure scenarios:** Disconnect the network, restart the broker, remove a sensor, and interrupt device power.
- **Performance and power:** Measure latency, memory use, message volume, and current consumption.
- **Debugging tools:** Use serial logs, debuggers, logic analyzers, oscilloscopes, and packet captures as needed.

### 13. Deployment and Device Lifecycle

[Detailed guide, exercises, and completion criteria](13-deployment-and-device-lifecycle/README.md)

Learn what changes when a prototype must run unattended or support multiple devices.

- **Provisioning:** Assign identities and configure connectivity without embedding shared secrets in source code.
- **Over-the-air updates:** Plan version checks, update validation, staged rollout, and recovery from interrupted updates.
- **Fleet monitoring:** Track firmware versions, device health, connectivity, and failed updates.
- **Physical design:** Consider enclosures, connectors, mounting, environmental exposure, and service access.
- **Operational planning:** Estimate power, bandwidth, storage, maintenance effort, and replacement needs.
- **Retirement:** Revoke credentials and remove stored personal or sensitive data when devices leave service.

### 14. Optional Specializations

[Detailed guide, exercises, and completion criteria](14-optional-specializations/README.md)

Choose an area after completing a working end-to-end project.

- **PCB design:** Schematics, board layout, component selection, and design for manufacture.
- **Industrial IoT:** Industrial interfaces, protocol integration, and dependable monitoring systems.
- **Edge machine learning:** Data collection, model evaluation, embedded inference, and memory and power constraints.
- **Robotics and control:** Feedback loops, motor control, and coordinated sensing and actuation.
- **Energy-efficient systems:** Battery characterization, duty cycling, and low-power communication.
- **Smart home and interoperability:** Protocol layers, device models, commissioning, ownership, and multi-controller lifecycle testing.

### 15. Power and Energy Engineering

[Detailed guide, exercises, and completion criteria](15-power-and-energy-engineering/README.md)

- **Power budgets:** Measure sleep, sensing, processing, and radio activity; distinguish peak current from average energy use.
- **Supply and batteries:** Study regulators, usable capacity, temperature, aging, supply transients, and appropriate protection.
- **Optimization:** Compare duty cycling, batching, wake-up costs, and changes in data freshness.
- **Verification:** Validate runtime assumptions and behavior at low supply voltage on the assembled system.

### 16. Sensing, Signal Processing, and Control

[Detailed guide, exercises, and completion criteria](16-sensing-signal-processing-and-control/README.md)

- **Measurement quality:** Sensor selection, calibration, uncertainty, drift, physical placement, and invalid readings.
- **Signal processing:** Analog conditioning, sampling, aliasing, digital filtering, and latency.
- **Control:** Hysteresis, feedback, introductory PID, saturation, and timing.
- **Failure behavior:** Define actuator behavior during startup, stale data, sensor faults, and lost communications.

### 17. Production and System Engineering

[Detailed guide, exercises, and completion criteria](17-production-and-system-engineering/README.md)

- **System design:** Requirements, resource budgets, design reviews, and failure-mode analysis.
- **Production preparation:** Controlled hardware revisions, component alternatives, test fixtures, calibration, and traceability.
- **Release and validation:** Compatibility, dependency inventory, manufacturing tests, environmental evaluation, and review of applicable requirements.
- **Sustained support:** Service access, incident response, replacement, ownership cost, and end-of-life planning.

## Hands-on Practice

Follow the staged [Projects and Assessment guide](18-projects-and-assessment/README.md) for prerequisites, acceptance criteria, a failure-test matrix, and an evidence template. The ideas below can be used for those milestones.

### Exercises

Practice one concept at a time before combining subsystems.

- Blink an LED without blocking the main loop, then add a debounced button.
- Read a sensor, convert its raw output into physical units, and report errors clearly.
- Smooth noisy readings with a moving average and compare the filtered and raw values.
- Exchange messages over UART or read a peripheral using I2C or SPI.
- Publish telemetry to an MQTT broker and display it with a subscriber.
- Simulate a network outage and verify that the device reconnects without losing control of its local tasks.

### Minor Projects

Build a small system with a clear input, output, and success criterion.

- **Room monitor:** Measure temperature and humidity, save readings, and display a history chart.
- **Plant monitor:** Track soil moisture, calibrate the sensor, and indicate when watering may be needed.
- **Door event logger:** Detect opening events, timestamp them, and handle switch bounce.
- **Low-voltage light controller:** Send commands to an LED device and report its actual state to a dashboard.

### Major Projects

Combine hardware, connectivity, software, and maintenance into a complete system.

- **Greenhouse monitoring and control:** Use multiple sensors, local control rules, a dashboard, and defined behavior during network failures.
- **Multi-room sensor network:** Manage several device identities, collect telemetry centrally, and identify offline devices.
- **Equipment condition monitor:** Collect vibration or temperature data, establish a baseline, and flag deviations for investigation.
- **Fleet management prototype:** Provision multiple devices, monitor health, and demonstrate validated updates with recovery behavior.

### Project Completion Checklist

- Describe the problem, intended users, and measurable success criteria.
- Include a system diagram, wiring diagram, and bill of materials.
- Document setup, dependencies, configuration, and how to reproduce the demonstration.
- Keep credentials out of the repository and explain how devices receive them.
- Record test results, failure behavior, limitations, and possible improvements.

## Career Path Choices

Use your projects to identify which part of IoT development you enjoy most.

| Career direction | Topics to emphasize | Portfolio evidence |
| --- | --- | --- |
| Embedded firmware development | C/C++, peripherals, timing, RTOS concepts, debugging | Reliable firmware with documented hardware tests |
| Hardware and PCB design | Electronics, schematics, layout, power design | A documented board design with measurement results |
| IoT backend development | Messaging, APIs, databases, device management | A telemetry service with device identity and monitoring |
| IoT application development | Dashboards, data visualization, APIs, user workflows | An application that clearly shows device state and history |
| IoT security | Device identity, access control, firmware updates, threat modeling | A threat model and demonstrated security controls |
| Systems integration and testing | Networking, gateways, protocol integration, failure testing | A working multi-device system with a repeatable test plan |

Start with a small sensor-to-dashboard project, then deepen the topics needed to make it reliable, secure, and maintainable.

## Technical references

Use these primary references alongside the category exercises. Check the documentation for the hardware target and software release used in your project.

- [NIST IoT device cybersecurity core baseline](https://csrc.nist.gov/pubs/ir/8259/a/final): device security capabilities for category 11.
- [NIST 8259 series](https://www.nist.gov/itl/applied-cybersecurity/nist-cybersecurity-iot-program/nistir-8259-series): manufacturer support and lifecycle considerations for categories 11, 13, and 17.
- [OASIS MQTT 5.0](https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html): delivery semantics, sessions, and message properties for category 08.
- [FreeRTOS mutexes](https://freertos.org/Real-time-embedded-RTOS-mutexes.html): priority inheritance and its limits for category 06.
- [OpenThread guides](https://openthread.io/guides): Thread networking and border routers for category 07 and the smart-home specialization.
- [Connectivity Standards Alliance Matter](https://csa-iot.org/all-solutions/matter/): smart-home interoperability for category 14.
- [Zephyr Twister](https://docs.zephyrproject.org/latest/develop/twister/index.html): an embedded testing implementation for category 12.
- [ESP-IDF OTA documentation](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/system/ota.html): image validation and recovery for category 13; behavior depends on target and configuration.
