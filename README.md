# AXI4 and AXI4-Lite: RTL Study and Verification

## Overview

This repository is my learning workspace for exploring AXI4 and AXI4-Lite bus protocols, RTL architecture, simulation, and hardware verification.

The codebase is based on the open-source **verilog-axi** project by Alex Forencich. I am using it to understand practical bus implementations and develop additional verification skills.

## Learning Objectives

- Understand AXI4 and AXI4-Lite interfaces and handshake mechanisms.
- Study read and write transaction paths.
- Explore RTL modules, FIFOs, adapters, and interconnects.
- Run existing testbenches and analyze simulation results.
- Develop additional test cases and verification checks.

## Repository Structure

- `rtl/` — RTL modules and AXI components.
- `tb/` — Testbenches and verification tests.
- `syn/` — Synthesis-related files and project configurations.
- `.github/` — Repository workflows and automation.

## Planned Contributions

- Add directed tests for AXI4-Lite read and write transactions.
- Develop protocol assertions using SystemVerilog Assertions (SVA).
- Add self-checking verification and error-case testing.
- Document simulation results and any original improvements.

## Reference and Attribution

Original project: [Alex Forencich — verilog-axi](https://github.com/AlexForencich/verilog-axi)

This repository is based on an existing open-source project. Original copyright notices and license terms are retained. Any new verification components or modifications will be documented separately.

## Current Status

Learning and verification extensions are in progress. Test results and coverage metrics will be added after they have been run and verified.
