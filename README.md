<h1> Brief on Phase-Locked-Loop-workshop-using-skywater-130nm </h1>
<h4 align="justify"> The basic agenda of this workshop was to design a Phase-Locked Loop using an Open-Source Google-Skywater 130nm node. In this workshop, tools like are Ngspice and Magic are used. Considering a layout and an end product(IC) perspective, the mathematical design aspects are totally avoided here, thus making this workshop a learn-by-doing program. A pre-requisites of Basic Electronics is sufficient.</h4>

<h1> CONTENTS </h1>
   
   i. [What is Phase Locked Loop](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#what-is-phase-locked-loop)
   
   ii. [Conceptual Framework](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#conceptual-framework)
   
   iii. [PLL Classification](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#pll-classification)
   
   iv. [Frequency synthesis: the journey so far](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#frequency-synthesis:-the-journey-so-far)
    
   ## *Day 1 – PLL Theory and Lab setup*
    
    
   1. [Introduction to PLL](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#introduction-to-pll)
                
   2. [Phase Frequency Detector](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#phase-frequency-detector)
         
   3. [Brief about Charge Pump](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#brief-about-charge-pump)
         
   4. [Introduction to VCO and Frequency Divider](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#introduction-to-vco-and-frequency-divider)
         
   5. [Tool setup and design flow](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#tool-setup-and-design-flow)
         
   6. [PDK, Design specifications and pre layout Simulation](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#pdk,-design-specifications-and-pre-layout-simulation)
         
   7. [Circuit Design and Simulation](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#circuit-design-and-simulation)

## *Day 2 – PLL Labs with pre and post-layout simulations*         
   
   8. [PLL components circuit design](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#pll-components-circuit-design)


   9. [Combining all the sub blocks to create a PLL](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#combining-all-the-sub-blocks-to-create-a-pll)

   10. [Pre Layout Output of PLL](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#pre-layout-output-of-pll)

   11. [Layout design](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#layout-design)

   12. [Parasitics Extraction](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#parasitics-extraction)
   
   13. [Post Layout Simulations](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#post-layout-simulations)
 
 
 <h1> What is Phase Locked Loop </h1>
<h4 align="justify">Today‟s era of the Integrated circuit (IC) has really changed the way how we see the outer world. The journey of Integrated Circuit (IC) technology is about to reach its zenith soon. IC technology has become an integrated part of today‟s life. These developments are mainly because of the rapid advancements in digital technology
which has paved the way for such advancements. Scaling capability, reduced area, and minimum power consumption are the key attributes of Metal oxide semiconductor (MOS) technology, but what does has made the CMOS technology a consistent performer in the technology marathon is its agility to different processes, easy re-design, and effortlessness behavior even in the sub-threshold region. Since many analog blocks are inevitably being used in several mixed-mode IC designs, the performance metrics of such analog blocks favor a thorough re-design and hence will be a crucial step in the entire fabrication process. To overcome this glitch the complete digitization of the entire process has carved the way for many opportunities in the system on chips (SoCs). The main advantage of digital technology is its versatility in adopting any technological scaling as and when the design process changes. Advantages like better reusability with the minimized area, power, and better integration are the results of a digital intensive approach as quoted by Homayoun and Razavi in 2013. (http://www.seas.ucla.edu/brweb/papers/Journals/HRTCASMar13.pdf). One of the foremost blocks that has seen a tremendous rise in its usage in the recent past is a phase-locked loop (PLL) system in communication systems. The most widely used component in almost all communication system blocks for frequency synthesis and data recovery is PLL. Cell phones, Laptops, Televisions, communication devices are a few examples that depend on PLLs to perform properly. </h4> 
  
<h1> Conceptual Framework </h1>
<h4 align="justify">The RF transceivers demand good battery life with minimal power consumption. Typically most of the RF transceiver circuits spend 90% of their time in standby mode and only 10 in active mode. Hence the demand for low power consumption ads key value in the design of RF transceivers. The most inevitable block that is present in the transceivers generating a local signal is the frequency synthesizer or phase-locked loop. A receiver waits for the incoming wake-up signal and upon detection, the PLL should wake up and achieve the process of locking in a minimal time of the active time frame duration. The PLL circuit is by virtue a closedloop system. Though it has a simple operating principle, the PLL technique received much attention since it was first conceived by the French scientist De Bellescise in his paper, "La Reception Synchrone", in 1932. The PLL started as a discrete element implementation and transformed into a partially integrated circuit, then to a fully integrated analog circuit, and finally to an all-digital circuit in recent years. Most of the early PLL implementations are analog circuits.</h4>

<h4 align="justify"> The early digital form of the PLL often refers to the digital implementation with only a few building blocks due to the prohibitively high cost of the digital elements. The cost for the integrated circuit has been reduced to the point where the cost for the digital circuit is much less than the cost for the analog counterpart of the same functionality or the cost for the extra transistors required by the digital circuit can be ignored. This makes it possible to convert every single component in the PLL into a digital block.</h4>
  
<h4 align="justify"> In ADPLL each building blocks are implemented digitally and have a digital interface between them and have the state of the art mechanism to mitigate all
the drawbacks of analog PLL. The ADPLL itself is also fully integrated with other bigger digital circuits, such as digital signal processing (DSP), on a single die. Most often, there is more than one ADPLL in a single chip. </h4>


  <h1> PLL Classification </h1>
<h4 align="justify">  The author Roland Best(https://www.amazon.in/Phase-Locked-Loops-Simulation-Applications/dp/0071493751) Classifies PLL into four major categories
  
    1. Analog PLL (LPLL)  
    2. Classical Digital PLL (DPLL)  
    3. All Digital PLL (ADPLL)  
    4. Software PLL (SPLL)  
The LPSS or analog PLL is one of the oldest types of PLL. The Analog multiplier is typically used as a phase detector. The digital PLL is the digital version of analog-PLL with a digital phase detector. The all-digital PLL is typically different from any other PLLs mentioned so far. The ADPLL is completely digital having either all digital components or all digital (discrete-time) signals. Putting all the components of ADPLL together poses a greater challenge. The VCO is replaced with a DCO. Phase frequency Detectors are used for phase and frequency detection when speed is the key concern for any application. The Time to Digital Converter is sometimes used as an alternative for PFD in some of the architectures. </h4>
  
  <h1> Frequency synthesis: the journey so far </h1>
<h4 align="justify">The expectation from the RF industry is always been on the higher side especially when it comes to delivering high performing, cost-effective, and low power
consuming synthesizer designs. With the advent of frequency synthesizers many decades ago, one most challenging question that comes to one‟s mind is, do we have
ideal synthesizer architecture? Although all synthesizers show critical contrasts because of particular applications, they do have certain common requirements - low
power consumption, wide frequency range, good switching speed. Of all the concerns, the major worry is the power consumption and spectral purity of the signal. One of the prime factors of the synthesizer that influence by and large system‟s performance is the frequency switching speed. The frequency switching speed and time of the synthesizers have become very vital in the present scenario, as this time cannot be utilized for processing the data. As a result, because of the ongoing rise in the data rates of RF systems, many modern synthesizers are coming up which have good switching speed. Another major criterion with the frequency synthesizers is its cost, as it limits the designer‟s choice in selecting appropriate designs that can be used. The frequency synthesizer‟s characteristics depend a lot on a particular architecture. 
  Frequency synthesis majorly has three conventional techniques, 
  
      First one being the phaselocked loop synthesis, or indirect synthesis, which is found in almost all sophisticated systems. This is a feedback system.  
      The second kind of technique is called as direct analog (DA) frequency synthesis. This technique does not involve feedback and has the best spectral purity almost close to the carrier. The DA procedure is substantially more complex than PLL to execute and is along these lines more costly. 
      The third one is direct digital synthesis (DDS) or Numerically Controlled Oscillator was invented almost 35 years ago but due to advancements in digital technology, it has become popular in the last decade or so.  
  
  To give better insight, the synthesizers can be classified as direct and indirect architectures. Figure below gives a broader classification </h4>
 
 ![Freq Syn classification](https://user-images.githubusercontent.com/91013053/134052284-ec1060c3-a718-4348-ad6b-6c29f15c5909.png)

       
   
   <h1> Introduction to PLL </h1>

<h4 align="justify">
   
   
   Frequencies in communication systems = ACCURATE + AGILE
   1. QUARTZ CRYSTALS are Accurate but have narrow range.
   2. VOLTAGE CONTROLLED OSCILLATORS are Agile but unstable, as any change in the voltage will lead to instability. Hence, We need a technique to join these two.
   So we need to build a system which can mimic the oscillations of the QUARTZ crystal that controls the VCO.
   3. This can be obtained through what we call as FREQUENCY SYNTHESIS or PHASE LOCKED LOOPS
   4. Generating a range of frequencies from a single reference frequency is known ad Frequency Synthesis.
   5. More precisely, a PLL synchronizes the output phase and frequency of a controllable oscillator to match the output phase and frequency of a reference oscillator. 
   6. The simplest analog PLL consists of four basic functional blocks.
</h4>

![image](https://user-images.githubusercontent.com/91013053/134051674-65564303-ca0a-462b-82be-4827d4515a44.png)

   <h4 align="justify"> These following two concepts usually provide enough information to analyze the loop dynamics of the PLL. The two concepts are:
1. The order of the PLL is the number of poles in the loop
2. The type of the PLL is the number of integrators in the loop
   
   VCO has a pole at origin. In addition, the transfer function also indicates that the VCO acts as an integrator.

   Thus, any VCO based PLL has to be at least 1st order and type 1.

   The additional order and type will increase as the number of Loop Filter poles increases.
   </h4>

   <h1> Phase Frequency Detector </h1>
 <h4 align="justify"> 
Whenever any signal leads or lags the other signal, the difference of lead and lag information also known as error signal becomes very important. The very job of
PFD is to produce this error signal between lead and lag signal. The following observations can be made w.r.t PFD,

   Of the entire blocks that are present in PLL, the PFD circuit is very important as the signals are compared in this block only, and the key feature of any ADPLL is
to see that the smallest of the small phase differences must also be detected and no edges must go undetectable.

   Key issues of concern while designing PFD

   1. The problem of the dead zone must be addressed while designing any PFD.
   2. Linearity range - the designed PFD must maintain the linear relationship, between input and output.
   3. The blind zone arising due to any transitions of the input signals must be taken care </h4>
   
   Figure below describes a TRI-STATE PFD with linear range of 2π 
   
   ![image](https://user-images.githubusercontent.com/91013053/134044030-84b12b99-51a3-4970-b0ae-b9e17c753584.png)

   
   
   <h4> Brief about Charge Pump </h4>
  
  The role of a CP in PLL is to convert the difference in phase or frequency which is measured digitally into an analog signal that can be used to control the VCO. It can be done by using current steering circuits.
    
    
   Analog PLL is also called as Charge pump PLL. 
    
   ![image](https://user-images.githubusercontent.com/91013053/134044734-afbc3e68-62d6-45d5-9e49-e3dba25f3519.png)

   ![image](https://user-images.githubusercontent.com/91013053/134044755-437af1fd-b195-4481-b8c6-de30238d65f2.png)

  
   <h4> LOOP FILTER:  
  
      The loop filter is usually in the form of a low pass filter 
   
- Suppresses the high frequency switching noise.
- Holds the charges to control VCO
      - However RC network is unstable, hence extra zero is added to stabilise (C2) </h4>
   
   
   ![image](https://user-images.githubusercontent.com/91013053/134045377-506ab025-9bf9-4180-af6e-11af5014d0f0.png)

  <h1> Introduction to VCO and Frequency Divider <h1>
  
   <h4> The most important component in the PLL is the VCO. It generates the output clock frequency according to the voltage provided from the Loop Filter. <h4>

   ![image](https://user-images.githubusercontent.com/91013053/134045581-16aef0d6-0ada-43aa-bc9f-3d1d7bbb57c1.png)

- Fosc  > Fref   then, Divide the Fosc &compare it with Fref

- Fosc  < Fref   then, Multiply the Fosc & compare it with Fref

- Fosc = Fref then, No need of Divider

<h1> Tool setup and design flow </h1>
  
Best to build any software tool from its source code, as it will be the latest version.

The following tools were used in this program:

Ngspice: For transistor level simulation
Magic: For layout design and parasitic extraction

## Installation Procedure for Ngspice 


Open the terminal and type
sudo apt-get install ngspice

## Installation Procedure for Magic: 
<h4>
- sudo apt-get update && sudo apt-get upgrade This step is used to update the OS.
              
- git clone git://opencircuitdesign.com/magic This step clones the Magic Repository
              
- sudo apt-get install csh This step installs the csh shell
              
- cd magic This step is to go into the cloned directory
              
- ./configure This step runs the configure script
              
- make This step runs the make command to compile
              
- sudo make install This step installs magic on the device
      </h4>
      
   <h1> PDK, Design specifications and pre-layout Simulation. </h1>

  
1. PDK is provided by the fabrication centres because thats where the transistors get fabricated.
2. The characteristics of those transistors in the technology node of interest are available to us through the scripts.
3. Other than transistor characteristics, a lot of information is available to help the design process.
4. The specifications give the operationg condition at which the PLL has to operate.
5. It is based on these specifications, that we will design the circuit.
6. We will use the simplified IP specifications from VSD for our PLL design:
    - Corner \- TT
    - Supply \- 1.8V
    - Room Temperature
    - VCO mode and PLL mode
    - Input Fmin = 5MHz and Fmax = 12.5MHz
    - Multiplier \- 8x
    - Jitter (RMS) <~ 20ns
    - Duty Cycle \- 50%
7. The first three specifications together are called as PVT corner or Process\-Voltage\-Temperature corner
8. Pre\-layout:
    - This phase is all about development and the transistor level simulation of the circuits.
    - In this phase all the circuits are developed in such a way that most of the disadvantages are already overcome.            
              
<h1> Circuit Design and Simulation </h1>
 
 <h2> Steps to install MAGIC </h2>
                      
<h4>                      

   1. The first step is to install ngspice using ubuntu's package manager
   
   2. We have to clone the google skywater pdk.

   3. Go to https://github.com/google/skywater-pdk

   - Click on libraries

   - Click sky130_fd_pr

   - Click latest @ f62031a


   4. In the right corner click on code and copy the link and use the command "git clone https://github.com/google/skywater-pdk-libs-sky130_fd_pr.git" in the terminal

   5. Then go to the folder skywater-pdk-libs-sky130_fd_pr manually in your machine

      -  enter the folder "cells" 

      -  In that enter "nfet_01v8" folder

   6. Copy the file "sky130_fd_pr__nfet_01v8__tt.pm3.spice" file.

      -  In the mean time create a new folder called spice_lib folder in the work_dir folder and paste that file in that folder.

      -  enter the folder "cells" 
   
      -  In that enter "pfet_01v8" folder

      -  copy the file "sky130_fd_pr__pfet_01v8__tt.pm3.spice" file and paste it in spice Lib folder.

   7. In skywater-pdk-libs-sky130_fd_pr/ folder enter models folder and then in parameters folder

   8. Copy invariant.spice file and lod.spice file and paste it in spice Lib folder.

   <h2> Create our own library by the name sky130.lib.</h2>

   Steps:
   -  Be in the terminal cd spice_lib
   -  Use the command nano skulib30.lib
   -  In that include all the 4 files copied in spice_lib folder usig the commands

   *comment:skylib.30
   
.include invariant.spice
   
.include lod.spice
   
.include sky130_fd_pr__nfet_01v8__tt.pm3.spice
   
.include sky130_fd_pr__pfet_01v8__tt.pm3.spice

   -  ctrl+s 

   -  you should see a message 5 lines have been written

   - ctrl+x

                      
                      
                      
 <h2> Steps to install MAGIC </h2>

   <h4>
- go to http://opencircuitdesign.com/

- on left panel, you wll see a tab called Magic, click on that, in that click on Donwload

- In that use the git link mentioned under the title "Source Distribution Git Repository"

- copy the link "git clone git://opencircuitdesign.com/magic" in the terminal.

- Now we need to install the dependencies, for that you will find the commands to install the depencies in the install page of magic website.

- go to https://github.com/RTimothyEdwards/open_pdks on browser                     
   </h4>                     
  
   
## *Day 2 – PLL Labs with pre and post layout simulations*
<h4 align="justify">

   On Day 2, pre-layout simulations & Post-Layout simulations were performed for all the components individually. 
   Upon Combining all the files a pre-layout & Post layout simulations were run to cross check the correctness of the PLL
   We then created the GDS file for the designed layout aleading to the final tapeout process.  
   </h4>
 
   <h1>PLL components circuit design</h1>
   
   <h2> Frequency Divider Block </h2>
   
   A circuit description ngspice for the frequency divider circuit was created.
   A spice file is just a text file with a .spice or .cir extension.
   To make the file use the following command in the terminal 
   - touch FreqDiv.cir.

   -  Now open the file using the file browser.
   -  The first line is always given as a comment and we gave the circuit name as the comment.
   -  Write the spice code in the file:


   Few highlighting part of the code

   v1 1 0 1.8

   v2 Clk 0 PULSE 0 1.8 1n 6p 6p 5ns 10ns 


   c1 6 0 10f

   .control

   tran 0.1ns 0.2us

   plot v(6) v(Clk)+2

here <h4 align=justyfy>
   For v2, each terms represent voltage1, voltage2, delay, rise time, fall time, pulse width, period respectively.

   .control tells the simulator to perform transient analysis with a sampling rate of 0.1ns for a time 0.2us.
   
   The plot v(6) v(Clk)+2 tells it what signals to plot.
   
   The control block ends with the .endc and the spice file ends with .end.
   </h4>
   
   <h2> Use the command ngspice FD.cir for simulation </h2>
   
   <h3> On similar lines we follow the procedure and simulate all the blocks of PLL viz, PFD, Charge Pump, VCO </h3>
   
   
   
   <h1> Combining all the sub blocks to create a PLL </h1>
   
   - Here we execute the combined spice file to get the result of entire PLL
   ```
   *PLL
.include sky130nm.lib

xx1 Clk_Ref Clk_Out_by_8 up down pd
xx2 up down VCtrl cp

*Loop Filter
r1 VCtrl rc1 490
c1 rc1 0 355f
r2 rc1 rc2 490
c2 rc2 0 350f
r3 rc2 rc3 490
c3 rc3 0 345f

xx3 rc3 Clk_Out vco

xx4 Clk_Out Clk_Out_by_2 fd
xx5 Clk_Out_by_2 Clk_Out_by_4 fd
xx6 Clk_Out_by_4 Clk_Out_by_8 fd

v1 Clk_Ref 0 PULSE 0 1.8 0 6ps 6ps 40ns 80ns

.ic v(VCtrl) = 0
.ic v(Clk_Out_by_2) = 0
.ic v(Clk_Out_by_4) = 1.8
.ic v(Clk_Out_by_8) = 0
.control
tran 0.1ns 180us
plot v(Clk_Ref) v(Clk_Out_by_8) v(Clk_Out_by_4)+2 v(Clk_Out_by_2)+4 v(Clk_Out)+6 v(up)+8 v(down)+10 v(VCtrl)+12
.endc

*PFD
.subckt pd Clk1 Clk2 up down 
xm1 1 clk1 3 1 sky130_fd_pr__pfet_01v8 l=150n w=640n 
xm2 3 clk1 4 0 sky130_fd_pr__nfet_01v8 l=150n w=1800n
xm3 4 clk2 0 0 sky130_fd_pr__nfet_01v8 l=150n w=360n

xm4 1 clk2 6 1 sky130_fd_pr__pfet_01v8 l=150n w=640n 
xm5 6 clk2 7 0 sky130_fd_pr__nfet_01v8 l=150n w=1800n
xm6 7 clk1 0 0 sky130_fd_pr__nfet_01v8 l=150n w=360n

xm7 8 clk1 3 0 sky130_fd_pr__nfet_01v8 l=150n w=2400n 
xm8 clk1 clk1 8 1 sky130_fd_pr__pfet_01v8 l=150n w=640n

xm11 upb 8 1 1 sky130_fd_pr__pfet_01v8 l=150n w=720n
xm12 upb 8 0 0 sky130_fd_pr__nfet_01v8 l=150n w=360n

xm15 up upb 1 1 sky130_fd_pr__pfet_01v8 l=150n w=720n
xm16 up upb 0 0 sky130_fd_pr__nfet_01v8 l=150n w=360n
  
xm9 9 clk2 6 0 sky130_fd_pr__nfet_01v8 l=150n w=2400n
xm10 clk2 clk2 9 1 sky130_fd_pr__pfet_01v8 l=150n w=640n

xm13 downb 9 1 1 sky130_fd_pr__pfet_01v8 l=150n w=720n
xm14 downb 9 0 0 sky130_fd_pr__nfet_01v8 l=150n w=360n

xm17 down downb 1 1 sky130_fd_pr__pfet_01v8 l=150n w=720n
xm18 down downb 0 0 sky130_fd_pr__nfet_01v8 l=150n w=360n


*output cap
*c1 up 0 6f
*c2 down 0 6f

v1 1 0 1.8
.ends pd


*CP
.subckt cp up down out
xm43 3 2 1 1 sky130_fd_pr__pfet_01v8 l=150n w=18u 
xm44 out downb 3 1 sky130_fd_pr__pfet_01v8 l=150n w=420n 
xm31 out up 7 0 sky130_fd_pr__nfet_01v8 l=150n w=420n
xm32 7 8 0 0 sky130_fd_pr__nfet_01v8 l=150n w=4.8u

xm33 2 2 1 1 sky130_fd_pr__pfet_01v8 l=150n w=420n 
xm34 8 8 0 0 sky130_fd_pr__nfet_01v8 l=150n w=420n

xm35 9 down 3 1 sky130_fd_pr__pfet_01v8 l=150n w=5400n 
xm36 9 9 0 0 sky130_fd_pr__nfet_01v8 l=150n w=420n

xm37 10 10 1 1 sky130_fd_pr__pfet_01v8 l=150n w=420n 
xm38 10 upb 7 0 sky130_fd_pr__nfet_01v8 l=150n w=5400n

xm39 1 down downb 1 sky130_fd_pr__pfet_01v8 l=150n w=720n 
xm40 0 down downb 0 sky130_fd_pr__nfet_01v8 l=150n w=360n 

xm41 1 up upb 1 sky130_fd_pr__pfet_01v8 l=150n w=720n 
xm42 0 up upb 0 sky130_fd_pr__nfet_01v8 l=150n w=360n 

*r1 out rc 200
*c1 rc 0 8f

v1 1 0 1.8
.ends cp


*VCO
.subckt vco in 17
xm1 10 16 3 10 sky130_fd_pr__pfet_01v8 l=150n w=420n
xm2 3 16 9 9  sky130_fd_pr__nfet_01v8 l=150n w=420n

xm3 10 3 4 10 sky130_fd_pr__pfet_01v8 l=150n w=420n
xm4 4 3 9 9 sky130_fd_pr__nfet_01v8 l=150n w=420n

xm5 10 4 12 10 sky130_fd_pr__pfet_01v8 l=150n w=420n
xm6 12 4 9 9 sky130_fd_pr__nfet_01v8 l=150n w=420n

xm11 10 12 13 10 sky130_fd_pr__pfet_01v8 l=150n w=420n
xm12 13 12 9 9 sky130_fd_pr__nfet_01v8 l=150n w=420n

xm13 10 13 14 10 sky130_fd_pr__pfet_01v8 l=150n w=420n
xm14 14 13 9 9 sky130_fd_pr__nfet_01v8 l=150n w=420n

xm15 10 14 15 10 sky130_fd_pr__pfet_01v8 l=150n w=420n
xm16 15 14 9 9 sky130_fd_pr__nfet_01v8 l=150n w=420n

xm17 10 15 16 10 sky130_fd_pr__pfet_01v8 l=150n w=2400n
xm18 16 15 9 9 sky130_fd_pr__nfet_01v8 l=150n w=1200n

xm7 10 5 1 1 sky130_fd_pr__pfet_01v8 l=150n w=1080n
xm8 5 5 1 1 sky130_fd_pr__pfet_01v8 l=150n w=840n
xm9 5 in 0 0 sky130_fd_pr__nfet_01v8 l=150n w=840n
xm10 9 in 0 0 sky130_fd_pr__nfet_01v8 l=150n w=1080n

xm19 1 16 11 1 sky130_fd_pr__pfet_01v8 l=150n w=720n
xm20 11 16 0 0 sky130_fd_pr__nfet_01v8 l=150n w=360n

xm21 1 11 17 1 sky130_fd_pr__pfet_01v8 l=150n w=720n
xm22 17 11 0 0 sky130_fd_pr__nfet_01v8 l=150n w=360n

*c1 11 0 24f
v1 1 0 1.8
.ends vco


*FD
.subckt fd Clk 10

xm1 1 2 3 1 sky130_fd_pr__pfet_01v8 l=150n w=720n 
xm2 0 2 3 0 sky130_fd_pr__nfet_01v8 l=150n w=360n 

xm3 3 Clkb 4 1 sky130_fd_pr__pfet_01v8 l=150n w=420n 
xm4 3 Clk 4 0 sky130_fd_pr__nfet_01v8 l=150n w=840n 

xm7 1 4 5 1 sky130_fd_pr__pfet_01v8 l=150n w=720n 
xm8 0 4 5 0 sky130_fd_pr__nfet_01v8 l=150n w=360n 

xm9 5 Clk 6 1 sky130_fd_pr__pfet_01v8 l=150n w=420n 
xm10 5 Clkb 6 0 sky130_fd_pr__nfet_01v8 l=150n w=640n 

xm11 1 6 2 1 sky130_fd_pr__pfet_01v8 l=150n w=720n 
xm12 0 6 2 0 sky130_fd_pr__nfet_01v8 l=150n w=360n 

xm13 1 Clk Clkb 1 sky130_fd_pr__pfet_01v8 l=150n w=720n 
xm14 0 Clk Clkb 0 sky130_fd_pr__nfet_01v8 l=150n w=360n 

xm15 7 6 1 1 sky130_fd_pr__pfet_01v8 l=150n w=720n 
xm16 7 6 0 0 sky130_fd_pr__nfet_01v8 l=150n w=360n

xm19 1 7 10 1 sky130_fd_pr__pfet_01v8 l=150n w=720n
xm20 10 7 0 0 sky130_fd_pr__nfet_01v8 l=150n w=360n 


*c1 7 0 18f
v1 1 0 1.8
.ends fd
 ```
   <h2> Pre Layout Output of PLL </h2>
   
   ![pre layout full PLL](https://user-images.githubusercontent.com/91013053/134059671-2dff2ddc-4306-4730-9df9-33632b85dc86.jpg)

   
<h1> Layout design </h1>

   <h4 align=left>

      1.Enter the directory containing the "sky130A.tech" file using the "cd" commands.

      2.Type magic -T sky130A.tech in the terminal window.

      3.Two files will open up - one is magic layout editor and another is console window to check the DRCs.

      4. In the magic window we can draw the layout.
   
      (Refer this page for detailed description on usage of Magic tool http://opencircuitdesign.com/magic/tutorials/tut1.html(

   <h4>
   
<h1> Parasitics Extraction </h1>
<h4 align=left>


Lets say, we want to know the parasitics of FD(Frequency Divider) block, use the command i to select all the layout in the current window then in the console type 
*extract all*

   
   
   *A message Extracting FD into FD.ext* will be displayed

   
   Then use the commands
   
   
   
   *ext2spice cthresh 0 rthresh 0*

   *ext2spice*
   

*A message exttospice finished* will be displayed.

   <h3> Few points to note: </h3>

   -  In the command "ext2spice cthresh 0 rthresh 0"

      
   
      cthresh 0 rthresh 0 --> means any amount of resistive and capacitive effect present will be extracted.

   -  If we mention as 1fF means extarct the paasitice greater than 1fF.  


   -  If we open up the FD.spice file which is the extracted version, we can see lot of additional capacitances extracted by magic, these are parasitics.
      
   -  Few other parameters in this file are area of drain(ad), perimeter of drain(pd) etc.

   - We also see a scale factor being mentined on top.

   - .option scale indicates a multiplication factor thae needs to be multiplied with all the parameter.

   - We know that the minimum length when we use skywater is L=150nm, and if we mention L=15 the scale factor must be choosen as 10n

   -  A total of 
         84 parasitic capacitance for VCO
         
         43 for FD
         
         47 for PFD
         
         68 for CP
 
   can be observed from .spice files.

<h1> Post Layout Simulations </h1>     
      
<h4> 
For post layout simulation of PFD block

   run the command
   
   nano PFD_postlay.cir and type the following

 ```  
.include spice_lib/sky130.lib
.include PFD.spice

XX1 Ref_clk Up Down clk2 GND VDD PFD

v1 VDD GND 1.8
v2 Ref_clk 0 PULSE 0 1.8 0n 6p 6p 40ns 80ns
v3 Clk2 0 PULSE 0 1.8 1n 6p 6p 40ns 80ns

.control
tran 0.1ns 5us
plot v(Up) v(Down)+2 v(Ref_clk)+4 v(clk2)+6
.endc
.end
```   
   
<h3> Similarly we do it for other blocks as well </h2>   

   </h2> The final spice code for the PLL to perform post layout simulation is </h2> 

Post layout code

 ```
*PLL
.include sky130nm.lib
.option scale = 0.01u
xx1 Clk_Ref Clk_Out_by_8 up down pd
xx2 up down VCtrl cp

*Loop Filter
r1 VCtrl rc1 490
c1 rc1 0 215f
r2 rc1 rc2 490
c2 rc2 0 210f
r3 rc2 rc3 490
c3 rc3 0 205f

xx3 rc3 Clk_Out vco

xx4 Clk_Out Clk_Out_by_2 fd
xx5 Clk_Out_by_2 Clk_Out_by_4 fd
xx6 Clk_Out_by_4 Clk_Out_by_8 fd

v1 Clk_Ref 0 PULSE 0 1.8 0 6ps 6ps 40ns 80ns

.ic v(VCtrl) = 0
.ic v(Clk_Out_by_2) = 0
.ic v(Clk_Out_by_4) = 1.8
.ic v(Clk_Out_by_8) = 0
.control
tran 0.1ns 180us
plot v(Clk_Ref) v(Clk_Out_by_8) v(Clk_Out_by_4)+2 v(Clk_Out_by_2)+4 v(Clk_Out)+6 v(up)+8 v(down)+10 v(VCtrl)+12
plot v(Clk_Ref) v(Clk_Out_by_8)+2
.endc

*PFD
.subckt pd Clk_Ref Clk2 Up Down 
XM1000 VDD a_7_412# a_460_368# VDD sky130_fd_pr__pfet_01v8 w=72 l=15
+  ad=1664.03 pd=142.146 as=2232 ps=206
XM1001 GND a_7_412# a_460_368# GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=842.4 pd=91.8 as=1116 ps=134
XM1002 a_264_92# Clk2 a_208_92# GND sky130_fd_pr__nfet_01v8 w=240 l=15
+  ad=7920 pd=546 as=5314.29 ps=321.143
XM1003 VDD Clk2 a_208_92# VDD sky130_fd_pr__pfet_01v8 w=65 l=15
+  ad=1502.25 pd=128.326 as=2145 ps=196
XM1004 Up a_460_368# GND GND sky130_fd_pr__nfet_01v8 w=48 l=15
+  ad=1392 pd=154 as=1123.2 ps=122.4
XM1005 GND a_264_92# a_485_83# GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=842.4 pd=91.8 as=1116 ps=134
XM1006 a_151_92# Clk_Ref GND GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=1044 pd=74 as=842.4 ps=91.8
XM1007 VDD a_264_92# a_485_83# VDD sky130_fd_pr__pfet_01v8 w=72 l=15
+  ad=1664.03 pd=142.146 as=2232 ps=206
XM1008 Down a_485_83# VDD VDD sky130_fd_pr__pfet_01v8 w=96 l=15
+  ad=2880 pd=252 as=2218.71 ps=189.528
XM1009 a_7_412# Clk_Ref a_7_356# GND sky130_fd_pr__nfet_01v8 w=240 l=15
+  ad=7920 pd=546 as=5314.29 ps=321.143
XM1010 Up a_460_368# VDD VDD sky130_fd_pr__pfet_01v8 w=96 l=15
+  ad=2880 pd=252 as=2218.71 ps=189.528
XM1011 VDD Clk_Ref a_7_356# VDD sky130_fd_pr__pfet_01v8 w=65 l=15
+  ad=1502.25 pd=128.326 as=2145 ps=196
XM1012 Down a_485_83# GND GND sky130_fd_pr__nfet_01v8 w=48 l=15
+  ad=1392 pd=154 as=1123.2 ps=122.4
XM1013 Clk_Ref Clk_Ref a_7_412# VDD sky130_fd_pr__pfet_01v8 w=65 l=15
+  ad=2145 pd=196 as=2145 ps=196
XM1014 a_7_299# Clk2 GND GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=1044 pd=74 as=842.4 ps=91.8
XM1015 a_208_92# Clk2 a_151_92# GND sky130_fd_pr__nfet_01v8 w=180 l=15
+  ad=3985.71 pd=240.857 as=5220 ps=370
XM1016 Clk2 Clk2 a_264_92# VDD sky130_fd_pr__pfet_01v8 w=65 l=15
+  ad=2145 pd=196 as=2145 ps=196
XM1017 a_7_356# Clk_Ref a_7_299# GND sky130_fd_pr__nfet_01v8 w=180 l=15
+  ad=3985.71 pd=240.857 as=5220 ps=370
C0 Down Up 0.00fF
C1 a_264_92# VDD 0.13fF
C2 a_208_92# a_485_83# 0.02fF
C3 a_460_368# Clk_Ref 0.00fF
C4 Clk2 a_485_83# 0.06fF
C5 a_7_412# VDD 0.14fF
C6 Up VDD 0.13fF
C7 a_460_368# a_485_83# 0.01fF
C8 Down VDD 0.56fF
C9 a_264_92# a_208_92# 0.49fF
C10 a_264_92# Clk2 0.27fF
C11 a_264_92# Clk_Ref 0.01fF
C12 a_7_412# a_208_92# 0.01fF
C13 a_7_412# Clk2 0.01fF
C14 a_7_412# Clk_Ref 0.19fF
C15 a_264_92# a_460_368# 0.00fF
C16 a_7_412# a_7_356# 0.49fF
C17 a_264_92# a_485_83# 0.37fF
C18 a_7_412# a_460_368# 0.34fF
C19 Down Clk2 0.02fF
C20 a_7_412# a_485_83# 0.00fF
C21 a_460_368# Up 0.16fF
C22 Up a_485_83# 0.00fF
C23 a_208_92# VDD 0.27fF
C24 Clk2 VDD 0.08fF
C25 VDD Clk_Ref 0.20fF
C26 Down a_485_83# 0.16fF
C27 a_7_356# VDD 0.15fF
C28 a_7_412# a_264_92# 0.03fF
C29 a_460_368# VDD 0.20fF
C30 VDD a_485_83# 0.31fF
C31 a_208_92# Clk2 0.05fF
C32 a_208_92# Clk_Ref 0.01fF
C33 a_7_412# Up 0.01fF
C34 Clk2 Clk_Ref 0.11fF
C35 Down a_264_92# 0.01fF
C36 a_7_356# a_208_92# 0.02fF
C37 a_7_356# Clk2 0.01fF
C38 a_7_356# Clk_Ref 0.10fF
C39 Up GND 0.22fF
C40 VDD GND 4.13fF
C41 a_485_83# GND 0.34fF
C42 a_264_92# GND 0.52fF
C43 a_208_92# GND 0.10fF
C44 a_7_356# GND 0.34fF
C45 a_460_368# GND 0.34fF
C46 a_7_412# GND 0.65fF


*output cap
*c1 up 0 6f
*c2 down 0 6f

v1 VDD GND 1.8
.ends pd


*CP
.subckt cp Up Down Out
XM1000 a_174_531# a_127_486# a_248_475# VDD sky130_fd_pr__pfet_01v8 w=1800 l=15
+  ad=59400 pd=3728.85 as=47294.2 ps=2895.72
XM1001 GND a_340_202# a_462_191# GND sky130_fd_pr__nfet_01v8 w=480 l=15
+  ad=15785.8 pd=1205.27 as=10416.3 ps=592.994
XM1002 a_248_475# a_134_73# Out VDD sky130_fd_pr__pfet_01v8 w=42 l=15
+  ad=1103.53 pd=67.5667 as=1386 ps=150
XM1003 a_134_73# Down GND GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=1188 pd=138 as=1183.94 ps=90.395
XM1004 VDD ENb a_31_494# VDD sky130_fd_pr__pfet_01v8 w=60 l=15
+  ad=2023.9 pd=185.854 as=2340 ps=198
XM1005 a_248_475# Down a_248_427# VDD sky130_fd_pr__pfet_01v8 w=540 l=15
+  ad=14188.3 pd=868.715 as=17820 ps=1146
XM1006 a_258_74# Up GND GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=1188 pd=138 as=1183.94 ps=90.395
XM1007 GND a_340_202# a_340_202# GND sky130_fd_pr__nfet_01v8 w=44 l=15
+  ad=1447.03 pd=110.483 as=1452 ps=154
XM1008 a_462_143# a_462_143# VDD VDD sky130_fd_pr__pfet_01v8 w=42 l=15
+  ad=1386 pd=150 as=1416.73 ps=130.098
XM1009 a_174_531# a_127_486# a_127_486# VDD sky130_fd_pr__pfet_01v8 w=44 l=15
+  ad=1452 pd=91.1497 as=1452 ps=154
XM1010 Out Up a_462_191# GND sky130_fd_pr__nfet_01v8 w=42 l=15
+  ad=1386 pd=150 as=911.424 ps=51.887
XM1011 a_248_427# a_248_427# GND GND sky130_fd_pr__nfet_01v8 w=42 l=15
+  ad=1386 pd=150 as=1381.26 ps=105.461
XM1012 a_462_191# a_258_74# a_462_143# GND sky130_fd_pr__nfet_01v8 w=540 l=15
+  ad=11718.3 pd=667.119 as=17820 ps=1146
XM1013 a_258_74# Up VDD VDD sky130_fd_pr__pfet_01v8 w=72 l=15
+  ad=2376 pd=210 as=2428.68 ps=223.024
XM1014 a_134_73# Down VDD VDD sky130_fd_pr__pfet_01v8 w=72 l=15
+  ad=2376 pd=210 as=2428.68 ps=223.024
C0 a_258_74# VDD 0.18fF
C1 VDD Up 0.21fF
C2 a_248_427# Out 0.00fF
C3 a_258_74# Up 0.09fF
C4 a_462_191# a_340_202# 0.01fF
C5 a_134_73# Down 0.12fF
C6 Down ENb 0.00fF
C7 a_462_191# a_462_143# 0.72fF
C8 a_134_73# VDD 0.16fF
C9 a_248_475# a_248_427# 0.58fF
C10 VDD ENb 0.01fF
C11 a_174_531# a_248_427# 0.25fF
C12 a_134_73# a_258_74# 0.05fF
C13 a_134_73# Up 0.41fF
C14 VDD Out 1.29fF
C15 a_462_191# a_248_427# 0.02fF
C16 a_127_486# Down 0.03fF
C17 a_462_143# a_248_427# 0.01fF
C18 Out Up 0.03fF
C19 a_127_486# VDD 0.05fF
C20 a_174_531# Down 0.02fF
C21 a_248_475# VDD 1.18fF
C22 a_174_531# VDD 2.61fF
C23 a_340_202# VDD 0.02fF
C24 a_340_202# a_258_74# 0.13fF
C25 a_340_202# Up 0.02fF
C26 a_462_191# VDD 0.13fF
C27 a_134_73# Out 0.05fF
C28 a_174_531# a_31_494# 0.12fF
C29 a_462_143# VDD 0.23fF
C30 a_462_191# a_258_74# 0.00fF
C31 a_462_191# Up 0.09fF
C32 a_258_74# a_462_143# 0.02fF
C33 a_462_143# Up 0.08fF
C34 a_127_486# ENb 0.01fF
C35 a_248_427# Down 0.00fF
C36 a_134_73# a_248_475# 0.02fF
C37 a_248_427# VDD 0.14fF
C38 a_134_73# a_174_531# 0.01fF
C39 a_134_73# a_340_202# 0.00fF
C40 a_174_531# ENb 0.01fF
C41 a_258_74# a_248_427# 0.00fF
C42 a_248_475# Out 0.40fF
C43 a_174_531# Out 0.24fF
C44 a_127_486# a_248_475# 0.02fF
C45 a_462_191# Out 0.04fF
C46 a_127_486# a_174_531# 0.13fF
C47 Down VDD 0.05fF
C48 a_462_143# Out 0.02fF
C49 a_134_73# a_248_427# 0.09fF
C50 a_258_74# Down 0.00fF
C51 Down Up 0.15fF
C52 a_174_531# a_248_475# 2.05fF
C53 Up GND 1.42fF
C54 Out GND 2.98fF
C55 VDD GND 0.08fF
C56 a_462_143# GND 0.58fF
C57 a_462_191# GND 0.58fF
C58 a_340_202# GND 0.31fF
C59 a_258_74# GND 0.51fF
C60 a_134_73# GND 2.42fF
C61 a_248_427# GND 0.69fF
C62 a_248_475# GND 0.49fF
C63 a_127_486# GND 0.24fF
C64 a_174_531# GND 1.49fF

*r1 out rc 200
*c1 rc 0 8f

v2 ENb 0 0
v1 VDD GND 1.8
.ends cp


*VCO
.subckt vco VCtrl Clk_Out
XM1000 GND VCtrl a_19_462# GND sky130_fd_pr__nfet_01v8 w=84 l=15
+  ad=2436 pd=227.415 as=2436 ps=226
XM1001 a_653_144# a_553_144# a_109_144# GND sky130_fd_pr__nfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=124.6
XM1002 a_453_144# a_353_144# a_109_144# GND sky130_fd_pr__nfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=124.6
XM1003 a_553_144# a_453_144# a_109_144# GND sky130_fd_pr__nfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=124.6
XM1004 a_353_144# a_253_144# a_109_144# GND sky130_fd_pr__nfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=124.6
XM1005 a_253_144# a_153_144# a_109_144# GND sky130_fd_pr__nfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=124.6
XM1006 a_153_144# a_109_205# a_109_144# GND sky130_fd_pr__nfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=124.6
XM1007 Clk_Out a_109_205# a_393_418# VDD sky130_fd_pr__pfet_01v8 w=108 l=15
+  ad=3132 pd=274 as=3185.05 ps=291.789
XM1008 a_109_205# a_653_144# a_109_253# VDD sky130_fd_pr__pfet_01v8 w=240 l=15
+  ad=7200 pd=540 as=6960 ps=665.6
XM1009 a_653_144# a_553_144# a_109_253# VDD sky130_fd_pr__pfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=116.48
XM1010 a_109_205# a_653_144# a_109_144# GND sky130_fd_pr__nfet_01v8 w=120 l=15
+  ad=3480 pd=298 as=3480 ps=356
XM1011 a_453_144# a_353_144# a_109_253# VDD sky130_fd_pr__pfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=116.48
XM1012 a_553_144# a_453_144# a_109_253# VDD sky130_fd_pr__pfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=116.48
XM1013 a_353_144# a_253_144# a_109_253# VDD sky130_fd_pr__pfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=116.48
XM1014 a_393_418# ENb VDD VDD sky130_fd_pr__pfet_01v8 w=42 l=15
+  ad=1238.63 pd=113.474 as=1386 ps=150
XM1015 GND VCtrl a_109_144# GND sky130_fd_pr__nfet_01v8 w=108 l=15
+  ad=3132 pd=292.39 as=3132 ps=320.4
XM1016 a_253_144# a_153_144# a_109_253# VDD sky130_fd_pr__pfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=116.48
XM1017 a_153_144# a_109_205# a_109_253# VDD sky130_fd_pr__pfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=116.48
XM1018 Clk_Out a_109_205# GND GND sky130_fd_pr__nfet_01v8 w=54 l=15
+  ad=1566 pd=166 as=1566 ps=146.195
XM1019 a_393_418# a_19_462# a_19_462# VDD sky130_fd_pr__pfet_01v8 w=84 l=15
+  ad=2477.26 pd=226.947 as=2436 ps=226
XM1020 a_393_418# a_19_462# a_109_253# VDD sky130_fd_pr__pfet_01v8 w=108 l=15
+  ad=3185.05 pd=291.789 as=3132 ps=299.52
C0 a_353_144# a_453_144# 0.12fF
C1 a_353_144# a_253_144# 0.12fF
C2 a_19_462# a_453_144# 0.01fF
C3 a_653_144# Clk_Out 0.03fF
C4 a_109_205# a_393_418# 0.23fF
C5 a_19_462# VCtrl 0.04fF
C6 a_19_462# ENb 0.01fF
C7 VDD a_453_144# 0.02fF
C8 VDD a_253_144# 0.02fF
C9 a_653_144# a_393_418# 0.01fF
C10 a_109_205# a_553_144# 0.19fF
C11 VDD VCtrl 0.01fF
C12 VDD ENb 0.14fF
C13 a_109_205# a_109_144# 0.22fF
C14 a_353_144# VDD 0.02fF
C15 a_19_462# VDD 0.43fF
C16 a_653_144# a_553_144# 0.11fF
C17 a_653_144# a_109_144# 0.17fF
C18 a_109_205# a_109_253# 0.31fF
C19 a_393_418# a_453_144# 0.02fF
C20 a_653_144# a_109_253# 0.17fF
C21 a_393_418# ENb 0.36fF
C22 a_553_144# a_453_144# 0.12fF
C23 Clk_Out VDD 0.01fF
C24 a_393_418# a_353_144# 0.01fF
C25 a_109_205# a_153_144# 0.21fF
C26 a_109_144# a_453_144# 0.18fF
C27 a_393_418# a_19_462# 0.28fF
C28 a_109_144# a_253_144# 0.18fF
C29 ENb a_553_144# 0.00fF
C30 VCtrl a_109_144# 0.11fF
C31 a_393_418# VDD 0.49fF
C32 a_353_144# a_553_144# 0.04fF
C33 a_109_253# a_453_144# 0.19fF
C34 a_353_144# a_109_144# 0.18fF
C35 a_19_462# a_553_144# 0.00fF
C36 a_109_253# a_253_144# 0.18fF
C37 a_19_462# a_109_144# 0.01fF
C38 ENb a_109_253# 0.10fF
C39 VDD a_553_144# 0.02fF
C40 VDD a_109_144# 0.38fF
C41 a_353_144# a_109_253# 0.19fF
C42 a_19_462# a_109_253# 0.05fF
C43 a_393_418# Clk_Out 0.13fF
C44 VDD a_109_253# 0.13fF
C45 a_153_144# a_253_144# 0.12fF
C46 a_153_144# VCtrl 0.00fF
C47 Clk_Out a_109_144# 0.01fF
C48 a_153_144# a_353_144# 0.04fF
C49 a_393_418# a_553_144# 0.01fF
C50 Clk_Out a_109_253# 0.03fF
C51 a_109_205# a_653_144# 0.26fF
C52 a_153_144# VDD 0.02fF
C53 a_393_418# a_109_253# 0.33fF
C54 a_109_144# a_553_144# 0.18fF
C55 a_109_253# a_553_144# 0.18fF
C56 a_109_144# a_109_253# 0.33fF
C57 a_109_205# a_453_144# 0.15fF
C58 a_109_205# a_253_144# 0.17fF
C59 a_109_205# VCtrl 0.00fF
C60 a_109_205# ENb 0.07fF
C61 a_653_144# a_453_144# 0.04fF
C62 a_109_205# a_353_144# 0.15fF
C63 a_109_205# a_19_462# 0.00fF
C64 a_653_144# ENb 0.03fF
C65 a_153_144# a_109_144# 0.24fF
C66 a_109_205# VDD 0.25fF
C67 a_153_144# a_109_253# 0.17fF
C68 a_653_144# VDD 0.02fF
C69 a_453_144# a_253_144# 0.04fF
C70 a_109_205# Clk_Out 0.13fF
C71 VDD GND 0.09fF
C72 VCtrl GND 0.28fF
C73 a_553_144# GND 0.31fF
C74 a_453_144# GND 0.31fF
C75 a_353_144# GND 0.31fF
C76 a_253_144# GND 0.33fF
C77 a_153_144# GND 0.32fF
C78 a_109_205# GND 1.62fF
C79 a_109_253# GND 1.89fF
C80 a_109_144# GND 1.78fF
C81 a_653_144# GND 0.33fF
C82 a_393_418# GND 0.66fF
C83 a_19_462# GND 1.44fF

*c1 11 0 24f
v2 ENb 0 0
v1 VDD GND 1.8
.ends vco


*FD
.subckt fd Clk_In Clk_Out

XM1000 a_79_75# Clk_In VDD VDD sky130_fd_pr__pfet_01v8 w=72 l=15
+  ad=2088 pd=202 as=1824 ps=170.667
XM1001 GND a_597_66# a_787_62# GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=912 pd=110.667 as=1116 ps=134
XM1002 a_332_67# a_79_75# a_190_75# VDD sky130_fd_pr__pfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=126.737
XM1003 a_463_74# a_332_67# VDD VDD sky130_fd_pr__pfet_01v8 w=72 l=15
+  ad=2088 pd=217.263 as=1824 ps=170.667
XM1004 a_79_75# Clk_In GND GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=1044 pd=130 as=912 ps=110.667
XM1005 a_190_75# a_143_127# GND GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=1044 pd=106.8 as=912 ps=110.667
XM1006 a_143_127# a_597_66# VDD VDD sky130_fd_pr__pfet_01v8 w=72 l=15
+  ad=2088 pd=202 as=1824 ps=170.667
XM1007 a_597_66# a_79_75# a_463_74# GND sky130_fd_pr__nfet_01v8 w=84 l=15
+  ad=2436 pd=226 as=2436 ps=249.2
XM1008 a_143_127# a_597_66# GND GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=1044 pd=130 as=912 ps=110.667
XM1009 VDD a_597_66# a_787_62# VDD sky130_fd_pr__pfet_01v8 w=72 l=15
+  ad=1824 pd=170.667 as=2232 ps=206
XM1010 Clk_Out a_787_62# GND GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=1044 pd=130 as=912 ps=110.667
XM1011 a_190_75# a_143_127# VDD VDD sky130_fd_pr__pfet_01v8 w=72 l=15
+  ad=2088 pd=217.263 as=1824 ps=170.667
XM1012 a_332_67# Clk_In a_190_75# GND sky130_fd_pr__nfet_01v8 w=84 l=15
+  ad=2436 pd=226 as=2436 ps=249.2
XM1013 a_597_66# Clk_In a_463_74# VDD sky130_fd_pr__pfet_01v8 w=42 l=15
+  ad=1218 pd=142 as=1218 ps=126.737
XM1014 Clk_Out a_787_62# VDD VDD sky130_fd_pr__pfet_01v8 w=72 l=15
+  ad=2143 pd=204 as=1824 ps=170.667
XM1015 a_463_74# a_332_67# GND GND sky130_fd_pr__nfet_01v8 w=36 l=15
+  ad=1044 pd=106.8 as=912 ps=110.667
C0 VDD a_143_127# 0.38fF
C1 VDD Clk_Out 0.10fF
C2 a_332_67# a_463_74# 0.12fF
C3 a_332_67# a_190_75# 0.28fF
C4 Clk_Out a_143_127# 0.04fF
C5 VDD a_79_75# 0.37fF
C6 Clk_In a_597_66# 0.17fF
C7 a_79_75# a_143_127# 0.84fF
C8 VDD a_463_74# 0.19fF
C9 VDD a_190_75# 0.22fF
C10 a_463_74# a_143_127# 0.21fF
C11 a_190_75# a_143_127# 0.20fF
C12 VDD a_787_62# 0.21fF
C13 a_463_74# a_79_75# 0.12fF
C14 a_787_62# a_143_127# 0.12fF
C15 a_190_75# a_79_75# 0.29fF
C16 Clk_Out a_787_62# 0.17fF
C17 Clk_In a_332_67# 0.14fF
C18 a_463_74# a_190_75# 0.04fF
C19 a_332_67# a_597_66# 0.02fF
C20 VDD Clk_In 1.10fF
C21 VDD a_597_66# 0.19fF
C22 Clk_In a_143_127# 1.17fF
C23 a_597_66# a_143_127# 0.64fF
C24 Clk_Out a_597_66# 0.01fF
C25 Clk_In a_79_75# 0.60fF
C26 a_597_66# a_79_75# 0.03fF
C27 Clk_In a_463_74# 0.20fF
C28 Clk_In a_190_75# 0.30fF
C29 a_463_74# a_597_66# 0.32fF
C30 VDD a_332_67# 0.15fF
C31 Clk_In a_787_62# 0.01fF
C32 a_332_67# a_143_127# 0.19fF
C33 a_787_62# a_597_66# 0.44fF
C34 a_332_67# a_79_75# 0.16fF
C35 VDD GND 3.76fF
C36 a_787_62# GND 0.47fF
C37 a_597_66# GND 1.33fF
C38 a_463_74# GND 0.36fF
C39 a_332_67# GND 0.44fF
C40 a_190_75# GND 0.38fF
C41 a_79_75# GND 1.06fF
C42 a_143_127# GND 0.99fF 


*c1 7 0 18f
v1 VDD GND 1.8
.ends fd
```
   
<h1> Post Layout Simulation Results <h1>
   
   <h2> Post Layout Simulation for Frequency Divider </h2>   
   
   ![Post Layout Simulation for Frequency Divider](https://user-images.githubusercontent.com/91013053/134064602-91bdcbe1-689b-4347-98f3-677ad9ccba6f.jpg)

   <h2> Post Layout Simulation for Charge Pump </h2>  
   
   ![Post Layout Simulation for Charge Pump](https://user-images.githubusercontent.com/91013053/134064321-6404de68-39a8-4697-bba0-f6676843ade6.jpg)
   
   <h2> Post Layout Simulation for PFD </h2>
   
   ![Post Layout Simulation for PFD](https://user-images.githubusercontent.com/91013053/134064646-94b5902f-16b9-4a0d-be8f-98a6dbb3196f.jpg)

   <h2> Post Layout Simulation for PFD_Detecting the difference as small as 0.25ns</h2>
   
   ![Post Layout Simulation for PFD_Detecting the difference as small as 0 25ns](https://user-images.githubusercontent.com/91013053/134064688-fdcb436c-9faa-4abe-b2d0-b4da7e90ee1e.jpg)

   <h2> Post Layout Simulation for PFD_Detecting the difference as small as 1ns</h2>
   
   ![Post Layout Simulation for PFD_Detecting the difference as small as 1ns](https://user-images.githubusercontent.com/91013053/134064746-f361395b-5844-4353-8b02-ce4d479387f3.jpg)

   <h2> Post Layout Simulation for VCO <h2> 
   
   ![Post Layout Simulation for VCO](https://user-images.githubusercontent.com/91013053/134064789-377676d8-301d-49f1-9184-4bf2d6e736f2.jpg)

   <h2> Post Layout Simulation for entile PLL </h2>
   
   ![post layout](https://user-images.githubusercontent.com/91013053/134064810-a1b08803-bfeb-4bb4-8051-ceacfa41e990.jpg)

   
   <h1> Tapeout </h1>
<h4 align="justify">
   
   1. Use the downloaded layout file ine analog user project area.
   
   2. Create a new directory and extract it there. 

   3. Open this file with magic with the technology file sky130A.tech

   4. Do the pin connections after placing the design in the user project area. 

   5. Use only those pins that are needed and connect them to the design.

   6. We can see that at the bottom of the user project area there are wishful ports.
   
   7. On left of the user project area we have input-output ports, Vdd and Vss.

   8. On the right of the user project area we have few more input-output ports and power ports like Vccd, Vssd, Vcca and Vssa.

   9. On top of the user project We can find the analog input-output pins.

   10. In our design, we have five pins:
    - Enable pins for CP and VCO.
    - Reference clock input pin.
    - Output clock pin.
    - VCO direct input pin.

   11. The enable pins are connected to the digital input-output pins.
   
   12. Reference clock input pin and output clock pin are also digital and so we connect them to the digital input-output pins.

   13. VCO direct input pin is control voltage pin of analog nature. So, we need to connect it to an analog input-output pin.

   14. Considering this scenarion, we place our design at the top-right corner and make the connections to the pins using wire tool and contact layers.
   </h4>                   
                      
                      
  <h1> References </h1>

   1. [https://github.com/lakshmi-sathi/avsdpll_1v8](https://github.com/lakshmi-sathi/avsdpll_1v8)

   2. [https://drive.google.com/file/d/18BG4zzpRrcHP0UoBcNLA3sWFDVdNlUtp/view](https://drive.google.com/file/d/18BG4zzpRrcHP0UoBcNLA3sWFDVdNlUtp/view)

   3. [https://github.com/google/skywater-pdk-libs-sky130_fd_pr.git](https://github.com/google/skywater-pdk-libs-sky130_fd_pr.git)

   4. [https://github.com/efabless/caravel-lite/blob/cda6c3ca1158b495f002bf90860941c3a9af1784/gds/user_analog_project_wrapper_empty.gds.gz](https://github.com/efabless/caravel-lite/blob/cda6c3ca1158b495f002bf90860941c3a9af1784/gds/user_analog_project_wrapper_empty.gds.gz)

   5. [https://www.vsdiat.com/](https://www.vsdiat.com/)

   6. [https://www.vlsisystemdesign.com/](https://www.vlsisystemdesign.com/)

   7. [https://github.com/kunalg123/vsdflow](https://github.com/kunalg123/vsdflow)

   8. [https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

   9. [http://opencircuitdesign.com/magic/download.html](http://opencircuitdesign.com/magic/download.html)

   10. [http://opencircuitdesign.com/magic/](http://opencircuitdesign.com/magic/)
