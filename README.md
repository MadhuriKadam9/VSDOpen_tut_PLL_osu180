# VSD Open 21 Phase Locked Loop using OSU180
![image](https://user-images.githubusercontent.com/58599984/137940739-15b4f9e6-d14d-4921-996c-1d48569e3c19.png)

This repo contains detailed documentation of the "VSD Open On-Chip Clock Multiplier (PLL) on OSU180" tutorial. 

-----------------------------------------------------------------------------------------------------------------------------------------------
# Contents
- [Introduction](#introduction)
- [Block Diagram of PLL](#block-diagram-of-pll)
- [Reference Books for Literature review and architecture design](#reference-books-for-literature-review-and-architecture-design)
- [Setting up Linux Environment](#setting-up-linux-environment)
- [Installations](#installations)
  * [Git](#git)
  * [eSim](#esim)
  *  [Magic](#magic)
- [Running eSim and Ngspice](#running-esim-and-ngspice)
  * [eSim Schematic of inverter example](#esim-schematic-of-inverter-example)
  * [Running Ngspice](#running-ngspice)
  * [Output Waveforms](#output-waveforms)
- [Prelayout](#prelayout)
  * [PFD Design](#pfd-design)
  * [Charge Pump with Low Pass Filter](#charge-pump-with-low-pass-filter)
  * [VCO](#vco)
  * [freq_div](#freq-div)
  * [PLL Prelayout](#pll-prelayout)
- [Layout Design](#physical-design)
  * [Layout of Inverter](#layout-of-inverter)
  * [Layout of PFD](#layout-of-pfd)
  * [Layout of VCO](#layout-of-vco)
  * [Layout of FreqDiv8](#layout-of-freqdiv8)
  * [Layout of mux21](#layout-of-mux21)
  * [Final Layout of PLL](#final-layout-of-pll)
- [Acknowlegment](#acknowlegment)
- [References](#references)



# Introduction
The phase locked loop is a circuit which takes the external low frequency clock signal generated with the help of crystal oscillator and gives the High frequency clock signal as the output in this case it is 8 times input clock frequency. This high frequency clock generated can be given to different circuits on chip. The clock signal generated by PLL is stable in terms of clock frequency and clock phase.

# Block Diagram of PLL
<p align="center">
  <img src="/Images/blockdiagram.jpg">
</p>


# Reference Books for Literature review and architecture design
1. Design of Analog CMOS Integrated Circuits Behzad Razavi
2. Design of CMOS Phase Locked Loops Behzad Razavi


# Setting up Linux Environment
Download the latest version of Virtual Box from the following link:
https://www.virtualbox.org/
After installation it will look somewhat like this:
![image](https://user-images.githubusercontent.com/58599984/137799120-6b9eb544-bccc-48b9-8e44-99d417506a08.png)
Download the Ubuntu Disk Image:
https://ubuntu.com/download/desktop
Create a new machine:
![image](https://user-images.githubusercontent.com/58599984/137799330-77062e35-35fe-44bc-bc6f-aa348c28f879.png)
Follow the steps hereafter.

After complete installation the Ubuntu window looks like this:
![image](https://user-images.githubusercontent.com/58599984/137799601-0bc2c1de-46ff-4fdc-9650-45f808ed0766.png)

# Installations
## Git
Open terminal and run:
```
sudo apt-get install git
```
Then do:
```
git clone https://github.com/parasgidd/avsdpll_3v3.git
```

## eSim
Install eSim and follow steps from here:
https://esim.fossee.in/downloads

## Magic
Run following Commands in the terminal:
git clone git://opencircuitdesign.com/magic
```
cd magic
sudo ./configure
sudo make
sudo make install
```
# Running eSim and Ngspice

## eSim Schematic of inverter example

## Running Ngspice
```
cd /avsdpll_3v3/prelayout$
ngspice inv.cir
```

## Output Waveforms
![image](https://user-images.githubusercontent.com/58599984/137800823-dfd01f99-bffb-4a99-9d9d-e8d466ae1ba2.png)

# Prelayout
## PFD Design
![image](https://user-images.githubusercontent.com/58599984/137802291-905fe5c0-c849-476d-b887-3892ba66a1f9.png)
![image](https://user-images.githubusercontent.com/58599984/137803982-d01ec0cc-3009-453c-84b0-a5d5759f27a4.png)
<p align="center">
  <img src="/Images/s1.PNG">
</p>

## Charge Pump with Low Pass Filter
![image](https://user-images.githubusercontent.com/58599984/137802034-14a9f0f7-fcc7-4cfe-ad53-17594d4c8283.png)
<p align="center">
  <img src="/Images/cp-wlp.PNG">
</p>


## VCO
![image](https://user-images.githubusercontent.com/58599984/137802397-405da180-9bdd-439b-ac85-f7fb59a12b76.png)
<p align="center">
  <img src="/Images/vco.PNG">
</p>
<p align="center">
  <img src="/Images/vco-0.4.PNG">
</p>


## freq_div
![image](https://user-images.githubusercontent.com/58599984/137803268-58e658e0-c078-486b-b16b-d5c16d28d823.png)
<p align="center">
  <img src="/Images/freq-div.PNG">
</p>


## PLL Prelayout
<p align="center">
  <img src="/Images/pll.PNG">
</p>

# Physical Design
## Layout of Inverter
Run the following command to open Magic:
```
magic -T SCN6M_SUBM.10.tech
```
![image](https://user-images.githubusercontent.com/58599984/137804925-456124c5-572c-4967-aac0-be0c58751d5c.png)

## Layout of PFD
![image](https://user-images.githubusercontent.com/58599984/137805430-9c634f42-baca-4add-b448-5c845f06b344.png)
<p align="center">
  <img src="/Images/pfd-laysim.PNG">
</p>


## Layout of VCO
![image](https://user-images.githubusercontent.com/58599984/137805522-cda4d825-74c4-48ad-82c4-a6ee3a0d463c.png)
<p align="center">
  <img src="/Images/vco-laysim.PNG">
</p>


## Layout of FreqDiv8
![image](https://user-images.githubusercontent.com/58599984/137805681-dd68d1d5-dd36-471f-b9d9-44bd924e47bc.png)
<p align="center">
  <img src="/Images/freq-div8.PNG">
</p>

## Layout of mux21
![image](https://user-images.githubusercontent.com/58599984/137805764-7e073d29-ccb9-4744-bd42-84d0683a5eae.png)
<p align="center">
  <img src="/Images/freq-div8-laysim.PNG">
</p>

## Final Layout of PLL
![image](https://user-images.githubusercontent.com/58599984/137808002-3792ab3e-71d8-4a63-9fac-dfc1fa886a32.png)
<p align="center">
  <img src="/Images/pll-laysim.PNG">
</p>

# Acknowlegment
I would like to thank Mr.Kunal Ghosh and Mr. Paras Gidd for explaining the the detail designing procedure of PLL circuit. This tutoril helped me to understand the the analog design flow right from circuit simulation to post layout simulation.

# References
1. https://www.vlsisystemdesign.com/registration/<br>
2. https://vsdiat.com/<br>
3. https://github.com/parasgidd/avsdpll_3v3<br>
4. https://www.virtualbox.org/<br>
5. http://opencircuitdesign.com/magic/download.html<br>
6. https://esim.fossee.in/downloads<br>










