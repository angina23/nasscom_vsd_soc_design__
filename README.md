![image](https://github.com/user-attachments/assets/3ead1197-87fd-4021-97c2-afe5fe01a041)# Nasscom_vsd_soc_design__
### `DURATION : 21 AUGUST 2024 -3 SEPTEMBER 2024`
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9498c3a9-02f9-427c-a6d4-a4a554a6a4f6/d91631cb-a7dc-4ec6-8ae7-71b90e07b813/6b739dc0-3610-4cb4-a7a8-4d5d2ec54456.png)

**LEARNING  THROUGH LABWORK :** 

- Engaged in a two-week intensive workshop focused on the complete Physical Design process, from RTL to GDSII.
- Gained hands-on experience with Google-SkyWater 130nm technology using open-source tools like Yosys, Magic, and NGSpice.
- Developed and characterized standard cells, contributing to the generation of a GDSII file for System-on-Chip (SoC)
design.
- Did Post-Synthesis timing analysis with OpenSTA tool and made timing ECO fixes to remove all violations(setup and hold time violations).
- Cloned a custom inverter standard cell design and  run the openlane flow to verifiy that it is accepted in PnR flow.

### **DAY 1: Inception of open source EDA, openLANE and Sky130 PDK.**
### **STARTING WITH OPENLANE**

```c
//Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

//we can invoke the OpenLANE flow docker sub-system by just running this command
docker

// After entering the OpenLANE flow, we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

// Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

// Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

// Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

// To exit from OpenLANE flow
exit

```

