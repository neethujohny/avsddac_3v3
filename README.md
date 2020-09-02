# 10bit-potentiometric-DAC-3.3V-analog-voltage-1.8V-digital-voltage-and-1-off-chip-voltage-reference

This work is aimed at design of a 10bit potentiometric DAC with 3.3V analog output volatge and 1.8V digital inputs with a single external reference voltage source. The DAC is designed using multiple stages for better performance and less area requirements compared to a single stage DAC.

  ![block diagram](https://user-images.githubusercontent.com/65214115/92021510-836be980-ed77-11ea-8246-8c1da8a081be.PNG)

The required design specifications can be found here [pdac_IP.pdf](https://github.com/neethujohny/avsddac_3v3/files/5164067/pdac_IP.pdf)

# Table of contents

* [Need for a potentiometric DAC(PDAC) IP](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#need-for-a-potentiometric-dacpdac-ip)

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
 
 * [Author](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#author)
 
 * [Acknowledgements](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#acknowledgements)
 
 * [Contact Information](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#contact-information)
  
  

## Need for a potentiometric DAC(PDAC) IP

Modern electronic systems dominate due to the evolution in digital technology. However the outside world remains analog in nature. DACs form an important link to connect between the digital systems to the analog world. Binary weighted DAC, R-2R DAC, current steering DAC, resister string DAC are some of the other DAC architectures used in various applications.


### Design of 10bit PDAC

The 10bit DAC is designed in three stages to save area and reduce the runtime. 
   - The development of an area-efficient multiple-output voltage selector starts from a 5-b tree-type two-voltage selector. This circuit requires two sets of 5-b tree-type          decoders, arranged with a 1-b offset, in order to select two adjacent voltages from a resistor string. 
     -  One set outputs VH and the other set outputs VL. A total of 124 switches are required. The two-voltage selector chooses two adjacent voltages from the reference                 voltages of a global resistor string according to the higher digital bits (MSB bits b9 to b5) and connects them to the succeeding DAC stages. 
   - The second stage is again a 3-b tree-type two-voltage selector which outputs VH and VL based on subsequent LSB bits from b4 to b2. 
   - The third stage ia a 2 bit DAC which subsequently divides the voltage between these two voltage levels based on lower 2 digital bits b1 and b0.

 
         Note: The accuracy of the conversion can be still improved by adjusting the number of stages and granularity of the various stages. 


#### Stage 1 Circuit Diagram - VH VL 5-bitstage

The circuit is an extended version of stage 2 circuit with 5-bit selector switches. It is created using the subcircuits of stage 2 circuit.


![stage1](https://user-images.githubusercontent.com/65214115/92019614-89140000-ed74-11ea-8b38-4579eea33e9f.PNG)


#### Stage 2 Circuit Diagram - VH VL 3-bitstage


![stage2_circuit diagram](https://user-images.githubusercontent.com/65214115/92018009-30436800-ed72-11ea-9940-9ec261c5dbd4.PNG)


#### Stage 3 Circuit Diagram - 2 bit DAC


![stage3_circuit](https://user-images.githubusercontent.com/65214115/92018889-69300c80-ed73-11ea-96b8-1bfcfb71238c.PNG)


#### Subcircuit- Switch_pair

![switch](https://user-images.githubusercontent.com/65214115/92019282-fa9f7e80-ed73-11ea-8c12-b2e83cdbd909.PNG)


### Complete Schematic of 10bit PDAC


![completecircuit](https://user-images.githubusercontent.com/65214115/92020000-18211800-ed75-11ea-89d8-c20330282068.PNG)


The complete circuit diagram can be downloaded using this link [10bitDAC_Circuit.pdf](https://github.com/neethujohny/avsddac_3v3/files/5078507/10bitDAC_Circuit.pdf)

Note- While integrating the different stages, the resistance values have been changed appropriately.


#### 10bit DAC Output and Inputs plot

![dac_output margin based](https://user-images.githubusercontent.com/65214115/90310313-14386d80-df0e-11ea-9c24-7aa74c3a0dba.PNG)


## To obtain DNL vs Input code characteristics @T=27C and VREF&VDD=3.3

The differential nonlinearity (DNL) is the difference between the measured and ideal 1LSB amplitude change of any two adjacent codes. Using the values noted earlier and the formula given below, we can find all the DNL values. These vaues are uploaded in the repository with the name DNL_INL_calculations.

DNL(LSB)= (Actual height- Ideal height)/1LSB



![DNL](https://user-images.githubusercontent.com/65214115/90310268-a55b1480-df0d-11ea-8aeb-d972454d7643.jpg)


## To obtain INL vs Input code characteristics @T=27C and VREF&VDD=3.3

The relative accuracy or integral nonlinearity (INL) is the maximum deviation of the output from the line between zero and full scale excluding the effects of zero code and full-scale errors. The calculated INL values are uploaded in the repository in the file with the name DNL_INL_calculations.

INL(LSB)= (Actual Vout-Reference Vout)/1LSB



![INL](https://user-images.githubusercontent.com/65214115/90310285-c91e5a80-df0d-11ea-8229-c1868439badc.jpg)


### DNL and INL Table

| Parameter    | Pre-layout     |
| ------------- | -------------   |
| DNL(LSB)     |-1.0 to +1.7     |
| INL	(LSB)    | -2.0 to +2.654  |




## To obtain Output Voltage vs Input code characteristics @T=27C and VREF&VDD=3.3

![OUTPUT vs INPUT](https://user-images.githubusercontent.com/65214115/90310494-64fc9600-df0f-11ea-9a82-64a97d47ada3.jpg)

Note- The input code ranges from 0 to 1023. The Full Scale output voltage, VFS =3.292069V


## Open source EDA Tools used to develop the IP

The design is done using opensource EDA tools such as eSim for the prelayout simulatioms and MAGIC for the layout and postlayout simulations. eSim is a free and open source EDA tool for circuit design, simulation, analysis and PCB design. It is an integrated tool built using open source software such as KiCad, Ngspice and GHDL. Magic is an opensource VLSI layout tool.

### Steps to Install eSim on Ubuntu 16.04

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
  

### Steps to Install Magic 8.1 on Ubuntu 16.04

* Download the https://drive.google.com/file/d/1F0y1xuYWIgeYEpzKnGlaCQH3urdSFc4E/view file

* Copy paste the below commands one after another

'''
    
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

$  sudo apt install -y git

$  git clone https://https://github.com/neethujohny/avsddac_3v3

$  cd avsddac_3v3/Prelayout_Netlist

* To run the Transient Analysis , enter the following command

$ ngspice Vh_Vl_cascaded.cir.out

$ plot out_10bitdac

#### Output of 10bit PDAC - Transient Analysis Prelayout

![10bit_dac_output](https://user-images.githubusercontent.com/65214115/89987830-4c387a00-dc9c-11ea-9722-3f6dcdaf27c3.PNG)


## 10bit PDAC Layout


#### Stage 1 Circuit Layout


![5bitstage](https://user-images.githubusercontent.com/65214115/92036288-9c7f9500-ed8d-11ea-8b5f-3b023897a42d.PNG)


#### Stage 2 Circuit Layout


![3bitstage_layout](https://user-images.githubusercontent.com/65214115/92035192-fb440f00-ed8b-11ea-8782-30c39654c919.PNG)


#### Stage 3 Circuit Layout

![2bitstage_layout](https://user-images.githubusercontent.com/65214115/92035187-fa12e200-ed8b-11ea-8e99-dbe0d8ec6da7.PNG)


#### Subcircuit- Switch_pair Layout


![switch](https://user-images.githubusercontent.com/65214115/92036291-9db0c200-ed8d-11ea-8908-7ad8a319deef.PNG)


#### Complete Circuit Layout

![10bitdac_layout](https://user-images.githubusercontent.com/65214115/92035196-fb440f00-ed8b-11ea-9a2f-a67dca694a7d.PNG)


## Postlayout Simulations

* To clone the Repository and download the Netlist files for Simulation, enter the following commands in your terminal.

$  sudo apt install -y git

$  git clone https://https://github.com/neethujohny/avsddac_3v3

$  cd avsddac_3v3/PostLayout_magic and spice files

* To run the Transient Analysis , enter the following command

$ ngspice 10bit_dac.spice


### Output of 10bit PDAC - Post Layout

![10bitdac_out](https://user-images.githubusercontent.com/65214115/92032729-37757080-ed88-11ea-9a77-d384cd36dbbf.PNG)


    Note: For the individual block post simulation outputs, please refer post layout simulation file uploaded above.


## Author

Neethu Johny, B.M.S College of Engineering, Bangalore

## Acknowledgements

Kunal Ghosh, Director, VSD Corp. Pvt. Ltd.

Philipp Gühring, Software Architect, LibreSilicon Assocation

## Contact Information

Neethu Johny, B.M.S College of Engineering, Bangalore - neethujohny123@gmail.com

Kunal Ghosh, Director, VSD Corp. Pvt. Ltd. - kunalghosh@gmail.com

Philipp Gühring, Software Architect, LibreSilicon Assocation - pg@futureware.at
