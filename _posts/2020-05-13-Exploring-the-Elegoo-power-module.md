---
layout: post
date: 2020-05-13
category: electronics
summary: "What exactly are the components on the Elegoo power module."
content_description: "What is on the Elegoo power module. Power module electronic components."
---
<div media:type="text/omd" class="blog_title_style container">
    <h1><span>Exploring the Elegoo Power Module</span></h1>
    <small>13 May 2020</small>
</div>

<div media:type="text/omd" class="blog_content_style container">

<p id="blog_text">
<kbd>If</kbd> you are like me, as in you need to understand some things that might not be relevant to others then you are in the right place. The macro concept of things is something nice to understand; however, the micro concepts are the things that I find intriguing and that are important when you are trying to understand how something works from inside out.
</p>

<p id="blog_text">
As I have been using my Elegoo power module to create some basic circuits such as the <a target="_blank" href="https://dotja.github.io/electronics/2020/03/28/4N35-Optocoupler.html">Optocoupler</a>, I was interested to know what the components on the power module itself were, so I did a bit of exploration.  This wasn't straight forward using a simple Google search since the explanations I came across only mostly described the major components on the module which were just 4 out of roughly 20! So here is what I gathered and hopefully you find this useful.
</p>


<div class="centered_div">
<img class="power_module_image" src="/assets/images/power_module_labels.jpg">
</div>

<h3 id="blog_text">1) Power plug input</h3>
<p id="blog_text">
This provides a direct current of about 9V via a 5.5mm x 2.1mm plug that goes into the wall outlet. This voltage is reduced by some of the components on the module which I will list below.
</p>

<h3 id="blog_text">2) Vcc and GND pins</h3>
<p id="blog_text">
Vcc is the voltage common collector that has the higher voltage with respect to the other pin V(GND) or ground. If you look at the module from below, you can see that those are the pins that attach to the breadboard and provide voltage for the protruding header pins.
</p>

<h3 id="blog_text">3) Header</h3>
<p id="blog_text">
These are 2 4-pin rows that can be insulated using the cap you see in the figure.
</p>

<h3 id="blog_text">4) CJT1117-5</h3>
<p id="blog_text">
This is a voltage regulator that provides a voltage of 5.0v from an input voltage. This component provides regulated voltage to the adjustable voltage pins.
</p>

<h3 id="blog_text">5) Header</h3>
<p id="blog_text">
This is a 4-pin dual row which is 2 rows made of 4 pins.
</p>

<h3 id="blog_text">6) Capacitors</h3>
<p id="blog_text">
3 capacitors of 0.1microF.
</p>

<h3 id="blog_text">7) Header cap</h3>
<p id="blog_text">
This is a removable cap. It can be used to insulate the pins and halt the current flow.
</p>

<h3 id="blog_text">8) AMS1117-3.3</h3>
<p id="blog_text">
This is a voltage regulator that provides 3.3v from an input voltage. This component provides regulated voltage to the adjustable voltage pins.
</p>

<h3 id="blog_text">9) M7</h3>
<p id="blog_text">
This is known as the default diode or rectifier diode. A rectifier is able to convert alternating current (AC) into direct current (DC).
The M7 has a V(RRM) repetitive peak reverse voltage of 1000v. This means that while a device can block a maximum value of reverse voltage before it gets damaged, the V(RRM) can block that repeatadly without any damage.
</p>

<h3 id="blog_text">10) USB connector</h3>
<p id="blog_text">
This provides power to an external device. So you can use this power module to power a device via usb.
</p>

<h3 id="blog_text">11) Power switch</h3>
<p id="blog_text">
This is a 3-pin dual row switch which means it has a total of 6 pins. It allows the power module to turn on and this is indicated by the LED next to it which turns on.
</p>

<h3 id="blog_text">12) Fuse</h3>
<p id="blog_text">
Which is a component that protects the circuit from getting injured due to excess current.
</p>

<h3 id="blog_text">13) LED</h3>
<p id="blog_text">
This LED is used as an indicator for when the power switch is turned on.
</p>

<h3 id="blog_text">14) Resistor</h3>
<p id="blog_text">
This resistor is labelled as 470R which means 470.0 ohm. A resistor is able to provide resistance for the circuit mostly the LED, which is a sensitive component that burns out under high current.
</p>

<h3 id="blog_text">15) Capacitor</h3>
<p id="blog_text">
This is a big capacitor of 10 microF.
</p>


<br />

</div>




