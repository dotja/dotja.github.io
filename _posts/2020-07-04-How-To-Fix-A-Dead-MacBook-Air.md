---
layout: post
date: 2020-07-04
category: electronics
summary: "Reviving a 2013 MacBook Air that shuts down suddenly and is not responsive."
content_description: "How to fix a Macbook air."
---
<div media:type="text/omd" class="blog_title_style container">
    <h1><span>How To Fix a Dead MacBook Air</span></h1>
    <small>04 Jul 2020</small>
</div>

<div media:type="text/omd" class="blog_content_style container">

<p id="blog_text">
<kbd>There</kbd> is nothing worse than seeing your laptop suddenly shut down and not respond when you press the power button.
It is for sure a good reminder that those machines will someday break so backing up your data is a good investment.
Luckily, my machine was on the older Apple design which allows unscrewing the SSD, pluging it into an adapter to restore the user's files in case of no backup.
</p>

<p id="blog_text">
It all started when my Mac shut down on it's own and refused to turn back on. I did the usual "pressing the power button for 10 seconds" with no result.
In this article I will go through some steps you can take if you come accross this issue and hopefully something will be useful for you.
</p>

<h3 id="blog_text">Reset the SMC</h3>
<p id="blog_text">
SMC or System Management Controller is involved in roles such as keyboard backlighting, the responsiveness of the power button, the responsiveness of the lid as it closes/opens as well as other things related to the fan, battery, etc.
So resetting the SMC might help. To do this you need to press SHIFT + CONTROL + OPTION and then the power button. Hold for about 5 seconds then release. You will see the power plug green light turn red then back to green again because the SMC has reset.
</p>

<h3 id="blog_text">Reset the NVRAM</h3>
<p id="blog_text">
The non-volatile memory is a small module that stores settings that need to be accessed quickly. It is not meant to be changed and it relates to configurations such as volume level, display resolution, timezone, etc.
To restart the NVRAM, you would press OPTION + CMD + P + R and then the power button.
</p>

<h3 id="blog_text">The Battery</h3>
<p id="blog_text">
Something that you should frequently do is clean up your machine from the inside. This requires specific screwdrivers for the MacBook Air: a pentalobe 1.2mm for the external screws and a tork T5 for the battery screws inside.
</p>

<p id="blog_text">
When you open the back side, you need to disconnect the battery. You then press the power button and hold, then plug the charging cable to the laptop . Sometimes this allows the Mac to start again. You then shut down the laptop and connect the battery back and then try to restart the machine.
</p>

<p id="blog_text">
You can also check the battery's health condition from the utilities option to look for a battery-related problem.
</p>

<h3 id="blog_text">Check the keyboard wire</h3>
<p id="blog_text">
Another issue I had with my Mac was that it didn't respond to keyboard strokes or the trackpad. One thing that might help in this case is unscrewing the battery so that you can reach the cable behind it that connects the trackpad/keyboard to the motherboard.
</p>

<p id="blog_text">
You can disconnect this wire and gently clean its tip from both sides. Sometimes you would notice some corrossion or other issues that might cause problems.
</p>

<h3 id="blog_text">Run First Aid on the Disk</h3>
<p id="blog_text">
After attempting the above-mentioned measures, and after thoroughly examining the motherboard components for any signs of corrossion or decay, I decided that the internal hardware of the machine was clean.
My laptop at this point could turn on and the keyboard/trackpad were responsive. However after I loggged in, the laptop then shut down on it's own and restarted itself.
</p>

<p id="blog_text">
That led me to think that I might have a corrupt software or corrupt SSD. To test the latter, I decided to start the Mac in safe mode where only important applications turn on. In safe mode, my laptop was acting normally and did not restart on its own. So I decided to try to recover the SSD by using the Mac's First Aid utility in Disk Utilities. I ran this on my hard disk and it completed successfully.
</p>

<p id="blog_text">
The First Aid approach gracefully unmounts then mounts back the volume. After that, I restarted the machine in normal user mode. And that fixed it for me.
</p>

<h3 id="blog_text">More Advice</h3>
<p id="blog_text">
The above trials might not work for your machine. In this case, you can do an AHT (Apple Hardware Test) on your laptop by holding the D key on power-on.
</p>


<p id="blog_text">
Online resources I found useful include: <a href="https://www.ifixit.com/" target="_blank">ifixit</a> and <a href="https://www.appledollars.com/" target="_blank">appledollars</a>.
</p>


</div>

