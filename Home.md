# Welcome to Underwater Modem Project

Welcome to our wiki! 
Team: Nghia Tran and Hoa Nguyen


Click this page for final document 
https://bitbucket.org/maswes/acoustic_modem-cohort3/wiki/Underwater%20Modem


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

**17-23-April-2015**

Worked in Transmitter part, created Modulated signal output.[Transmitted Signal](https://bitbucket.org/txnghia/capstone/wiki/Transmitted%20Signal)

**24-April-2015**

Worked with Prof Eldon about Simulink BPSK in Receiver part (Hoa)

**28-April-2015**

Downloaded: ZynqBook, ZynqBook tutorial, and Source tutorial from http://www.zynqbook.com/downloads.html

Completed a tutorial from ZynnBook that generate LEDs test IP with Vivado.  The instructions were very easy to follow.  Will go through some other tutorial generate IP from MatLab Simulink.

**29-April-2015**

Worked with Hoa, went through Simulink code for BPSK transmitter

Xilinx Vivado got error at start up for my laptop. Reinstalled Vivado 14.2

**30-April-2015**

Worked with Prof Eldon about Transmitter.  The Transmitted signal looks better.

Run HDL, created Verilog code for transmitter.[Transmitted Signal Updated]( https://bitbucket.org/repo/Lx4j45/images/3662998166-Transmitter_Updated.PNG)

Ready Power point for Presentation

**01-May-2015**

Worked with Patrick and Rick about Demod signal and the LPF but SIM was not working.

**02,03-May-2015**

Worked with Prof Eldon. Without RRC filter, new Mod and Demod can get 0 error. [Transmitted signal without RRC ](https://bitbucket.org/repo/Lx4j45/images/2333873457-Transmited%20signal.PNG)

 [Received signal without RRC ](https://bitbucket.org/repo/Lx4j45/images/1451673545-Receiver%20without%20RRC.PNG)



**04-May-2015**

Digikey parts will be delivered on 5/5/15

Got shipping confirmation from PCB manufacture.  The Board will also be delivered by 8:00 pm on 5/5/15

PCB Manufacture. (http://www.PCBnet.com) 
Imagineering, Inc.
2425 Touhy Ave
Elk Grove Village, IL 60007
Phone: (847) 806-0003
Fax: (847) 806-0004

The total price for PCB:

Part Number = NT_04252015 
 Quantity = 4 
 Unit price = $37.96 
 Tooling Charge: $100.00 
 Testing: $0.00 
 Total Quantity = 4 
 Our Price = $251.84 
 Terms: Credit Card 
 Lead Time: 5 Days

PO DATE: 4/27/2015
 SHIPOUT DATE: 5/4/2015
 CUT OFF TIME: 4/27/2015 12:00p


Tasks need to complete by 15-May-2015

1. Complete assembly and test PCB boards for UW modem.

2. Establish AXI interface to connect ARM processor from PS to modem section in PL on Zynq.

3. Demo FIR filter design using MatLab and Vivado.  We planned to implement the FIR filter on ZedBoard.  Our customed build ADC and DAC boards will be connected to the FIR fitler via FMC conector as input and output ports.

4. We may able to transmit our BPSK/QPSK signal on our modem.

5. Continue update coding from Simulink.

**05-07-May-2015** 

Assembled the board with Nghia after work. 

Connected RRC in, found right delay to get zero error output [Received Signal with RRC](https://bitbucket.org/repo/Lx4j45/images/1056547846-Received%20Signal%20with%20RRC.PNG) [RRC Filter](https://bitbucket.org/repo/Lx4j45/images/4136884445-RRC%20Filter.PNG)

**08-May-2015** 

Worked with Prof Eldon to figure out how to decode the received signal in Receiver.

**09-11-May-2015** 

Found some output but they were not the same as we sent in transmitter. We sent " Hello world 00#" but attachment is something we received. [Output Message in Receiver](https://bitbucket.org/repo/Lx4j45/images/611252069-Capture.PNG) 

**12-14-May-2015** 

Worked Decoding in Receiver, but so far the output is still not good. ( although working online with Prof Eldon)
    