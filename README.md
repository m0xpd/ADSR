# ADSR
A Looping Version of the YuSynth ADSR

# Background

I decided to build a new envelope generator back in December 2022 to supplement / replace my old AR generators made from [MFOS](http://musicfromouterspace.com/) designs and my 
own ["ADSRduino"](https://github.com/m0xpd/ADSRduino).

I already knew Yves Usson's excellent [YuSynth site](https://yusynth.net/Modular/index_en.html) (having published a Eurorack version of the ['Simple VCA'](https://github.com/m0xpd/YuSynth-VCA-for-Eurorack)), and was interested by a comment on 
[Eddy Bergman's website](https://www.eddybergman.com/2020/03/synthesizer-build-part-24-adsr-with.html) about the YuSynth ADSR.

Eddy said:

> "I can say without any doubt that this design is perfect if you want a good and reliable ADSR to pair with your VCA or to drive a filter. " 

That settled it - I would make a Eurorack version of Yves' 7555-based design. However, having added looping to my ADSRduino, 
I decided that I would also like to include the same looping functionality on the new envelope generator. 

So - here it is. A version of the YuSynth 7555 ADSR in 8HP with looping...

<p width=100%, align="center">
<img height="400", src="Images/ADSR%20Front.png"> &nbsp &nbsp &nbsp &nbsp<img height="400", src="Images/ADSR%20Side.png"> &nbsp &nbsp &nbsp &nbsp<img height="400", src="Images/ADSR%20Rear.png"> 
</p>

# Circuit Details

The schematic is seen below (click for a full-sized version and/or download from the 'images' folder).

<p width=100%, align="center">
<img width=50%, src="Images/m0xpd%20Looping%20ADSR%20v2.0%20Schematic.png"> 
</p>

You will see that I follow Yves' original schematic pretty closely, apart from the addition of the elements required to realise the 
looping functionality. These are:
* a comparator (IC1B) to detect when the envelope falls below the PN junction drop (over D5)
* a positive edge detector (R24/C4/D6) to get a trigger when the envelope falls below the PN junction drop and
* a one-shot monostable multivibrator (Q5,6 etc), to generate a defined pulse from this trigger, 

which is applied via D7 back to the input stage. If the looping switch (SW2) is set appropriately, this pulse can re-trigger the 
envelope and cause 'looping'.

The old-school transistor one-shot is included because I didn't want to add another IC package (having already 'spent' the last stage 
of IC1 on the comparator task).

Other minor departures from Yves' "words and music" include a reduction in input resistor R6 (I had trouble with the specified 1M) and 
substitution of a 2N7000 for Yves' specified BS170 (I see others have had difficuty sourcing these rarer FETs and the garden-variety 
2N7000 works fine). 

I also chose to use once again the lovely [low-profile push button](https://www.thonk.co.uk/shop/low-profile-led-buttons/) as both 
manual gate switch and indicator. It is the right height to work with [Thonkiconns](https://www.thonk.co.uk/shop/thonkiconn/) and [Alpha pots](https://www.thonk.co.uk/shop/alpha-9mm-pots-vertical-t18/), which makes mechanical assembly a breeze.

# Construction Details

Full details of the PCB are given in the [PCB folder](PCB), which includes a .sch and .brd file, developed in EAGLE.

A front panel is decribed by a Kicad project in the [Front Panel folder.](Front%20Panel)

My original boards and Front panel (seen in the images above) were made by JLC, who did their usual competent job. 

The images show the v0.1 boards, which include a Molex KK connector for power which is not on the present V2.0 design. They also have 
different silkscreening, influencing most significantly the licensing...

# Licensing

<p width=100%, align="left">
<img width=20%, src="Images/by-nc-sa.eu.png"> 
</p>

Yves is clear on the position with copyright on his website:

> "All circuits, schematics, printed circuit board, panel design and associated data published on (yusynth.net) can be used for private use only." 

and:

> "The projects of (yusynth.net) may be build for personal, private usage or educative purpose. Commercial exploitation of the schematics, circuits, 
front panels and software shown on (yusynth.net), is not permitted without a formal agreement with (Yves Usson)".

Accordingly, **the copyright for the core of this ADSR circuit rests with Yves and no commercial exploitation is permitted**.

I have reflected this in the [License](LICENSE.txt) for the looping Eurorack version presented in this repository.

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License.](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.en)


# Specifications

The looping ADSR is 8HP wide and extends 25mm behind the front panel.

It consumes: 
7.1mA from the 12V rail (max current in looping mode; quiescent current drain is 3.7mA)  
1.1mA from the -12V rail (in all conditions) 
nothing from the 5V rail.

