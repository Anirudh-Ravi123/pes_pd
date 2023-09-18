# pes_pd
# ADVANCED PHYSICAL DESIGN USING OPENLANE/SKY130

## DAY 1- Inception of open-source EDA, OpenLANE and Sky130 PDK

**How to talk to Computers**
**Introduction to QFN-48 Package, chip, pads, core, die and IPs**

Lets us discuss this with an Aurdino board as an example.
An Arduino board is a popular open-source electronics platform that consists of a microcontroller, development environment. It is a small computer chip that processes instructions and controls the behavior of your electronic project.Arduino boards work by providing a platform for you to write and upload code that controls the behavior of the microcontroller on the board.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/3c9c1cb2-abef-4592-9456-4f93f9224a1d)

This board can describe it in a form of a block diagram:

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/9a3fb263-e0bd-4a43-96c4-6cf5bfe105e8)

- This is the typical board diagram with the processor and all the interfaces

the IC it looks something like this
![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/4eb85a39-26e1-4977-b477-e1954dbf552a)

- This IC contains the QFN-48(Quad Flat No-Leads) 7nmx7nm package
-  contains 48 electrical connections or pins
-  pin locations of the ackage are given by the arduino board.

The main chip is located at the centre of the package and is connected to the pins by wire bounds.
These wire bounds trasnfer all the incoming signals to the chip

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/edf8e92c-6063-416f-b96f-9ffdb2548fc8)

The chip in the package when opened up looks like this:

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/85a1f1d3-c0e4-4b5c-ba93-76eee42fe166)

-  PADs in chip are like the  metal  points on the bottom of the chipthat are  used to connect the chip to a circuit through signal can be sent into the chip.
-  Core of a chip is  the central part that  processes the information.Its a place where all our Digital logical sitslike the AND gate,OR gate,MUXs,etc.
-  Die s a tiny, flat piece of silicon that contains the actual electronic circuits and defines the size of the chip. The  Die is manufactured on a Silicon wafer.

The core of the CHIP contains  an SoC SRAM,ADCs,DACs,PLL,SPI and some momre components.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/439258ad-5afa-497d-8b8c-50b34274dcb1)

- the SRAM,ADC,DAC,PLL  are known As Foundry IP's.
-  a foundry refers to a specialized facility or company that manufactures integrated circuits (ICs) or microchips.
-  the SoC and the SPI are basically called as Macros.

  
  **Introduction to RISC-V**

  RISC-V is an open-source instruction set architecture (ISA) for designing and implementing custom microprocessors and other hardware.
- HIGH LEVEL CODING LANGUAGE Like C or C++
- Complied to RISCV assembly language program converted to binary level logic 1 and logic 0
- HARDWARE DESCRIPTION LANGAUGE implements the RISCV assembply program using an RTL(register transfer logic)
- RTL converted to layout (GDS - Graphic Data System)

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/ca4052e8-bdc3-474f-ae66-4e7e53449c1d)

**From Software Applications to Hardware**
- Apps: Application software is a type of computer software that is designed to perform specific tasks or functions for end-users.

- System software: System software refers to a category of computer software that acts as an intermediary between the hardware components of a computer system and the user-facing application software. It provides essential services, manages hardware resources, and enables the execution of application programs.

- Operating System: The operating system is a fundamental piece of software that manages hardware resources and provides various services for both users and application programs. It controls tasks such as memory management, process scheduling, file system management, and user interface interaction.

- Compiler: A compiler is a type of software tool that translates high-level programming code written by developers into assembly-level language.

- Assembler: An assembler is a software tool that translates assembly language code into machine code or binary code that can be directly executed by a computer's processor.

- RTL: RTL serves as an abstraction level in the design process that represents the behavior of a digital circuit in terms of registers and the operations that transfer data between them.

- Hardware: Hardware refers to the physical components of a computer system or any electronic device. It encompasses all the tangible parts that make up a computing or electronic device and enable it to perform various tasks.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/1609a405-fae2-4670-9361-bea50432ae4a)



**SoC design and OpenLANE**

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/9efd82d1-2a6d-42a9-b830-bdddff55bc2a)


