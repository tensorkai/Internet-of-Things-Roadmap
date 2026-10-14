# Development Tools and Workflow

[Back to roadmap](../README.md)

## Prerequisites

Basic programming from category 04.

## Topics to learn

- [ ] Use terminal commands, file paths, environment variables, serial ports, and platform-specific permissions.
- [ ] Practice Git commits, branches, diffs, merges, conflict resolution, tags, and reviews. Keep credentials and generated build output out of source control.
- [ ] Install a supported toolchain and board package; pin dependency versions and record the exact board, MCU, SDK, compiler, and flashing configuration.
- [ ] Read datasheets, reference manuals, schematics, errata, and SDK examples. Distinguish typical values, recommended operating conditions, and absolute maximum ratings.
- [ ] Learn build systems, build profiles, linker output, reproducible clean builds, dependency licenses, and configuration templates.
- [ ] Flash and recover a board; use serial logs and SWD/JTAG where supported. Record boot messages and reset causes.
- [ ] Create a project layout separating firmware, backend, application, tests, hardware, and documentation.
- [ ] Set up continuous integration for compilation, linting/static analysis, and host-side tests. Store versioned release artifacts and checksums.
- [ ] Write setup instructions, wiring diagrams, configuration reference, troubleshooting notes, and a decision log.

## Hands-on work

1. Create a small repository with a clean-build command, test command, example configuration, and a useful ignore file.
2. Rebuild from a fresh checkout and compare the documented environment with what was actually required.
3. Tag a release and demonstrate reverting a change without losing unrelated work.

## Completion evidence

- [ ] A second person can follow your setup instructions without hidden files or credentials.
- [ ] CI runs meaningful checks, and each released image can be traced to source and configuration.

Keep code, diagrams, measurements, and notes from these exercises with your project. Record failures and fixes, not just the successful demonstration.

