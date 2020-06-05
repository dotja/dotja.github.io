---
layout: post
date: 2020-06-05
category: ml
summary: "A dive into the theory of univariate linear regression."
content_description: "Understanding the theory of simple linear regression with simple mathematics."
---
<div media:type="text/omd" class="blog_title_style container">
    <h1><span>Understanding Simple Linear Regression</span></h1>
    <small>05 Jun 2020</small>
</div>

<div media:type="text/omd" class="blog_content_style container">

<p id="blog_text">
<kbd>A</kbd> model is an abstract term that is used to represent reality. A mathematical model is one that is able to describe an observation with room for error.
</p>

<p id="blog_text" class="maths_symbol">
$$observation\ =\ model +\ error$$
</p>

<p id="blog_text">
There are 2 types of models we will encounter here. A deterministic model and a probabilistic model.
</p>

<h3 id="blog_text">A Deterministic Model</h3>

<p id="blog_text">
It describes an exact relationship between 2 or more variables. It predicts with certainty and without any random error for example when you convert a celsius temperature into kelvin, you follow a determined equation with no error involved.
</p>

<h3 id="blog_text">A Probabilistic Model</h3>

<p id="blog_text">
This model makes a prediction where there exists a random error. This error can be caused by an unknown variable(s) that wasn't considered, a low quality measurement for a variable or other.
</p>

<p id="blog_text">
In simple linear regression, there exists a linear relation between a predictor (feature) and an outcome (label). This is seen in the equation below:
$$Y\ =\ \beta_{0} \ + \beta{1} X + \ \epsilon$$
</p>

<p id="blog_text">
This is a probabilistic model because it takes into account a random error epsilon.
Epsilon accounts for the failure of the data to lie on the straight line and represents the difference between true and observed values of y.
The 2 betas are parameters also known as regression coefficients that are estimated using the sample data.
</p>

<p id="blog_text">
On the other hand:
</p>

<p id="blog_text" class="maths_symbol">
$$E(Y)\ =\ \beta_{0} \ + \beta{1} X$$
</p>

<p id="blog_text">
The equation above is a deterministic model where E(Y) assumes that the response of Y is the mean value and that the random errors balance out and average to zero, hence epsilon is abscent.
</p>

<p id="blog_text" class="maths_symbol">
$$\mu(\epsilon)\ =\ 0;\ \ \ \ var(\epsilon)\ =\ \sigma^2$$
</p>

<h3 id="blog_text">Machine learning context</h3>
<p id="blog_text">
In a machine learning setting, the simple linear regression equation becomes:
$$y'\ =\ b\ +\ w_{1}\ x_{1}$$
</p>

<p id="blog_text">
This is the equation of a straight line passing through the data. Here the predicted label equals a bias plus feature 1 and its weight. In ML, to train the model is jargon for finding the best fit of the regression line. The best values for the weight and bias from the training data.
</p>

<p id="blog_text">
To achieve a best fit of the regression line, the error \(\epsilon_{i}\) for all observations needs to sum up to a minimum possible value. This is discussed in detail below.
</p>

<h3 id="blog_text">Least Squares Method</h3>
<p id="blog_text">
To estimate the model parameters, several methods can be employed. Here we will discuss the least squares method.
</p>

<p id="blog_text">
1. We start with a sample with n observations having 2 values \((x_{i}, y_{i})\)
</p>

<p id="blog_text">
2. By looking at the scatterplot of those observations, we assume they satisfy a simple linear regression model. The hat indicates that those are estimated values.
$$\hat y_{i}\ =\ b_{0}\ +\ b_{1} x_{i}$$
</p>

<p id="blog_text">
3. We then write down our loss function which is the sum of squares that shows the difference between the observed values and the values predicted by the regression line.
</p>
<p id="blog_text" class="maths_symbol">
$$residuals:\ \ \ \hat \epsilon_{i}\ =\ y_{i}\ -\ \hat y_{i}$$
$$residual\ sum\ of\ squares\ RSS\ :$$
$$\sum_{i=1}^n \epsilon_{i}^2 \ =\ \sum_{i=1}^n (y_{i}\ -\ \hat y_{i})^2$$
</p>
<p id="blog_text">
Instead of finding every possible residual value manually which gives a perfectly fitted straight line, we use calculus which says that the RSS function (which is convex) has a minimum value where its slope or derrivative is equivalent to zero.
</p>

