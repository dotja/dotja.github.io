---
layout: post
date: 2020-04-27
category: electronics
title: NPN Transistor - Inverter Circuit
summary: "How to build an inverter using an NPN transistor."
content_description: "Build an inverter circuit with an npn transistor."
---
<div media:type="text/omd" class="blog_title_style container">
    <h1><span>NPN Transistor - Inverter Circuit</span></h1>
    <small>27 Apr 2020</small>
</div>

<div media:type="text/omd" class="blog_content_style container">

<p id="blog_text">
<kbd>A</kbd> transistor is made of 2 diodes joined together. A NPN transistor has 2 diodes joined at the P-type region. This transistor is also called a bipolar junction (BJT) since it has 2 PN junctions.
</p>

<div class="centered_div">
<img class="transistor_img" src="/assets/images/npn.png">
</div>


<p id="blog_text">
When the 2 joined diodes are connected to a power source, reverse bias occurs where the electrons are not able to flow all the way in the circuit. In the image below, the electrons moving from the negative pole can only move so much into the P region of the diode but are not able to pass the second N region.
</p>

<div class="centered_div">
<img class="transistor_img" src="/assets/images/transistor_reverse_bias.png">
</div>


<p id="blog_text">
To achieve a state of forward bias where electrons are able to flow in the circuit, a small current is supplied as shown below called the base current. This current is enough to allow electrons to pass through the circuit. So a transistor is able to amplify a small current into a bigger one.
</p>

<div class="centered_div">
<img class="transistor_img" src="/assets/images/transistor_forward_bias.png">
</div>

<p id="blog_text">
In the image below we see the main parts of a transistor: the base, emitter and collector. The base is where the small current is applied, and the large current is then able to flow from the collector to the emitter side. This acts as a switch which is off in the absence of a base current and which is turned on when the base current is applied.
</p>

<div class="centered_div">
<img class="transistor_img_small" src="/assets/images/transistor_schema.png">
<img class="transistor_img_small" src="/assets/images/transistor_pins.png">
</div>

<div class="centered_div">
<img class="transistor_img" src="/assets/images/transistor.jpg">
</div>

<p id="blog_text">
The ability of a transistor to act as a switch is useful when building an inverter. The idea of an inverter is that provided an input, the output is the opposite of it. The inverter logic is used in programming as the "not" where if you have a variable with a boolean value of true, putting a "not" before the variable converts it to false (the opposite of true).
</p>

<p id="blog_text">
In the schematic below, when the switch is not on, the LED is able to have a full circuit with the positive and negative poles. When the switch is turned on, the current flow moves strongly between the positive pole to the negative pole such that the LED becomes off as it is connecting more the negative pole found near the emitter.
</p>

<div class="centered_div" media:type="text/omd">
<img class="transistor_img_big" src="/assets/images/transistor_circuit.png">
</div>

<div class="centered_div" media:type="text/omd">
<img class="transistor_img" src="/assets/images/transistor_led_on.jpg">
</div>

<div class="centered_div" media:type="text/omd">
<img class="transistor_img" src="/assets/images/transistor_led_off.jpg">
</div>

<br />

</div>