PDK(Process Development Kit)
A Process Development Kit (PDK) is a set of tools, libraries, and data files provided by semiconductor manufacturers to integrated circuit (IC) designers. PDKs are essential for IC designers because they contain information and resources specific to the manufacturer's semiconductor fabrication process.
PDK contains
- Technology Files: PDKs include technology files that describe the manufacturing process details, such as transistor models, device parameters, interconnect layers, and design rules.
- Design Libraries: PDKs contain design libraries, which are collections of pre-designed and characterized circuit components, such as standard cells, memory elements, and analog circuit blocks.
- Simulation Models: PDKs provide simulation models for various components and elements used in IC designs.
- Layout and Mask Information: PDKs offer layout and mask design information, which is essential for creating the physical layout of the IC.
- Design Rule Checking (DRC) and Extraction Tools: PDKs often include tools for checking designs against manufacturing-specific design rules (DRC) and for extracting parasitic parameters that affect circuit performance.
- Calibration Data: Some PDKs include calibration data to ensure that the design tools accurately reflect the manufacturing process's characteristics.
- Documentation: Comprehensive documentation is typically part of a PDK, providing designers with information on how to use the kit effectively and design guidelines.


**Simplified RTL2GDS flow**

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/4fe32ecc-076b-4414-abe0-6f150129907a)

- Synthesis: is the process of converting the RTL description of a digital design into a gate-level netlist. This netlist consists of logical elements (gates) and their interconnections.

 ![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/bdf8b089-cd8e-4320-88d5-305e71f0a9f7)


- Floor/Power Planning: In this phase, the chip's overall floorplan is defined. It determines the approximate locations of key components, such as blocks and macros, and how power is distributed across the chip.
  
  - Macro Floor Planning - We define the macro dimensions, pin locations and rows are defined.
 
  ![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/b0e43593-ec5c-47a6-b7f0-51e70c9fb8e1)

  - Chip Floor Planning - Partition the chip die between different system building blocks and place the I/O pads.


  - Power Planning - The power distribution network is contructed.
  
  ![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/c127a7d4-9cce-470e-8e94-09b9ee280ec8)

- Placement: Placement involves assigning specific locations on the chip for each gate and macro from the synthesized netlist. The goal is to optimize for various objectives, including minimizing wirelength, meeting timing constraints, and managing thermal considerations.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/1082057c-bb1a-4316-8c2f-32fa46f81bb3)


- Clock Tree Synthesis: Clock tree synthesis (CTS) is a crucial step in ensuring that the clock signals reach all parts of the chip with minimal skew and jitter. It involves the generation of a hierarchical tree structure to distribute the clock signals uniformly and meet timing requirements.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/78add544-29d3-4e18-924c-0ac60c3b8651)


- Routing: After placement and CTS, routing is performed to create the physical wires (metal traces) that connect all the components on the chip. This process adheres to design rules and timing constraints.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/c7d898ed-afac-48b4-a059-f1f61a6a4ab3)

- Signoff: The Signoff stage encompasses a series of verification and validation steps


**Introduction to OpenLANE and Strive chipsets**

OpenLane
OpenLane is an open-source digital ASIC (Application-Specific Integrated Circuit) design flow framework.esigned to automate the process of designing and fabricating digital integrated circuits. OpenLane aims to make custom ASIC design more accessible to a broader range of engineers and researchers.


striVe is a family of open souces tools like open PDK, open EDA ,open RTL.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/97399b2b-2408-4fa0-b2d8-81b7967854d7)



**OpenLANE ASIC  flow**

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/ba36bb0a-b15f-4e2e-ab8a-c8f923da64ee)


- Synthesis exploration is a process in digital integrated circuit  design where designers explore various design options and configurations during the synthesis stage. The goal is to find the best combination of logic optimizations, architecture choices, and design constraints to meet the desired performance, power consumption, and area targets for the design. 

- Design exploration refers to the process of investigating and evaluating various design alternatives, configurations, and choices to optimize a system or product's performance, functionality, cost, or other key attributes.

- Regression testing uses design exploration utility on approximately 70 designs and compares the results with the best known ones.

  ![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/4d0445ba-0390-498a-9c7a-4bfbc10c70ca)

- Design for Test (DFT) is a set of engineering techniques and practices employed during the design of integrated circuits and electronic systems to facilitate and improve the testing and verification process. The main objective of DFT is to make it easier to detect and diagnose faults, defects, or issues within the IC or system.

- Physical implementation  refers to the process of transforming a high-level logical description of an IC into a physical layout that can be fabricated. Process involves Floorplanning, Placement, Clock Tree Synthesis, Routing etc

