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
# 2 - Understand importance of good floorplan vs bad floorplan and introduction to library cells

## 1. Define Width and Height of Core and Die

The **core and die** dimensions are determined based on the **netlist**, which defines the connectivity between all components in the circuit.

   <img width="1363" height="971" alt="image" src="https://github.com/user-attachments/assets/ffd1f5ba-2b2a-4bb9-8289-b763d4d4818a" />

For example: 

<img width="566" height="192" alt="image" src="https://github.com/user-attachments/assets/da1dcd5a-1934-42f6-83ef-9dee4d0fbd7b" />

- The **dimensions** depend on the number of **logic gates** and **flip-flops**, each having a specific length and width.  


  <img width="1393" height="893" alt="image" src="https://github.com/user-attachments/assets/e363305d-b7b3-4382-9948-57331c64c854" />

- Example:  
  If the minimum area is **2 × 2 = 4 units**, then the chip occupies **4 units** with **100% area utilization**.
  
<img width="1285" height="578" alt="image" src="https://github.com/user-attachments/assets/af6244bc-eda7-46ad-91d2-6d55ef9b04f1" />

### Utilization Factor

> **Utilization Factor** = (Area Occupied by Netlist) / (Total Area of the Core)

for example
 Utilization = (4 × 1) / (2 × 2)
 Utilization = 1 → No space left

> In practice, designs typically target **0.6 to 0.7 utilization**  
to allow space for routing and optimization.

### Aspect Ratio

> **Aspect Ratio (AR)** = Height / Width

| Aspect Ratio | Shape Description |
|---------------|------------------|
| AR = 1 | Square Shape |
| AR > 1 | Horizontal Rectangular Shape |
| AR < 1 | Vertical Rectangular Shape |


For example:

<img width="1732" height="986" alt="image" src="https://github.com/user-attachments/assets/f0c59db6-a142-4af4-b8c5-c28a0e348f6c" />

```mathematica
  Utilization Factor = (Area Occupied by Netlist) / (Total Area of the Core)
                     = (2 x 2) / (4 x 4)
                     = 4 / 16
                     = 0.25
- 75% is left for place the aditional cells, routing

  Aspect Ratio (AR) = Height / Width
                    = 4 / 4
                    = 1 (Square Shape)
```

## 2. Define Locations of Pre-Placed Cells

Pre-placed cells are **fixed physical blocks** (IPs or hard macros) whose positions are defined **before standard-cell placement** in the ASIC flow.

These blocks are not negotiable. Once fixed, the rest of the design must work around them.

### Characteristics of Pre-Placed Cells

- Assigned **fixed coordinates** during the floorplanning stage
- Typically consist of **hard macros or reusable IP cores**
- May include **dedicated or extended I/O pins** for connectivity
- Strongly influence **routing congestion, timing closure, and power distribution**
<img width="1602" height="997" alt="image" src="https://github.com/user-attachments/assets/bca3efdc-1295-4711-8c42-e7efc3362e9e" />
<img width="583" height="191" alt="image" src="https://github.com/user-attachments/assets/182b90bd-ecff-4248-b0d0-a89c0699576e" />

### Pre-Placement in the ASIC Flow

- Macro and IP locations are defined **manually or via constraints**
- In OpenLane, this step occurs **before global placement**
- Once placed, these blocks act as **placement blockages**
- Automated tools place and route **remaining standard cells** around them
  
## 3. Surround Pre-Placed Cells with Decoupling Capacitors

Pre-placed cells must be surrounded with **decoupling capacitors (decaps)** to maintain power integrity during switching activity.

This is not optional. Ignoring decaps is how designs fail silently.
<img width="1499" height="963" alt="image" src="https://github.com/user-attachments/assets/67058ea8-7de7-4f87-a38b-f9dea17efd5e" />

### Placement of Pre-Placed Cells

- The location of pre-placed cells depends on **functional requirements and design constraints**
- Placement is chosen to optimize **connectivity, timing, and power distribution**
- Poor placement directly increases **IR drop and supply noise**
<img width="1415" height="861" alt="image" src="https://github.com/user-attachments/assets/93daad1d-a725-4faa-97b4-936d1835ba26" />

### Decoupling Capacitors (Decaps)

