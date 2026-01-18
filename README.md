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

check equidistant pins:
<img width="1920" height="923" alt="mla2" src="https://github.com/user-attachments/assets/a1bee816-ce71-4808-af04-89cc657cd284" />
see the diagonal placement of cells inside:
<img width="1920" height="923" alt="w6 magic diagnol" src="https://github.com/user-attachments/assets/a53013a0-2ff5-4b57-acb2-130cd91f8b19" />
see the standard library:
<img width="1920" height="923" alt="mla3" src="https://github.com/user-attachments/assets/d3ddec25-b482-4101-ab51-8e279e7e9a97" />

## Placement

### 1. Binding Netlist with Physical Cells

After floorplanning, the next step is **placement**, where the logical netlist is **mapped to physical cells** from the standard cell library.

i.Before placement
 <img width="1205" height="1000" alt="Before Placement" src="https://github.com/user-attachments/assets/692157b6-a4c4-4aae-bf01-7c2182940e85" />
 ii.After placement
  <img width="1492" height="987" alt="After Placement" src="https://github.com/user-attachments/assets/14f71495-9c5b-4de9-ba20-fedbaaed4a90" />

In real silicon, logic gates have **physical shapes** with defined width and height.

These gates are stored in a **standard cell library**, which provides:

- **Shape and Size** – Physical dimensions of each cell  
- **Timing** – Propagation delay characteristics  
- **Power** – Power consumption data  
- **Area** – Silicon area occupied  
- **Operating Conditions** – Voltage, temperature, and process limits

<img width="1825" height="456" alt="image" src="https://github.com/user-attachments/assets/6cbffb00-e862-44e7-8f3f-8a32ab4727fb" />


###  2. Cell Placement

During **placement**, the tool takes all physical cells from the library and places them into the **floorplan region** according to connectivity and timing requirements.

<img width="1894" height="744" alt="image" src="https://github.com/user-attachments/assets/47b36a1b-a951-46a7-a669-5d67d6599a7a" />

- The placement step determines **exact locations** of standard cells inside the chip core.  
- **Pre-placed IPs (macros)** are already fixed in the floorplan, so **no standard cells** should be placed near or overlap them.  

  <img width="1898" height="914" alt="image" src="https://github.com/user-attachments/assets/c5ccb39f-4df1-4c48-8bac-c1fa033b9248" />

## 3. Optimize Placement

Placement optimization improves **timing**, reduces **wire length**, and minimizes **congestion** while preserving signal integrity.

- **Wire Length Estimation**  
  The placement tool estimates wire lengths between connected cells.  
  Shorter wires reduce delay and routing complexity.

- **Resistance and Capacitance**  
  Longer wires increase **resistance (R)** and **capacitance (C)**.  
  Higher R and C degrade signal quality and timing.  

  Wire resistance is given by:  
  `R = ρ × (L / A)`

  where:  
  - `ρ` = material resistivity  
  - `L` = wire length  
  - `A` = cross-sectional area  

- **Signal Integrity and Repeaters**  
  Long interconnects weaken signals.  
  **Repeaters (buffers)** are inserted to restore signal strength.  
  Repeaters improve integrity but consume extra silicon area.

- **Slew (Transition Time)**  
  Slew depends on **load capacitance**.  
  Higher capacitance causes slower signal transitions.  
  Slow transitions can violate timing constraints.

### Optimization Goals

Placement optimization ensures:
- **Optimal wire length**
- **Minimal routing congestion**
- **Improved timing performance**
- **Better signal integrity**

### Timing Analysis

After placement optimization:
- **Data paths** are analyzed for timing closure.
- The **clock is treated as ideal** with zero skew.
- **Setup timing** is checked against design specifications.
- Signal arrival times are verified to confirm correct placement.

<img width="1895" height="925" alt="image" src="https://github.com/user-attachments/assets/57bb14e5-f011-4c83-a0a9-8b69aa612f8c" />

> Placement optimization adjusts cell locations to balance **area**, **timing**, and **signal quality**.  
It prepares the design for **clock tree synthesis** and **routing**.

**Library characterization and modeling** are the foundation of the ASIC flow.  
Each standard cell is modeled for **timing**, **power**, and **area**.  
Models are defined across **process, voltage, and temperature (PVT)** conditions.

### Design Flow Stages Using the Same Cells

1. **Logic Synthesis**  
   Converts RTL into a gate-level netlist using standard cells.

2. **Floorplanning**  
   Defines chip area, power grid, and macro placement.

