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

## Simplified RTL2GDS Flow
Step 1. Synthesis:- In the synthesis, the design RTL is translated to a circuit out from the SCL. The resultant circuit is describes in HDL and usualy refered to the gate level netlist. the gate level netlist is functionaly equivelent to the RTL. "standard Cells" have regular layouts like Electrical. HDL,SPICE

Step 2. Floor/Power Planning:-The main objective here is that to plan silicon area and distribute the power to the whole circuit. In the chip floor planning, the partition chip die between different system building blocks and place the i/o pads. In micro floor planning, we define the dimensions, pin locations, rows. In power planning, the power network is connstructed. tipically, the chip is power by multiple VDD and GND. so, total components are connected to power supply horizontaly and vertically by metal streps. here parallel structures are used to reduce the resistance. To address the electromagnetization problem, power distribution network uses upper metal leyers, which are thicker than lower metal layers. Hence have less resistance.
<img src="https://github.com/Dayakar631/Nasscom_vsd_soc_design-_program/blob/main/Screenshot 2024-10-06 001914.png?raw=true" alt="something"/>
Step 3. Placement:- In this process, we place the gate level netlist on the floor planning rows, alligned with the sites. cells should be placed very closed to eachother to reduce the interconnnect delay. Usually placement is done in 2 steps:

Global placement:- It is very first stage of the placement where cells are placed inside the core area for the first time looking at the timing and congestion. Global Placement aims at generating a rough placement solution that may violate some placement constraints while maintaining a global view of the whole Netlist.

Detailed placement:- In detailed placements, we determined the exact route and layers for each netlist. the objective of detailed placement is valid routing, minimize area and meet timing constrains. Additional objective is minimum via and less power.
Step 4. Clock Tree Synthesis:- Before routing the signals, we have to route the clock. In the process of clock synthesis, we have distribute the clock to the every sequential elements. for example flipflops, registers, ADC, DAC ete. basically clock netwroks looks likes a tree. where the clock source is roots and the clock elements are end leaves. Synthesization should be done in a manner that with minimum skew and in a good shape.To minimize the clock skew by using the low-skew global routing resources for clock signals.Microsemi devices provide various types of global routing resources that significantly reduce skew.Usually a tree is a H tree, X tree etc.

Step 5. Routing:- After routing the clock, the signal routing comes. Making physical connections between signal pins using metal layers are called Routing. Routing is the stage after CTS and optimization where exact paths for the interconnection of standard cells and macros and I/O pins are determined. There are two types of nets in VLSI systems that need special attention in routing:

Clock nets Power/Ground nets The sky130 PDK defines the 6 routing leyers. the lowest leyer is called local interconnect layer (titanium nitride layer). Other five layers are alluminium layersIn the proccess of routing, metal trackes forms a routing grids and these grids are huge. so, devide and conquer approach is use for routing. The two types of routing is used:
Step 6. Sign Off:- Once the routing is done, we can construct the final layout. This final layout will goes under the verification. Two types of verifications are there:

Physical verification: Here design rule checking will done and it will check the final layout and owners layout Timing Verification: Here Static Timing Analysis will done.

Global routing: Generates the routing guides

Detailed Routing: Uses the routing guides to implement the actual wiring.
<img src="https://github.com/Dayakar631/Nasscom_vsd_soc_design-_program/blob/main/Screenshot 2024-10-06 001010.png?raw=true" alt="something" />

## Introduction to OpenLANE and Strive Chipsets
OPENLANE is an automated RTL to GDSII flow that is composed of several tools such as OpenROAD, Yosys, Magic, Netgen, Fault, CVC SPEF-Extractor, CU-GR, Klayout and a number of scripts used for design exploration and optimization. It is started as an Open-source flow for a true Open Source tape-out Experiment. striVe is a family of open everything SoCs: Open PDK, Open EDA, Open RTL

