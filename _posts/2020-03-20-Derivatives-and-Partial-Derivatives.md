---
layout: post
date: 2020-03-20
summary: "An example of how to differnetiate a univariate and a multivariate function."
content_description: "Derivatives for univariate and multivariate functions. Relevant in gradient descent the optimisation algorithm in machine learning."
---
<div media:type="text/omd" class="blog_title_style container">
    <h1><span>Derivatives and Partial Derivatives</span></h1>
    <small>20 Mar 2020</small>
</div>

<div media:type="text/omd" class="blog_content_style container">

<p id="blog_text">
<kbd>Derivatives</kbd> allow us to know how things change. For example, in what direction a straight line or a curve is moving. The derivative; or rate of change, of a straight line is its slope which is described by the change in y over the change in x of 2 points that lie on that straight line. In case of a curve, we can have more than 1 slope because a curve is able to have several changes occuring within it.
</p>

<p id="blog_text">
In machine learning, gradient descent; which is the optimisation algorithm used in neural networks, is able to find the minimum of a function where there is the least amount of loss. The local minimum or local maximum for a function is where the derivative of the function equals zero. And this is because the tangent line to the curve at these points is parallel to the coordinate axis giving a rate of change of null.
</p>

<p id="blog_text">
Usually there exists packages that implement ML algorithms with the gradient descent and differentiation built-in. This article is meant to focus on the concept of differentiation for univariate and multivariate functions.
</p>

<h3 id="blog_text">Univariate Functions</h3>
<p id="blog_text">
Let's consider the following function: $$y = x^2$$
<br />
To see what this function looks like, we can simply pick a bunch of x values and compute their corresponding y values and then plot the result. Here is what it looks like in Python.
</p>

<pre>
from matplotlib import pyplot as plt

x_vec = range(-5,6)

## defining my function
def fn(x):
&nbsp;&nbsp;&nbsp;&nbsp;return x ** 2

y_vec = list(map(fn, x_vec))

plt.title("plotting f(x)=x^2")
plt.xlabel("x")
plt.ylabel("y")
plt.grid(True)
plt.plot(x_vec, y_vec)
plt.show()
</pre>

<div class="centered_div" media:type="text/omd">
<img class="function_img" src="/assets/images/y_equal_x_square.png">
</div>

<br />
<p id="blog_text">
We now want to calculate the formula for the derivative of the function above.
<br />
Since we know that the derivative of a straight line is the slope, the derivative of a curve is equivalent to the slope of the tangent line to that curve where the 2 points defining the tangent line are infinitely close.
</p>

<p id="blog_text">
Let's define the 2 points P and Q on the curve. If we move P and Q closer to each other, the slope of the curve eventually becomes almost equivalent to the slope of the tangent.
</p>

<p id="blog_text">
If the distance between P and Q is h:
$$P(x,\ y)$$
$$Q(x + h,\ y)$$
where h is a very small value. Then:
$$P(x,\ f(x))$$
$$Q(x + h,\ f(x + h))$$
</p>

<p id="blog_text">
If we try to calculate the slope from the points above:
$$slope = \frac{\delta y}{\delta x}$$
$$= \frac{f(x+h) - f(x)}{x+h-x}$$
$$\ $$
$$= \frac{(x+h)^2 - (x)^2}{h}$$
$$\ $$
$$= \frac{x^2 + h^2 + 2xh - x^2}{h}= 2x+h$$
</p>

<p id="blog_text">
Now as h approaches zero i.e. the distance between P and Q becomes very very very small,
$$ slope\ of\ PQ\ ==\ slope\ of\ tangent\ to\ curve$$

$$slope_{h\to 0} = 2x + (0) = 2x$$

$$\lim_{h\to 0} \frac{\partial x^2}{\partial x} = 2x$$
</p>


<h3 id="blog_text">Multivariate Functions</h3>
<p id="blog_text">
A multivariate function is described by having more than 1 variable. For example:
$$f(x, y) = x^2 + y^2$$
Unlike a univariaite function, the derivative of a multivariate function is a vector called the gradient.
<br />
The partial derivatives are obtained when you take turns calculating the derivative of a function w.r.t. 1 variable at a time while holding the other variables constant.
<br />
<br />
I will first plot the function in Python:
</p>

<pre>
from numpy import arange
from pylab import meshgrid
from mpl_toolkits.mplot3d import Axes3D
import matplotlib.pyplot as plt

## defining my function
def func(x,y):
&nbsp;&nbsp;&nbsp;&nbsp;return (y**2) + (x**2)
 
x = arange(-5,6,0.1)
y = arange(-5,6,0.1)
X,Y = meshgrid(x, y)
Z = func(X, Y)

fig = plt.figure()
ax = fig.gca(projection='3d')
surf = ax.plot_surface(X, Y, Z)

plt.show()
</pre>

<div class="centered_div" media:type="text/omd">
<img class="function_img" src="/assets/images/x_square_plus_y_square.png">
</div>


<h5 id="blog_text">1) Differentiate by the first variable:</h5>
<p id="blog_text">
$$f(x, y) = x^2 + y^2$$
$$let:\ \ \ \ b = y^2$$
$$then:\ \ \ \ f(x, y) = x^2 + b$$
<br />
$$\frac{\partial f(x, y)}{\partial x} = \lim_{h\to 0} \frac{f(x+h) - f(x)}{h}$$
$$\ $$
$$= \lim_{h\to 0} \frac{(x+h)^2 + b - (x^2 + b)}{h}$$
$$\ $$
$$= \lim_{h\to 0} \frac{x^2 + 2xh + h^2 + b - x^2 - b}{h}$$
<br />
$$\lim_{h\to 0} = 2x + h = 2x$$
<br />
$$\therefore\ \frac{\partial f(x, z)}{\partial x} = \lim_{h\to 0} 2x + h = 2x$$
</p>

<h5 id="blog_text">2) Differentiate by the second variable:</h5>
<p id="blog_text">
We follow the same steps as above but for the y variable:
$$\frac{\partial f(x, y)}{\partial y} = 2y$$
<br />
Therefore the partial derivative vector of f(x, y) is:
$$\nabla f(x, y) = 
\begin{bmatrix}
\frac{\partial f(x, y)}{\partial x} \\
\frac{\partial f(x, y)}{\partial y} \\
\end{bmatrix} =
\begin{bmatrix}
2x \\
2y \\
\end{bmatrix}
$$
</p>
<br />


</div>