3. **Placement**  
   Positions all standard cells within the floorplan.

4. **Clock Tree Synthesis (CTS)**  
   Distributes the clock evenly to all flip-flops.

5. **Routing**  
   Connects all cells according to logical nets.

6. **Static Timing Analysis (STA)**  
   Checks timing constraints and validates performance.

>  All these stages use the **same standard cells** characterized in the technology library.

# Placement in OpenLANE

### 1. Global Placement

- Performs a **coarse placement** of standard cells.
- Targets **wire length reduction** and better connectivity.
- No **legalization** is performed at this stage.
- OpenLane uses **Half-Perimeter Wire Length (HPWL)** for optimization.

### 2. Detailed Placement

- Refines results from global placement.
- Aligns standard cells within defined **rows**.
- Eliminates **cell overlaps**.
- Produces a legal, manufacturable layout.

> go to the docker in openlane and enter interactive mode and do the design prep and then after synthesis do this

` 
  run_placement
  `

<img width="1920" height="923" alt="w6-pl1" src="https://github.com/user-attachments/assets/f18b9d55-9f00-40c7-b03e-92722f90a67f" />
<img width="1920" height="923" alt="w6-pl2" src="https://github.com/user-attachments/assets/159917b0-6700-4ce5-8f48-a6dc5ba82e65" />

The command to open result after running run_placement is 
```
cd /work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-10_09-36/results/placement
 magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef  def read picorv32a.placement.def &
```

And the result is
<img width="1920" height="923" alt="w6-pl3" src="https://github.com/user-attachments/assets/0584b8d7-bef3-45d4-a5f4-fadd414f0c51" />


- standard cells are overlaped

<img width="1920" height="923" alt="w6-pl4" src="https://github.com/user-attachments/assets/59ccfeeb-5397-4b6b-bb00-6e642c805caf" />

## Standard Cell Design

A **standard cell** is a basic building block in digital IC design.  
The standard cell design flow ensures each cell is verified and ready for synthesis and physical design.

### Standard Cell Design Flow

The flow consists of **three main elements**.

### Inputs

These resources are required to begin standard cell design:

- **PDKs (Process Design Kits)**  
  Provide technology-specific rules and parameters.

- **DRC & LVS Rules**  
  Define layout and verification constraints.

- **SPICE Models**  
  Describe electrical behavior of devices.

- **Library and User Specifications**  
  Define timing, power, and area targets.

### Design Steps

Core steps in standard cell creation:

- **Circuit Design**  
  Create the transistor-level schematic.

- **Layout Design**  
  Draw physical geometry following DRC and LVS rules.

- **Characterization**  
  Measure timing, power, and area across operating conditions.

### Outputs

The standard cell design flow produces:

- **CDL (Circuit Description Language)**  
  Describes the transistor-level circuit.

- **GDSII**  
  Final physical layout for fabrication.

- **LEF (Library Exchange Format)**  
  Abstract physical view for placement and floorplanning.

- **Extracted SPICE Netlist (.crc)**  
  Includes parasitic effects for accurate analysis.

---

## Standard Cell Characterization Flow

**Characterization** models standard cell behavior under different electrical conditions.  
It generates data for **timing**, **power**, and **noise** analysis.

### Standard Characterization Steps

1. **Read Model Files**  
   Load transistor and device models from the PDK.

2. **Read Extracted SPICE Netlist**  
   Import the post-layout netlist with parasitics.

3. **Identify Circuit Behavior**  
   Define logic function and pin roles.

4. **Read Subcircuits**  
   Include all referenced dependent subcircuits.

5. **Attach Power Sources**  
   Connect **VDD** and **VSS** rails.

6. **Apply Stimulus**  
   Apply input transitions for testing.

7. **Add Output Capacitances**  
   Model real interconnect and fan-out loads.

8. **Run Simulations**  
   Measure delay, slew, power, and noise.


<p align="center">
  <img src="https://github.com/user-attachments/assets/ec2e78d9-d9c1-4b3c-91bd-04df204bbe52" alt="GUNA Input Setup" width="48%"/>
  <img src="https://github.com/user-attachments/assets/01165e93-608f-44c1-a7cf-1ef28fd21aa0" alt="GUNA Output Results" width="48%"/>
</p>


After completing all the setup and simulation steps,  
**all the generated files** (model files, extracted SPICE netlist, subcircuits, stimulus, and simulation scripts)  
are provided as **inputs to the GUNA characterization software**.

