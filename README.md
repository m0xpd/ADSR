# ADSR
A Looping Version of the YuSynth ADSR

# Background

I decided to build a new envelope generator back in December 2022 to supplement / replace my old AR generators made from [MFOS](http://musicfromouterspace.com/) designs and my 
own ["ADSRduino"](https://github.com/m0xpd/ADSRduino).

I already knew Yves Usson's excellent [YuSynth site](https://yusynth.net/Modular/index_en.html) (having published a Eurorack version of the ['Simple VCA'](https://github.com/m0xpd/YuSynth-VCA-for-Eurorack)), and was interested by a comment on 
[Eddy Bergman's website](https://www.eddybergman.com/2020/03/synthesizer-build-part-24-adsr-with.html) about the YuSynth ADSR.

Eddy said:

"I can say without any doubt that this design is perfect if you want a good and reliable ADSR to pair with your VCA or to drive a filter. " 

That decided it - I would make a Eurorack version of Yves' 7555-based design. 

However, having added looping to my ADSRduino, I decided that I would also like to include the same looping functionality on the new envelope generator. 

So - here it is. A version of the YuSynth 7555 ADSR in 8HP with looping...

<p width=100%, align="center">
<img height="400", src="https://github.com/m0xpd/ADSR/blob/main/Images/ADSR%20Front.png"> &nbsp &nbsp &nbsp &nbsp<img height="400", src="https://github.com/m0xpd/ADSR/blob/main/Images/ADSR%20Side.png"> &nbsp &nbsp &nbsp &nbsp<img height="400", src="https://github.com/m0xpd/ADSR/blob/main/Images/ADSR%20Rear.png"> 
</p>

# Circuit Details

The schematic is seen below (click for a full-sized version and/or download from the 'images' folder).

<p width=100%, align="center">
<img width=50%, src="https://github.com/m0xpd/ADSR/blob/main/Images/m0xpd%20Looping%20ADSR%20v2.0%20Schematic.png"> 
</p>

You will see that I follow Yves' original schematic pretty closely, apart from the addition of the elements required to realise the 
looping functionality. These are:
* a comparator (IC1B) to detect when the envelope falls below the PN junction drop (over D5)
* a positive edge detector (R24/C4/D6) to get a trigger when the envelope falls below the PN junction drop and
* a one-shot monovibrator (Q5,6 etc), to generate a defined pulse from this trigger, 

which is applied via D7 back to the input stage. If the looping switch (SW2) is set appropriately, this pulse will re-trigger the 
envelope and cause 'looping' 
