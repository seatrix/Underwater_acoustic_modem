# Seatrix Underwater Modem #
Please contact info@seatrix.com if you need commercial underwater acoustic modem.

![EiglVvsUYAAbe_-.jpg](https://github.com/seatrix/Underwater_acoustic_modem/blob/master/EiglVvsUYAAbe_-.jpg) 

Depth: 2000m

Weight: 15kg in air

Power supply: 400W*Hr rechargeable battery 

Acoustic baud rate: 100-2400bps

data redundancy, multi-path protection period selection for convolutional coding, MFSK modulation scheme.


# Underwater Modem #

### Motivation ###
A few years ago, I worked in a project developing data glove system.  It converts motion sensors mounted on fingers and palm glove into computer data type and transmit the data out in radio frequency.  We used it in helping deaf people talking.  We used it as a wireless mouse and key board.  We used it to control a mobile robot as well.

![1_black_box.jpg](https://bitbucket.org/repo/Lx4j45/images/1679730286-1_black_box.jpg) 

Many people asked if data glove could work underwater so divers could use?  We didn’t have a good answer for it at that time.  Now, after nearly two years went through the wireless embedded system program, I believe we have gained enough information to build a complete underwater modem system.


### Concept ###

![2_human_talk.jpg](https://bitbucket.org/repo/Lx4j45/images/3911339345-2_human_talk.jpg)


### Choosing hardware ###
I have looked for several hardware candidate for system.  I came up with some of the hard tools we could use.  BeMicro board from Altera has all specs as need, low price ($50), and easy to develop with I/O pin brought to 0.1’ pitch header.  The basic software is similar to Xilinx that we can use the Webpack with some limited utilization.

### Altera BeMicro CV Board ###

![3_BeMicro_CV_Board.jpg](https://bitbucket.org/repo/Lx4j45/images/1725440143-3_BeMicro_CV_Board.jpg)

BeMicro CV adopts Altera’s 28-nm, low-cost FPGA – Cyclone V. It retains all the benefits of its predecessor including the 80-pin edge connector interface. Users can migrate their designs from BeMicro SDK to BeMicro CV easily. Besides, more user’s GPIOs are available. Moreover, it supports a hard memory controller for DDR3. Users don’t pay much attention to timing closure.
The Altera 5CEFA2F23C8N Cyclone V FPGA resident on the Be Micro CV features a hardened memory controller (HMC) that supports DDR2, DDR3 and LPDDR3. On the BeMicro CV the HMC is connected to a single 16-bit wide, 1Gb DDR3 SDRAM device (From Arrow website)
https://parts.arrow.com/item/detail/arrow-development-tools/bemicrocv#MGGy

![4_P5LP_DVK_500.jpg](https://bitbucket.org/repo/Lx4j45/images/2207680928-4_P5LP_DVK_500.jpg)

### PSoC5 Development Kit ###
PSoC5 (Programmable System on Chip) from Cypress  has analog, digital, processor, and DSP on chip.  This PSoC system allow to design with very low cost, small size platform, and great design tool.  The developing software is no cost.   

The CY8CKIT-050 PSoC® 5LP Development Kit enables you to evaluate, develop and prototype high precision analog, low-power and low-voltage applications powered by Cypress’s CY8C58LP high precision analog device family (From Cypress website).
http://www.cypress.com/?rID=51577&source=shop


### ZedBoard ###
The ZedBoard was hard since there were not hardware available for our application.  We needed to have a good ADC and ADC capabilities that could generate and process sinewave from 10 to 100 KHz.  The XADC port on the ZedBoard could process ADC and DAC but a little bit slow, not satisfy my need.

However, choosing the ZedBoard would have us to access power design tool like MATLAB, Vivado system design, Vivado HLS, and that we could employ as much as I could what I learned from previous course to the capstone underwater capstones project.

![5_zedboard_pcba.jpg](https://bitbucket.org/repo/Lx4j45/images/403224342-5_zedboard_pcba.jpg)

We finally decided to go with the ZedBoard, but I to the FMC connector on the ZedBoard
One another way to have good speed ADC and DAC is to access the Zynq FPGA I/O pin via FMC connector.  This is not easy to make this FMC connector on the ZedBoard because all pins are array surface mount, very hard to solder by hand.  I tried to use edged row pins of the array so I could stick my solder in there and omitted inside the row.   I planned for it but crossing my finger for luck.  



### Assignment ###
Hoa Nguyen: Implement MATLAB Simulink  for BPSK/QPSK.  Generate IP Core for Vivado  system desing
Nghia Tran: Develop complete hardware system of an underwater acoustic transmitter and receiver.  Drove drivers for hardware.  Implement 2-FSK modem in parallel with Hoa.

Here is the block hardware block diagram

![6_BlockDiagram.png](https://bitbucket.org/repo/Lx4j45/images/3238753408-6_BlockDiagram.png)

The printer circuit boards are planned and layout as below.  We wanted to make the as separated individual module so I could access to signals easily, so we can debug, replace, and learn. 

![7_Boards.PNG](https://bitbucket.org/repo/Lx4j45/images/3932441408-7_Boards.PNG)

### Hardware Build ###
I started with research and looked for electronic parts that fit the specification for the modem.  That was not easy because the there were not many parts designed for underwater communication.  One could easy part for audible frequency application or high frequencies part for radio application, but not for frequency range from 10 – 100Khz as underwater modem need.  

### Schematic and Layout Design ###
Tool: Altium
Time: 2 months

I spent a lot time and effort to built the boards for the modem.  It seemed to me that I compressed a year full-time work in to two month of nights and week ends.  I did all tasks almost by myself for A to Z, from searching parts, order parts, schematic and layout design, solder, assembly, wiring, testing and repair.

![8_schematic_zedboard_fmc.png](https://bitbucket.org/repo/Lx4j45/images/938767581-8_schematic_zedboard_fmc.png)
FMC connector board schematic

![9_board_fmc_top.png](https://bitbucket.org/repo/Lx4j45/images/2879958037-9_board_fmc_top.png)
Zedboard FMC connector board – Top

![10_board_fmc_bottom.png](https://bitbucket.org/repo/Lx4j45/images/2224055913-10_board_fmc_bottom.png)
Zedboard FMC connector board - Bottom

![11_schematic_dac.png](https://bitbucket.org/repo/Lx4j45/images/601825399-11_schematic_dac.png)
DAC schematic

![12_board_dac.png](https://bitbucket.org/repo/Lx4j45/images/2135474960-12_board_dac.png)
DAC board

![13_schematic_pa.png](https://bitbucket.org/repo/Lx4j45/images/1004767664-13_schematic_pa.png)
Power amplifier schematic

![14_board_pa.png](https://bitbucket.org/repo/Lx4j45/images/413592757-14_board_pa.png)
Power amplifier board

![15_schematic_tr_sw.png](https://bitbucket.org/repo/Lx4j45/images/2535870237-15_schematic_tr_sw.png)
Transmit/Receive Switch

![16_board_TR_SW.png](https://bitbucket.org/repo/Lx4j45/images/2862445917-16_board_TR_SW.png)
Transmit/Receive Switch schematic

![17_schematic_preamp.png](https://bitbucket.org/repo/Lx4j45/images/1322248083-17_schematic_preamp.png)
Preamp schematic

![18_board_preamp.png](https://bitbucket.org/repo/Lx4j45/images/2007285465-18_board_preamp.png)
Preamp board

![19_schematic_adc.png](https://bitbucket.org/repo/Lx4j45/images/3598803844-19_schematic_adc.png)
ADC schematic

![20_board_adc.png](https://bitbucket.org/repo/Lx4j45/images/828288917-20_board_adc.png)
ADC board

![21_schematic_power_supply.png](https://bitbucket.org/repo/Lx4j45/images/1293712397-21_schematic_power_supply.png)
Power supply schematic

![22_board_power_supply.png](https://bitbucket.org/repo/Lx4j45/images/3934988698-22_board_power_supply.png)
Power supply board

### Modify and troubleshooting hardware ###
![23_floating.PNG](https://bitbucket.org/repo/Lx4j45/images/1873384266-23_floating.PNG)

As initial design, I had this point left floating.  When I have power supplied to the board, the power amplifier chip U12 (yellow) was warm quickly.  That because the amplifier amplified floating voltage at its input gate. The high voltage output was almost sunk to ground, like a short circuit, caused the chip get warm.  I removed the capacitor C41 have direct connector signal path from the U13 to U12.  Also placed 10K resister for R47.  This keep the input signal not floating.  I solved it. 

![24_short_pcb.PNG](https://bitbucket.org/repo/Lx4j45/images/2610477303-24_short_pcb.PNG)
Board came from manufacture got failure at this two places.  I think because I choose a low cost PCB fabs, so the fabrication process was not high precision.  The copper of the vias touched traces.  This caused me two days to figure out.  

### Vivado Design ###
In parallel with Hoa and Prof. Eldon working on MATLAB for QPSK, I implemented 2-FSK modem with Vivado.  Below is my block diagram. 

![25_FSK_Diagram.png](https://bitbucket.org/repo/Lx4j45/images/2903722580-25_FSK_Diagram.png)
2-FSK modem block diagram

In the block diagram above, the modulator receives a stream of serial bit sending form ARM processor and generate two frequencies, 52 kHz represented symbol ‘0’ and 54 kHz represented symbol ‘1’.  The sinewave output at the DAC interface is 12-bit at rate of 1.5 mega symbol per second to achieve 32 points 50 kHz sinewave.  With this configuration,  the system expect to have the center carrier frequency is 50 kHz.  The 2 kHz represent symbol ‘0’ and 4 kHz represent symbol ‘1’.  The 50 kHz is a typical for our application.  We can also configure the carrier frequency via user terminal.

The first action in the demodulator is to remove 50 kHz component.  To perform this, a mixer is used.  The 50 kHz DDS is mixed with the input signal, and that produce 2 kHz, 4 kHz, 102 kHz and 104 Khz.  A FIR filter is used to filter out the 102 kHz and 104 kHz.  The 2 kHz and 4 kHz are feed in to  1x and 2x frequency matching filter.  The 1X matching filter give high scalar value if the signal input is 2kHz, and that is symbol ‘0’.  The 2X matching filter give high scalar value if the signal input is 4 kHz, and that is symbol ‘1’.  The Detector compares the scalar values outputs form the two matching filter and decide ‘0’ or ‘1’, and form a serial bit stream sending to the Parallel/Serial block.  This block convert the serial data stream to parallel byte data and pushes it up to the ARM processor via AXI interface.  

The controller, via hyperterminal, let user to configure carrier center frequency, transmit and receive gain, switch to RX/TX mode, and type message to send and display message received.

![26_FSK_Vivado_System_Design.png](https://bitbucket.org/repo/Lx4j45/images/1326469526-26_FSK_Vivado_System_Design.png)
Capture of 2-FSK Vivado system design diagram.

Right after we had all the board and hardware ready, I devoted a huge amount of time to learn the Vivado.  It was pain, but I had gain.  As indicated in the figure above, several IP core were place in the system.  Some of the IPs were create from Vivado HLS (that I learned from prof. Kastner), some of blocks were from available Xilinx libraries, some from MATLAB, and from VHDL code. 

With scope reading actual modulated signal and internal Vivado ILA (integrated Logic Analyzer), I verified that the Modulator work fine and most of the Demodulator achieved.  We got to last stage of the demodulator that detecting ‘0’ and ‘1’.  There was a difficulties, really painful, we I tried to probe the detection signal with Vivado ILA.  This limited me to go further in determine ‘1’ or ‘0’ when signal output from the 1x and 2x matching filter.  

![27_ErrorOnDacPath.PNG](https://bitbucket.org/repo/Lx4j45/images/1243002546-27_ErrorOnDacPath.PNG)

The figure above is a bug I found in the ADC clock.  The second line waveform was transmit out of DAC port and the first line waveform was loop back in to ADC port.  One of FPGA internal clock was not sync with the hardware sampling clock.  

![28_ErrorOnDacPathFixed.PNG](https://bitbucket.org/repo/Lx4j45/images/717413369-28_ErrorOnDacPathFixed.PNG)

I fixed the internal FPGA clock for the ADC port 180 degree shift from the clock for hardware ADC sampling circuit.  Now we had the good sine wave output and good sine wave input.  Fixing this let me allowed to go further designing the receiver  

### Digital filter design ###
One of the interesting thing we went through was to place the hand on the FIR filter.  I start with MATLAB tool, design the filter that I need, and generate FIR coefficients.  This coefficients are loaded in to the filter configuration in Xilinx FIR compiler.    

![29_fir_lp_cut_off_50khz.PNG](https://bitbucket.org/repo/Lx4j45/images/1380681422-29_fir_lp_cut_off_50khz.PNG)


### MATLAB design for 50 kHz low pass filter. ###

![30_fir_lp_cut_off_50khz_config.PNG](https://bitbucket.org/repo/Lx4j45/images/2472981655-30_fir_lp_cut_off_50khz_config.PNG)
The coefficient was loaded to FIR compiler

![31_mix_and_fir.PNG](https://bitbucket.org/repo/Lx4j45/images/1305432007-31_mix_and_fir.PNG)

The capture above is the capture of the FIR compiler in use in the demodulator. The first line waveform is 50 kHz carrier in the demodulator.  The second line is output of the mixer, that mix the input (52 & 54 Khz) signal with the 50 kHz carrier signal.

The third waveform is the output of the FIR low pass filter.  That’s the 2 kHz and 4 kHz components.  These two components are feed into the two matching filters.


Below are design of the two matching filter and their coefficients

![32_fir_lp_cutoff_20khz.PNG](https://bitbucket.org/repo/Lx4j45/images/2706116339-32_fir_lp_cutoff_20khz.PNG)
1x matching filter frequency response

![33_fir_mf_1x_config.PNG](https://bitbucket.org/repo/Lx4j45/images/2328694491-33_fir_mf_1x_config.PNG)
1x matching filter coefficients

![34_fir_mf_2x.PNG](https://bitbucket.org/repo/Lx4j45/images/623579372-34_fir_mf_2x.PNG)
2x matching filter frequency response

![35_fir_mf_2x_config.PNG](https://bitbucket.org/repo/Lx4j45/images/2898420665-35_fir_mf_2x_config.PNG)
2x matching filter coefficients

![36_detection.PNG](https://bitbucket.org/repo/Lx4j45/images/464063095-36_detection.PNG)
Output of Matching filter

### Testing in water ###
![38_transdec2.jpg](https://bitbucket.org/repo/Lx4j45/images/1655391303-38_transdec2.jpg)
![37_transdec.jpg](https://bitbucket.org/repo/Lx4j45/images/1432289283-37_transdec.jpg)

We actual see surface reflection.  The test setup and the echo signal are described in the figure above.  We setup sending out a burst of sine wave 0.5 ms duration.  On the right side, we saw signal on the scope with two bursts of sinewave.  The taller one was the directed path and the short one was the echo, the surface reflection

![39_echo.PNG](https://bitbucket.org/repo/Lx4j45/images/356470520-39_echo.PNG)
Distance: 1 ft
The flection was not too bad
![40_good_condition.PNG](https://bitbucket.org/repo/Lx4j45/images/1625158774-40_good_condition.PNG)

Distance: 6 ft
The flection caused distorted receive modulated signal and then cause error in detection stage

![41_not_good_condition.PNG](https://bitbucket.org/repo/Lx4j45/images/645423318-41_not_good_condition.PNG)
First line: Received modulated signal
Second line: Remove the carrier frequency with mixer and low pass filter
Third line: Decode signal in bit stream
Fourth line: Byte received data.

### Conclusion ###
We remember when we attended the MATLAB presentation by Houman nearly two years ago, during the orientation. He was talking all about the design digital receiver.  But I was more interested in transmitters.  We dreamed we could use it to jam my friend phone for fun or we could make a secret strong power mobile radio station.   So, we finally broke into words:  Why don’t you teach us about transmitter.  He said: Transmitter is easy and gave a brief explanation.  We didn’t believe that we thought he was hiding some thing.

He was right.  Now, it seems to me that designing receiver is 10 times harder than transmitter.  The transmitter just transmit things out, but receiver have to take care all kind of thing, like mom.  It has to due with synchronization, multipath, equalization, frequency and time correction, message decoding and correction.  All this stuffs are hard.  This class end today.  We felt a little not happy because we don’t have enough chance to tackle one of these thing. We strongly believe we could implement one of these and make it work in the near future.
       