GUNA uses these inputs to:
- Perform **timing**, **power**, and **noise** characterization.  
- Generate **.lib (timing library)** files used in synthesis and static timing analysis.

<img width="1756" height="668" alt="image" src="https://github.com/user-attachments/assets/312f5dd2-56f1-4549-b527-5609cdf8723c" />

## Timing Characterization 

| Parameter | Description | Typical Value |
|------------|--------------|----------------|
| **Slew low rise threshold** | Voltage level where rising transition starts (low reference) | 20% of swing |
| **Slew high rise threshold** | Voltage level where rising transition ends (high reference) | 80% of swing |
| **Slew low fall threshold** | Voltage level where falling transition ends (low reference) | 20% of swing |
| **Slew high fall threshold** | Voltage level where falling transition starts (high reference) | 80% of swing |
| **Input rise threshold** | Input voltage reference for rise delay | 50% |
| **Input fall threshold** | Input voltage reference for fall delay | 50% |
| **Output rise threshold** | Output voltage reference for rise delay | 50% |
| **Output fall threshold** | Output voltage reference for fall delay | 50% |

> Percentages are relative to the **actual low and high voltages** of each transition.


### 1. Propagation Delay (`tpd`)

Time difference between when the **input** signal crosses its 50% level and when the **output** signal crosses its 50% level.

Propagation delay (rise):
t_pd,rise = t_out,50 - t_in,50

Propagation delay (fall):
t_pd,fall = t_out,50 - t_in,50

### 2. Transition Time / Slew

Duration for a signal to transition between two threshold points.

#### For Rising Edge:

Rise time:
t_rise = t_80 - t_20

Fall time:
t_fall = |t_80 - t_20|

These are also referred to as **input slew** or **output slew**, depending on which pin the waveform corresponds to.

# Day-3 - Design and characterize one library cell using Magic Layout tool and ngspice

## Modifying the Flow & Re-Running Floorplan

If any changes are made to the flow — for example, adjusting the **input and output port spacing** —  
you can update the configuration in the shell and **re-run the floorplan** command to observe the new I/O pin alignment.


```
set ::env(FP_IO_MODE) 2
run_floorplan
```
To see how I/O pins are aligned after changing the value in ioPlacer,this is new mode of placement of io pins. 

<img width="960" alt="reset" src="https://user-images.githubusercontent.com/64173714/215265586-4619331d-3f95-4573-9765-2c9d07226e55.png">

## SPICE Simulations (Pre-Layout)

SPICE simulations help verify the **functional** and **static behavior** of a circuit **before layout**.  
They are an essential step in validating circuit performance at the transistor level.

### SPICE Deck
- Defines the **circuit connectivity**, **component values**, and **node names**.  
- Acts as the input file for SPICE simulation.  
- Includes details such as voltage sources, resistors, capacitors, and transistors.

### NGSPICE 
- **NGSPICE** is an open-source circuit simulator used for **analog** and **mixed-signal** analysis.  
- It interprets the SPICE deck to perform simulations like DC, AC, and transient analysis.

### Static Behavior Evaluation
- Determines the **DC operating points**, **logic voltage levels**, and **steady-state conditions**.  
- Helps confirm the circuit’s correct operation before applying dynamic or transient signals.



## SPICE Simulation Lab for CMOS Inverter

This lab demonstrates how to perform a **SPICE simulation** for a CMOS inverter using the **Sky130 PDK** and **Magic** layout tool.

### Step 1: Clone the Standard Cell Repository

Use the following commands to clone the standard cell design repository and navigate into it:

```bash
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
cd vsdstdcelldesign
```
### Step 2: Prepare the Magic Technology File

Before opening the layout in Magic, you need the technology file `(sky130A.tech)`.

Navigate to the tech file location and copy it into your vsdstdcelldesign directory:
Do this to get vsdstdcelldesign file into your openlane directory
  
```
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech \
/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
```
Step 3: Open the Layout in Magic

Use the following command to open the CMOS inverter layout (sky130_inv.mag) in Magic:

```
magic -T sky130A.tech sky130_inv.mag &
```

<img width="1920" height="923" alt="w6-inv" src="https://github.com/user-attachments/assets/8174055b-50cf-4317-9e69-cfda8fc82c18" />

16 mask CMOS fabrication process  
``` 
https://www.vlsisystemdesign.com/wp-content/uploads/2017/07/16-mask-process.pdf

```
- To view the layout:
  - Press **`s`** for *Select*
  - Press **`z`** for *Zoom*
