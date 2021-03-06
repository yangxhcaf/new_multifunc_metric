# Exploring the relationship between E and A
Robert Bagchi  
`r format(Sys.time(), '%d %B, %Y')`  

## 1. Definitions

The data inputted into the equations are:

*  $S$   = number of functions
*  $F_i$ = observed provision of each function, $i$, standardised by dividing by the observed (or theoretical) maximum of $i$.

### 2. Calculated metrics

The terms above are then used to estimate a number of metrics, including:

1. The average level of theset of ecosystem functions considered. 
$$
\tag{eq. 1}
A = \frac{1}{S}\cdot{\sum_{i=1}^S {F_i}} 
$$

2. The proportion of the total functioning contributed 
$$
\tag{eq. 2}
p_i = \frac{F_i}{\sum_{i=1}^S{F_i}}
$$
3. The effective number of functions, $^qN$
$$
\tag{eq. 3}
^{q}N = \left(\sum_{i=1}^{S}p_{i}^q \right)^{1/(1-q)}
$$
which can be converted into 

4.  the evenness of functioning, $^qE$

$$
\tag{eq. 4}
^qE = {^qN}/S
$$
## 3. Examining the relationships

The first thing we need to do is to incorporate $A$ into the equations for $^qN$ and $^qE$. To do so, we first note that $p_i$ can be related to $A$ using eq. 1 to express $\sum_{i=1}^SF_i = AS$ to replace the denominator of eq. 2 and get.

$$
\tag{eq. 5}
p_i = \frac{F_i}{A \cdot S}
$$

This allows us to replace $p_i$ with a function of $A$ in subsequent equations. Thus, we get,

$$
\tag{eq. 6}
^{q}N = \left[\sum_{i=1}^{S}\left({\frac{F_{i}}{A \cdot S}}\right)^q \right]^{1/(1-q)}
$$
Which can be simplified by removing the constants $A$ and $S$ out of the parentheses.
$$
\tag{eq. 7}
^{q}N = \left[{\frac{1}{A^q \cdot S^{q}}} \cdot \sum_{i=1}^{S}F_{i}^q \right]^{1/(1-q)}
$$
Because both $q$ and $F_i$ are always positive, we can express $^qE$ as

$$
\begin{aligned} 
^{q}E &= \frac{1}{S}\left[{\frac{1}{A^q \cdot S^{q}}} \sum_{i=1}^{S}F_{i}^q \right]^{1/(1-q)} \\
&\Rightarrow \frac{1}{S}\left[{\frac{1}{A \cdot S}}\right]^{q/{1-q}}\left[ \sum_{i=1}^{S}F_{i}^q \right]^{1/(1-q)} \\
&\Rightarrow \left[ {\frac{1}{A^q \cdot S}}\sum_{i=1}^{S}F_{i}^q \right]^{1/(1-q)} \\
\end{aligned}
$$
From these formula, the relationship between $^qE$ and $A$ can be derived for specific values of $q$ as 

* q = 0 (number of functions with non-zero provision)

$$
^{0}E = \frac{1}{S}\cdot \sum_{i=1}^{S}F_{i}^0 = 1
$$
**If** I've got the maths right, then this is a way of checking!

* q = 2 (equivalent to Simpson's index)

$$
^{2}E = \frac{S\cdot A^{2}}{\sum_{i=1}^{S}F_{i}^2}
$$
* q = 1 (equivalent to Shannon's entropy)
The $q = 1$ case is a little trickier because of the need to use limits. Rather than use limits themselves here, we start off with the equation for the effective number of species for $q = 1$, $^1S = \exp(H) = \exp(-\sum_{i=1}^{S}{p_i \cdot \log{p_i}})$. We can then derive $^1E$ as:

$$
\begin{align*}
^1E &= \frac{1}{S}\exp{\left[\sum_{i=1}^S{\frac{F_i}{A\cdot S}\cdot \log{\frac{F_i}{A \cdot S}}}\right]} \\
&\Rightarrow \frac{1}{S}\exp{\left[\frac{1}{A\cdot S}\sum_{i=1}^S{F_i \cdot 
\left( \log F_i - \log{A \cdot S} \right)} \right]} \\
\end{align*}
$$
 
To examine the relationship between A and E we need to find equations for the maximum and minimum of E for a given A. How you do that with the current equation however, is beyond me! @jebyrnes

I tried substituting $\sum{F_i}$ with $c$ and $\sum{F_i\log F_i}$ with $d$ and throwing it into Mathematica. Not sure that is kosher, but it was the best I could think of. We then get the derivative as:

$$
\begin{align*}
\frac{dE}{dA} &= \frac{1}{S}\exp \left[\frac{d-c\cdot \log (S\cdot A)}{SA} \right] 
\cdot\left[\frac{ c\cdot (\log (S\cdot A) -1) - d}{S \cdot A^2}  \right]\\
 &\Rightarrow \frac{1}{S}\exp \left[\frac{\sum{F_i\log F_i}-\sum{F_i}\cdot \log (S\cdot A)}{SA} \right] 
 \cdot \left[\frac{ \sum{F_i}\cdot (\log (S\cdot A) -1) - \sum{F_i\log F_i}}{S \cdot A^2}  \right]
\end{align*}
$$

I don't know how correct that is, and if anyone is better at the maths, please check what I've done. I have as much confidence in this as in the future prosperity of the human species...

Armed with that equation, we can then set the rhs to 0 and solve to find out how the minimum (and maximum) changes with A. However, I don't want to embark on this until someone has had chance to look at it. Could someone (@jebyrnes) take a look? 
