# Microcontrollers and Embedded Systems

[Back to roadmap](../README.md)

## Prerequisites

Categories 02–05.

## Topics to learn

- [ ] Compare MCUs and single-board computers; study CPU, RAM, flash, buses, registers, clock trees, reset sources, and memory-mapped peripherals.
- [ ] Understand reset/startup, interrupt vectors, linker scripts and memory maps, bootloaders, and flash partition constraints at a practical reading level.
- [ ] Configure GPIO and pin multiplexing; implement button debounce and nonblocking finite-state machines.
- [ ] Use hardware timers, PWM, capture/compare, ADC, and DMA when supported. Budget interrupt latency, execution time, and buffer ownership.
- [ ] Integrate UART, I2C, and SPI: framing, baud rates, addressing, chip select, clock modes, pull-ups, bus contention, and timeout/recovery behavior.
- [ ] Read sensor registers, verify device identity, detect missing or stuck sensors, and separate drivers from application logic.
- [ ] Design watchdog supervision, brownout/reset diagnostics, and persistent configuration with atomic updates, integrity checks, wear awareness, and schema migration.
- [ ] Begin with a cooperative loop; then learn RTOS task states, priorities, queues, semaphores, mutexes, event groups, and task notifications.
- [ ] Handle race conditions, deadlock, priority inversion, stack sizing, and ISR-safe APIs. Measure scheduling behavior instead of assuming that an RTOS guarantees deadlines.
- [ ] Introduce sleep/wakeup behavior and retained state; complete the detailed power work in category 15.

## Hands-on work

1. Build a nonblocking sensor-and-button application with a visible heartbeat and explicit timeout states.
2. Capture an I2C or SPI transaction and relate its bytes to the datasheet.
3. Port acquisition and networking into separate RTOS tasks; bound queues and demonstrate behavior when the consumer is slower.
4. Interrupt a configuration write and verify recovery to a valid old or new configuration.

## Completion evidence

- [ ] Provide a memory budget, timing measurements, peripheral traces, and reset diagnostics.
- [ ] Demonstrate that a disconnected sensor and a stalled network do not freeze essential local work.
- [ ] Explain each shared resource and how concurrent access is controlled.

Keep code, diagrams, measurements, and notes from these exercises with your project. Record failures and fixes, not just the successful demonstration.