- In **`tkcon`**, type the `what` command to view the **mask layers**.

<img width="1920" height="923" alt="w6-magic1" src="https://github.com/user-attachments/assets/34fb64f7-90ba-463a-abf2-66bf51f05dd8" />

<img width="1920" height="923" alt="w6-magic2" src="https://github.com/user-attachments/assets/f503983a-f685-4833-a99a-8bf572d1d3c1" />



- We need to **extract the parasitics** and **characterize the design**.  
- Open the **tkcon** window and execute the following commands:

```bash
  extract all
  ext2spice cthresh 0 rthresh 0
  ext2spice
```

<img width="1920" height="923" alt="w6d3" src="https://github.com/user-attachments/assets/1720f68d-6ca4-458c-8eb5-93b5eb265735" />


### Modifying the SPICE File for Transient Response

To plot a **transient response**, we modify the SPICE file as follows:

1. **Change the scale value**  
   - Adjust the `.option scale` parameter according to the grid dimensions.  
   - Example:  
     ```spice
     .option scale=0.01u
     ```

2. **Include the NMOS and PMOS library files**  
   - Add the model library files for transistor definitions:  
     ```spice
     .include ./libs/pshort.lib
     .include ./libs/nshort.lib
     ```

3. **Define the supply voltage**  
   - Provide the power supply sources:  
     ```spice
     VDD VPWR 0 3.3V
     VSS VGND 0 0V
     ```

4. **Add the input signal**  
   - Define a pulse input for simulation:  
     ```spice
     Va A VGND PULSE(0V 3.3V 0 0.1ns 0.1ns 2ns 4ns)
     ```

5. **Include simulation commands**  
   - Add the transient analysis and control commands:  
     ```spice
     .tran 1n 20n
     .control
     run
     .endc
     .end
     ```
6. **Check and update model names**  
   - Open the included NMOS and PMOS library files (e.g., `pshort.lib`, `nshort.lib`)  
   - Verify the model names defined inside these files.  
   - Update the transistor definitions in your SPICE file to match them.  
     Example:  
     ```spice
     M0 Y A VGND VGND nshort_model.0 ...
     M1 Y A VPWR VPWR pshort_model.0 ...
     ```
     If the model names differ (e.g., `sky130_fd_pr__nfet_01v8` or `sky130_fd_pr__pfet_01v8`), change them accordingly.
     


```
* SPICE3 file created from sky130_inv.ext - technology: sky130A

.option scale=0.01u 
.include ./libs/pshort.lib
.include ./libs/nshort.lib

* .subckt sky130_inv A Y VPWR VGND
M0 Y A VGND VGND nshort_model.0 ad=1435 pd=152 as=1365 ps=148 w=35 l=23
M1 Y A VPWR VPWR pshort_model.0 ad=1443 pd=152 as=1517 ps=156 w=37 l=23
C0 A VPWR 0.08fF
C1 Y VPWR 0.08fF
C2 A Y 0.02fF
C3 Y VGND 0.18fF
C4 VPWR VGND 0.74fF
* .ends

* Power supply 
VDD VPWR 0 3.3V 
VSS VGND 0 0V 
* Input Signal
Va A VGND PULSE(0V 3.3V 0 0.1ns 0.1ns 2ns 4ns)

* Simulation Control
.tran 1n 20n
.control
run
.endc
.end
```
After saving the changes, run the simulation using:  
```bash
ngspice sky130A_inv.spice
```
<img width="1920" height="920" alt="w6d33" src="https://github.com/user-attachments/assets/30a0723f-76e5-40ef-840d-6891ceda8836" />

plot the transient response with:
```
plot y vs time a
```

<img width="1920" height="920" alt="w6d34" src="https://github.com/user-attachments/assets/b7ff7116-3c4c-45c6-bc80-4bf07725c945" />



- In the transient response **graph**, we can observe **spikes** due to a **small load capacitance (Cload)**.  
- To reduce these spikes, **increase the load capacitance** value.

Modify the capacitor line in the SPICE file as follows:

```spice
C3 Y VGND 2fF
```
then plot y vs time a again:

<img width="1920" height="920" alt="w6d35" src="https://github.com/user-attachments/assets/f2122b1e-a27b-4766-b31e-b8e3be2150ac" />


> The output spikes are slightly reduced compared to the previous result, leading to a smoother transient response.

## Characterization of Cell Slew Rate and Propagation Delay

### Slew Rate

