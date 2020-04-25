---
layout: post
date: 2020-04-02
category: ml
summary: "A simple introduction to Bayes' theorem with examples."
content_description: "A simple step-by-step introduction to bayes theory."
---
<div media:type="text/omd" class="blog_title_style container">
    <h1><span>Introduction to Bayes' Theorem</span></h1>
    <small>02 Apr 2020</small>
</div>

<div media:type="text/omd" class="blog_content_style container">

<p id="blog_text">
<kbd>Bayes'</kbd> rule has 2 main roles, first providing an estimation of an outcome based on previous knowledge and second, being able to constantly update this estimate as more data comes in.
<br />
<br />
Bayes' rule can be used for both continuous and discrete values. In this article, we will go through a simple example that would help understand the idea better. And then we will look at derriving the famous equation for Bayes' theorem. In later articles, I will cover the implementation of this in machine learning.
</p>


<h3 id="blog_text">A Simple Example</h3>
<p id="blog_text">
Let's imagine a person suddenly develops spots on their face and they suspect they have either smallpox or chickenpox. We want to compute the probability that this person has smallpox given the spots on the face i.e.

$$P(smallpox|spots)$$
<br />
We know that the probability of having spots when having smallpox is 90% whereas the probability of having spots when having chickenpox is 80% i.e.
$$P(spots|smallpox)\ =\ 0.9$$
$$P(spots|chickenpox)\ =\ 0.8$$
<br />
With the information above, you might rush to the conclusion that this patient has smallpox, but this is not accurate.
<br />
</p>
<p id="blog_text">
In a case like this, Bayes' rule helps us make an educated guess based on previous information we have.
We know that chickenpox is more prevalent in the population than smallpox:
$$P(chickenpox)\ =\ 0.1$$
$$P(smallpox)\ =\ 0.001$$
With this knowledge, we can tweak our conclusion and make it more accurate based on prior data. The probability of having smallpox (given the spots) becomes also dependent on how much smallpox is prevalent in the community.
</p>
<p id="blog_text">
$$P(smallpox|spots)\ =\ P(spots|smallpox). P(smallpox)$$
<br />
When we do the calculation we find out that:
$$P(smallpox|spots)\ =\ (0.9)\ .\ (0.001)\ =\ 0.0009$$
$$P(chickenpox|spots)\ =\ (0.8)\ .\ (0.1)\ =\ 0.08$$
<br />
This probability is a weighted one that takes into account prior information. And we can see that it is more probable that the patient suffers from chickenpox.
</p>

<h3 id="blog_text">Derriving Bayes' Rule</h3>
<p id="blog_text">
Let's consider a number of coins of which some have 20% bias and the rest have 80% bias. We randomly choose a coin and flip it, we get heads. We want to find the probability that given heads is the outcome, the coin has 80% bias i.e. \(P(\theta_{0.8}|x_h)\)
<br />
<br />
\(\theta\) is a parameter representing bias
<br />
\(x_h\) is the event that we get heads
</p>
<p id="blog_text">
We intuitively know that the probability of getting heads is the sum of getting it from both \(\theta_{0.8}\) and \(\theta_{0.2}\) coins.
$$P(x_h)\ =\ P(x_h, \theta_{0.8})\ +\ P(x_h, \theta_{0.2})$$
$$So:\ \ \ P(\theta_{0.8}|x_h)\ =\ \frac{P(x_h, \theta_{0.8})}{P(x_h)}\ \ \ \ \ (Eq.1)$$
</p>
<p id="blog_text">
After establishing the equation above, let's look at a Venn diagram:
</p>

<div class="centered_div" media:type="text/omd">
<img class="bayes_imgs" src="/assets/images/venn.png">
</div>

<p id="blog_text">
We can see that (b) is the intersection of (a) and (c). By looking at the Venn diagram above and by using (Eq.1) we can compute the following:
$$P(\theta_{0.8}|x_h)\ =\ \frac{b}{a}\ \ \ \rightarrow\ \ b\ =\ a.P(\theta_{0.8}|x_h)$$
$$P(x_h|\theta_{0.8})\ =\ \frac{b}{c}\ \ \ \rightarrow\ \ b\ =\ c.P(x_h|\theta_{0.8})$$
<br />
$$Since\ \ \ b\ =\ b$$
$$\Rightarrow\ \ \ a.P(\theta_{0.8}|x_h)\ =\ c.P(x_h|\theta_{0.8})$$
<br />
$$where\ \ \ a\ =\ p(x_h)\ \ \ and\ \ \ c\ =\ p(\theta_{0.8})$$
<br />
</p>

<p id="blog_text">we get Bayes' equation:</p>
<div class="centered_div" media:type="text/omd">
<img class="bayes_imgs" src="/assets/images/bayes.png">
</div>

<br />

</div>