- Logic Equivalence Check  done by using yosys. Every time the netlist is modified ,verification must be performed. CTS modifies the netlist, post placement optimizations modifies the netlist

- Antenna Rules ViolationsWhen ametal wire segment is fabricated ,it can act as an antenna. Reactive ion etching causes charges to accumulate on the wire due to which transistor gates are damaged during fabrication. Solutions are bridging attaches a higher layer intermediary or adding  antenna diode cell to leak away charges

- Static Timing Analysis RC Extraction : DEF2SPEF and 
- Static Timing Analysis RC Extraction : DEF2SPEF and


**Getting Familiar with the Open Source EDA Tools**

Tool we will be  working on pdk variant called sky130_fd_sc_hd

- sky130 : is the process name
- fd : skywater foundary
- sc : standard cell
- hd(high density) : variant of pdk

**Design Preperation step**
First we go the the working directory 
```
cd Desktop/work/tools/
cd openlane_working_dir/
cd openlane
```
Now when we  type the ```docker``` command a shell opens .
In the shell we type ```./flow.tcl -interactive```


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/a6129d96-95c1-48bf-aa4b-f11f1d1b911b)


Then we type ```package require openlane 0.9``` to import all the packages 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/84eeda59-504b-406f-b97a-e7afec32e34e)


Now for the design setup stage, we will be working on picorv32a design.

```
prep -design picorv32a
```

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/9c6e9c0a-cbcd-472e-af24-a666bfb78444)

After preparing the design, we can see that a new 'runs' folder is created.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/ab072ac0-842b-4391-82cf-bf8ff7c8014d)


Now we synthesis the design
```
run_synthesis
```

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/ed9950fb-d0c8-4704-bb09-9ab5025ecf78)

Synthesized 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/6b1fc802-218d-4b66-b152-6ea447aa03df)


Flop ratio = 1613/14876 = 0.108

10.8% of the cells in our design are flip flops

Netlist is generated in the runs folder 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/aebfb15a-047a-409c-838e-72b2d0ea4a1b)




##  DAY 2 - Good floorplan vs bad floorplan and introduction to library cells

**Chip Floor planning considerations**

-  Define Width and height of core and die:
  The die refers to the entire semiconductor chip, including the core, I/O pads, and any additional features.The core refers to the central area of the chip where most of the active circuitry resides. It includes components like the CPU, GPU, memory, and other logic.

Utilisation factor plays an important role in floor planning
It is given by 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/fde5cfbf-b49c-4ca8-9c84-204d9095d32c)


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/547d08b1-287c-41ea-8fa3-fe01d4c48dc2)


- Define Location of Pre-Placed cells

Pre-Placed Cells are specific blocks or cells like memories, clock gating cells, comparator, mux etc within an integrated circuit layout that are manually placed by the chip designer in predetermined locations before the automated placement and routing tools are used to complete the rest of the design.


- De-coupling capacitors
  
In large circuits with many resistors there are time when the capacitor may not get charged fully due to voltage drops. The solution for this is to use de-  coupling capacitors. Decoupling capacitors store and discharge electrical energy quickly or decoupling capacitors absorb excess charge to filter out high- 
frequency noise and transient voltage fluctuations.



- Power Planning
  
Power planning during the Floorplanning phase is essential to lower noise in digital circuits attributed to voltage droop and ground bounce.When a transition occurs on a net, charge associated with coupling capacitors may be dumped to ground. If there are not enough ground taps charge will accumulate at the tap and the ground line will act like a large resistor, raising the ground voltage and lowering our noise margin. To bypass this problem a robust PDN with many power strap taps are needed to lower the resistance associated with the PDN.



- Pin Placement

Pin placement is an essential part of floorplanning to minimize buffering and improve power consumption and timing delays we use the HDL netlist to determine where a specific pin should be placed in the circuit. We join the common pins and try to keep the connections as effecient as possible.



**Steps to run FLoorplan using OpenLANE**
First we run the floop plan in openLane using the command ```run_floorplan```


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/472365f3-63e3-437b-83ed-c5a388076682)


Then we navigate to the /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/11-09_17-53/results/floorplan directory 
Then we type the command 
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/d8cc2ef6-57b3-4e7a-a133-d517a6926a7e)


Layout 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/fefa4336-a641-468f-9304-3ee241847ab1)