1. **Rise Transition**
   - Measures output transition from **20% (0.66 V)** to **80% (2.64 V)** of **VDD (3.3 V)**.
   - Calculation:
     ```
     2.19945 ns - 2.15722 ns = 0.03728 ns
     ```
   - **Rise Slew Rate = 0.03728 ns**

2. **Fall Transition**
   - Measures output transition from **80% (2.64 V)** to **20% (0.66 V)** of **VDD**.
   - Calculation:
     ```
     4.06716 ns - 4.03940 ns = 0.02776 ns
     ```
   - **Fall Slew Rate = 0.02776 ns**

### Propagation Delay

3. **Rise Cell Delay**
   - Measured at **50% (1.65 V)** crossing of input and output.
   - Output rises while input falls.
   - Calculation:
     ```
     2.18132 ns - 2.14945 ns = 0.03187 ns
     ```
   - **Rise Propagation Delay = 0.03187 ns**

4. **Fall Cell Delay**
   - Measured at **50% (1.65 V)** crossing of input and output.
   - Output falls while input rises.
   - Calculation:
     ```
     4.059292 ns - 4.04958 ns = 0.009712 ns
     ```
   - **Fall Propagation Delay = 0.009712 ns**

---

## Tools and Technology

### Magic Tool

Magic is an open-source **VLSI layout editor**, **circuit extractor**, and **DRC tool**.  
Documentation and downloads:  
http://opencircuitdesign.com/magic/

### SkyWater 130nm PDK

The **SkyWater 130nm PDK** provides design rules, layers, and device models.  
Official documentation:  
https://skywater-pdk.readthedocs.io/en/main/index.html  

Detailed design rules:  
https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html#m3


#### Lab Steps

To download and extract the DRC test files for Sky130 PDK:

```bash
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
tar -xvzf drc_tests.tgz
```
<img width="1920" height="920" alt="w6d36" src="https://github.com/user-attachments/assets/7c146117-39a2-4b98-9d42-ea938fc88490" />


> These files contain the design rules used for the Sky130 PDK.


To open Magic, use the following command:
```
magic -d XR &
```

1.  When you open the met3.mag layout file, you may observe various DRC (Design Rule Check) violations.

<img width="1920" height="920" alt="w6d37" src="https://github.com/user-attachments/assets/196068ab-3493-480c-9d69-69c18a921bd4" />


### Metal Layer DRC Violations

#### **M3.1 – Metal Width DRC**
- **Violation:** The metal trace width in **M3.1** is below the specified minimum width threshold.  
- **Error:** Metal width does not meet design rules.

#### **M3.2 – Metal Spacing DRC**
- **Violation:** The distance between adjacent metal traces in **M3.2** does not meet the required spacing.  
- **Error:** Metal spacing violation.

#### **M3.5 – Via Overlapping DRC**
- **Violation:** The vias in **M3.5** overlap with each other.  
- **Error:** Via overlapping issue.

#### **M3.6 – Minimum Area DRC**
- **Violation:** The enclosed area within **M3.6** does not meet the specified minimum area requirement.  
- **Error:** Minimum area violation.


<img width="965" height="250" alt="image" src="https://github.com/user-attachments/assets/a22171f3-ed0d-431f-aabf-ee96b046bc41" />

# Day 4 - Pre-layout timing analysis and importance of good clock tree

## LABS

* OpenLANE is a tool for place and route, which places cells in a design. When using this tool, the full information contained in the .mag file, which includes boundry,power and ground, logic, etc., is not necessary. Instead, only the essential information, such as the placement boundary, power and ground rails, and input and output ports, is required. This information is contained in lef files, which protect the IP(intellectual property). 
* The goal is to extract the lef file from the .mag file and use it to replace the standard cells in the design. There are guidelines to follow when creating a standard cell set for use in place and route
   * I/p and O/p port must lies on the intersection of the vertical and horizontal tracks
   * Width oof the std cell should be in the odd ultiples of the track pitch
   * Height should be odd multiples of vertical track pitch
   
  * To run the previous flow follow this command
 ```
   prep -design picorv32a -tag
 
 ```
 
 * open the layout from vsdstdcelldesign directory
 
 ``` 
    magic -T sky130.tech sky130_inv.mag
 
 ```
In the tkon terminal, use the grid command to compare the tracks' information

<img width="960" alt="4 2" src="https://user-images.githubusercontent.com/64173714/215494843-c069b012-c948-4dd9-9164-d43678a4d5cc.png">

