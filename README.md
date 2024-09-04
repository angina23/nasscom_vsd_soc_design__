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

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9498c3a9-02f9-427c-a6d4-a4a554a6a4f6/3f232372-f9b9-4900-9c2b-02c95a22f2ee/Untitled.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9498c3a9-02f9-427c-a6d4-a4a554a6a4f6/ca339fc7-a5cf-4cfc-ae9b-dd8172f01c71/Untitled.png)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9498c3a9-02f9-427c-a6d4-a4a554a6a4f6/126423ef-4182-489b-a885-ffed9ffdb2d4/image.png)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/9498c3a9-02f9-427c-a6d4-a4a554a6a4f6/7234e31c-2bd7-4e13-a386-3184e95805db/image.png)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9498c3a9-02f9-427c-a6d4-a4a554a6a4f6/73c7459d-2725-46f7-9c70-210d380fd2e0/Untitled.png)

### **TO CHECK THE synthesized netlist**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9498c3a9-02f9-427c-a6d4-a4a554a6a4f6/313092b0-97f9-45b5-b85a-698f40b14786/Untitled.png)

## **To calculate the flop ratio**

FLOP RATIO  = NO. OF D FLIP FLOP/ TOTAL NUMBER OF CELLS

$$
FLOP ratio  = 1613/14876 *100 =10.84
$$

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9498c3a9-02f9-427c-a6d4-a4a554a6a4f6/a488e043-7e14-4d43-b126-237b5801a703/Untitled.png)

### **To check the timing and other reports**

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/9498c3a9-02f9-427c-a6d4-a4a554a6a4f6/5ae79a2b-d4c6-4059-9237-ab3d82e781ce/Untitled.png)