Decoupling capacitors are **special capacitive cells** placed near pre-placed cells to stabilize the local power supply.

They compensate for power fluctuations caused by switching activity.

### Why Decaps Are Required

- On-chip interconnects exhibit **resistance (R), inductance (L), and capacitance (C)**
- During logic transitions (`0 → 1` or `1 → 0`), sudden current demand causes **voltage droop**
- Without decaps, this droop leads to **timing failures and functional errors**

### Working Principle

- Decaps act as **local charge reservoirs**
- During switching, they **supply immediate current** to nearby logic
- After switching, they **recharge from the main power grid**
- This process:
  - Reduces **IR drop**
  - Suppresses **power noise**
  - Minimizes **crosstalk**
  - Improves overall **power integrity**
<img width="1290" height="970" alt="image" src="https://github.com/user-attachments/assets/f7bf7a18-f8e3-49e8-a627-3bf82a8d3670" />

## 4. Power Planning

### Purpose of Power Planning

**Power Planning** ensures that every part of the chip receives a stable and sufficient power supply (VDD and VSS).  
It involves designing a power distribution network that connects all major blocks (macros) and standard cells efficiently.

### Example Scenario

Consider a design with **4 macros**.  

<img width="967" height="807" alt="image" src="https://github.com/user-attachments/assets/9f6db2ac-427a-444b-a0d8-021a192a599f" />

Each macro must:
- Receive consistent power from **VDD** (power) and **VSS** (ground).  
- Maintain equal signal strength between the **driver** and the **load** across the chip.

<img width="1308" height="995" alt="image" src="https://github.com/user-attachments/assets/86153d94-4251-4610-9941-a942a4f25a2f" />

### Power Integrity Issues

Assume a **16-bit bus** connected to an inverter:

<img width="1448" height="880" alt="image" src="https://github.com/user-attachments/assets/d595416f-53c1-4e1f-b9e1-20e3536ceba6" />

- When logic `1` (VDD) becomes logic `0`, and vice versa,  
  the switching current passes through a **single VDD tap point**.
- This creates a momentary voltage imbalance, leading to:
  1. **Ground Bounce** – Increase in ground voltage at the VSS node.

<img width="1474" height="886" alt="image" src="https://github.com/user-attachments/assets/7b567e75-ef9a-484a-945f-7e50d5c116ed" />

 2. **Voltage Droop** – Drop in supply voltage at the VDD node.
    
<img width="1435" height="333" alt="image" src="https://github.com/user-attachments/assets/e4fed4b1-dd9d-4a19-98e7-b7f319fbb2df" />

These effects can cause **timing violations**, **logic instability**, and **signal noise**.


### Solution: Multiple Power Supply Connections

To minimize these effects:
- Use **multiple power and ground connections** distributed across the chip.  
- This reduces the current drawn from any single point, minimizing **voltage droop** and **ground bounce**.  
- Ensures a **uniform power distribution network (PDN)** throughout the design.

<img width="1899" height="986" alt="image" src="https://github.com/user-attachments/assets/b90616a9-f9ed-4e64-a97b-b8b90b7a0f3a" />
 
> Connecting all macros to multiple **VDD** and **VSS** taps improves power integrity, reduces noise, and ensures reliable chip operation during switching events.

## 5. Pin Placement

**pin placement**, where **input** and **output** ports are positioned around the chip core.  
Proper pin placement ensures efficient routing and balanced signal flow across the design.

###  Key Points

- **Input/Output Ports:**  
  Define where signals enter (inputs) and exit (outputs) the chip.

- **Ordering of Ports:**  
  The placement order depends on the **connectivity** between cells to minimize wire length and congestion.

- **Clock Pins:**  
  Clock ports are designed to be **larger in size** to reduce **resistance** and ensure low **clock skew** across the circuit.

<img width="1808" height="972" alt="image" src="https://github.com/user-attachments/assets/7f1be7ba-8568-4472-a456-94671faac67e" />

> **Good pin placement** improves timing, reduces routing complexity, and helps achieve better power and signal integrity.

## 6. Logical Cell Placement Blockage

### What Is a Placement Blockage?

A **placement blockage** is a **reserved area** on the chip where **no standard cells** can be placed.  
These regions are intentionally left empty to ensure proper spacing, routing, and signal isolation.