The three guidelines are clearly shown in the illustration in this image

<img width="958" alt="4 3" src="https://user-images.githubusercontent.com/64173714/215496521-f3f79ae8-e302-4155-8946-244049d897dd.png">

* The information from the .mag file will be extracted into a LEF file, which will contain essential details for placement and routing, such as cell dimensions, port information, and specific properties. The first step in creating the LEF file is to clearly define the port definitions, including the class and intended use of each port
* Save the mag file and relaunch the magic tool. Then run the command below to create the lef file
```
    lef write
```
<img width="1258" height="638" alt="Screenshot 2025-11-12 105006" src="https://github.com/user-attachments/assets/ab291006-0aea-4cb1-8536-591ed9bb6437" />

#### 4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.

Commands to copy necessary files to 'picorv32a' design 'src' directory

```bash
# Copy lef file
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# Copy lib files
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```

Screenshot of commands run

<img width="1920" height="920" alt="w6d41" src="https://github.com/user-attachments/assets/aec75594-9954-46ee-8e2d-aa69c741e6f9" />


#### 5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.

Commands to be added to config.tcl to include our custom cell in the openlane flow

```tcl
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```

Edited config.tcl to include the added lef and change library to ones we added in src directory


#### 6. Run openlane flow synthesis with newly inserted custom inverter cell.

Commands to invoke the OpenLANE flow include new lef and perform synthesis 
First do it normally without changing anythng you will get:
<img width="1920" height="923" alt="w6d49" src="https://github.com/user-attachments/assets/68924c7f-929c-4f44-ae4a-acb14e13292c" />

Here the wns is very high

Now do these changes:
```bash


Commands to view and change parameters to improve timing and run synthesis

```tcl
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 31-10_13-15 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled
echo $::env(SYNTH_BUFFERING)

# Command to display current value of variable SYNTH_SIZING
echo $::env(SYNTH_SIZING)

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```


Screenshots of commands run
<img width="1920" height="923" alt="w6d48" src="https://github.com/user-attachments/assets/c4f8089a-3317-4ce5-af7e-934e1a16e6c3" />

<img width="1920" height="923" alt="w6d410" src="https://github.com/user-attachments/assets/6c3f4c22-2649-4f17-8f51-0e20a23b282c" />


Comparing to previously noted run values area has increased and worst negative slack has become 0

![Screenshot from 2024-03-24 17-11-08](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/81418082-747e-4702-b5ad-bb3e450eceb3)
![Screenshot from 2024-03-24 17-11-19](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a1bdb538-527c-4edd-877d-d4263e777321)

#### 8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.

Now that our custom inverter is properly accepted in synthesis we can now run floorplan using following command

```tcl
# Now we can run floorplan
run_floorplan
```


If you are facing unexpected un-explainable error while using `run_floorplan` command, we can instead use the following set of commands available based on information from `Desktop/work/tools/openlane_working_dir/openlane/scripts/tcl_commands/floorplan.tcl` and also based on `Floorplan Commands` section in `Desktop/work/tools/openlane_working_dir/openlane/docs/source/OpenLANE_commands.md`

```tcl
# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or
```
This will do the thing

Now that floorplan is done we can do placement using following command

```tcl
# Now we are ready to run placement
run_placement
```


Commands to load placement def in magic in another terminal

```bash
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-10_13-15/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```


Screenshot of custom inverter inserted in placement def with proper abutment

<img width="1920" height="923" alt="w6d411" src="https://github.com/user-attachments/assets/281c8812-f075-4284-bfcf-bcc05a3b0b02" />


Command for tkcon window to view internal layers of cells

```tcl
# Command to view internal connectivity layers
expand
```

Abutment of power pins with other cell from library clearly visible

<img width="1920" height="923" alt="w6d412" src="https://github.com/user-attachments/assets/970f7bf1-ff12-48b5-b078-68b8d7b08c18" />

#### 9. Do Post-Synthesis timing analysis with OpenSTA tool.

Since we are having 0 wns after improved timing run we are going to do timing analysis on initial run of synthesis which has lots of violations and no parameters were added to improve timing

Commands to invoke the OpenLANE flow include new lef and perform synthesis 

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

again you get wns as -23.89.

Newly created `pre_sta.conf` for STA analysis in `openlane` directory

![Screenshot from 2024-03-26 05-53-06](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/0a02d055-f012-44bd-a750-4508bbfc771e)

Newly created `my_base.sdc` for STA analysis in `openlane/designs/picorv32a/src` directory based on the file `openlane/scripts/base.sdc`

![Screenshot from 2024-03-26 05-55-17](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/8c917d87-5507-4079-ba6b-facbf18c238f)
![Screenshot from 2024-03-26 05-55-38](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e07d05db-2f06-47ab-bff7-2af88c39d001)

Commands to run STA in another terminal

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```

