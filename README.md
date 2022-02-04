
# Static Timing Analysis(STA) Workshop: Basics to Advanced
**Motivation to attend workshop **:  As we are seeing that the semiconductor industries are growing at a very faster rate. After some years later, it is going to be a boom of semiconductor industries. In VLSI, there are generally two types of domain namely front-end and back-end.
Front-end involves marketing Analysis, Design Entry, Simulation, Verification, Synthesis and Pre-layout STA.
Back-end involves Floorplanning, Place & Route, Post-layout STA and Signoff.
As we know that how much timing plays a very important role in meeting the design in Static Timing Analysis(STA). So, STA plays a vital role in the ASIC flow. It involves lots of things to learn and understand in STA which motivates me to attend this workshop.

ASIC Design Flow:
<img width="397" alt="bg1a" src="https://user-images.githubusercontent.com/98880516/152572049-4d8c543b-504f-44e8-86fc-6d9f647c8dd0.png">

**Day 1**
•	What is Static Timing Analysis:  Static Timing Analysis is a method of verifying timing performance of the design.
•	Features of STA :
	It is static in nature.
	It is exhaustive.
	Doesn’t verify logic functionality.
	It is conservative in nature.

•	Types of timing paths:

	Input to ouput
	Input to Reg
	Reg to Reg
	Output to Reg
•	Startpoint:  Usually input port or clock pin of flop/register.
•	Endpoint:  Usually output port or register data pin.
•	Hold Check:  It is time time required after the active transition of a clock so, the data has to be maintained at stable state.
•	Setup Check:  It is time time required before the active transition of a clock so, the data has to be maintained at stable state.
•	Slack time: The difference between the arrival time and the required time. For setup analysis, arrival time <= required time. For hold analysis,  arrival time >= required time.
•	Constraints  required for timing: 


**Lab1:**
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
