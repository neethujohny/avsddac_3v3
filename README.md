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




## Open source EDA Tools used to develop the IP

The design is done using opensource EDA tools such as eSim for the prelayout simulatioms and MAGIC for the layout and postlayout simulations. eSim is a free and open source EDA tool for circuit design, simulation, analysis and PCB design. It is an integrated tool built using open source software such as KiCad, Ngspice and GHDL. Magic is an opensource VLSI layout tool.

*  Steps to Install eSim

*  Steps to Install Magic tool
