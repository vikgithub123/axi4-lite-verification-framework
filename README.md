# AXI4-Lite Protocol Verification Framework

### Assertion-Driven RTL Verification | SystemVerilog | Functional Coverage

**Verifying the protocol, not just the functionality.**

## Project Vision

A hardware design can produce correct data in a simple test and still fail under timing stalls, independent channel handshakes, or reset conditions.

This project focuses on developing a structured verification framework for an AXI4-Lite interface that checks transaction correctness and protocol behavior using assertion-based verification, directed testing, constrained-random stimulus, functional coverage, and automated error detection.

The goal is to move beyond basic read/write testing toward systematic verification of important protocol scenarios.

## What Makes This Project Different?

| Verification challenge | Proposed approach |
|---|---|
| Incorrect handshake behavior | SystemVerilog Assertions (SVA) |
| Write address and data arrive at different times | Independent AW/W handshake scenarios |
| Receiver temporarily blocks transfers | Back-pressure testing |
| Read data does not match the written value | Reference-model scoreboard |
| Important scenarios remain untested | Functional coverage analysis |
| Bugs appear only in unusual sequences | Randomized transaction testing |
| Repeated manual testing is inefficient | Automated simulation and regression |

## Verification Architecture

```text
          TEST SEQUENCE GENERATOR
                     |
          +----------+----------+
          |                     |
    Directed Tests       Randomized Tests
          |                     |
          +----------+----------+
                     |
              AXI4-Lite Driver
                     |
              AXI4-Lite DUT
                     |
          +----------+----------+
          |          |          |
       Monitor   Assertions   Coverage
          |
      Scoreboard
          |
     RESULT ANALYSIS
          |
    PASS / FAIL / COVERAGE
```

## Verification Strategy

### 01 — Transaction Integrity

Verify register writes and reads. Compare actual read responses against a reference model.

### 02 — Handshake Stress Testing

Exercise independent write-address and write-data handshakes. Introduce stalls to verify that outstanding transfers are handled correctly.

### 03 — Assertion-Based Verification

Develop SVA properties to check signal stability during stalls, legal handshake behavior, and response consistency according to the protocol and DUT specification.

### 04 — Coverage-Driven Testing

Track scenarios such as read/write operations, response outcomes, stalled transfers, and address/data handshake ordering. Use coverage gaps to guide additional tests.

### 05 — Randomized Regression

Generate legal transaction sequences and run repeatable simulations using controlled random seeds.

### 06 — Failure Analysis

Capture assertion failures, transaction mismatches, and relevant waveform information to help identify the cause of a failure.

## Key AXI4-Lite Concepts

The interface contains five independent channels:

- **AW:** Write address
- **W:** Write data and byte strobes
- **B:** Write response
- **AR:** Read address
- **R:** Read data and response

Each channel uses a `VALID`/`READY` handshake. A transfer occurs when both signals are asserted at the active clock edge.

## Corner Cases to Verify

- Write address accepted before write data.
- Write data accepted before write address.
- Read and write activity occurring concurrently.
- Extended back-pressure on response channels.
- Reset during idle and selected transaction scenarios.
- Byte-enable behavior through write strobes.
- Repeated accesses to the same register.
- Randomized transaction sequences.

*Expected behavior for reset, invalid addresses, and responses must follow the selected DUT specification and applicable AXI requirements.*

## Technology Stack

| Technology | Purpose |
|---|---|
| SystemVerilog | Testbench and verification logic |
| SVA | Protocol property checking |
| Functional coverage | Scenario measurement |
| Reference-model scoreboard | Data integrity checking |
| RTL simulator | Functional simulation and waveform analysis |
| Git and GitHub | Source control and project documentation |

## Metrics to Report

Record actual simulation evidence rather than claiming results before testing:

- Directed tests passed / total.
- Randomized transactions completed.
- Assertion failures detected.
- Functional coverage achieved.
- Read/write data mismatches.
- Regression pass/fail status.

## Project Status

**Development focus:** Building a reusable AXI4-Lite verification environment.

### Planned Milestones

- [ ] Understand AXI4-Lite channels and handshake rules.
- [ ] Create a reproducible simulation setup.
- [ ] Implement directed read/write tests.
- [ ] Add a reference-model scoreboard.
- [ ] Develop and validate protocol assertions.
- [ ] Add randomized stimulus and functional coverage.
- [ ] Run regression tests and document measured results.

## References

- [Arm AMBA AXI Protocol Specifications](https://developer.arm.com/documentation/ihi0022/latest/)
- [Open-source AXI RTL reference](https://github.com/AlexForencich/verilog-axi)

## Author

**Sumanth SG**

Electronics and Communication Engineering

Interests: RTL Design, VLSI Design Verification, SystemVerilog, and Digital Design.

GitHub: [vikgithub123](https://github.com/vikgithub123)

## License and Attribution

This project builds on an existing open-source RTL codebase. Original copyright notices and applicable license terms are retained. Independently developed verification components and modifications will be documented as they are implemented.