### **Screenshots of running each commands**
![image](https://github.com/user-attachments/assets/e8ecd05e-e36c-4fdb-ac71-b00b53db9e40)
![image](https://github.com/user-attachments/assets/f2c717f1-e15d-484c-95bb-f41ae356103d)
![image](https://github.com/user-attachments/assets/7a856080-e73c-45c5-b865-4a82954d72fb)
![image](https://github.com/user-attachments/assets/621a2d35-01e8-418f-bdb7-50115772e251)
![image](https://github.com/user-attachments/assets/50cc484d-b4a7-420d-bd8d-d02b12c157d1)
TO CHECK THE synthesized netlist
![image](https://github.com/user-attachments/assets/714ab350-d052-45aa-b24d-1770c14a08fb)
## **To calculate the flop ratio**

FLOP RATIO  = NO. OF D FLIP FLOP/ TOTAL NUMBER OF CELLS

$$
FLOP ratio  = 1613/14876 *100 =10.84
$$

![image](https://github.com/user-attachments/assets/4f88cd13-3947-45ca-ab3a-043ccca4b06d)
To check the timing and other reports

![image](https://github.com/user-attachments/assets/5227d3b4-91a3-4294-ae5e-c1b5b9f61d97)


# **DAY 2:Good floorplan vs Bad floorplan and introduction to library cells.**

## **Chip Floor planning considerations.**

Steps to run floor plan using openLane

```c
//Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

//we can invoke the OpenLANE flow docker sub-system by just running this command
docker

// After entering the OpenLANE flow, we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

// Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

// Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

// Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

// To exit from OpenLANE flow
exit

```

In this we see the different TCL files and one read me file in  configuration  folder.
![image](https://github.com/user-attachments/assets/12c76982-0869-444b-82f3-d726eb8db832)
After opening READ.me file we see global variables and similarly in floorplan we see  whole set of switches.
![image](https://github.com/user-attachments/assets/0f9ffc1c-de4c-4cba-b01f-16d01e95182e)
![image](https://github.com/user-attachments/assets/67fb8f2c-17eb-4cf1-adb7-6af55cfc48c7)
![image](https://github.com/user-attachments/assets/ea99590a-9380-45dc-ac3f-1b03d1edaf24)
![image](https://github.com/user-attachments/assets/8f6d68c9-dde7-4578-a667-d102203c0090)
After opening the floorplan.tcl file we see the default parameters set for the floorplan

![image](https://github.com/user-attachments/assets/eda9fede-260f-41d6-b857-fd8c4c222dc0)
After opening the details in the config.tcl file.
![image](https://github.com/user-attachments/assets/869ef60a-1af0-486d-ad3d-22e3644296aa)
```c
//To run floorplan give the following command
run_floorplan

```
![image](https://github.com/user-attachments/assets/271bb172-6564-43d2-92a3-ae4b9a99dad1)
After running commands 
```c
// In directory /Desktop/work/tools/openlane_working_dir/designs/picorv32a/runs/28-08_16-10/results/floorplan$
  less picorv32a.floorplan.def
```
![image](https://github.com/user-attachments/assets/555cdf9d-6cc4-493c-ada2-95fd4a480bfe)
**This shows the dimension of the die area where (0 0)(for the lower left corner) and (660685 , 671405)(for the right up corner).**

**Also 1 um is equal to 1000 database units and thus these units should be divided by 1000 to get dimension in um.**
![image](https://github.com/user-attachments/assets/27a833a3-7c21-4f7a-8b6a-483df272d739)

$$
Die width = 660685 , Die height = 671405
$$

$$
Die width(um) = 660685/1000 = 660.685 um
$$

$$
Die height(um) = 671405/1000 = 671.405 um
$$

$$
AREA OF DIE  = 660.685*671.405 = 443587.21 um^2
$$

```c
// For placement run
run_placement 
```
![image](https://github.com/user-attachments/assets/89e0196a-1803-4de9-baf2-4c8daaeb45a3)
```c
// Change directory to path containing generated floorplan def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-08_12-26/results/floorplan/

//To load the floorplan in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![image](https://github.com/user-attachments/assets/bfcf2bdb-b12d-4914-b1cb-23943bdf2e21)
As the pin mode was set =1 , meaning the pins are equidistant.  This also shows the decap cells and tap cells.
![image](https://github.com/user-attachments/assets/40021525-c704-4d8b-96bd-e3f503b3a14a)
This shows the information of the pin like this pin is in metal layer 3.
![image](https://github.com/user-attachments/assets/d025fddc-fde6-44b3-bbc6-822bbb184065)
Similarly this shows the pin is in metal layer 2.
![image](https://github.com/user-attachments/assets/0c10af5c-f3ca-4b3c-ba6e-9a47ad98f970)
Standard cell at the origin
![image](https://github.com/user-attachments/assets/42fd9efd-d03e-4e49-ae6c-2bef0ab01d8a)

```c
// Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-08_12-26/results/placement/

//To load the floorplan in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
![image](https://github.com/user-attachments/assets/04afbbfa-399c-4c39-872f-459c1e83582d)
The floorplan in magic window shows the standard cells placed in the standard cell rows.
![image](https://github.com/user-attachments/assets/6654a35f-945d-474d-8f7b-7689740672cf)
![image](https://github.com/user-attachments/assets/c0c9cc0a-d394-454f-b28a-44d093c06dd3)



# **DAY 3_Design library cell using magic layout,ngspice characterisation and CMOS fabrication.**

**To make a change in openlane flow a variable is reset(in this case the IO pin placement) and the flow is run again. Here  is the values in the floorplan.tcl file in the configuration directory.**
![image](https://github.com/user-attachments/assets/db77cec3-bab6-4fa7-b5d0-e15882abf8af)
```c
// Run the commands
set ::env(FP_IO_MODE) 2    
run_floorplan
```

**The IO pin placement is changed and can be seen in the floorplan of the magic window.**

```c
 // Change directory to path containing generated floorplan def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-08_12-26/results/floorplan/

//To load the floorplan in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```
![image](https://github.com/user-attachments/assets/30f27d45-4c93-428e-8c50-14dd87940de2)
![image](https://github.com/user-attachments/assets/f33f218d-c0f6-444c-8b33-a10f1e348964)
Cloning a github repository in openlane. using the command:

```c
//Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

// Clone the repository with custom inverter design
git clone https://github.com/nickson-jose/vsdstdcelldesign

// Change into repository directory
cd vsdstdcelldesign
```
![image](https://github.com/user-attachments/assets/adb2b3d2-b169-41a2-839a-539b01762843)
**Copied the file [sky130A.tech](http://sky130A.tech) into vsdstdcell design folder using the command:**

```c

// Copy magic tech file to the repo directory 
cp [sky130A.tech](http://sky130A.tech) /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign/

// Check contents whether everything is present
ls
```
![image](https://github.com/user-attachments/assets/492f7716-b51b-46f3-a6a3-0a5bcc55d33d)
```c
// Command to load custom inverter layout in magic  in vsdstdcelldeisgn directory:
magic -T sky130A.tech sky130_inv.mag &
```
![image](https://github.com/user-attachments/assets/27ca7c5b-f2f0-48ff-93c6-9569b8a481a7)
Checking for PMOS
![image](https://github.com/user-attachments/assets/cbc78b0b-9bf9-4ac1-9c7a-15f7c19b7331)
Checking for NMOS
![image](https://github.com/user-attachments/assets/6651a3d1-9e29-4cd0-aedc-b3f1c38768b7)
![image](https://github.com/user-attachments/assets/1d06a3c3-d06d-4e80-b378-6af77408d2d4)
**To extract the inverter on SPICE, the following commands were given in tckon .**
```c
// Extraction command to extract to .ext format
extract all

// Before converting ext to spice this command enable the parasitic extraction also
ext2spice cthresh 0 rthresh 0

// Converting to ext to spice
ext2spice
```

 **A spice file of inverter has been created in vdsstscelldesign directory.**
![image](https://github.com/user-attachments/assets/3890577c-3bff-43f4-b153-4484bd1e1371)
```c
#To open the spice file 
vim sky130_inv.spice
```

**A spice file has been generated. Here  for PMOS: Y(drain)  A(gate) VPWR(source)VPWR(substrate).**

**Similarly  for NMOS: Y(drain)  A(gate) VGND(source)VGND(substrate)**
![image](https://github.com/user-attachments/assets/3fe4dcb7-16d1-4a72-aff2-ddcdf9a0069e)
**Size of the minimum value of the layout is the found by the minimum grid size. So here is the dimension of the box( 0.010 X0.010 )microns .**
 ![image](https://github.com/user-attachments/assets/3d5df735-70de-4ba5-b1d3-584137713522)
Model file of PMOS inside libs folder which shows the name of the model file and also all the parameters of PMOS.
![image](https://github.com/user-attachments/assets/f06d5ab7-b2ef-4d4f-b3de-d36903acc7c8)
**Model file of NMOS inside libs folder which shows the name of the model file and also all the parameters of NMOS.**
![image](https://github.com/user-attachments/assets/eec55cff-5597-4097-aae7-4c746426a747)
**The SPICE file contains the control inputs VDD, VSS ,Va where pulse info format is (low value, high value, starting point, rise time, fall time, on time, time period).**

**the .trans is for the transient analysis.**  

```c
 
 // at the end of the spice file after Esc(to exit from insert mode)
:wq!

```
![image](https://github.com/user-attachments/assets/c1378eac-45ca-4f3e-b3a1-1799eda02ccb)
The sky130_inv.spice  file is opened in ngspice.
![image](https://github.com/user-attachments/assets/59e29034-36d4-40b4-8fdb-93f9929420fd)
```c
// Command to directly load spice file for simulation to ngspice
ngspice sky130_inv.spice

// Now to load the plot
plot y vs time a

```
![image](https://github.com/user-attachments/assets/72e44fcc-8a48-4bff-91c0-e712b024c899)
After changing the value of  C3 from 0.024 fF to 2fF.
![image](https://github.com/user-attachments/assets/1d511915-a374-4b1e-82ae-674b6b030c5a)
### **Finding TIMING characteristics. We need to find:**

- Rise transition time = output_rise(80%) - output_rise(20%)
- Fall transition time = output_fall(20%) - output_fall(80%)
- Rise cell delay  = output_rise(50%) - input_fall(50%)
- Fall cell delay =  output_fall(50%) - input_rise(50%)

Maximum voltage = 3.3V

80% of maximum voltage = 2.64V

20% of maximum voltage = 0.66V

50%of maximum voltage = 1.65V

**OUTPUT SIGNAL = y**

**INPUT SIGNAL = a**

1. **Rise transition time**
![image](https://github.com/user-attachments/assets/8784ec51-e661-43f2-ac3b-4567fc0c2d80)
![image](https://github.com/user-attachments/assets/528f7b6c-5305-48b8-81bd-99268496cdda)
Rise transition time = output_rise(80%) - output_rise(20%)
![image](https://github.com/user-attachments/assets/83479e7f-10fb-4268-9876-461171d90245)
<aside>
💡 **Rise transition time = 0.0641 ns**

</aside>

1. **Fall transition time**
![image](https://github.com/user-attachments/assets/e2dca38c-aa65-4b3c-9ee7-0ede1332428e)
![image](https://github.com/user-attachments/assets/422fb3e7-2ca3-4749-b231-fe154ba9c6f5)
- Fall transition time = output_fall(20%) - output_fall(80%)
- ![image](https://github.com/user-attachments/assets/e0b9db9b-3c29-48a3-8078-51408948853b)
<aside>
💡 Fall transition time = 0.042ns

</aside>

1. **Rise cell delay**
![image](https://github.com/user-attachments/assets/4909b359-6a25-43cc-aae8-751e1d39ee39)
Rise cell delay  = output_rise(50%) - input_fall(50%)
![image](https://github.com/user-attachments/assets/1e64ea6f-c120-4c5d-8b70-d93dc7133678)
<aside>
💡 Rise cell delay  = 0.0615ns

</aside>

1. **Fall cell delay**
![image](https://github.com/user-attachments/assets/251402d1-9f14-4115-9386-43665ac06f77)
Fall cell delay =  output_fall(50%) - input_rise(50%)
![image](https://github.com/user-attachments/assets/c6125bed-f20d-478c-b98c-0c9f822dcb06)
<aside>
💡 Fall cell delay  = 0.028ns

</aside>

Commands to download and view the corrupted skywater process magic tech file and associated files to perform drc corrections

```c
// Change to home directory
cd

// Command to download the lab files
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

// Since lab file is compressed command to extract it
tar xfz drc_tests.tgz

// Change directory into the lab folder
cd drc_tests

// List all files and directories present in the current directory
ls -al

//Command to view .magicrc file
gvim .magicrc

// Command to open magic tool in better graphics
magic -d XR &
```

Link to Sky130 Periphery rules: https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html
![image](https://github.com/user-attachments/assets/7dcbbe86-76db-4e69-8001-ae9158c805c9)
![image](https://github.com/user-attachments/assets/e73fa622-e187-4b54-80a9-28a36d0b75c8)
![image](https://github.com/user-attachments/assets/1a91ef29-1029-4dc8-ae45-595a9220026e)
![image](https://github.com/user-attachments/assets/c04ebfcd-fd4d-41b7-b66a-6022375660d8)
![image](https://github.com/user-attachments/assets/37c5e8a1-20e0-48ec-a58a-b3d9db6b7bbd)
![image](https://github.com/user-attachments/assets/569d88d6-0872-4b64-93fc-08370a05a3b7)
![image](https://github.com/user-attachments/assets/07734fc2-3c88-4175-a841-07ee85b05973)
![image](https://github.com/user-attachments/assets/2f0b1b94-1698-458e-9a0e-d2d76e3fdde9)
![image](https://github.com/user-attachments/assets/ca0239f7-0c20-43cf-9298-4beb5e3286fc)
![image](https://github.com/user-attachments/assets/5e1a0df9-feef-4803-a1fe-8ab47e99a442)
![image](https://github.com/user-attachments/assets/b8c7589c-5c3a-4fc1-adfc-cbea31a95d9d)
```c
 // To open sky130A.tech file
 vi [sky130A.tech](http://sky130A.tech) file
```
![image](https://github.com/user-attachments/assets/2a57f57a-da50-4847-99b4-59c9e6269b1f)
New commands inserted in sky130A.tech file to update drc
![image](https://github.com/user-attachments/assets/d366f522-2c14-479e-8a8f-058806e4b214)
![image](https://github.com/user-attachments/assets/03c49def-a5e2-459d-9b16-fe1a135046e6)
![image](https://github.com/user-attachments/assets/10d27032-7aa8-4465-a86a-af7cada88bef)
![image](https://github.com/user-attachments/assets/6841d9ae-01ec-4eda-a679-26358630e7bb)
![image](https://github.com/user-attachments/assets/2bf3ccc7-6cf2-4aa6-bf41-4cac1d316af6)
![image](https://github.com/user-attachments/assets/836a141e-564a-4f24-84ce-f7f536efc8ec)
![image](https://github.com/user-attachments/assets/6fd9e4c7-431c-458d-9843-376ea9a53cd6)
![image](https://github.com/user-attachments/assets/4002198d-ffa1-44dc-88c8-13efa90ea9ed)
![image](https://github.com/user-attachments/assets/17390904-fc51-47e8-aba9-d0e82b9b5f37)
![image](https://github.com/user-attachments/assets/b5b00db9-1a8b-4305-ac01-62323a8c1448)
New commands inserted in sky130A.tech file to update drc
![image](https://github.com/user-attachments/assets/2c1d8c6b-4cf4-4a9a-9cd4-463a829a06c8)
![image](https://github.com/user-attachments/assets/09b3b25b-e70e-40bf-810c-94737029a4ad)
![image](https://github.com/user-attachments/assets/aaab06b7-c35b-47f1-90f9-9eb1d0a2e943)
