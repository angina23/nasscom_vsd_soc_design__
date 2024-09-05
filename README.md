# Nasscom_vsd_soc_design__
### `DURATION : 21 AUGUST 2024 -3 SEPTEMBER 2024`
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9498c3a9-02f9-427c-a6d4-a4a554a6a4f6/d91631cb-a7dc-4ec6-8ae7-71b90e07b813/6b739dc0-3610-4cb4-a7a8-4d5d2ec54456.png)

**LEARNING  THROUGH LABWORK :** 

- Engaged in a two-week intensive workshop focused on the complete Physical Design process, from RTL to GDSII.
- Gained hands-on experience with Google-SkyWater 130nm technology using open-source tools like Yosys, Magic, and NGSpice.
- Developed and characterized standard cells, contributing to the generation of a GDSII file for System-on-Chip (SoC)
design.
- Did Post-Synthesis timing analysis with OpenSTA tool and made timing ECO fixes to remove all violations(setup and hold time violations).
- Cloned a custom inverter standard cell design and  run the openlane flow to verifiy that it is accepted in PnR flow.

DAY 1: Inception of open source EDA, openLANE and Sky130 PDK.
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
