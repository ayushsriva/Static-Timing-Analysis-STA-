
# Static Timing Analysis(STA) Workshop: Basics to Advanced
**Motivation to attend workshop **: ** As we are seeing that the semiconductor industries are growing at a very faster rate. After some years later, it is going to be a boom of semiconductor industries. In VLSI, there are generally two types of domain namely front-end and back-end.
Front-end involves marketing Analysis, Design Entry, Simulation, Verification, Synthesis and Pre-layout STA.
Back-end involves Floorplanning, Place & Route, Post-layout STA and Signoff.
As we know that how much timing plays a very important role in meeting the design in Static Timing Analysis(STA). So, STA plays a vital role in the ASIC flow. It involves lots of things to learn and understand in STA which motivates me to attend this workshop.**



                                                           **ASIC Design Flow:**
<img width="397" alt="bg1a" src="https://user-images.githubusercontent.com/98880516/152572049-4d8c543b-504f-44e8-86fc-6d9f647c8dd0.png">
                            Reference: https://fdocuments.in/reader/full/advanced-asic-chip-synthesis-bhatnagar


## Day 1:
-	What is Static Timing Analysis:  Static Timing Analysis is a method of verifying timing performance of the design. Also, it is the process of adding the cell delays and the net delays to obtain the path delays and of comprising the path delays to timing specification and then compare to timing constraints.

1. Features of STA :
   - It is static in nature.
   - It is exhaustive.
   - Doesn’t verify logic functionality.
   - It is conservative in nature.

2. Types of timing paths:
    - Input to ouput
    - Input to Reg
    - Reg to Reg
    - Output to Reg
3.	Startpoint:  Usually input port or clock pin of flop/register.
4.	Endpoint:  Usually output port or register data pin.
5.	Hold Check:  It is time time required after the active transition of a clock so, the data has to be maintained at stable state.
6.	Setup Check:  It is time time required before the active transition of a clock so, the data has to be maintained at stable state.
7.	Slack time: The difference between the arrival time and the required time. For setup analysis, arrival time <= required time. For hold analysis,  arrival time >= required time.
8.	Constraints  required for timing: There are various constraints like clock constraints, power constraints, external constraints, environmental constraints, net delay constraints and design rule constraints.


