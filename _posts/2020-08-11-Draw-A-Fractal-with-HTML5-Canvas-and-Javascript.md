---
layout: post
date: 2020-08-11
category: programming
title: Draw a Fractal with HTML5 Canvas and Javascript
summary: "Use code to draw a circle fractal with HTML5 canvas and Javascript."
content_description: "Javascript code to draw a circle fractal. Digital art."
---
<div media:type="text/omd" class="blog_title_style container">
    <h1><span>Draw a Fractal</span></h1>
    <h4><span>with HTML5 Canvas and Javascript</span></h4>
    <small>11 August 2020</small>
</div>

<div media:type="text/omd" class="blog_content_style container">

<p id="blog_text">
<kbd>Art</kbd> with coding is something I've never thought of. But I have friends that make art for a living and they were interested in seeing how they could express art in a digital way. As a result, I spent some time exploring the world of coding art.
</p>

<p id="blog_text">
It turns out that coding art is actually a thing! Throughout my research on the topic, I came across different ways that art can be created whether mathematically or by creating fractals.
</p>

<p id="blog_text">
There are many Javascript libraries that allow you to create an impressive and interactive artistic canvas. But in this article, I will show you how you can create a simple fractal pattern using HTML5 Canvas and vanilla Javascript. And maybe in a future article, I will talk about trigonometric abstract art.
</p>


<h3 id="blog_text">Fractals</h3>
<p id="blog_text">
A fractal is a never-ending pattern. It is a geometrical shape where similar patterns repeat infinitly at a smaller and smaller scale. The amazing thing about fractals is that they are all around us, existing in nature. To understand how abundant and popular fractals are, check out <a target="_blank" href="https://www.youtube.com/watch?v=DHNooAe44dY">this</a> TEDx talk.
</p>


<p id="blog_text">
The way to code a fractal is by simply using <strong>recursion</strong>. A recursive function is one that calls itself over and over again infinitly or until a condition is satisfied. This goes well with what a fractal essentially is, an infinitely repetitive pattern.
</p>

<h3 id="blog_text">The Code</h3>
<p id="blog_text">
The tools I've chosen are: 1) HTML5 Canvas, which is the latest version of HTML that helps you create tags that you can control with 2) Javascript. Those 2 simple tools allow you to create from beginner to complex-level graphics and animations. You can start small and certainly go far with them if you decide to pick this up as a hobby.
</p>

<p id="blog_text">
To start, you can create a canvas tag with an "id" attribute in the HTML code as such:
</p>

<pre>
&lt;canvas id="canvas"&gt;&lt;/canvas&gt;
</pre>


<p id="blog_text">
Using Javascript, you can render graphics in this canvas. First you have to locate the tag and set the context which is 2D in this case. The "ctx" object is our canvas object that has all the methods we need to start drawing:
</p>

<pre>
let canvas = document.getElementById('canvas');
let ctx = canvas.getContext('2d');
</pre>

<p id="blog_text">
Then you can determine the width and height of the canvas as well as move to the start point at which you want to start drawing:
</p>

<pre>
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
ctx.translate(canvas.width / 2, canvas.height / 2);
</pre>


<p id="blog_text">
After that, we can write our recursive function. The arguments of this function is an x and a y coordinate as well as a radius. It sets the stroke color to "black".
</p>

<pre>
function drawCircle(x, y, radius) {
    ctx.strokeStyle = 'black';
    <span class="code_comments">//use the arc method to draw a full circle</span>
    ctx.arc(x, y, radius, 0, Math.PI * 2, true);
    <span class="code_comments">// determine the color of the circle</span>
    ctx.fillStyle = "#4A9297";
    ctx.fill();
    <span class="code_comments">// set a break condition for the loop</span>
    if (radius > 2) {
        <span class="code_comments">// recursion when the function calls itself</span>
        <span class="code_comments">// draw 2 circles side by side</span>
        drawCircle(x + radius/2, y, radius/2);
        drawCircle(x - radius/2, y, radius/2);
    }
    ctx.stroke();
}
</pre>


<p id="blog_text">
Finally call the function.
</p>

<pre>
drawCircle(10, 10, 300);
</pre>

<div class="centered_div">
<img class="" src="/assets/images/circle_fractal1.png">
<img class="" src="/assets/images/circle_fractal2.png">
</div>

<p id="blog_text">
Find the code <a target="_blank" href="https://github.com/dotja/digital_art/blob/master/circle_fractal.html">here</a>.
</p>

</div>


