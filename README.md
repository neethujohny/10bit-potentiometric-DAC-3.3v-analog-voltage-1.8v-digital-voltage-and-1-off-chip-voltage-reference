# 10bit-potentiometric-DAC-3.3V-analog-voltage-1.8V-digital-voltage-and-1-off-chip-voltage-reference

This work is aimed at design of a 10bit potentiometric DAC with 3.3V analog output volatge and 1.8V digital inputs with a single external reference voltage source. The DAC is designed using multiple stages for better performance and less area requirements compared to a single stage DAC.

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
 
 * [Author](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#author)
 
 * [Acknowledgements](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#acknowledgements)
 
 * [Contact Information](https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference#contact-information)
  
  

## Need for a potentiometric DAC(PDAC) IP

Modern electronic systems dominate due to the evolution in digital technology. However the outside world remains analog in nature. DACs form an important link to connect between the digital systems to the analog world. Binary weighted DAC, R-2R DAC, current steering DAC, resister string DAC are some of the other DAC architectures used in various applications.

### Design of 10bit PDAC

The 10bit DAC is designed in three stages to save area and reduce the runtime. The development of an area-efficient multiple-output voltage selector starts from a 5-b tree-type two-voltage selector. This circuit requires two sets of 5-b tree-type decoders, arranged with a 1-b offset, in order to select two adjacent voltages from a resistor string. One set outputs VH and the other set outputs VL. A total of 124 switches are required. The two-voltage selector chooses two adjacent voltages from the reference voltages of a global resistor string according to the higher digital bits (MSB bits b9 to b5) and connects them to the succeeding DAC stages. The second stage is again a 3-b tree-type two-voltage selector which outputs VH and VL based on subsequent LSB bits from b4 to b2. The third stage ia a 2 bit DAC which subsequently divides the voltage between these two voltage levels based on lower 2 digital bits b1 and b0.

Note: The accuracy of the conversion can be still improved by adjusting the number of stages and granularity of the various stages.

#### Stage 1 Circuit Diagram - VH VL 5-bitstage

The circuit is an extended version of stage 2 circuit with 5-bit selector switches. It is created using the subcircuits of stage 2 circuit.

#### Stage 2 Circuit Diagram - VH VL 3-bitstage

[Stage 2 Circuit.pdf](https://github.com/neethujohny/avsddac_3v3/files/5078502/Stage.2.Circuit.pdf)

#### Stage 3 Circuit Diagram - 2 bit DAC

[stage3 Circuit.pdf](https://github.com/neethujohny/avsddac_3v3/files/5078505/stage3.Circuit.pdf)

#### Subcircuit- Switch_pair

[Switchpair_circuit.pdf](https://github.com/neethujohny/avsddac_3v3/files/5078506/Switchpair_circuit.pdf)

#### Complete Schematic of 10bit PDAC

[10bitDAC_Circuit.pdf](https://github.com/neethujohny/avsddac_3v3/files/5078507/10bitDAC_Circuit.pdf)

Note- While integrating the different stages, the resistance values have been changed appropriately.

#### 10bit DAC Output and Inputs plot

![dac_output margin based](https://user-images.githubusercontent.com/65214115/90310313-14386d80-df0e-11ea-9c24-7aa74c3a0dba.PNG)

## To obtain DNL vs Input code characteristics @T=27C and VREF&VDD=3.3

The differential nonlinearity (DNL) is the difference between the measured and ideal 1LSB amplitude change of any two adjacent codes. Using the values noted earlier and the formula given below, we can find all the DNL values. These vaues are uploaded in the repository with the name DNL_INL_calculations.

DNL(LSB)= (Actual height- Ideal height)/1LSB

### DNL(LSB) vs Input code

![DNL](https://user-images.githubusercontent.com/65214115/90310268-a55b1480-df0d-11ea-8aeb-d972454d7643.jpg)


## To obtain INL vs Input code characteristics @T=27C and VREF&VDD=3.3

The relative accuracy or integral nonlinearity (INL) is the maximum deviation of the output from the line between zero and full scale excluding the effects of zero code and full-scale errors. The calculated INL values are uploaded in the repository in the file with the name DNL_INL_calculations.

INL(LSB)= (Actual Vout-Reference Vout)/1LSB

### INL(LSB) vs Input code

![INL](https://user-images.githubusercontent.com/65214115/90310285-c91e5a80-df0d-11ea-8229-c1868439badc.jpg)


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
  
 ### eSim Spoken Tutorials
 
  Refer `Spoken Tutorial` (https://spoken-tutorial.org/tutorial-search/?search_foss=eSim) for eSim installation on Linux and MS Windows.
  

## Prelayout Simulations

* To clone the Repository and download the Netlist files for Simulation, enter the following commands in your terminal.

$  sudo apt install -y git

$  git clone https://github.com/neethujohny/10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference

$  cd 10bit-potentiometric-DAC-3.3v-analog-voltage-1.8v-digital-voltage-and-1-off-chip-voltage-reference/Prelayout_Netlist

* To run the Transient Analysis , enter the following command

$ ngspice Vh_Vl_cascaded.cir.out

$ plot out_10bitdac

#### Output of 10bit PDAC - Transient Analysis

![10bit_dac_output](https://user-images.githubusercontent.com/65214115/89987830-4c387a00-dc9c-11ea-9722-3f6dcdaf27c3.PNG)


## Author

Neethu Johny, B.M.S College of Engineering, Bangalore

## Acknowledgements

Kunal Ghosh, Director, VSD Corp. Pvt. Ltd.

Philipp Gühring, Software Architect, LibreSilicon Assocation

## Contact Information

Neethu Johny, B.M.S College of Engineering, Bangalore - neethujohny123@gmail.com

Kunal Ghosh, Director, VSD Corp. Pvt. Ltd. - kunalghosh@gmail.com

Philipp Gühring, Software Architect, LibreSilicon Assocation - pg@futureware.at
