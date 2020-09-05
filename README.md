# 10bit-potentiometric-DAC-3.3V-analog-voltage-1.8V-digital-voltage-and-1-off-chip-voltage-reference

This work is aimed at design of a 10bit potentiometric DAC with 3.3V analog output volatge and 1.8V digital inputs with a single external reference voltage source. The DAC is designed using multiple stages for better performance and less area requirements compared to a single stage DAC.

 The required design specifications can be found [here](https://github.com/neethujohny/avsddac_3v3/files/5164067/pdac_IP.pdf)

# Table of contents

* [Need for a potentiometric DAC(PDAC)](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#need-for-a-potentiometric-dacpdac-ip)

* [IP Block diagram and parameters](https://github.com/neethujohny/avsddac_3v3/blob/master/README.md#ip-block-diagram-and-parameters)

* [Design of 10bit PDAC](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#design-of-10bit-pdac)

  - [Stage 1 Circuit Diagram](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#stage-1-circuit-diagram---vh-vl-5-bitstage)
  - [Stage 2 Circuit Diagram](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#stage-2-circuit-diagram---vh-vl-3-bitstage)
  - [Stage 3 Circuit Diagram](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#stage-3-circuit-diagram---2-bit-dac)
  - [Subcircuit Diagram](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#subcircuit--switch_pair)
  - [Complete Schematic of 10bit PDAC](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#complete-schematic-of-10bit-pdac)
  - [10bit DAC Output and Input plot](https://github.com/neethujohny/avsddac_3v3#ngspice-output-plot-with-10bit-inputs)
  
 * [To obtain DNL vs Input code characteristics](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#to-obtain-dnl-vs-input-code-characteristics-t27c-and-vrefvdd33)
 
 * [To obtain INL vs Input code characteristics](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#to-obtain-inl-vs-input-code-characteristics-t27c-and-vrefvdd33)
 
 * [Open source EDA Tools used to develop the IP](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#open-source-eda-tools-used-to-develop-the-ip)
 
 * [Prelayout Simulations](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#prelayout-simulations)
 
 * [10bit PDAC Layout](https://github.com/neethujohny/avsddac_3v3#10bit-pdac-layout)
 
   - [Stage 1 Circuit Layout](https://github.com/neethujohny/avsddac_3v3#stage-1-circuit-layout)
   - [Stage 2 Circuit Layout](https://github.com/neethujohny/avsddac_3v3#stage-2-circuit-layout)
   - [Stage 3 Circuit Layout](https://github.com/neethujohny/avsddac_3v3#stage-3-circuit-layout)
   - [Subcircuit Layout](https://github.com/neethujohny/avsddac_3v3#subcircuit--switch_pair-layout)
   - [Complete Layout of 10bit PDAC](https://github.com/neethujohny/avsddac_3v3#complete-circuit-layout)
 
 * [Postlayout Simulations](https://github.com/neethujohny/avsddac_3v3#postlayout-simulations)
 
 * [Future Works](https://github.com/neethujohny/avsddac_3v3#future-work)
 
 * [Author](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#author)
 
 * [References](https://github.com/neethujohny/avsddac_3v3#references)
 
 * [Acknowledgements](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#acknowledgements)
 
 * [Contact Information](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#contact-information)
  
  

## Need for a potentiometric DAC(PDAC) 

Modern electronic systems dominate due to the evolution in digital technology. However the outside world remains analog in nature. DACs form an important link to connect between the digital systems to the analog world. 

Binary weighted DAC, R-2R DAC, current steering DAC, resister string DAC are some of the other DAC architectures used in various applications.

## IP Block Diagram and parameters

![IP Block](https://user-images.githubusercontent.com/65214115/92079653-e4c6a380-eddd-11ea-9ce1-d0cf2178a660.PNG)

### Terminal Functions

   |Name |	No.|	I/O |	Description   |
|------| ----|  -----|  -----------|
  |D[0:9]|1-10|I   |	Digital inputs |
  | EN  |	11 |	I|	Enable pin    |
  | VDD |	12 |	I|	Digital power supply(1.8)     |
  |VSS	|13  |   I	|Digital ground|
  |OUT	|14  |   O	|DAC analog voltage output|
  |VDDA	|1  |	I	|Analog voltage supply (3.3)|
  |VSSA	|16 |	I	|Analog ground   |
  |VREFH|17 |	I	|Reference voltage high for DAC|
  |VREFL|18 |	I	|Reference voltage low for DAC   |

### Parameters

  
  |Parameter | Description    | min      | typ     | max      | Unit     | Condition |
   | ------ | ---------- |  --- |  --- | --------- | ----------| -----  |
   |RL	|Load resistance|	50 |	|     |	Mohm     |	T=-40 to 85C  |
   |CL |	Load capacitance  |  |  | 1    |     pF	|T=-40 to 85C    |
   |VDDA|	Analog supply voltage  |	   |  3.3     |		 | V	    | T=-40 to 85C  |
   |VDD|	Digital supply voltage        |	    |	1.8  |	   |	V|	T=-40 to 85C |
   |VREFH|	Reference Voltage high   |	   |	 |3.3 |	V   |	T=-40 to 85C|
   |VREFL|Reference Voltage low	   |0	      |          |    |  V  |	T=-40 to 85C     |
   |RES |	Resolution    |		 | 10       |		    |bits|	On all above condition for "typ" (T=27C)       |
   |INL |	Integral non-linearity   |		 | -2.0 to +2.654      |		    |LSB |	On all above condition for "typ" (T=27C)  |
   |DNL	|Differential non-linearity      |	   |-1.0 to +1.7    |	    |LSB	    |On all above condition for "typ" (T=27C)  |
   |TCONV|	Conversion time    |	9.99|		||us  |	T=27C    |
   |IDDA|	Analog supply current    |    |100    |	      |	mA       | T=27C, Data change=16K samples/sec  |
   |IDD|	Digital supply current 	 |    |114.25    |    |   mA|   T=27C, Data change=16K samples/sec|


## Design of 10bit PDAC

The 10bit DAC is designed in three stages to save area and reduce the runtime. The prelayout and postlayout simulations ran within 3 minutes. It requires a total of 44 resistors and 79 switch pairs.
   - The development of an area-efficient multiple-output voltage selector starts from a 5-b tree-type two-voltage selector. This circuit requires two sets of 5-b tree-type          decoders, arranged with a 1-b offset, in order to select two adjacent voltages from a resistor string. 
     -  One set outputs VH and the other set outputs VL. A total of 124 switches are required. The two-voltage selector chooses two adjacent voltages from the reference                 voltages of a global resistor string according to the higher digital bits (MSB bits b9 to b5) and connects them to the succeeding DAC stages. 
   - The second stage is again a 3-b tree-type two-voltage selector which outputs VH and VL based on subsequent LSB bits from b4 to b2. 
   - The third stage ia a 2 bit DAC which subsequently divides the voltage between these two voltage levels based on lower 2 digital bits b1 and b0.

 
    Note: The accuracy of the conversion can be improved by adjusting the number of stages and granularity of the various stages. 


### 1. Stage 1 Circuit Diagram - VH VL 5-bitstage

The circuit is an extended version of stage 2 circuit with 5-bit selector switches. It is created using the subcircuits of stage 2 circuit and switch pair circuit.


![final stage1_ckt](https://user-images.githubusercontent.com/65214115/92308156-43944480-efb9-11ea-9ad6-6920324d6030.PNG)


### 2. Stage 2 Circuit Diagram - VH VL 3-bitstage


![stage2](https://user-images.githubusercontent.com/65214115/92308157-468f3500-efb9-11ea-9f2a-0dfc19364d89.PNG)


### 3. Stage 3 Circuit Diagram - 2 bit DAC


![stage3](https://user-images.githubusercontent.com/65214115/92308161-4a22bc00-efb9-11ea-90f7-f16d2270c83e.PNG)


### 4. Subcircuit- Switch_pair


![switch](https://user-images.githubusercontent.com/65214115/92308164-4c851600-efb9-11ea-8279-08636e57fcab.PNG)


### 5. Complete Schematic of 10bit PDAC


![completeckt](https://user-images.githubusercontent.com/65214115/92308153-3e36fa00-efb9-11ea-8251-40b920d6af9a.PNG)


The complete circuit diagram can be downloaded using this link [10bitDAC_Circuit.pdf](https://user-images.githubusercontent.com/65214115/92308153-3e36fa00-efb9-11ea-8251-40b920d6af9a.PNG)

Note- While integrating the different stages, the resistance values have been changed appropriately.


### 10bit DAC Output and Inputs plot


![dac_output margin based](https://user-images.githubusercontent.com/65214115/90310313-14386d80-df0e-11ea-9c24-7aa74c3a0dba.PNG)



## To obtain DNL vs Input code characteristics @T=27C and VREF&VDD=3.3V

The differential nonlinearity (DNL) is the difference between the measured and ideal 1LSB amplitude change of any two adjacent codes. Using the values noted earlier and the formula given below, we can find all the DNL values. These vaues are uploaded in the repository with the name DNL_INL_calculations.

DNL(LSB)= (Actual height- Ideal height)/1LSB


## 1.  Pre-layout DNL characteristics

![DNL_prelayout](https://user-images.githubusercontent.com/65214115/92308969-029f2e80-efbf-11ea-95e5-478443eb0bb1.PNG)


## 2. Post-layout DNL characteristics

![DNL_postlayout](https://user-images.githubusercontent.com/65214115/92308966-00d56b00-efbf-11ea-9991-d18aa68c7cfc.PNG)


## To obtain INL vs Input code characteristics @T=27C and VREF&VDD=3.3V

The relative accuracy or integral nonlinearity (INL) is the maximum deviation of the output from the line between zero and full scale excluding the effects of zero code and full-scale errors. The calculated INL values are uploaded in the repository in the file with the name DNL_INL_calculations.

INL(LSB)= (Actual Vout-Reference Vout)/1LSB


## 1.  Pre-layout INL characteristics

![INL_prelayout](https://user-images.githubusercontent.com/65214115/92308973-05018880-efbf-11ea-9d18-0557441d6ffd.PNG)


## 2. Post-layout INL characteristics

![INL_postlayout](https://user-images.githubusercontent.com/65214115/92308972-03d05b80-efbf-11ea-8356-8a11c59c4796.PNG)



## DNL and INL Table

|Parameter | Pre-layout   | Post-layout   |
| -------  | ------------ | ----      |
|DNL(LSB)      |-1.0  to  +1.7    | -0.247  to  +1.44 |
|INL	(LSB)     | -2.0  to  +2.654 |  -0.921  to  +2.374|



## To obtain Output Voltage vs Input code characteristics @T=27C and VREF&VDD=3.3V

The obtained ouptput values are tabulated and given in the folder 'caluclations and plots' and can be plotted using excel or SciDAVis plotting software.


## 1.  Pre-layout Output characteristics

![vout_prelayout](https://user-images.githubusercontent.com/65214115/92308977-07fc7900-efbf-11ea-8235-ea4561e2a0cc.PNG)


Note- The input code ranges from 0 to 1023. The Full Scale output voltage, VFS =3.292069V


## 2.  Post-layout Output characteristics

![Vout_postlayout](https://user-images.githubusercontent.com/65214115/92308976-06cb4c00-efbf-11ea-8db4-e2189e4871db.PNG)



## Open source EDA Tools used to develop the IP

The design is done using opensource EDA tools such as eSim for the prelayout simulatioms and MAGIC for the layout and postlayout simulations. eSim is a free and open source EDA tool for circuit design, simulation, analysis and PCB design. It is an integrated tool built using open source software such as KiCad, Ngspice and GHDL. Magic is an opensource VLSI layout tool.

### 1.  Steps to Install eSim on Ubuntu 16.04

* Go to the link https://github.com/FOSSEE/eSim/releases/tag/v1.1.3 and download eSim-1.1.3 for Ubuntu.

* After downloading eSim, extract it using: 
  
      $ unzip eSim-1.1.3.zip

* Now change directories in to the top-level source directory (where this INSTALL file can be found).

   To install eSim and other dependecies run the following command.

      $ ./install-eSim.sh --install

   Above script will install eSim along with dependencies.
   
* To Run eSim

  Double click eSim desktop icon. To open through terminal, use the command
           
       $ esim
  
 ##### eSim Spoken Tutorials
 
  Refer `Spoken Tutorial` (https://spoken-tutorial.org/tutorial-search/?search_foss=eSim) for eSim installation on Linux and MS Windows.
  

### 2. Steps to Install Magic 8.1 on Ubuntu 16.04

* Download the https://drive.google.com/file/d/1F0y1xuYWIgeYEpzKnGlaCQH3urdSFc4E/view file

* Copy paste the below commands one after another

    
      $ cd Downloads/
    
      $ chmod +x magic.sh
  
      $ ./magic.sh
  

* Magic tool will be opened with minimum technology file by default. Follow below steps to open magic with osu180nm tech file.

* Download the SCN6M_SUBM.10.tech from the uploaded files. Copy and paste the entire content in Text Editor and save it as osu180nm.tech.

* Open the Terminal and copy, paste the commands mentioned below.

      $ sudo cp osu180nm.tech /usr/local/lib/magic/sys/

      $ cd /usr/local/lib/magic/sys/

      $ ls 

      $ cd

      $ clear

You have successfully added osu180nm.tech file!

Just open the terminal and type magic -T osu180nm.tech filename.mag to begin layout.

## Prelayout Simulations

* To clone the Repository and download the Netlist files for Simulation, enter the following commands in your terminal.

      $ sudo apt install -y git

      $ git clone https://https://github.com/neethujohny/avsddac_3v3

      $ cd avsddac_3v3/Prelayout_Netlist

* To run the Transient Analysis , enter the following command

      $ ngspice Vh_Vl_cascaded.cir.out

      $ plot out_10bitdac


#### Output of 10bit PDAC - Transient Analysis Prelayout

![10bit_dac_output](https://user-images.githubusercontent.com/65214115/89987830-4c387a00-dc9c-11ea-9722-3f6dcdaf27c3.PNG)


# 10bit PDAC Layout


## 1. Stage 1 Circuit Layout


![5bitstage](https://user-images.githubusercontent.com/65214115/92036288-9c7f9500-ed8d-11ea-8b5f-3b023897a42d.PNG)


## 2. Stage 2 Circuit Layout


![3bitstage_layout](https://user-images.githubusercontent.com/65214115/92035192-fb440f00-ed8b-11ea-8782-30c39654c919.PNG)


## 3. Stage 3 Circuit Layout

![2bitstage_layout](https://user-images.githubusercontent.com/65214115/92035187-fa12e200-ed8b-11ea-8e99-dbe0d8ec6da7.PNG)


## 4. Subcircuit- Switch_pair Layout


![switch](https://user-images.githubusercontent.com/65214115/92036291-9db0c200-ed8d-11ea-8908-7ad8a319deef.PNG)


## 5. Complete Circuit Layout

![10bitdac_layout](https://user-images.githubusercontent.com/65214115/92035196-fb440f00-ed8b-11ea-9a2f-a67dca694a7d.PNG)


## Postlayout Simulations

* To clone the Repository and download the Netlist files for Simulation, enter the following commands in your terminal.

      $ sudo apt install -y git

      $ git clone https://https://github.com/neethujohny/avsddac_3v3

      $ cd avsddac_3v3/PostLayout_magic and spice files

* To run the Transient Analysis , enter the following command

      $ ngspice 10bit_dac.spice


## Output of 10bit PDAC - Post Layout

![10bitdac_out](https://user-images.githubusercontent.com/65214115/92032729-37757080-ed88-11ea-9a77-d384cd36dbbf.PNG)


Note: For the stage wise simulation outputs, please refer post layout simulation file uploaded above.

## Future Works

  - Build a more compact layout to meet the area specifications.
  - Improve the DNL and INL by increasing the resolution of different stages.
  - Improve the conversion rate to meet the specification.
  - Modify the design (Resistor chain) to meet the power consumption requirements.
  - Build the layout of a capacitor (the necessary layers are not included in the osu). In this project the capacitor is manually added in the extracted netlist.
  
  
## Author

Neethu Johny, Research Scholar, B.M.S College of Engineering, Bangalore

## References

1. https://patents.google.com/patent/US6249239
2. Chih-Wen Lu, Member, IEEE, Ching-Min Hsiao, and Ping-Yeh Yin, A 10-b Two-Stage DAC with an Area-Efficient Multiple-Output Voltage Selector and a Linearity-Enhanced DAC-     Embedded Op-Amp for LCD Column Driver ICs, IEEE JOURNAL OF SOLID-STATE CIRCUITS, VOL. 48, NO. 6, JUNE 2013
3. Yoo-Chang Sung, Oh-Kyong Kwon,Jong-Kee Kim ,10-bit source driver with resistor-resistor-string digital-to-analog converter,Journal of the SID 14/4, 2006 
4. https://github.com/ankursah5/avsdbgp_3v3
5. https://github.com/VSD-DACteam/avsddac_3v3
6. https://github.com/FOSSEE/eSim
7. http://opencircuitdesign.com/magic


## Acknowledgements

Kunal Ghosh, Director, VSD Corp. Pvt. Ltd.

Philipp Gühring, Software Architect, LibreSilicon Assocation

FOSSEE Team, IIT Bombay

R. Timothy Edwards, Open Circuit Design


## Contact Information

Neethu Johny, B.M.S College of Engineering, Bangalore - neethujohny123@gmail.com

Kunal Ghosh, Director, VSD Corp. Pvt. Ltd. - kunalghosh@gmail.com

Philipp Gühring, Software Architect, LibreSilicon Assocation - pg@futureware.at