<p id="blog_text">
4. Use calculus to obtain the value of \(\hat \beta_{0}\):
</p>
<p id="blog_text" class="maths_symbol">
$$RSS\ =\ \sum_{i=1}^n (y_{i}\ -\ (b_{0}\ +\ b_{1} x_{i}))^2$$

$$= \sum_{i=1}^n (y_{i}^2\ -2y_{i} (b_{0}\ +\ b_{1}x_{i})\ +\ b_{0}^2\ +\ 2b_{0}b_{1}x_{i}\ +\ b_{1}^2 x_{i}^2 )$$

$$= \sum_{i=1}^n (y_{i}^2\ -\ 2y_{i}b_{0}\ -\ 2y_{i}b_{1}x_{i}\ +\ b_{0}^2 \ +\ 2b_{0}b_{1}x_{i} \ +\ b_{1}^2 x_{i}^2)$$

$$\frac {dRSS}{db_{0}}\ =\ \sum_{i=1}^n (-2y_{i} \ +\ 2b_{0} \ +\ 2b_{1}x_{i})$$

$$0 \ = \sum_{i=1}^n (-y_{i} \ +\ b_{0} \ +\ b_{1}x_{i})$$

$$0 \ = - \bar y \ +\ b_{0} \ +\ b_{1} \bar x$$

$$\Rightarrow \ b_{0} \ =\ \bar y \ -\ b_{1} \bar x$$
</p>

<p id="blog_text">
5. Use calculus to obtain the value of \(\hat \beta_{1}\):
</p>
<p id="blog_text" class="maths_symbol">
$$= \sum_{i=1}^n (y_{i}^2\ -\ 2y_{i}b_{0}\ -\ 2y_{i}b_{1}x_{i}\ +\ b_{0}^2 \ +\ 2b_{0}b_{1}x_{i} \ +\ b_{1}^2 x_{i}^2)$$

$$\frac {dRSS}{db_{1}}\ =\ \sum_{i=1}^n (-2x_{i}y_{i} \ +\ 2b_{0}x_{i} \ +\ 2b_{1}x_{i}^2)$$

$$=\ \sum_{i=1}^n (-x_{i}y_{i} \ +\ b_{0}x_{i} \ +\ b_{1}x_{i}^2)$$

$$=\ \sum_{i=1}^n (-x_{i}y_{i} \ +\ (\bar y\ -\ b_{1} \bar x) x_{i} \ +\ b_{1}x_{i}^2)$$

$$0 \ =\ \sum_{i=1}^n x_{i} (y_{i}\ -\ \bar y) \ -\ b_{1}(\sum_{i=1}^n x_{i}^2 \ -\ \sum_{i=1}^n x_{i} \bar x)$$

$$\Rightarrow \ b_{1} \ =\ \frac {\sum_{i=1}^n x_{i} (y_{i} \ -\ \bar y)}{\sum_{i=1}^n x_{i} (x_{i} \ -\ \bar x)} \ .\ \frac {(x_{i} \ -\ \bar x)}{(x_{i} \ -\ \bar x)}$$

$$=\ \frac {\sum_{i=1}^n (y_{i} \ -\ \bar y)(x_{i} \ -\ \bar x)}{\sum_{i=1}^n (x_{i} \ -\ \bar x)(x_{i} \ -\ \bar x)} \ =\ \frac {S_{xy}}{S_{xx}}$$
</p>

<p id="blog_text">
6. A computer program is able to estimate the model's parameters using their equations. To interpret the regression line results, we look at it as a regular line having this equation \(y\ =\ mx + b\) which means that when the x value is increased by 1 unit, the y response increases by m.
</p>

</div>

