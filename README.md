<h1> Phase-Locked-Loop-using-skywater-130nm </h1>
The basic agenda of this workshop was to design a Phase-Locked Loop using an Open-Source Google-Skywater 130nm node. In this workshop, tools like are Ngspice and Magic are used. Considering a layout and an end product(IC) perspective, the mathematical design aspects are totally avoided here, thus making this workshop a learn-by-doing program. A pre-requisites of Basic Electronics is sufficient.


<h1> What is Phase Locked Loop (PLL) </h1>
<h4 align="justify">Today‟s era of the Integrated circuit (IC) has really changed the way how we see the outer world. The journey of Integrated Circuit (IC) technology is about to reach its zenith soon. IC technology has become an integrated part of today‟s life. These developments are mainly because of the rapid advancements in digital technology
which has paved the way for such advancements. Scaling capability, reduced area, and minimum power consumption are the key attributes of Metal oxide semiconductor (MOS) technology, but what does has made the CMOS technology a consistent performer in the technology marathon is its agility to different processes, easy re-design, and effortlessness behavior even in the sub-threshold region. Since many analog blocks are inevitably being used in several mixed-mode IC designs, the performance metrics of such analog blocks favor a thorough re-design and hence will be a crucial step in the entire fabrication process. To overcome this glitch the complete digitization of the entire process has carved the way for many opportunities in the system on chips (SoCs). The main advantage of digital technology is its versatility in adopting any technological scaling as and when the design process changes. Advantages like better reusability with the minimized area, power, and better integration are the results of a digital intensive approach [Homayoun and Razavi, 2013] (http://www.seas.ucla.edu/brweb/papers/Journals/HRTCASMar13.pdf). One of the foremost blocks that has seen a tremendous rise in its usage in the recent past is a phase-locked loop (PLL) system in communication systems. The most widely used component in almost all communication system blocks for frequency synthesis and data recovery is PLL. Cell phones, Laptops, Televisions, communication devices are a few examples that depend on PLLs to perform properly. </h4>

<h1> Conceptual Framework <h1>
<h4 align="justify">  The RF transceivers demand good battery life with
minimal power consumption. Typically most of the RF transceiver circuits spend
90% of their time in standby mode and only 10 in active mode (Khalil et al., 2011).
Hence the demand for low power consumption ads key value in the design of RF
transceivers. The most inevitable block that is present in the transceivers generating
a local signal is the frequency synthesizer or phase-locked loop.
A receiver waits for the incoming wake-up signal and upon detection, the PLL
should wake up and achieve the process of locking in a minimal time of the active
time frame duration (Shashidharan et al., 2010). The PLL circuit is by virtue a closedloop system. Though it has a simple operating principle, the PLL technique received much
attention since it was first conceived by the French scientist De Bellescise in his
paper, "La Reception Synchrone", (De Bellescise, 1932). The PLL started as a
discrete element implementation and transformed into a partially integrated circuit,
then to a fully integrated analog circuit, and finally to an all-digital circuit in recent
years. Most of the early PLL implementations are analog circuits.

  The early digital form of the PLL often refers to the digital implementation with
only a few building blocks due to the prohibitively high cost of the digital elements.
The cost for the integrated circuit has been reduced to the point where the cost for
the digital circuit is much less than the cost for the analog counterpart of the same
functionality or the cost for the extra transistors required by the digital circuit can be
ignored. This makes it possible to convert every single component in the PLL into a
digital block.
  In ADPLL each building blocks are implemented digitally and have a
digital interface between them and have the state of the art mechanism to mitigate all
the drawbacks of analog PLL. The ADPLL itself is also fully integrated with other
bigger digital circuits, such as digital signal processing (DSP), on a single die. Most
  often, there is more than one ADPLL in a single chip. </h4>
