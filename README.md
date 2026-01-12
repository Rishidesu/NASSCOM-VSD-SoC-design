## Day-1:Inception of Open-Source EDA,OpenLANE and Sky130 PDK
### QFN-48 Package and VSD Squadron Board Overview
---
The QFN-48 package consists of peripheral pads for I/O and power, an exposed pad for grounding and thermal dissipation, and an internal silicon die containing the processor core and integrated IP blocks. On the VSD Squadron Board, the highlighted region contains this microprocessor. The design of this processor follows the RTL-to-GDS flow, translating a high-level hardware description into a manufacturable physical layout.
<img width="1549" height="867" alt="image" src="https://github.com/user-attachments/assets/d50de763-d8d1-4803-8596-e8ef570cadc6" />
<img width="1000" height="813" alt="image" src="https://github.com/user-attachments/assets/e312f25f-c880-49b8-89dd-82d63b9c64ff" />
<img width="1229" height="847" alt="image" src="https://github.com/user-attachments/assets/d4a763cb-f760-41b5-998c-9d282679539f" />

Some Key Terms are:
#### Package
The package is the physical enclosure of the semiconductor device. It protects the silicon die from mechanical and environmental damage while providing electrical and thermal interfaces to the printed circuit board. An example is the QFN-48 (Quad Flat No-Leads) package, which offers 48 external pads for compact, low-profile integration.

#### Chip (Die)
The chip, or silicon die, is mounted inside the package and electrically connected to the package pads through wire bonding or flip-chip techniques. It contains the active circuitry, including I/O pads, the core logic region, and on-chip interconnects.

#### Core
The core is the functional region of the chip where computation happens, integrating digital logic and custom IP blocks like SRAM and PLLs.


#### Analog / Custom IP Blocks
- Foundry-provided, full-custom designed and pre-verified IPs  
- Handle analog signals, clock generation, or dense on-chip memory  
- Examples: ADC, DAC, PLL, SRAM  

---

#### Digital Blocks
- Implement digital logic and control functionality  
- Built using RTL → synthesis → place-and-route flow  
- Examples: RISC-V SoC, SPI controller

## Introduction to RISC-V
#### RISC-V ISA(Instruction Set Architecture):
RISC-V ISA (Instruction Set Architecture) is an open, modular specification that defines how software communicates with processor hardware. It specifies instructions, registers, memory addressing, and privilege levels, but not the internal implementation. RISC-V follows Reduced Instruction Set Computing principles, keeping instructions simple and efficient. Its modular design allows a small base ISA to be extended with optional features such as multiplication, floating point, vector processing, and custom accelerators. Because it is royalty-free and extensible, RISC-V is widely used in research, embedded systems, and modern SoC designs where flexibility, transparency, and long-term control matter more than vendor lock-in.

<img width="1728" height="1015" alt="image" src="https://github.com/user-attachments/assets/4f33bbc8-4024-4514-8bbe-5a73daaba146" />

## From Software Applications to Hardware
## How Application Software Communicates with Hardware

In real-world systems, users interact with application software rather than directly with hardware. The interaction is handled by system software, which translates high-level requests into instructions that the hardware can execute.

### System Software Layers

**Operating System (OS)**
- Manages hardware resources such as CPU, memory, storage, and I/O devices  
- Provides system calls and APIs for application programs  
- Controls program execution and hardware access  

**Compiler**
- Translates high-level source code (C, C++, Java, etc.) into machine-specific executables  
- Produces architecture-dependent binaries (e.g., ELF, `.exe`)  

**Assembler**
- Converts assembly instructions into binary machine code  
- Generates the final instruction stream executed by the hardware  

### SoC Design using OpenLANE

<img width="952" height="928" alt="image" src="https://github.com/user-attachments/assets/d62cf938-f002-479e-93ca-eedc94825af1" />

## Open-Source Components Required for Digital ASIC Design

### 1. RTL Designs
- Describe the digital behavior of the circuit  
- Written in hardware description languages such as Verilog or VHDL  
- Define how data is stored, transferred, and processed  
- Available from open-source platforms like GitHub, LibreCores, and OpenCores  

---

### 2. Process Design Kit (PDK)
- Represents the semiconductor manufacturing process  
- Connects circuit design with fabrication constraints  
- Provides rules, models, and libraries required for ASIC design  

