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
         
   6. [PDK, Design specifications and pre-layout Simulation](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#pdk,-design-specifications-and-pre-layout-simulation)
         
   7. [Simulation tool - Ngspice Setup](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#simulation-tool-ngspice-setup)
         
   8. [Layout tool - Magic Setup](https://github.com/vikasbalikai/Phase-Locked-Loop-using-skywater-130nm/edit/main/README.md#layout-tool-magic-setup)

  ## *Day 2 – PLL Labs with pre and post-layout simulations*

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
 
![Freq Syn classification](https://user-images.githubusercontent.com/91013053/133984785-d33042a6-5ebb-40ad-8aca-64104e841d8b.png)
   
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
              
              