Zoomed in view 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/eeba75c7-b8ca-4718-96fb-1fc3a4710b5b)


Standard cells that are used in the design

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/02b5c7da-f5d8-4522-b296-aa7b1882ae36)



**Library Binding and Placement**


**Netlist binding and initial place design**

Netlist binding is the process of mapping the logical representation of a digital design (typically described in a hardware description language l onto a library of standard cells.

Each component is mapped to a given shape. All these shapes and the working  are defined in the library. Then all these shapes from each stage of the netlist are placed onto the floorplan in a efficient way so that delay is minimal.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/28a1cacd-c02e-4e50-8817-768de9ed30a0)

- The components of the netlist are placed in the core area.
- They are placed according to the convenience of distance from the pins.
- When sending signal from FF1 to FF2, according to the circuit requirements, there has to be a very fast propogation of signals. Hence, they are placed very close and buffers are added since there is a small 
  delay for the signal from the pin to reach FF1. The buffers maintain signal integrity
**Optimize placement using estimated wire-length and capacitance**

Estimated wire-length and capacitance is a crucial step to ensure that the physical layout of components and interconnections meets performance and power goals. Wire-length estimation and capacitance modeling help guide the placement process, especially when considering factors like signal delay, power consumption, and signal integrity.
If the wire area is big then the resistance and capacitance huge. To maintain signal inteegrity we route the signal through buffers that replicates and routes the signals.

The integration of wire-length and capacitance estimates into the placement optimization process helps balance performance, power, and area trade-offs in the design. The goal is to achieve a placement that minimizes signal delays, reduces power consumption, maintains signal integrity, and meets all design constraints.


**Final placement optimization**

When performing final placement optimization with timing analysis using an ideal clock, you are essentially optimizing the physical placement of components within an integrated circuit while assuming that the clock signal is perfect.. This approach allows you to focus primarily on optimizing the physical layout of the design without considering clock-related timing challenges.



**Need for libraries and characterization**

Libraries and characterization are foundational elements of the IC design process. Libraries provide standardized building blocks that enhance design productivity and reusability, while characterization provides the essential data needed to accurately model and simulate the behavior of these components, ensuring that the final design meets its performance, power, and reliability goals.


**Congestion aware placement using RePlAce**

For global placement we run the ```run_placement``` command 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/2d61b79b-5291-42a8-8702-fa7f3d145376)


Here the Half parameter wire lenght and overflow are changed throught the iterations. Our objective is to reduce the overlfow


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/19347f4e-767b-4d5b-890e-bf64cea664ac)


then we type the command 
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/eb056a69-65aa-4d9a-bff7-a42104184083)


On zooming in we can see the placement of the standard cells

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/f0bc4e14-94f9-4125-986f-3fb12f370c85)





**Cell design and characterization flows**

**Inputs for cell design flow**

Cell design flow refers to the process of creating and optimizing individual digital logic cells that are part of a standard cell library. These libraries contain a set of pre-designed, characterized, and reusable logic gates, flip-flops, and other basic building blocks used in the design of integrated circuits.
These libraries include  PDK, DRC and LVS rules, SPICE models, libraries, user-defined specifications.
User derfined specifications like Pin location, drawn gate lenght are added to the libarary by the library developer.

**Circuit Design**

 Circuit design:Implment function using nmos and pmos and then derive the network graph. Derive the Euler's path and stick diagram from the graph.
 
**Layout design**
 Convert stick diagram according to the DRC rules
Extraction of parasitics,extracted spice list

**Characterization**
timing ,noise power.libs functions
Read in the models and tech files and generate extracted spice Netlist. Read the subcircuits and attach power sources. Apply stimulus to characterization setup, provide neccesary output capacitance loads and provide neccesary simulation commands.



**General timing characterization parameters**

**Timing threshold definitions**

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/10949764-a9f2-4860-9f8c-90d092ea32ef)



**Propagation Delay**
The time difference between when the transitional input reaches 50% of its final value and when the output reaches 50% of its final value. 

```
Propagation delay=time(out_fall_thr)-time(in_rise_thr)
```

**Transition Time**
The time it takes the signal to move between states is the transition time , where the time is measured between 10% and 90% or 20% to 80% of the signal levels.

```
Rise transition time = time(slew_high_rise_thr) - time (slew_low_rise_thr)
```


