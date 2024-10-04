# DIGITAL VLSI SOC DESIGN AND PLANNING

## Topics Covered

1. [**Day 1 - Inception of Open-Source EDA, OpenLANE, and Sky130 PDK**](#day-1---inception-of-open-source-eda-openlane-and-sky130-pdk)
2. [***How to Talk to Computers***](#how-to-talk-to-computers)
3. [***SoC Design and OpenLANE***](#soc-design-and-openlane)
4. [***Getting Familiar with Open-Source EDA Tools***](#getting-familiar-with-open-source-eda-tools)

---

### Day 1 - Inception of Open-Source EDA, OpenLANE, and Sky130 PDK
- Overview of open-source Electronic Design Automation (EDA) tools.
- Introduction to OpenLANE, a toolchain for digital design.
- Sky130 PDK and its integration with open-source tools.

---

### How to Talk to Computers

#### Introduction to QFN-48 Package, Chip, Pads, Core, Die, and IPs
- **QFN-48 Package**: Overview of this chip packaging technology.
- **Chip**: Internal structure and components.
- **Pads**: Electrical connection points.
- **Core and Die**: What they are and their significance in chip design.
- **IPs**: Intellectual properties and their role in SoC design.

#### Introduction to RISC-V
- **RISC-V Architecture**: A brief introduction to this open-source instruction set architecture.
- **Advantages**: Why RISC-V is gaining popularity.
- **Usage**: How RISC-V is utilized in modern hardware design.

#### From Software Applications to Hardware
- **Conversion Process**: How software applications are translated into hardware components.
- **Steps Involved**: Compilation, logic synthesis, and implementation in hardware.
- **Challenges**: Common issues during software-to-hardware transitions.

---

### SoC Design and OpenLANE

#### Introduction to All Components of Open-Source Digital ASIC Design
- **Digital ASIC Design Flow**: From specification to GDSII.
- **Open-Source Tools**: Available tools for each step of the flow.
- **Challenges and Advantages**: Considerations in using open-source tools.

#### Simplified RTL2GDS Flow
- **RTL**: Register Transfer Level, the starting point for design.
- **GDS**: The final layout used for chip fabrication.
- **Flow Steps**:
  - Synthesis
  - Place and Route (P&R)
  - Verification

#### Introduction to OpenLANE and Strive Chipsets
- **OpenLANE**: Overview of the toolchain.
- **Strive Chipsets**: Use cases and significance.
- **Real-World Applications**: Examples of projects using these technologies.

#### Introduction to OpenLANE Detailed ASIC Design Flow
- **OpenLANE Flow**: A detailed guide through each step.
- **Phases**:
  - Synthesis
  - Floorplanning
  - Placement
  - Routing
  - Timing Analysis
  - DRC (Design Rule Check)

---

### Getting Familiar with Open-Source EDA Tools

#### Detailed Overview of the OpenLANE Directory Structure
- **Key Directories**:
  - `designs/`: Contains your design files.
  - `scripts/`: Scripts used for automation.
  - `pdks/`: Process Design Kits.
  - `logs/`: Logs generated during the design flow.
- **File Organization**: How files are managed throughout the OpenLANE flow.

#### Design Preparation Step
- **Initial Setup**: Steps to prepare a design for synthesis.
- **Preparing RTL Files**: What files are needed and their structure.
- **Tool Configuration**: Setting up tools and configurations for successful synthesis.

#### Reviewing Files After Design Prep and Running Synthesis
- **Files to Review**:
  - Netlists
  - Timing Reports
  - Power Reports
- **Synthesis Results**: Key metrics to focus on after synthesis.
- **Verification**: How to verify that the design meets specifications.

#### OpenLANE Project Git Link Description
- **OpenLANE Repository**: Overview of the OpenLANE GitHub repository.
- **Cloning the Repository**: How to clone and set up the OpenLANE project.
- **Exploring the Project**: A brief guide to understanding the files and structure of the OpenLANE GitHub project.

#### Steps to Characterize Synthesis Results
- **Timing Analysis**: How to interpret timing reports.
- **Power Analysis**: Understanding power consumption in the design.
- **Area Analysis**: Measuring the chip area and optimizing layout.
- **Verification**: Ensuring that the synthesized design matches the original RTL.




