# Welcome to Underwater Modem Project

Welcome to our wiki! 
Team: Nghia Tran and Hoa Nguyen

## Journal

**17-April-2015**

We have first presentation. Here is the [slides](https://bitbucket.org/txnghia/capstone/downloads/Progress_04162015.pptx)

Complete schematic design for modem hardware.  [Acomm_Modem_Schematic](https://bitbucket.org/txnghia/capstone/downloads/PCB_Acomm_Project.pdf)

Testing Mod/Demod with FSK underwater. [FSK_waveform](https://bitbucket.org/txnghia/capstone/wiki/FSK%20test%20underwater)

Tasks need to complete by 01-May-2015

1. Complete PCB layout for modem hardware and send it to manufacture to fabricate.
 
2. Create basic ZedBoard project to test output pin at the FMC connector.  The underwater modem hardware interface with the Zynq device on the ZedBoard via this FMC connector.

3. Generate BPSK modulation with Simulink, Generate HDL code.

4. Design a FIR filter, generate HDL code for Zynq. Plan to have simulation first, then run on the ZedBoard when the hardware is built.


**28-April-2015**

Downloaded: ZynqBook, ZynqBook tutorial, and Source tutorial from http://www.zynqbook.com/downloads.html

Completed a tutorial from ZynnBook that generate LEDs test IP with Vivado.  The instructions were very easy to follow.  Will go through some other tutorial generate IP from MatLab Simulink.

**29-April-2015**

Worked with Hoa, went through Simulink code for PBSK transmitter

Xilinx Vivado got error at start up for my laptop. Reinstalled Vivado 14.2