```
Fall transition time = time(slew_high_fall_thr) - time (slew_low_fall_thr)
```



## DAY 3 - Design library cell using Magic Layout and ngspice characterization

**Labs for CMOS inverter ngspice simulations**

IO Placer revision
PnR is a iterative flow and hence, we can make changes to the environment variables when required.
For example we can change the  pin configuration along the core from equvi distance randomly placed to someother placement.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/83069431-583f-4228-9bda-cb47b37015ba)


**SPICE deck creation for CMOS inverter**


To simulate standard cells  we  need to  create spice deck for our cell.
The spice deck will contain
- Component connectivity which include the substrate taps that  tunes the threshold voltage of the MOS
- Component values like values of PMOS and NMOS, Output load, Input Gate Voltage, supply voltage
- Node names which  are required to define the SPICE Netlist


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/e70a334f-604f-42ce-81af-986009595de5)


**Switching Threshold of a CMOS Inverter**
CMOS cells have three modes of operation:

Cutoff - No inversion
Triode - Inversion but no pinchoff in channel
Saturation - Inversion and pinchoff in channel

The voltages at which the switch between the modes of operation happens is dependent on the threshold voltage of the device. Threshold voltage is a function of the W/L ratio of a device, therefore varying the W/L ratio will vary the output waveform of CMOS devices.
To enable efficient description of the varying waveforms a single parameter called switching threshold is used. Switching threshold is defined at the intersection of Vin = Vout. 


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/28a7e92a-bbfd-4428-a2c5-748995227b16)


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/93ea6940-f72d-4181-8d61-45bb83130fd3)


**Inception of Layout of CMOS fabrication process**

**16 mask CMOS process**

- Substrate Selection: In the initial phase, the appropriate semiconductor substrate is chosen.
- Create an active region for transistors : to isolate the active regions for transistors SiO2 and Si3N2 deposited. Pockets created using photoresist and lithography.
- Nwell & Pwell formation : P-well formation involves photolithography and ion implantation of p-type Boron material into the p-substrate.N-well is formed similarly with n-type Phosphorus material.. Drive in 
  diffusion by placing it in a high temperature furnace.
- Gate Formationg.A polysilicon layer is deposited and photolithography techniques are applied to create NMOS and PMOS gates
- Lightly Doped Drain (LDD) formation : LDD done to avoid hot electron effect and short channel effect.
- Source & Drain Formation: Thin oxide layers are added to avoid channel effects during ion implantation.N+ and P+ implants are performed using Arsenic implantation and high-temperature annealing.
- Local Interconnect Formation: Thin screen oxide is removed through etching in HF solution.Titanium deposition through sputtering is initiated. Heat treatment results in chemical reactions, producing low-    
  resistant titanium silicon dioxide for interconnect contacts and titanium nitride for top-level connections, enabling local communication.
- Higher Level Metal Formation: To achieve suitable metal interconnects, non-planar surface topography is addressed.Chemical Mechanical Polishing (CMP) is utilized by doping silicon oxide with Boron or   
  Phosphorus to achieve surface planarization.TiN and blanket Tungsten layers are deposited and subjected to CMP.An aluminum (Al) layer is added and subjected to photolithography and CMP
- Dielectric Layer Addition: Finally, a dielectric layer, typically Si3N4, is applied to safeguard the chip.


**LAB**

Cloning repository

```
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```


command for layout
```
magic -T sky130A.tech sky130_inv.mag &
```

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/49e9db46-f491-4b02-940e-073314e4a465)

Click on the component and type ```what``` in the tkcon window

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/26bb651d-da09-4199-a2b9-c5ecb8253425)

**DRC Errors**

DRC errors in magic will be highlighted with white dotted lines:

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/7e023b4b-2c28-473d-a879-029feeb593a1)

To identify DRC errors select DRC find next error:
it will be displayed on the tkcon window

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/5a339793-7050-4f7f-94f2-9eefaa3f9073)

**Extracting to SPICE**
Command 
```
extract all
ext2spice cthresh 0 rthresh 0
```
cthresh and rthresh are used to extract all parasatic capacitances.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/1bbef24c-f86b-4b54-b9e5-e70fc9edd21d)


SPICE file 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/9665e29b-cb88-4aa6-a408-e26a520628f3)


**Spice Wrapper for Simulation**

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/0140489c-834e-4ffe-a6e6-6e19b2cf9091)


