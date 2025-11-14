# 32-BIT_ALU Simulation and Synthesis

## Aim:
Write a Verilog code for a 32-bit ALU supporting four logical and four arithmetic operations. Use case statements in behavioural modelling.
To verify functionality using the Test Bench, synthesize and analyse area and Power reports of a 32 Bit ALU design 

## Tool Required:
Functional Simulation: Incisive Simulator (ncvlog, nclaunch, ncsim)

Synthesise using Genus

## Design Information and Block Diagram:
The ALU will take in two 32-bit values and a control line. An Arithmetic unit does the following tasks like addition, subtraction, multiplication and logical operations. As the input is given in 32-bit, we get a 32-bit output. The arithmetic will show only one output at a time, so a selector is necessary to select one of the operators.

<img width="668" height="344" alt="image" src="https://github.com/user-attachments/assets/1195efe3-e2dd-443c-8bf0-be1579c06533" />

#### Fig 1: Block Diagram of 32 Bit ALU

## Creating a Workspace:

Create a folder in your name (Note: Give folder name without any space) and create a new sub-Directory name it as Exp3 or alu_32bit for the Design and open a terminal from the Sub-Directory.

## Creating Source Codes
In the Terminal window, type gedit <filename>.v (ex: gedit alu_32bit.v)

A Blank Document opens up into which the following source code can be typed.

(Note: File name should be with HDL Extension)

#### a)	To verify the Functionality using the Test Bench

## Source Code – Using Case Statement :

(Include program here)

Use the Save option or Ctrl+S to save the code, or click on the save option from the top-right corner and close the text file.

## Creating a Test Bench:

Similarly, create your test bench using gedit <filename_tb>.v to open a new blank document (alu_32bit_tb_case).

## Test Bench :

(Include test bench program here)

Use the Save option or Ctrl+S to save the code, or click on the save option from the top-right corner and close the text file.

## Functional Simulation:

Invoke the cadence environment by typing the commands below

tcsh (Invokes C-Shell)

source /cadence/install/cshrc (mention the path of the tools)

(The path of cshrc could vary depending on the installation destination)

