# Programming Foundations: C and C++

[Back to roadmap](../README.md)

## Prerequisites

Categories 01 and 03; electronics can proceed in parallel.

## Topics to learn

- [ ] Learn variables, fixed-width types, operators, conditions, loops, functions, scope, const correctness, and explicit error returns.
- [ ] Practice arrays, bounded strings, structures, enumerations, pointers, references, and ownership of buffers.
- [ ] Understand stack, heap, static storage, alignment, object lifetimes, undefined behavior, bounds errors, integer conversions, and endianness.
- [ ] Use masks and shifts carefully; distinguish volatile access from synchronization. Volatile alone does not make concurrent code safe.
- [ ] Separate headers and implementations; learn preprocessing, compilation, linking, libraries, compiler warnings, and debug/release builds.
- [ ] Use C++ classes, constructors/destructors, RAII, and interfaces where they clarify ownership. Understand target/toolchain constraints on exceptions, RTTI, and allocation.
- [ ] Implement state machines, ring buffers, bounded parsers, and nonblocking work with explicit memory and time limits.
- [ ] Use a debugger, assertions, host-side tests, and memory/undefined-behavior checks when supported. Practice reading compiler diagnostics.
- [ ] Use Python for test fixtures, serial tools, and data analysis; add JavaScript or TypeScript for web applications. These complement firmware skills.

## Hands-on work

1. Build a sensor conversion library with tests for normal, invalid, and boundary inputs.
2. Implement a fixed-capacity ring buffer and verify wraparound, full, and empty behavior.
3. Parse a length-limited command into a state machine and reject malformed input without corrupting memory.

## Completion evidence

- [ ] Build from documented commands with no unexplained compiler warnings.
- [ ] Explain the ownership, lifetime, maximum size, and failure behavior of each buffer.
- [ ] Provide tests and a debugger trace showing a bug identified and corrected.

Keep code, diagrams, measurements, and notes from these exercises with your project. Record failures and fixes, not just the successful demonstration.