**NGPSICE**
![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/e9c1c6e3-db9b-4a67-90c0-3130db690dca)


Next we type the command 
```
plot y vs time a
```

**WAVEFORM**

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/5b1f8fb1-24b1-4ae9-bb40-cd9ceffded75)



**Introduction to Magic tool options and DRC rules**

(refer:http://opencircuitdesign.com/magic/)
Magic is a venerable VLSI layout tool, written in the 1980's at Berkeley by John Ousterhout, now famous primarily for writing the scripting interpreter language Tcl. Due largely in part to its liberal Berkeley open-source license, magic has remained popular with universities and small companies. The open-source license has allowed VLSI engineers with a bent toward programming to implement clever ideas and help magic stay abreast of fabrication technology. However, it is the well thought-out core algorithms which lend to magic the greatest part of its popularity. Magic is widely cited as being the easiest tool to use for circuit layout, even for people who ultimately rely on commercial tools for their product design flow.


Drc section
The design rules used by Magic's design rule checker come entirely from the technology file. We'll look first at two simple kinds of rules, width and and spacing. Most of the rules in the drc section are one or the other of these kinds of rules.


SKY130 pdk
SKY130 is a mature 180nm-130nm hybrid technology developed by Cypress Semiconductor that has been used for many production parts. SKY130 is now available as a foundry technology through SkyWater Technology Foundry.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/37b78da5-b313-47a1-ae9d-6d92911cab33)



![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/04b4381b-b92f-40ed-a403-09c0be903743)




Commands to open magic 
```
magic -d XR
```

Then we open the met3.mag file


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/e746a4b8-cd4b-442e-8916-2bc8fdce4c9e)



To check which DRC rule is being violated select area and type drc why in tkcon 


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/be24dcd6-9893-4c5a-b2d1-5b2061b9370c)



to add contact cuts 
add met3 contact by selecting area and clicking on m3contact using middle mouse button.
then type ``` cif see VIA2``` in tkcon prompt


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/075377c5-4aa4-4583-9656-d0e87d5ab95a)



To fix errors

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/25ecd4e0-a818-478b-bd23-9832bf88d536)

the error is 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/46257981-a308-4be5-b684-ddedb0defc79)



To fix the error open the sky130A.tech file using a editor and search for poly.9 and make the changes

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/b78688b0-689a-4f18-af77-198c087daf32)


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/46d73847-29cc-4171-9746-1bb51090b71c)


Now load the sky130A.tech file again and type the command ```drc check```


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/5fe12345-e777-4215-9a15-c807b4d7ccae)



We can see the error is fixed 


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/d843fa0a-45f0-45f8-a148-f28fc61f7dee)



**DRC error as geometrical construct**

Open the nwell.mag file in magic. Seletch the nwell.6 and type the commands
```
cif ostyle drc
cif see dnwell_shrink
cif see dnwell_missing
```

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/5df2c37d-8812-4b99-9354-75df1b87f133)


Output 


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/a53fd631-d968-49ba-a1c2-3a839c7b2111)


**to find missing or incorrect rules and fix them**


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/3e68f2b7-5a31-4d46-b207-a65629b9c197)


ERROR

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/5b0b494d-4797-4da7-8340-9355e7f0a0d5)

To fix make the changes 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/0325097c-4ff8-4461-8063-34d274c1cf48)


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/8cd1215a-bf4f-4fa6-910b-eaad60d19c20)


Now load the sky130A.tech file and type the command ```drc check```  for both normal and drc fast 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/a843d9f6-ead2-45fc-81df-22d46b651bc4)


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/2cf31443-e887-4c36-9237-8ba889cab2fd)



## DAY 4

## Pre-layout timing analysis and importance of good clock tree

Place and routing (PnR) is performed using an abstract view of the GDS files generated by Magic. The PnR tool will use the abstract view information, formally defined as LEF information, to perform interconnect routing.
From PnR POV, We have to follow certain guidelines to get standard cell set

Input and output ports must lie on the intersection of vertical and horizontal tracks
Width of the standard cell should be odd multiples of the track pitch and height should be odd multiple of vertical track pitch

**steps to convert grid info to track info**

Path to track info
```
Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130fd_sc_hd
```

Now we open the track.info file


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/08bb1a3d-c41e-405e-b960-d3fe9323b8a9)