Screenshots of commands run

<img width="1920" height="923" alt="w6d4sta2" src="https://github.com/user-attachments/assets/6630ae7a-9574-459f-9950-d75b1250a468" />


Since more fanout is causing more delay we can add parameter to reduce fanout and do synthesis again

Commands to include new lef and perform synthesis 

```tcl
# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a -tag 25-03_18-52 -overwrite

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to set new value for SYNTH_MAX_FANOUT
set ::env(SYNTH_MAX_FANOUT) 4

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Commands run final screenshot

![Screenshot from 2024-03-26 06-20-29](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c5869cf5-ab95-46f9-9fd1-dc91e92455d8)

Commands to run STA in another terminal

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```

Screenshots of commands run

![Screenshot from 2024-03-26 06-22-31](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/0f3247fc-aaad-4e98-b23e-bdc9a361d08c)
![Screenshot from 2024-03-26 06-22-41](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/9fcc3975-0e03-4515-aee5-04b7c1c6a315)
![Screenshot from 2024-03-26 06-22-50](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e19db773-3995-4af4-b0a3-188b02fdf454)
![Screenshot from 2024-03-26 06-23-01](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c22c85fb-1a94-4639-a731-da4c364d1a78)

#### 10. Make timing ECO fixes to remove all violations.

OR gate of drive strength 2 is driving 4 fanouts

![Screenshot from 2024-03-26 06-55-46](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/73c58332-a212-4a24-b853-e8cae3b385a6)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11672_

# Checking command syntax
help replace_cell

# Replacing cell
replace_cell _14510_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot from 2024-03-26 07-02-44](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c50c6023-1836-468d-a8c3-955b02e4224c)
![Screenshot from 2024-03-26 07-04-08](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/6059a511-9977-4d9e-8dde-8939f0e1b8f7)
![Screenshot from 2024-03-26 09-42-15](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/df3dba3c-9445-4d51-9842-bf4410f05cf5)
![Screenshot from 2024-03-26 07-07-50](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/f141d1ff-4e21-4f9a-ab47-19579a686ac4)

OR gate of drive strength 2 is driving 4 fanouts

![Screenshot from 2024-03-26 09-46-23](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/3f66eed9-c43d-483e-ab85-21d70452b81f)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11675_

# Replacing cell
replace_cell _14514_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot from 2024-03-26 09-49-29](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/d896c1fa-078e-4fe1-8e4d-60fae870d672)
![Screenshot from 2024-03-26 09-50-13](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a21abd89-b92a-4d28-b065-6b8b523026de)
![Screenshot from 2024-03-26 09-50-33](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/9b961126-3de7-450e-9789-5009ca7f6a16)

OR gate of drive strength 2 driving OA gate has more delay

![Screenshot from 2024-03-26 10-22-10](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/7669eeef-7b93-4cfd-a152-17eec772496a)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11643_

# Replacing cell
replace_cell _14481_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot from 2024-03-26 10-29-31](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c63cf6a1-582d-43e5-907f-e292b94cc086)
![Screenshot from 2024-03-26 10-29-55](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/6495c2e8-78c8-41d2-b783-628f36b982c5)

OR gate of drive strength 2 driving OA gate has more delay

![Screenshot from 2024-03-26 10-32-27](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/4185dc98-a065-49d3-a92f-fb4b02f23ee5)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11668_

# Replacing cell
replace_cell _14506_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![Screenshot from 2024-03-26 10-36-59](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/be71b3a4-efe1-4239-be5a-28ccebd2b7f4)
![Screenshot from 2024-03-26 10-37-14](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/2ae759b3-f9a7-478f-a34a-3f8706347eca)

Commands to verify instance `_14506_`  is replaced with `sky130_fd_sc_hd__or4_4`

```tcl
# Generating custom timing report
report_checks -from _29043_ -to _30440_ -through _14506_
```

Screenshot of replaced instance

![Screenshot from 2024-03-26 10-43-04](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/970b3cb7-fe10-4b5e-99c9-85059714f8f2)

*We started ECO fixes at wns -23.9000 and now we stand at wns -22.6173 we reduced around 1.2827 ns of violation*