striVe SoC Family
<img src="https://github.com/Dayakar631/Nasscom_vsd_soc_design-_program/blob/main/Screenshot 2024-10-06 130439.png?raw=true" alt="something" />
The main goal of OPENLANE is to produce a clean GDSII with no human intervation (no-human-in-the-loop). here the meaning of clean is that:

No LVS violations

No DRC Violations

No timing Violations

OPENLANE is tuned for skyWter130nm open PDK. it can be used to harden Macros and chips.there is two mode of operation Autonomus : it is the push botton flow. with the push botton , it is a some time base design and due to this push botton, we get final GDSII

interactive : here we can run comamds and steps one by one.

It has large number of design examples(43 designs with their best configurations).

## Introduction to OpenLANE Detailed ASIC Design Flow
<img src="https://github.com/Dayakar631/Nasscom_vsd_soc_design-_program/blob/main/Screenshot 2024-10-06 131055.png?raw=true" alt="something" />
The design exploration utility is also used for regression testing(CI). we run OpenLANE on ~ 70 designs and compare the results to the best known ones.

DFT(Design for Test) it perform scan inserption, automatic test pattern generation, Test patterns compaction, Fault coverage, Fault simulation.After that physical implementation is done by OpenROAD app. physical implementation involves the several steps:

Floor/Power Planning

End Decoupling Capacitors and Tap cells insertion

Placements: Global and Detailed

Post Placement Optimization

Clock Tree synthesis (CTS)

Routing: Global and Detailed

Every time the netlist is modified.(CTS modifies the netlist and Post Placements optimization also modifies the netlist).so for that verification must be performed. The LCE(yosys) is used to formally confirm that the function did not change after modifying the netlist. ### Dealing with antenna rules Violation: when a metal wire segment is fabricated, it can act as antenna.as an antenna, it collect charges which can demaged the transister gates during the fabrication.
To address this issue, we have to limit the lenght of the wire. usually this is the job of the router. If router fails to do this, then there are two solutions: Bridging attaches a higher layer intermediary.Add antenna diode cell to leak away charges.(Antenna diodes are provided by the SCL)
With OpenLANE, we took a preventive approach. here we add fake antenna diode next to every cell input after placement. Then run the Antenna checker on the routed layout. If the checker reports a violation on cell input pin, replace the fake diode cell by a real one.
Static Timing analysis(STA) It involves the interconnect RC Extraction(DEF2SPEF) from the routed layout, followed by STA on OpenSTA(OpenROAD) tool. resulting report will shows the timing violations if any violations is there.

Physical Verification (DRC and LVS) Magic is used for design Rules checking and SPICE Extraction from Layout. Magic and Netgen are used for LVS.
## OpenLANE Directory Structure in Detail
Basic Linux Commands

cd : opens the particular folder

ls : lists the content of the folder

pwd : shows the present working directory

mkdir : to make a new directory

command --help : shows the complete use that command

clear : clears the terminal screen

Here we are working in Sky130_fd_sc_hd PDK varient. where, "sky130" is process name or node name."fd" is a foundary name (skyWater foundary)."sc" means standerd cell librery files and the last one "hd" stands for high density(basically one type of varient).

Sky130_fd_sc_hd varient contains many technology files like verilog, spice, techlef, meglef,mag,gds,cdl,lib,lef,etc. (techlef file contains the layer information).

## Design Preparation Step
when we enter in the OpenLANE, we have to use flow.tcl because as a name says, it will goes with the flow using the script. And by using interactive switch, we will do step by step process. without interactive switch, it will run complete flow from RTL to GDSII. Now OpenLANE is open and we can see that prompt will change now.

## Review Files After Design Prep and Run Synthesis
After completing the preparation, in the picorv32a file, the run terictory is created. Inside the folder, Today's date is created. so in this terictory some folders are available which is required for openlane.

In the temp file, merged.lef file is available which was created in preparation time. if we open this merged.lef file, we get all the wire or layer level and cell level information.

## OpenLANE Project Git Link Description
(Provide content here...)

## Steps to Characterize Synthesis Results
(Provide content here...)




