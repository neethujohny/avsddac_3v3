# 10bit-potentiometric-DAC-3.3V-analog-voltage-1.8V-digital-voltage-and-1-off-chip-voltage-reference

This work is aimed at design of a 10bit potentiometric DAC with 3.3V analog output volatge and 1.8V digital inputs with a single external reference voltage source. The DAC is designed using multiple stages for better performance and less area requirements compared to a single stage DAC.

## Need for a potentiometric DAC(PDAC) IP

Modern electronic systems dominate due to the evolution in digital technology. However the outside world remains analog in nature. DACs form an important link to connect between the digital systems to the analog world. Binary weighted DAC, R-2R DAC, current steering DAC, resister string DAC are some of the DAC architectures used in various applications.

### Design of 10bit PDAC

The 10bit DAC is designed in three stages to save area and reduce the runtime. The development of an area-efficient multiple-output voltage selector starts from a 5-b tree-type two-voltage selector. This circuit requires two sets of 5-b tree-type decoders, arranged with a 1-b offset, in order to select two adjacent voltages from a resistor string. One set outputs VH and the other set outputs VL. A total of 124 switches are required. The two-voltage selector chooses two adjacent voltages from the reference voltages of a global resistor string according to the higher digital bits (MSB bits b9 to b5) and connects them to the succeeding DAC stages. The second stage is again a 3-b tree-type two-voltage selector which outputs VH and VL based on subsequent LSB bits from b4 to b2. The third stage ia a 2 bit DAC which subsequently divides the voltage between these two voltage levels based on lower 2 digital bits b1 and b0.

Note: The accuracy of the conversion can be still improved by adjusting the number os stages and granularity of the various stages.

#### Stage 1 Circuit Diagram - VH VL 5-bitstage

The circuit is an extended version of stage 2 circuit with 5-bit selector switches. It is created using the subcircuits of stage 2 circuit.

#### Stage 2 Circuit Diagram - VH VL 3-bitstage

![Vh_Vl_3bit_schematic](https://user-images.githubusercontent.com/65214115/89987102-1646c600-dc9b-11ea-8bbb-b13a4d8695b5.PNG)

#### Stage 3 Circuit Diagram - 2 bit DAC

![2bitdac_circuit](https://user-images.githubusercontent.com/65214115/89986616-6c673980-dc9a-11ea-8813-d7d20a94bbf4.PNG)

#### Subcircuit- Switch_pair

![switch_pair_schematic](https://user-images.githubusercontent.com/65214115/89986862-c667ff00-dc9a-11ea-8337-03cda4e5b57f.PNG)

#### Complete Schematic of 10bit PDAC

![schematic_10bitdac](https://user-images.githubusercontent.com/65214115/89987533-d7fdd680-dc9b-11ea-9867-d710c264c953.PNG)

#### Output of 10bit PDAC

![10bit_dac_output](https://user-images.githubusercontent.com/65214115/89987830-4c387a00-dc9c-11ea-9722-3f6dcdaf27c3.PNG)

## To obtain DNL vs Input code characteristics @T=27C and VREF&VDD=3.3

The differential nonlinearity (DNL) is the difference between the measured and ideal 1LSB amplitude change of any two adjacent codes. Using the values noted earlier and the formula given below, we can find all the DNL values. These vaues are uploaded in the repository with the name DNL_INL_calculations.

DNL(LSB)= (Actual height- Ideal height)/1LSB

## To obtain INL vs Input code characteristics @T=27C and VREF&VDD=3.3

The relative accuracy or integral nonlinearity (INL) is the maximum deviation of the output from the line between zero and full scale excluding the effects of zero code and full-scale errors. The calculated INL values are uploaded in the repository in the file with the name DNL_INL_calculations.

INL(LSB)= (Actual Vout-Reference Vout)/1LSB


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
  
 ### eSim Spoken Tutorials
 
  Refer `Spoken Tutorial` (https://spoken-tutorial.org/tutorial-search/?search_foss=eSim) for eSim installation on Linux and MS Windows.