#### 11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.

Now to insert this updated netlist to PnR flow and we can use `write_verilog` and overwrite the synthesis netlist but before that we are going to make a copy of the old old netlist

Commands to make copy of netlist

```bash
# Change from home directory to synthesis results directory
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52/results/synthesis/

# List contents of the directory
ls

# Copy and rename the netlist
cp picorv32a.synthesis.v picorv32a.synthesis_old.v

# List contents of the directory
ls
```

Screenshot of commands run

![Screenshot from 2024-03-26 10-54-15](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/90c90853-0664-44d7-8ff2-573621935870)

Commands to write verilog

```tcl
# Check syntax
help write_verilog

# Overwriting current synthesis netlist
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52/results/synthesis/picorv32a.synthesis.v

# Exit from OpenSTA since timing analysis is done
exit
```

Screenshot of commands run

![Screenshot from 2024-03-26 11-02-19](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/c6c8ce7f-5219-41bc-a5a8-47b0e1c62c7c)

Verified that the netlist is overwritten by checking that instance `_14506_`  is replaced with `sky130_fd_sc_hd__or4_4`

![Screenshot from 2024-03-26 11-01-25](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/1ddb66da-64cb-426d-8d78-30370c63dacb)

Since we confirmed that netlist is replaced and will be loaded in PnR but since we want to follow up on the earlier 0 violation design we are continuing with the clean design to further stages

Commands load the design and run necessary stages

```tcl
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts
```

Screenshots of commands run

![Screenshot from 2024-03-26 11-33-14](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a0f223bc-3cbb-4bb1-8c7e-d800f1a4efd7)
![Screenshot from 2024-03-26 11-33-22](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/9bd610a8-fd5e-452b-94b2-5a5fc76db5e9)
![Screenshot from 2024-03-26 11-35-40](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/283d9b5e-fc48-45a3-8548-c68fc8966f46)
![Screenshot from 2024-03-26 11-36-16](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/af866818-af6f-4bc4-96c0-cf3c99839003)
![Screenshot from 2024-03-26 11-37-36](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/55aa5130-8a9f-48d6-abc8-7aace68b58c8)
![Screenshot from 2024-03-26 11-38-26](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/755fc79a-2a77-402b-aa11-33799e31ee09)
![Screenshot from 2024-03-26 11-39-53](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/45fdc85e-cc32-4b08-954e-bd78dcec0891)
![Screenshot from 2024-03-26 12-00-48](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/5deb6b89-c81e-4b4d-a225-badc1f7c7299)

#### 12. Post-CTS OpenROAD timing analysis.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD

```tcl
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Check syntax of 'report_checks' command
help report_checks

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated

![Screenshot from 2024-03-26 12-55-00](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/ee26dfa7-715a-4df7-97e7-4c6e54d16522)
![Screenshot from 2024-03-26 12-57-40](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e04a4dfd-000c-406b-bdaa-f5314c4eedef)
![Screenshot from 2024-03-26 12-58-12](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/ac27d567-1b72-444d-a638-9be2db677ae2)
![Screenshot from 2024-03-26 13-09-57](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/e63cac70-072d-4453-992e-076b94f8f1a2)

#### 13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis after changing `CTS_CLK_BUFFER_LIST`

```tcl
# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Removing 'sky130_fd_sc_hd__clkbuf_1' from the list
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Checking current value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Setting def as placement def
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts1.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Report hold skew
report_clock_skew -hold

# Report setup skew
report_clock_skew -setup

# Exit to OpenLANE flow
exit

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)
```

Screenshots of commands run and timing report generated

![Screenshot from 2024-03-26 13-42-03](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/2191f13b-ff76-4281-9d3c-52cbf12f9142)
![Screenshot from 2024-03-26 13-45-28](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/3dcd6efe-d31a-4f72-aede-be1cdd7b078f)
![Screenshot from 2024-03-26 13-48-01](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/2cb2c6fd-1e8c-4921-8553-7dcfb51258e5)
![Screenshot from 2024-03-26 13-48-13](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/70353613-86f2-432c-a1d8-821083e8c209)
![Screenshot from 2024-03-26 13-50-12](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/bf6c116b-e31c-4dce-b04f-a75430b1d03b)
![Screenshot from 2024-03-26 13-53-30](https://github.com/fayizferosh/soc-design-and-planning-nasscom-vsd/assets/63997454/a26e9d23-d448-4512-8676-8a2b3fb22572)
