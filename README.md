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