- The tracks.info file is used during routing.
- Routes are the metal traces.

1st numeric column indicates the offset and 2nd indicates the pitch along provided direction


Setting grid values 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/06f300fa-2ffa-4227-b297-c08cc921b3d4)


We converge the grid definition in the layout to track definition


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/4509cd00-6502-42e2-a477-f7573e6b51f1)



![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/c3b28612-9767-4698-a9d3-f1837e5976ed)


From the above pic, its confirmed that the pins A and Y are at the intersection of X and Y tracks. So the first condition is met.
The next requirement is that the width of the cell should be the odd multiple of xpitch which is '0.46' as seen in the tracks.info file.


**Convert Magic Layout to Standard Cell LEF**

To generate the cell LEF file from Magic first we save the modified layout and then we open the file and extract LEF
we type the command in the tkcon window

```
save sky130_vsdinv.mag
```

Now in the terminal we type 

```
 magic -T sky130A.tch sky130_vsdinv.mag
lef write
```


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/74957701-02f0-40ca-b113-167915469817)



**Steps to Include New Cell in Synthesis**

We copy the lef file created and the sky130 library that to the src folder of picorv32a folder.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/29d1dee0-5a7c-4fa0-867b-bb754381a706)

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/cb1f179f-83c3-4e0d-b060-471f7f038846)


Modify config file to include the libraries and lef file 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/471697e5-1c73-4878-8f1c-d66b3c0694e4)


Next in OpenLANE we retrieve the 0.9 package.

We type the followig commands 
```
prep -design picorv32a -tag 16-09_19-58 -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
```

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/d42c354d-f6ca-4a01-8d41-d2df8c140a02)


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/201c1736-68fa-4621-a9e4-de6fe1be819a)


Now we ```run_synthesis```


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/b531af6c-3bb5-407c-b6eb-3321fe29dcd9)


**steps to configure synthesis settings to fix slack and include vsdinv**

Slack violations refer to timing violations in digital designs. These violations occur when the signal arrives at its destination too early or too late, violating the specified setup or hold time constraints. 

When referring to pre clock tree synthesis STA analysis we are mainly concerned with setup timing in regards to a launch clock. STA will report problems such as worst negative slack (WNS) and total negative slack (TNS). These refer to the worst path delay and total path delay in regards to our setup timing restraint. Fixing slack violations can be debugged through performing STA analysis with OpenSTA, which is integrated in the OpenLANE tool.
The desired value of slack is above or equal to 0. 

Ways to fix slack

1.Changing  synthesis strategy in OpenLANE
 - Enalbed CELL_SIZING
 - Enabled SYNTH_STRATEGY with parameter as DELAY 1

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/6cbde5c3-5b7b-4a76-88e4-2a5cf9f4c2f5)

Slack still isnt in the required range.

The sdc file used is my_base.sdc defined in pre_sta.conf using the command sta pre_sta.conf

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/f57ba8a6-fc74-455b-b323-017aeb6e46a6)

The delay is high when the fanout is high. Therefore we can re-run synthesis by changing the value of SYNTH_MAX_FANOUT variable

2.Enable cell buffering

3.Perform manual cell replacement on our WNS path with the OpenSTA tool
Net is driving most outputs and replace the driver cell with larger form of its own kind

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/de2cca82-aa2c-4d6d-8e1a-52864c2bba9e)

4.Optimize the fanout value with OpenLANE tool

Now since synthesised the core using our vsdinv cell too and as it got successfully synthesized. We go ahead with the floorplan 

```
init_floorplan
run_placement
```

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/5ac80fb7-d7d2-46bb-871e-9e27249eb3ab)


On zooming in 

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/f08dcba3-2f3f-442f-9a0a-9605348f4111)


**Introduction to delay tables**

Delay tables, also known as delay models or delay tables, are essential components in digital circuit design and analysis. They provide a way to model and understand the propagation delays of logic gates and interconnects within a digital integrated circuit (IC). These tables play a crucial role in ensuring that the circuit meets its timing requirements, such as setup and hold times, and they are fundamental to the design of synchronous digital systems. Here's an introduction to delay tables:

1. Purpose of Delay Tables:

Delay tables are used to represent the delays encountered by signals as they pass through various components of a digital circuit. The primary purposes of delay tables are as follows:

Timing Analysis: They are essential for performing timing analysis, ensuring that signals meet their timing constraints, and identifying potential violations.