After this, you can see the window like below
![WhatsApp Image 2025-11-12 at 10 14 41_105df371](https://github.com/user-attachments/assets/c934beeb-2867-41e2-b139-f4e9d6d26f32)

#### Fig 2: Invoke the Cadence Environment

To Launch the Simulation tool

•linux:/> nclaunch -new& // “-new” option is used for invoking NCVERILOG for the first time for any design

or

•linux:/> nclaunch& // On subsequent calls to NCVERILOG

It will invoke the nclaunch window for functional simulation. We can compile, elaborate and simulate it using Multiple Steps.

#### Fig 3: Setting Multi-step simulation

Select Multiple Step and then select “Create cds.lib File” as shown in the figure below

Click the .cds.lib file and save the file by clicking on the Save option
![WhatsApp Image 2025-11-12 at 10 15 45_e636970c](https://github.com/user-attachments/assets/20a20102-cd54-4eb7-b058-11d6297b5d40)


#### Fig 4:cds.lib file Creation
Save .lib file and select the correct option for cds.lib file format based on the HDL Language and Libraries used.

Select “Don’t include any libraries (verilog design)” from “New cds.lib file” and click on “OK” as in the figure below.

We are simulating a verilog design without using any libraries

Click “OK” in the “nclaunch: Open Design Directory” window, as shown in the figure below
![WhatsApp Image 2025-11-12 at 10 17 36_6364bd69](https://github.com/user-attachments/assets/44729ce9-eed9-47cb-b802-49b7eec044f6)


#### Fig 5: Selection of Don’t include any libraries
An ‘NCLaunch window’ appears as shown in the figure below

Left side, you can see the HDL files. The right side of the window has Worklib and snapshots directories listed.

Worklib is the directory where all the compiled codes are stored, while Snapshot will have the output of elaboration, which in turn goes for simulation.

To perform the function simulation, the following three steps are involved: Compilation, Elaboration and Simulation.
![WhatsApp Image 2025-11-12 at 10 20 45_7fbe5799](https://github.com/user-attachments/assets/a97d2c36-1297-4970-8d90-ea65bed4214e)



#### Fig 6: Nclaunch Window

### Step 1: Compilation:
– Process to check the correct Verilog language syntax and usage

Inputs: Supplied are Verilog design and test bench codes

Outputs: Compiled database created in mapped library if successful, generates report else error reported in log file

#### Steps for compilation:
1.	Create work/library directory (most of the latest simulation tools creates automatically)
   
2.	Map the work to library created (most of the latest simulation tools creates automatically)
   
3.	Run the compile command with compile options

i.e Cadence IES command for compile: ncverilog +access+rwc -compile filename.v

Left side select the file and in Tools: launch verilog compiler with current selection will get enable. Click it to compile the code
Worklib is the directory where all the compiled codes are stored while Snapshot will have output of elaboration which in turn goes for simulation.
![WhatsApp Image 2025-11-12 at 10 21 23_8b5b059a](https://github.com/user-attachments/assets/c473143c-f0c3-4e24-9ee7-d171aabed010)


#### Fig 7: Compiled database in WorkLib
After compilation, it will come under worklib. You can see on the right side window

select the test bench and compile it. It will come under Worklib. Under Worklib, you can see the module and test bench.

The cds.lib file is an ASCII text file. It defines which libraries are accessible and where they are located. It contains statements that map logical library names to their physical directory paths. For this Design, you will define a library called “worklib”

### Step 2: Elaboration:
To check the port connections in a hierarchical design

Inputs: Top-level design/test bench Verilog codes

Outputs: Elaborate database updated in the mapped library if successful, generates a report, else error reported in the log file

#### Steps for elaboration
– Run the elaboration command with elaborate options

1.It builds the module hierarchy

2. Binds modules to module instances
   
3.Computes parameter values

4. Checks for hierarchical name conflicts
   
5.It also establishes net connectivity and prepares all of this for simulation

After elaboration, the file will come under snapshot. Select the test bench and simulate it.
![WhatsApp Image 2025-11-12 at 10 22 36_6461efa1](https://github.com/user-attachments/assets/a09a96ef-7d19-498a-aaf4-b019d66508e9)


#### Fig 8: Elaboration Launch Option

### Step 3: Simulation:
– Simulate with the given test vectors over a period of time to observe the output behaviour.

Inputs: Compiled and Elaborated top-level module name

Outputs: Simulation log file, waveforms for debugging

Simulations allow dumping design and test bench signals into a waveform

Steps for simulation – Run the simulation command with simulator options


#### Fig 9: Design Browser window for simulation
<img width="1739" height="928" alt="image" src="https://github.com/user-attachments/assets/6c867751-635c-4b68-aa96-fd04c737fda3" />



#### Fig 10: Simulation Waveform Window

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

### Performing Synthesis
The Liberty files are present in the library path,

• The Available technology nodes are 180nm,90nm and 45nm.

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist. Or use source run.tcl command in the terminal window to view the netlist, and a log file will be created in the working folder.
<img width="1919" height="500" alt="498667185-e794f7cb-4f25-4e98-b228-0b9b5d43d4b7" src="https://github.com/user-attachments/assets/e68b9c4e-7a92-4193-9d4c-05d667c4d2bf" />



#### Fig 11: Synthesis RTL Schematic
<img width="1737" height="931" alt="image" src="https://github.com/user-attachments/assets/976c55bc-f936-4f14-8085-2dd04a201b86" />

#### Fig 12: Area report
![WhatsApp Image 2025-11-12 at 10 33 19_28c294dc](https://github.com/user-attachments/assets/49c894f6-7b0b-48fa-a0c7-8ba65e659e19)

#### Fig 13: Power Report
![WhatsApp Image 2025-11-12 at 10 33 37_658faad7](https://github.com/user-attachments/assets/1ccb28d7-2049-4c58-b59f-045c601505d6)


## Result
The functionality of the 32-bit ALU was successfully verified using a test bench and simulated with the nclaunch tool. Additionally, the generic netlist of the 32-bit ALU was generated, and the corresponding area and power reports were analyzed and tabulated using Cadence Genus.