**PDK typically includes:**
- Design rules for layout correctness (DRC, LVS, PEX)  
- Device models for accurate electrical simulation  
- Standard cell libraries for building digital logic  
- I/O libraries for chip-to-board signal connections  

**Example:**
- SkyWater 130nm Open-Source PDK  
- Enables open-source ASIC design and fabrication  

---

### 3. EDA Tools
- Software tools used to design and verify ASICs  
- Automate synthesis, placement, routing, and verification  
- Enable conversion from RTL code to physical chip layout  

**Common open-source tools include:**
- OpenROAD – automated physical design  
- OpenLANE – complete RTL-to-GDS flow  
- QFlow – open-source synthesis and layout suite  

### Simplified RTL2GDS flow
---
![215446489-bdfd9f74-92c4-40db-bb70-744d06a18289](https://github.com/user-attachments/assets/7286411c-d692-4dfd-85fb-3f5053173ca7)
#### RTL-to-GDS Physical Design Stages

1. **Synthesis**  
   Converts RTL code into a gate-level netlist using standard cell libraries.

2. **Floorplanning & Power Planning**  
   Defines chip core area, block placement, and creates power/ground distribution networks.

3. **Placement**  
   Places standard cells inside the core while optimizing for timing and congestion.

4. **Clock Tree Synthesis (CTS)**  
   Builds a balanced clock network to minimize skew and meet timing constraints.

5. **Routing**  
   Connects all cells using metal layers based on the placed design.

6. **Sign-off**  
   Performs final checks such as DRC, LVS, and timing analysis before GDS generation.

### Introduction to OpenLANE and Srive SoC family chipsets
---
<img width="1095" height="827" alt="image" src="https://github.com/user-attachments/assets/740cb4a0-84df-4cd8-ae80-1c1cd76a70e5" />

### OpenLANE ASIC Flow
<img width="1175" height="767" alt="image" src="https://github.com/user-attachments/assets/771465f3-c089-4cfc-be1b-fda38e455318" />

### OpenLane ASIC Flow Overview

- Provides a complete open-source RTL-to-GDS flow for digital ASIC design  
- Automates synthesis, floorplanning, placement, CTS, routing, and sign-off  
- Integrates multiple open-source tools into a single, reproducible flow  
- Commonly used with the SkyWater 130nm PDK for open-source chip fabrication

### Dealing with Antenna Rules Violation 
---
There are two solutions
<img width="846" height="550" alt="image" src="https://github.com/user-attachments/assets/6f1e851d-6adb-47e2-94e9-ff2343de7248" />

## Practical Implementation of What's Being taught(Labs)
## Basic Linux Terminal Commands

- **pwd** – Displays the present working directory and its full path  
- **cd** – Changes the current working directory  
- **ls** – Lists files and sub-directories in the current directory  
- **mkdir** – Creates a new directory  
- **rmdir** – Deletes an empty directory  
- **rm** – Removes files or directories  
- **help** – Shows usage information for commands  
- **clear** – Clears the terminal screen  

#### Steps to run Commands:
 Step 1: Go to this directory to give commands afterwards
```bash
cd work/tools/openlane_working_dir/openlane/
```
Step 2: Start the Docker Container
Run Docker command 
```
docker
```
Step 3:change openlane mode to Interactive
```
./flow.tcl -interactive
package require openlane 0.9
```
- After this command some animation will show openlane and openlane will enter interactice mode.
- Files are available in this  `openlane_working_dir/openlane/designs/picorv32a` Location.
- 
Step 4: Prepare the Design
```
prep -design picorv32a 
```
-After this command the configuration files will be merged.

Step 5: Run RTL Synthesis

-Converts the RTL code into a gate-level netlist.
```
run_synthesis
```
-after running it now check reports in this location 
```
/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-10_05-01/reports/synthesis
```
In the Reports you can find
- Total cell count
 - Number of flip-flops
 - Logic breakdown
 - Timing results
### Flop Ratio Calculation
Flop Ratio Formula:
```mathematica
Flop Ratio = (Number of D Flip-Flops) / (Total Number of Cells)


Flop Ratio = 1613 / 14876 = 0.108 ≈ 10.84 %
```
![Uploading image.png…]()






          









