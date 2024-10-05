# DIGITAL VLSI SOC DESIGN AND PLANNING

## Day 1 - Inception of Open-Source EDA, OpenLANE, and Sky130 PDK

### [1. How to Talk to Computers](#1-how-to-talk-to-computers)
- [Introduction to QFN-48 Package, Chip, Pads, Core, Die, and IPs](#introduction-to-qfn-48-package-chip-pads-core-die-and-ips)
- [Introduction to RISC-V](#introduction-to-risc-v)
- [From Software Applications to Hardware](#from-software-applications-to-hardware)

### [2. SoC Design and OpenLANE](#2-soc-design-and-openlane)
- [Introduction to All Components of Open-Source Digital ASIC Design](#introduction-to-all-components-of-open-source-digital-asic-design)
- [Simplified RTL2GDS Flow](#simplified-rtl2gds-flow)
- [Introduction to OpenLANE and Strive Chipsets](#introduction-to-openlane-and-strive-chipsets)
- [Introduction to OpenLANE Detailed ASIC Design Flow](#introduction-to-openlane-detailed-asic-design-flow)

### [3. Get Familiar with Open-Source EDA Tools](#3-get-familiar-with-open-source-eda-tools)
- [OpenLANE Directory Structure in Detail](#openlane-directory-structure-in-detail)
- [Design Preparation Step](#design-preparation-step)
- [Review Files After Design Prep and Run Synthesis](#review-files-after-design-prep-and-run-synthesis)
- [OpenLANE Project Git Link Description](#openlane-project-git-link-description)
- [Steps to Characterize Synthesis Results](#steps-to-characterize-synthesis-results)


---

## Introduction to QFN-48 Package, Chip, Pads, Core, Die, and IPs
Arduino Board:- This is an arduino microcontroller board. The encircled area shows the chip(microprocessor) which is interfaced with other components of the board. The designing of this chip from abstract level all the way down to the fabrication is done by RTL to GDSll flow.Arduino consists of both a physical programmable circuit board (often referred to as a microcontroller) and a piece of software, or IDE (Integrated Development Environment) that runs on the computer, used to write and upload computer code to the physical board.
<img src="https://github.com/Dayakar631/Nasscom_vsd_soc_design-_program/blob/main/Screenshot 2024-10-05 001356.png?raw=true" alt="something" />

chip components
(1) Pads: Through which we can send the signal inside the chip.
(2) Core: Place where all the logic gates are fixed.
(3) Die: Present at the corner. it is the size of the entire chip.
EX. RISC-V SoC:- It consist of SRAM,SOC,ADC,DAC,SPI these all are called foundary IP's.All devices depends upon foundary where all chips are fabricated using deposition and lithography techniques and so on.
<img src="https://github.com/Dayakar631/Nasscom_vsd_soc_design-_program/blob/main/Screenshot 2024-10-05 231805.png?raw=true" alt="something" />




## Introduction to RISC-V
RISC-V, where five refers to the number of generations of RISC architecture that were developed at the University of California, Berkeley. RISC is an open standard instruction set architecture (ISA) based on established RISC principles. Unlike most other ISA designs, RISC-V is provided under open source licenses that do not require fees to use. A number of companies are offering or have announced RISC-V hardware, open source operating systems with RISC-V support are available, and the instruction set is supported in several popular software toolchains.

The instruction set is designed for a wide range of uses. The base instruction set has a fixed length of 32-bit naturally aligned instructions, and the ISA supports variable length extensions where each instruction can be any number of 16-bit parcels in length. The instruction set specification defines 32-bit and 64-bit address space variants. The specification includes a description of a 128-bit flat address space variant, as an extrapolation of 32 and 64 bit variants, but the 128-bit ISA remains "not frozen" intentionally, because there is yet so little practical experience with such large memory systems. Chip is connected to the package with the help of bond wires.
<img src="https://github.com/Dayakar631/Nasscom_vsd_soc_design-_program/blob/main/Screenshot 2024-10-05 232556.png?raw=true" alt="something"/>

## From Software Applications to Hardware
Here we will se how apps runs on the system?
Application Software - System Software - Hardware chip
Apps enters into a block of system software and system sodtware converts the entire program into binary language. There are some layers inside the system software whish are as follows
Operating System, Compiler, Assembler
Operating system handles input/output operations and allocate memory also it manage the low level system functions.
Compiler takes the output from the operating system as C,C++,Java and convert them into intsructions. These instructions depends upon hardware.
Assembler take the instructions from compiler and convert them into respective binary numbers. This binary language now send to hardware and hardware performs ouput based on the function it recieve and gives the output.
Instruction acts as abstract interface between C-language and the hardware.
<img src="https://github.com/Dayakar631/Nasscom_vsd_soc_design-_program/blob/main/Screenshot 2024-10-05 235257.png?raw=true" alt="something" />

## Introduction to All Components of Open-Source Digital ASIC Design
To design Digital ASIC, few tools or things which are required from the day one. These are

RTL Design EDA tools PDK data what is RTL design? In digital circuit design, register-transfer level (RTL) is a design abstraction which models a synchronous digital circuit in terms of the flow of digital signals (data) between hardware registers, and the logical operations performed on those signals.for this designs many open sorces are available. like, librecores.org, opencores.org, github.com, etc...

What is EDA tools? The term Electronic Design Automation (EDA) refers to the tools that are used to design and verify integrated circuits (ICs), printed circuit boards (PCBs), and electronic systems, in general. many open sorces tools are available like Qflow, OpenROAD, OpenLANE, etc...

What is PDK Data? PDK is process design kit. It is interface between FAB and design. This data is collections of files like,

process design rules: DRC, LVS, REX Digital standerd cell libreries i/o librerirs etc..... which are used to model a fabrication process for the EDA tools used to design an ICs. for example, in 2020, google release the open source PDK for FOSS 130nm production with the skywater technology. But right now it is at cutting age of the 5 nm also. But in many applications, the advance node is not required, and the cost of advanced node is also high as compared to 130nm processors. This 130nm processors are also fast processor. for example,

intel: P4EE @3.46 GHz(Q4'o4)

sky130_OSU (single cycle RV32i CPU) pipeline version can achieve more than 1 GHz clock.
<img src="https://github.com/Dayakar631/Nasscom_vsd_soc_design-_program/blob/main/Screenshot 2024-10-06 001010.png?raw=true" alt="something" />
Step 1. Synthesis:- In the synthesis, the design RTL is translated to a circuit out from the SCL. The resultant circuit is describes in HDL and usualy refered to the gate level netlist. the gate level netlist is functionaly equivelent to the RTL. "standard Cells" have regular layouts like Electrical. HDL,SPICE

Step 2. Floor/Power Planning:-The main objective here is that to plan silicon area and distribute the power to the whole circuit. In the chip floor planning, the partition chip die between different system building blocks and place the i/o pads. In micro floor planning, we define the dimensions, pin locations, rows. In power planning, the power network is connstructed. tipically, the chip is power by multiple VDD and GND. so, total components are connected to power supply horizontaly and vertically by metal streps. here parallel structures are used to reduce the resistance. To address the electromagnetization problem, power distribution network uses upper metal leyers, which are thicker than lower metal layers. Hence have less resistance.

## Simplified RTL2GDS Flow
(Provide content here...)

## Introduction to OpenLANE and Strive Chipsets
(Provide content here...)

## Introduction to OpenLANE Detailed ASIC Design Flow
(Provide content here...)

## OpenLANE Directory Structure in Detail
(Provide content here...)

## Design Preparation Step
(Provide content here...)

## Review Files After Design Prep and Run Synthesis
(Provide content here...)

## OpenLANE Project Git Link Description
(Provide content here...)

## Steps to Characterize Synthesis Results
(Provide content here...)