## Lab:
•	Understanding of Open timer tool:  It is a Static Timing Analysis tool which is used to perform the timing checks like hold,  setup check and various other checks.
![20220204_222640](https://user-images.githubusercontent.com/98880516/152572709-95fced92-ec02-4042-9b17-8ec8074b369f.jpg)

•	Files required for STA: Design netlist, constraint file, and library file.
![20220204_223020](https://user-images.githubusercontent.com/98880516/152573059-79d1ef73-bff3-46e9-aafc-a989e89dfc89.jpg)

•	Opening the design file using leafpad command:  leafpad simple.v
In this, we find cells instantiations:

![20220204_223446](https://user-images.githubusercontent.com/98880516/152573255-c6d91514-e837-4547-a4ef-5e25745fb9aa.jpg)

•	Opening the library file using leafpad command:  leafpad osu018_stdcells.lib.
In this we find the cells information:

![20220204_223746](https://user-images.githubusercontent.com/98880516/152573536-afe35eca-83cf-434c-830c-26cc58decb05.jpg)

•	Opening the constraint  file using leafpad command:  leafpad simple.sdc
In this, we find various constraints:

![20220204_224041](https://user-images.githubusercontent.com/98880516/152573725-38c8352c-0a60-4daa-8a19-82afc5d615a8.jpg)

•	Opening the runscript using leafpad command: leafpad run.tcl
In this, we find all the commands to execute STA:

![20220204_224215](https://user-images.githubusercontent.com/98880516/152573994-9e796b04-093d-4421-88d8-e73356b2b9ae.jpg)

•	Command to run: ot-shell -i run.tcl -o opentimer.log

![Screenshot (985)](https://user-images.githubusercontent.com/98880516/152161941-d2cc4190-8049-42aa-bdf3-158f365bcbac.png)

![Screenshot (987)](https://user-images.githubusercontent.com/98880516/152633019-5af4cdce-4ca6-4e3d-93a5-ebf2d56886d8.png)

In above images, we can analyse the startpoint, endpoint, required time, data arrival time, slack, max/min analysis and whether the path is violated or not.

## Day 2:
- Apart from setup and hold checks, there are various other types of checks like clock gating checks, asynchronous pin checks and pulse width checks.
- Slew: It is the transistion from 0 to 1 or 1 to 0 from 70% to 30% or 30% to 70% respectively of the supply.
      - Rise Slew: It is the transistion from 1 to 0 from 30% to 70%
      - Fall Slew: It is the transistion from 0 to 1 from 70% to 30%
      
- Load Analysis depends upon min and max capacitance on ports and pins and fanout load on ports and output pins.
- Latch Based designs allow more flexibility in timing meaning that we can borrow timing from latch to meet the timing whether it will be setup or hold but this is not possible in case of flip flops.
- STA text report contains the lots of information in it.

## Lab:
- Understanding of Liberty(.lib) file. It contains the name of library, technology name, units and operating conditions.

![20220205_133151](https://user-images.githubusercontent.com/98880516/152677033-650ded35-bd1e-4a7b-9e1a-d07ff63e9a78.jpg)

![20220205_133204](https://user-images.githubusercontent.com/98880516/152677131-3ba3ec78-91ab-4154-9f1a-577a9e9dfa31.jpg)

- In liberty cell file name, there is cell name, power pin name, leakage power under various conditions, pin name and its direction, and pin capacitance.

- In this lab, we find early and late libraries file, we can open these file using "leafpad" command.

- By analysing the simple_Late.lib file, we can find there 211 cells in this.

![20220205_134609](https://user-images.githubusercontent.com/98880516/152677263-52c1ac33-c682-4a4a-80e6-b0d7b5069e74.jpg)

- In this simple_Late.lib file, we can find there are 3 pins of cell NAND2_X1.

![20220205_134929](https://user-images.githubusercontent.com/98880516/152677355-b70db870-77d4-47a8-8072-3d631e1e46b8.jpg)

![20220205_134957](https://user-images.githubusercontent.com/98880516/152677459-1c1cbabd-9773-46cd-849e-783fab44a6c1.jpg)

![20220205_135053](https://user-images.githubusercontent.com/98880516/152677548-4838da14-80e4-4719-9f73-a88f2e281b09.jpg)

- There are differences in cell_fall, fall_transition, cell_rise, and rise_transition values of a cell between the files simple_Late.lib and simple_Early.lib.

- We can parse the spef by the command  "read_spef" in open timer tool.

- Running ‘ot-shell –i run.tcl --log ot-shell.log’. 

![20220205_140716](https://user-images.githubusercontent.com/98880516/152677765-fe21f331-12e1-41d0-af17-3e5e7c2f17df.jpg)


![20220205_140156](https://user-images.githubusercontent.com/98880516/152677704-b9d67ae1-39f1-46f8-beb3-428e0f602d82.jpg)

In the above image, we can see loading libraries, loading netlist, loading sdc, loading spef and enable cppr analysis. Here "I" stands for information


- By doing report_timing command, we can do timing report on the design
- report_timing -num_paths 5 means we can do report timing on 5 paths.

- Running ‘ot-shell –i run.tcl –o out.txt’
- Open ‘leafpad out.txt’

![20220206_164625](https://user-images.githubusercontent.com/98880516/152677945-8dd52f62-6629-43bc-a61f-9e9b2af1ba58.jpg)

- We can increase the report timing paths by command: report_timing -num_paths 25.


# Day 3
- If there are multiple clocks in our design then we can do most restrictive setup and most restrictive hold analysis.
- There are generally four types of arcs:
      - Cell arc
      - Net arc
      - Sequential arc
      - Combinational arc
 - There are three types of timing sense:
      - Positive unate: If input is rising/falling then output must be rising/falling respectively.
      - Negative unate: If input is rising/falling then output must be falling/rising respectively.
      - Non unate: If input is rising/falling, then output can be falling or rising respectively.
 - Cell propagation delay is the difference between the input and output signal of 50% of its value.
 - Skew: Difference in arrival time of clocks.
 - Positive clock skew helps in setup check while negative clock skew helps in hold check.
 - Clock latency = source latency + newtork latency.
 - Clock jitter means uncertainity in clock.

# Lab:
- Run ‘ot-shell –i run.tcl –o out.txt’

![20220205_143057](https://user-images.githubusercontent.com/98880516/152678130-2dd8df6b-c37e-41a9-81bb-13e6a9e5889e.jpg)

- Type ‘leafpad out.txt’ the slack reported for the path is -212.323

![20220205_143123](https://user-images.githubusercontent.com/98880516/152678218-bbf17e19-80bf-466e-b61d-443b969ff35f.jpg)

- By seeing the above image, we can find, the slack reported for this path F1:CK→U3→U4→U6:A2→U7:A1→F2:D

- If we change the no. of reporting paths to 100 by command " report_timing -num_paths 100, then we can see there are different paths reported but not 100 since, in our design there are not 100 paths. 

![20220205_144028](https://user-images.githubusercontent.com/98880516/152678351-2f37fb77-efc6-4edc-9e37-7c596753ea77.jpg)

![20220205_144102](https://user-images.githubusercontent.com/98880516/152678494-09b7addc-8e91-4ec1-a206-65f940f7de1c.jpg)


# Day 4:
- Crosstalk: Noise caused by coupling of switching activity of the victim with switching activity of aggressors.
- A steady signal net can have a glitch due to charge transfered by switching.
- Global prcoess variation means the random and systematic variations which may occur in the chip. This chip may include On Chip Variation(OCV) effects.
- Clock gating checks are necessary to avoid the large power dissipation when clock is not in use in our design
- Asyn pin checks are necessary to avoid unknown state.

# Lab:
- In this goto lab6 by command "cd lab6", open the file using ‘leafpad run.tcl’ for clock gating check.

![20220205_145535](https://user-images.githubusercontent.com/98880516/152678701-6e419628-0ce7-4120-b7ed-490ffd3ba42c.jpg)

- In the above file, RAT can be identified using command ‘report_rat’ and AT can be identified using command ‘report_at’ and Slack can be identified using command ‘report_slack'.

- open the file using ‘leafpad run.tcl' from lab7 for async pin check.

![20220205_145921](https://user-images.githubusercontent.com/98880516/152678771-afe0c3da-e652-4662-9f59-791f0da946fc.jpg)

- In the above file, RAT can be identified using command ‘report_rat’ and AT can be identified using command ‘report_at’ and Slack can be identified using command ‘report_slack'.

# Day 5:
- In case of synchnonous clocks, events can happen at a fixed phase relation while in case of asynchnonous clocks, events can't happen at a fixed phase relation.
- There are various clock properties such as clock transition, clock uncertainity, clock latency, clock sense, and ideal network.
- We can specify various paths by using -through, -to and -from options. There are various types of paths like fallse paths, multicycle paths and many more.

# Lab:
- Goto the lab4 by doing "cd lab4".
- Run ‘ot-shell –i run.tcl –o out.txt’

![20220205_152244](https://user-images.githubusercontent.com/98880516/152678940-81c95f30-a9cf-4e38-a867-be9d84b495d5.jpg)

- Open the out.txt by command ‘leafpad out.txt’
![20220205_152047](https://user-images.githubusercontent.com/98880516/152678878-4b590c7f-14af-4c13-af3a-cb7d6075f87d.jpg)

- In the above image, we can find 6.585 is the CPPR.
-In Engineering Change order(ECO), we perform various analysis one by one for every check which we need to close but not closed till PnR stage. There are specialized signoff tools that help us to analyze the issue and also suggest the changes we need to do in order to close the issue. The suggested change is captured in an eco file.
- For ECO, goto lab5 by doing " cd lab5" and Open ‘run.tcl’

![20220205_152811](https://user-images.githubusercontent.com/98880516/152679045-7117fa19-e169-4b85-9679-6826d2b855ec.jpg)

- Run ‘ot-shell –I run.tcl –o out.txt’.

![20220205_152941](https://user-images.githubusercontent.com/98880516/152679098-65e0e2a6-96dd-4143-aaeb-efa97369cdf3.jpg)

We can see from the above image, slack has been increased now.



