# Preliminary Project Proposal: TEV core

## Summary of project

The **TEV** core is a configurable multi-purpose RISC-V core able to boot a rich OS like Linux.

From a single configuration source, several flavors can be generated: 32- or 64-bit architecture,
with or without FPU, with or without MMU, ...

It can be configured to achieve the minimal foot-print for low-power, low-area applications, and it can also be configured to achieve 

### Summary of Timeline

The goal is to have all most of the basic features verified and ready in **Dec 2025**. A refined planning should be agreed upon later.

## Summary of requirements

### Introduction

They are expected to evolve until project start. Any requirements added beyond the project start will be considered optional enhancements unless they are considered critical.

### Initial project requirements 

#### Functional

- `IMAC` set of instructions extensions
- Support for booting OS
- `FENCE` instructions
- L1 I+D caches
- Include or exclude the FPU (`F` and `D` extensions)
- Include or exclude the MMU
- Security and functional safety features (to be determined later)
- It is important that we design with AI in mind. Features that help accelerate AI application will be considered and determined at a later point.

#### Verification

- High coverage
- Complete package (incl. good quality documentation aligned with verification) 
- Coverage-driven verification to ensure completeness and quality of results
- Use of SystemVerilog and UVM
- On-the-fly, in-simulation checking of DUT against a Reference Model
    - Step-and-compare is current technique used

### Future enhancements:

Adding standard or custom extensions, superscalar, SMP multi-core processor, SoC building blocks, architecture generation, build a silicon application processor...

## List of project outputs

Design:
- Specification
- Core documentation (structure to be defined later)
- Configurable RTL source code

Verification:
- Verification plans (simulation)
- Versatile generic testbench with adaptation layers for CVA6
    - Subset compliant with _sustainable open-source solution_ expectactions
- Test sequences
- Verification results
     - Including code coverage and functional coverage
- Option: formal verification
     - Verification plan
	 - Bug reports
	 - Verification report

## Architecture diagram

|                  | TEV64                | TEV32                |
| :--------------- | :-----------------:  | :------------------: |
| ISA              | RV64IMA\[EFD\]CZicsr | RV32IMA\[EFD\]CZicsr |
| Privilege levels | M/S/U                | M/S/U                |
| [Virtual memory] | \[Sv39\]             | \[Sv32\]             |

\[\] denotes a configurable feature.

![TEV pipeline](TBD)

## Repository Structure

https://github.com/OYounis/TEV: Project master directory
https://github.com/<user>/tev-Core: core directory with a basic testbench for simple test
https://github.com/<user>/tev-dv: complete core test environment, and configuration and simulation scripts

## Preliminary Project plan

Preliminary (to be completed and reviewed by participants):

| Category                 | Task                                                            | Priority  |
| ------------------------ | --------------------------------------------------------------- | --------- |
| Design / Verification    | Microarchitecture                                               | 0         | 
| Design / Verification    | Specifications                                                  | 0         |
| Design / Verification    | Documentation                                                   | 0         |
| Design                   | Implement extendsion: I, M, A, C                                | 0         |
| Design                   | Fix warning and errors                                          | 0         |
| Design                   | Develop MMU                                                     | 1         |
| Design                   | Adapt F,D MMU to 32-bit architecture                            | 1         |
| Design                   | Develop Cache                                                   | 1         |
| Design                   | Safety and Security options                                     | 2         |
| Design                   | Configurable multiplier/divider: 1 or more cycles               | 2         |
| Design                   | Standard extensions: B, V, crypto...                            | 3         |
| Design                   | Generic reset (sync/async, active high/low)                     | 2         |
| Design                   | FPGA optimizations                                              | 4         |
| Design                   | _Other tasks?_                                                  | ?         |
| Verification (testbench) | Support open source simulator: Veripool (Verilator)             | 2         |
| Verification (testbench) | Support simulators: Mentor, Synopsys,                           | 1         |
| Verification (testbench) | Support open source ISS : Spike and Sail                        | 2         |
| Verification (testbench) | Support ISS : Imperas (OVPsim)                                  | 1         |
| Verification (testbench) | Support Riscv-dv Random Generation with VCS (Synopsys)          | 2         |
| Verification (testbench) | Support FORCE-RISCV generator (32 and 64 bit)                   | 3         |
| Verification (testbench) | Support “trace and compare” checker                             | 2         |
| Verification (testbench) | Support “step and compare” checker                              | 2         |
| Verification (testbench) | Define TEV HW configs (64/32bits, FPU disable/enable,…)         | 1         |        
| Verification (testbench) | Add functional coverage checkers                                | 1         |
| Verification (testbench) | Extract code coverage with Questa / VCS                         | 1         |
| Verification (testbench) | _Other tasks?_                                                  | ?         |
| Verification (tests)     | Edit and maintain verifications plans                           | 1         |
| Verification (tests)     | Riscv-compliance, riscv-tests regression suites                 | 1         |
| Verification (tests)     | Riscv-dv Instruction Random Generation                          | 2         |
| Verification (tests)     | FORCE-RISCV Instruction Random Generation                       | 2         |
| Verification (tests)     | Continous integration with different TEV configurations         | 2         |
| Verification (tests)     | Tests for added extensions                                      | 2         |
| Verification (tests)     | Add tests to increase coverage                                  | 2         |
| Verification (tests)     | Reach 100% code coverage                                        | 1         |
| Verification (tests)     | Reach 100% functional coverage                                  | 1         |
| Verification (tests)     | Option: formal verification plan                                | 4         | 
| Verification (tests)     | Option: execute formal verification                             | 4         | 
| Verification (tests)     | _Other tasks?_                                                  | ?         |

? denotes an optional task.