### Purpose of Placement Blockages

- Prevents cells from being placed **too close** to critical regions (e.g., pre-placed macros, power grids, or clock trees).  
- Ensures sufficient **routing space** and avoids **congestion**.  
- Used around **memory blocks, I/O pads**, and **analog IPs** where dense logic placement is undesirable.

<img width="1322" height="913" alt="image" src="https://github.com/user-attachments/assets/2108d874-2b5a-4393-8a8f-c13ebac6c6a2" />

### Types of Blockages

- **Hard Blockage:** No cells or routing allowed.  
- **Soft Blockage:** Placement restricted, but routing may pass through.

> Logical cell placement blockages help maintain routing quality and design reliability by controlling where standard cells can be placed.

## Floorplanning in OpenLANE

###  Default Configuration Files

The **default settings** of OpenLANE are stored in:

`/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/configuration`

<img width="1850" height="115" alt="image" src="https://github.com/user-attachments/assets/e5b1cf70-8011-403d-aec5-4b54593679a7" />


These files define the base parameters used during the flow unless overridden by user-specific configurations.

### User-Defined Configuration (`config.tcl`)

Each design has its own configuration file that defines project-specific parameters.  
For the **picorv32a** design, the configuration file is located at:


The user define config.tcl File
`/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a`

Below is an example of a typical **`config.tcl`** setup:

```tcl
# Design
set ::env(DESIGN_NAME) "picorv32a"

set ::env(VERILOG_FILES) "./designs/picorv32a/src/picorv32a.v"
set ::env(SDC_FILE) "./designs/picorv32a/src/picorv32a.sdc"

# Clock Configuration
set ::env(CLOCK_PERIOD) "10.000"
set ::env(CLOCK_PORT) "clk"
set ::env(CLOCK_NET) $::env(CLOCK_PORT)

# Floorplan Settings
set ::env(FP_CORE_UTIL) 65
set ::env(FP_IO_VMETAL) 4
set ::env(FP_IO_HMETAL) 3


set filename $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/$::env(PDK)_$::env(STD_CELL_LIBRARY)_config.tcl
if { [file exists $filename] == 1} {
	source $filename
}

```
To start the floorplanning process in OpenLANE, run the following command in interactive mode:
```
run_floorplan
```
<img width="1920" height="1080" alt="w6-fp1" src="https://github.com/user-attachments/assets/38773d6a-8ce7-454a-93a0-54688e74b023" />
<img width="1920" height="1080" alt="w6-fp2" src="https://github.com/user-attachments/assets/7aa5aead-2f1b-4a55-bf18-e8b3715ac52e" />


The generated DEF (Design Exchange Format) file can be found in:
```
/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-10_09-36/results/floorplan
```

<img width="1920" height="923" alt="w-6-fp3" src="https://github.com/user-attachments/assets/f97f94bd-14af-4899-b149-f61e50ec1bbb" />


Required Files for Viewing in Magic
To visualize the floorplan using the Magic layout tool, you’ll need the following three files:
- Magic Tech File: sky130A.tech
- LEF File: merged.lef
- DEF File: picorv32a.floorplan.def

Command to Open in Magic

Run the following command in your terminal to load the floorplan:
```bash
magic -T <location_of_techfile> \
      lef read <location_of_lef_file> \
      def read <location_of_floorplan_def_file>

cd /work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-10_09-36/results/floorplan

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef  def read picorv32a.floorplan.def &
```
Once the floorplan is loaded in **Magic**, you can interact with and inspect different parts of the design using the following controls:

<img width="1920" height="923" alt="mlayout" src="https://github.com/user-attachments/assets/525a2693-ed16-4f8d-87ba-923f43946a97" />


### Basic Controls

| Action | Key / Command | Description |
|:------|:--------------|:------------|
| **Fit Design to Screen** | `s` then `f` | Fits the full layout in the Magic window. |
| **Select a Region** | Left + Right Click | Drag to select a specific area. |
| **Zoom In** | `z` | Zooms into the current view. |
| **Identify Selection** | `s`, then `what` | Select an object and run `what` in the Tcl console. |

- Mouse scroll wheel can be used for smooth zooming.
- Ensure the design is fully loaded before interaction.
- `what` shows cell name, layer, and coordinates.