Synchronization: They help in synchronizing different parts of a digital system to ensure that data is sampled or latched correctly.

Power Estimation: Delay tables are used for estimating power consumption in digital circuits since power dissipation is directly related to signal transitions.

2. Components of Delay Tables:

Delay tables typically include the following components:

Input Conditions: These conditions specify the input signal values or transitions that trigger the delay calculation. Inputs can include input signal values, load conditions, and transition times.

Gate Delays: Delay tables include information about the propagation delays of various logic gates, such as AND, OR, NAND, NOR, XOR, and others. These delays depend on the gate's technology, fan-out, and input conditions.

Interconnect Delays: They account for the delays introduced by the wires and routing between logic gates. Interconnect delays depend on the physical characteristics of the wires, including length, resistance, and capacitance.

Output Loads: The output load conditions specify the capacitive load that the gate must drive, which affects the output delay.



**Timing analysis with ideal clocks using openSTA**


**Setup timing analysis and introduction to flip-flop setup time**

Setup Timing Analysis:

Setup timing analysis is a critical aspect of digital circuit design and verification. It focuses on ensuring that data signals meet the required setup time constraints at the inputs of sequential elements (e.g., flip-flops) in a digital system. The primary goal of setup timing analysis is to ensure that data is stable and valid before it is clocked into a flip-flop or other storage elements.


Introduction to Flip-Flop Setup Time:

The setup time (Ts) for a flip-flop is a critical parameter that determines when a data input signal must be stable before the arrival of the clock edge to guarantee proper data capture. It is defined as the minimum amount of time the data input must be held at a valid logic level before the active clock edge (e.g., rising edge) for reliable storage.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/51a27aca-0064-4ea9-844f-e0201e4ccfbb)



**Introduction to clock jitter and uncertainty**

Clock Jitter:

Clock jitter refers to the short-term variations or fluctuations in the timing of a clock signal's edges. It is a critical parameter in digital systems and communication systems, as it can affect the overall system's performance, especially in high-speed or sensitive applications. Clock jitter can be caused by various factors and can manifest as random or deterministic variations in the clock signal's timing. 

Clock Uncertainty:

Clock uncertainty, also known as clock skew, is related to the variation in the arrival times of clock signals at different points within a digital system. It is distinct from clock jitter but can also impact system performance and timing. Clock uncertainty can arise due to factors such as clock distribution network delays, routing delays, and variations in clock path lengths.




**Clock Tree Synthesis**

After all the above steps of fixing slack violations. A a mapped.v file is generated in synthesis results. Therefore we write this netlist using write_verilog and replace the openlane generated mapped file ie., picorv32a.synthesis.v

now in the openlane flow, continue with 
```
run_flooorplan 
run_placement 
run_cts
```

**Post CTS- STA Analysis**

OpenSTA is an open-source static timing analysis tool that is commonly used in digital circuit design. STA is a critical step in the design and verification of digital circuits, ensuring that the circuit meets its timing requirements. OpenSTA is part of the larger OpenROAD open-source RTL-to-GDSII  flow, which provides a complete ASIC design environment.

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/e456c956-fe9b-4429-9aca-d885cbb7a6e9)


- Launch OpenRoad.
- Read lef file from tmp folder of runs
- Read def file from results of cts
- Create and save the .db  file =```write_db pico_cts.db```
- Load the .db file = ```read_db pico_cts.db```
- Read the cts generated verilog file
- read both the minimum and maximum liberty files.
- set the clocks.
- Generate timing reports


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/9e95e09f-fde9-4a30-ab9a-44b461fa1dbf)



![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/9479e672-0111-4854-98b8-dfa930bb06af)


The timing results wont meet our expectations due to the utilization of minimum and maximum library files which OpenRoad does not currently support for multi-corner optimization. Hence we do it using only typical corner lib


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/6f44ed31-8a23-4401-9fb8-6061d1a787ac)


![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/9a337013-3870-4b29-b8ce-c33008ad409f)



![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/7410594e-b734-4b4a-b64a-822a36e68407)


We need to ensure that  skew is withing 10% of the clock period
To generate report type the command ```report_clock_skew -hold```

![image](https://github.com/Anirudh-Ravi123/pes_pd/assets/142154804/f67c5be4-658c-4713-842f-dbe876e75806)


## DAY 5
