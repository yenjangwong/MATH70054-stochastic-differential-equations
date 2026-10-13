# Coursework Solution CID: 02518058

## 1(a)

Use integrating factor $e^t$

$$
\begin{aligned}d(e^t X(t)) &= e^t dX(t) + X(t)de^t \\ &= e^t[(\mu - X(t))dt + \sigma dW(t)] + X(t)e^t dt \\&= \mu e^t dt + \sigma e^t dW(t).\end{aligned}
$$

Integrate both sides 

$$
e^t X(t) -e^0X(0)=  \mu \int_0^t e^s ds + \sigma \int_0^t e^s dW(s) \\= x_0 +\mu(e^t - 1) + \sigma \int_0^t e^s dW(s).
$$

Thus

$$
X(t) = x_0 e^{-t} + \mu(1-e^{-t}) + \sigma\int_0^t e^{-(t-s)}dW(s)
$$

## 1(b)

We have

$$
X(t) = x_0 e^{-t} + \mu(1-e^{-t}) + \sigma\int_0^t e^{-(t-s)}dW(s)
$$

Since $\langle dW(s) \rangle = 0$, taking expectations give

$$
\langle X(t) \rangle = x_0 e^{-t} + \mu(1-e^{-t})  \\
=\mu + (x_0 - \mu)e^{-t}
$$

For variance, use $dW(t)^2=dt$

$$
X(t) - \langle X(t) \rangle = \sigma \int_0^t e^{-(t-s)}dW(s)
$$

$$
\langle [X(t) - \langle X(t) \rangle]^2 \rangle = \sigma^2 \left\langle \left[\int_0^t e^{-(t-s)}dW(s)\right]^2 \right\rangle
\\= \sigma^2\int_0^t e^{-2(t-s)} ds = \frac{\sigma^2 }{2}(1 - e^{-2t})
$$

## 1(c)

Generator of the diffusion process is defined as 

$$
 \mathbb{L} := A(x)\frac{\partial }{\partial x} + \frac{1}{2}\Sigma(x)\frac{\partial^2 }{\partial x^2}
$$

For $f\in C_b^2(\R)$

$$
\mathbb{L}f = (\mu-x)f'(x) + \frac{\sigma^2}{2}f''(x)
$$

The $L^2$-adjoint of the generator $\mathbb{L}^*$ is 

$$
\mathbb{L}^*p = -\frac{\partial}{\partial x}[(\mu-x)p(x,t)] + \frac{\sigma^2}{2}\frac{\partial^2}{\partial x^2}p(x,t)
$$

Hence, the forward Fokker-Planck equation for density $p(x,t)$ is 

$$
\frac{\partial p}{\partial t} = \mathbb{L}^* p = -\frac{\partial}{\partial x}[(\mu-x)p] + \frac{\sigma^2}{2}\frac{\partial^2 p}{\partial x^2},
$$

with initial condition  

$$
p(x,0 \mid x_0) = \delta(x-x_0)
$$

## 1(d)

We can write the forward FP equation in conservative form as

$$
\frac{\partial p(x,t)}{\partial t} = -\frac{\partial J(x,t)}{\partial x}, 
$$

where $J(x,t)$ is the probability flux, defined as

$$
J(x,t) = (\mu-x)p(x,t) - \frac{\sigma^2}{2}\frac{\partial p(x,t)}{\partial x} 
$$

Steady state means probabiliy flux is zero $J(x,t)=0$, hence

$$
(\mu-x)p(x) - \frac{\sigma^2}{2}p'(x)=0\\
\frac{p'(x)}{p(x)} = \frac{2}{\sigma^2}(\mu-x)
$$

Integrate both sides, we obtain

$$
\ln p(x) = \frac{2\mu}{\sigma^2}x - \frac{x^2}{\sigma^2} + C 
$$

We know 

$$
x^2 - 2\mu x = (x-\mu)^2 - \mu^2\\
-\frac{x^2 - 2\mu x}{\sigma^2} = -\frac{(x-\mu)^2}{\sigma^2} + \frac{\mu^2}{\sigma^2}
$$

So

$$
p(x) = Ce^{\mu^2/\sigma^2}\exp\left(-\frac{(x-\mu)^2}{\sigma^2}\right)\\
p(x) = C\exp\left(-\frac{(x-\mu)^2}{\sigma^2}\right)
$$

We can normalise it with a normalisation constant 

$$
p(x) = \mathcal{N}\exp\left(-\frac{(x-\mu)^2}{\sigma^2}\right) 
$$

Compare to standard gaussian

$$
f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}
$$

We have mean $\mu$ and variance $\sigma^2/ 2$.

They are are consistent with the $t \to \infty$ limits from part (b):

$$
\mathbb{E}[X(t)] = \mu + (x_0-\mu)e^{-t} \to \mu
$$

$$
\text{Var}[X(t)] = \frac{\sigma^2}{2}(1-e^{-2t}) \to \frac{\sigma^2}{2}
$$

## 2(a)

Using Ito’s formula, 

$$
df(X) = \left[A(X)f'(X) + \frac{1}{2}B(X)^2 f''(X)\right]dt + B(X)f'(X)dW(t)
$$

With 

$$
A(x) = \frac{1}{4}-x, B(x) = \sqrt{x}
$$

Let $f(x) = 2\sqrt{x}$. Then

$$
f'(x) = \frac{1}{\sqrt{x}}, \quad f''(x) = -\frac{1}{2}x^{-3/2}
$$

Calcualte each terms

$$
B(X)f'(X)dW(t) = \sqrt{X(t)} \cdot \frac{1}{\sqrt{X(t)}}dW(t) = dW(t)
$$

$$
A(X)f'(X) = \frac{\frac{1}{4} - X(t)}{\sqrt{X(t)}} = \frac{1}{4\sqrt{X(t)}} - \sqrt{X(t)}
$$

$$

\frac{1}{2}B(X)^2 f''(X) = \frac{1}{2}X(t)\left(-\frac{1}{2}X(t)^{-3/2}\right) = -\frac{1}{4\sqrt{X(t)}}

$$

Combine:

$$
dY(t)=-\sqrt{X(t)}dt +dW(t) \\
dY(t)=-\frac{1}{2}Y(t)dt +dW(t)
$$

Use integrating factor $e^{t/2}$

$$
\begin{aligned}d(e^{t/2} Y(t)) &= e^{t/2} dY(t) + Y(t)de^{t/2} \\ &= e^{t/2}[-\frac{1}{2}Y(t)dt +dW(t)] + \frac{1}{2}Y(t)e^{t/2} dt \\&= e^{t/2}dW(t)\end{aligned}
$$

Integrate both sides 

$$
e^{t/2} Y(t) = Y_0 + \int_0^t e^{s/2} dW(s)
$$

Thus

$$
Y(t) = Y_0e^{-t/2} + \int_0^t e^{-(t-s)/2}dW(s), \quad Y_0 = 2\sqrt{x}.
$$

Transforming back

$$
X(t) = \frac{1}{4}Y(t)^2 = \frac{1}{4}\left(2\sqrt{x}e^{-t/2} + \int_0^t e^{-(t-s)/2}dW(s)\right)^2 
$$

## 2(b)

The general Stratonovich version of SDE has the form 

$$
dX(t) = A(X)dt + B(X) \circ dW(t)
$$

In this question, we have 

$$
A(X)=0, \quad B(X)=f(X(t)) 
$$

Given the equivalent Itô SDE of the form 

$$
dX = \left[A(X)+\alpha B(X)\frac{\partial B(X)}{\partial x}\right]dt + B(X)dW(t)
$$

With $\alpha =0.5$ for Stratonovich, we get

$$
dX(t) = \frac{1}{2}f(X(t))f'(X(t))dt + f(X(t))dW(t)
$$

Using change of variables $Y(t) = F(X(t))$ and the hint $F(X(t)) = \int^{X(t)} \frac{1}{f(y)}dy$

$$
F'(X) = \frac{1}{f(X)}, \quad F''(X) = -\frac{f'(X)}{f(X)^2}.
$$

Do taylor expansion

$$
df(X) = f(X+dX)-f(X) \\ = f'(X)dX + \frac{1}{2}f''(X)dX^2 + \dots
$$

So

$$
dY(t) = F'(X(t))dX(t) + \frac{1}{2}F''(X(t))(dX(t))^2.
$$

First term

$$
F'(X)dX = \frac{1}{f(X)}\left[\frac{1}{2}f(X)f'(X)dt + f(X)dW\right] = \frac{1}{2}f'(X)dt + dW.
$$

Second term

$$
(dX)^2 = f(X)^2 dW^2 = f(X)^2 dt
$$

$$
\frac{1}{2}F''(X)(dX)^2 = \frac{1}{2}\left(-\frac{f'(X)}{f(X)^2}\right)f(X)^2 dt = -\frac{1}{2}f'(X)dt.
$$

Combine and we get 

$$
dY(t) = \left(\frac{1}{2}f'(X(t)) - \frac{1}{2}f'(X(t))\right)dt + dW(t) = dW(t) \\
Y(0) = F(x_0).
$$

Integrating and we get

$$
Y(t) = F(x_0) + W(t).
$$

Hence

$$
X(t) = F^{-1}(Y(t)) = F^{-1}(F(x_0) + W(t)), \quad F(x) = \int^x \frac{1}{f(y)}dy.
$$

## 2(c)

If

$$
dX(t) = f(X(t)) \circ dW(t)
$$

then the equivalent Itô SDE for Stratonovich is 

$$
dX(t) = \frac{1}{2}f(X(t))f'(X(t))dt + f(X(t))dW(t)
$$

Take

$$
f(x) = \sqrt{1-x^2}
$$

Get derivatives

$$
f'(x)  = -\frac{x}{\sqrt{1-x^2}}
$$

$$
\frac{1}{2}f(x)f'(x) = \frac{1}{2}\sqrt{1-x^2}\left(-\frac{x}{\sqrt{1-x^2}}\right) = -\frac{1}{2}x
$$

So the corresponding Ito SDE is 

$$
dX(t) = -\frac{1}{2}X(t) dt + \sqrt{1-X(t)^2}dW(t)
$$

which is exactly the given Ito SDE. Therefore, we can write 

$$
dX(t) = \sqrt{1-X(t)^2} \circ dW(t)
$$

From part (b), the solution of this form is

$$
X(t) = F^{-1}(F(x_0) + W(t))
$$

where

$$
F(x) = \int^x \frac{1}{f(y)}dy = \int^x \frac{1}{\sqrt{1-y^2}}dy = \arcsin(x)
$$

So let

$$
F(x) = \arcsin(x), \quad F^{-1}(u) = \sin(u)
$$

Hence

$$
X(t) = F^{-1}(F(x_0) + W(t)) = \sin(W(t) + \arcsin(x_0))
$$

## 3(a)

Drift vector:

$$
\mathbf{A}(x,y,z) = \begin{pmatrix} y \\ -x+z \\ -z-y \end{pmatrix}
$$

There is one Brownian motion with coefficient vector

$$
B(x,y,z) = \begin{pmatrix} 0 \\ 0 \\ \sqrt{2} \end{pmatrix}
$$

so

$$
BB^\top = \begin{pmatrix} 0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 2 \end{pmatrix}
$$

Diffusion matrix $(\frac{1}{2}(\sqrt2)^2=1)$

$$
\mathbf{\Sigma} = \frac{1}{2}BB^\top = \begin{pmatrix} 0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 1 \end{pmatrix}
$$

The generator $\mathbb{L}$ acting on a smooth test function $f(x,y,z)$ is 

$$
\begin{aligned} \mathbb{L}f &= \mathbf{A} \cdot \nabla f + \frac{1}{2} \text{Tr}(BB^\top \nabla^2 f)  \\ &= \sum_{j=1}^d A_j\frac{\partial f}{\partial y_j} + \frac{1}{2}\sum_{i,j=1}^d (BB^\top)_{ij}\frac{\partial^2 f}{\partial y_i \partial y_j}
\\ &=  y\frac{\partial f}{\partial x} + (z-x)\frac{\partial f}{\partial y} - (y+z)\frac{\partial f}{\partial z} + \frac{\partial^2 f}{\partial z^2} 
\end{aligned}
$$

The $L^2$-adjoint $\mathbb{L}^*$is 

$$
\mathbb{L}^*f 
= -\nabla \cdot (\mathbf{A}f) +\frac{1}{2} \text{Tr}(BB^\top \nabla^2 f) ) \\
= -\sum_{j=1}^d \frac{\partial (A_jf)}{\partial y_j} + \frac{1}{2}\sum_{i,j=1}^d (BB^\top)_{ij}\frac{\partial^2 f}{\partial y_i \partial y_j}
\\ = -\frac{\partial}{\partial x}(yf) - \frac{\partial}{\partial y}((z-x)f) - \frac{\partial}{\partial z}((-y-z)f) + \frac{\partial^2 f}{\partial z^2} 
$$

The forward (Fokker-Planck) Kolmogorov equation for joint probability density $p(x,y,z,t)$ is 

$$
\frac{\partial p}{\partial t} = \mathbb{L}^*p = -y\frac{\partial p}{\partial x} + (x-z)\frac{\partial p}{\partial y} + \frac{\partial}{\partial z}((y+z)p) + \frac{\partial^2 p}{\partial z^2}
$$

With initial conditions

$$
X(0) = x_0, Y(0) = y_0, Z(0) \sim \mathcal{N}(0, 1)
$$

And initial density

$$
p(x, y, z, 0) = \delta(x - x_0) \delta(y - y_0) \frac{1}{\sqrt{2\pi}} e^{-z^2/2}
$$

## 3(b)

Use the integrating factor $e^t$

$$
d(e^tZ(t)) = e^tdZ(t) + e^tZ(t)dt = e^t(dZ+Zdt) \\= -e^tY(t)dt + \sqrt{2}e^tdW(t)
$$

Integrate

$$
e^tZ(t)  = Z(0) -\int_0^t e^s Y(s)ds + \sqrt{2}\int_0^t e^s dW(s)
$$

So

$$
Z(t) = e^{-t}Z(0) - \int_0^t e^{-(t-s)}Y(s)ds + \sqrt{2}\int_0^t e^{-(t-s)}dW(s)
$$

Let

$$
F(t) = e^{-t}Z(0) + \sqrt{2}\int_0^t e^{-(t-s)}dW(s)
$$

then

$$
Z(t) = F(t) - \int_0^t e^{-(t-s)}Y(s)ds
$$

Sub into $dY/dt$

$$
\frac{dY(t)}{dt} = -X(t) + Z(t) = -X(t) - \int_0^t e^{-(t-s)}Y(s)ds + F(t)
$$

Also from $dX = Ydt$

$$
\frac{dX(t)}{dt} = Y(t)
$$

Assume $t\ge s$, then

$$
F(t) = e^{-t}Z(0) + \sqrt{2}\int_0^t e^{-(t-u)}dW(u) \\
F(s) = e^{-s}Z(0) + \sqrt{2}\int_0^s e^{-(s-v)}dW(v)
$$

$$
\begin{aligned}
\mathbb{E}[F(t)F(s)] &= e^{-t-s}\mathbb{E}[Z(0)^2] \\
&+ \sqrt{2}e^{-t}\mathbb{E}\left[Z(0)\int_0^s e^{-(s-v)}dW(v)\right] \\
&+ \sqrt{2}e^{-s}\mathbb{E}\left[Z(0)\int_0^t e^{-(t-u)}dW(u)\right] \\
&+ 2\mathbb{E}\left[\int_0^t e^{-(t-u)}dW(u)\int_0^s e^{-(s-v)}dW(v)\right]
\end{aligned}
$$

Because $W(t)$ is a Brownian motion independent of $Z(0)$ and $\mathbb{E}[Z(0)]=0$, the second and third term vanish. 

For the first term:

$$
\mathbb{E}[Z(0)^2] = \text{Var}(Z(0)) + (\mathbb{E}[Z(0)])^2 = 1+0=1 
$$

so

$$
\\
e^{-t-s}\mathbb{E}[Z(0)^2]= e^{-t-s}
$$

For the forth term, since we assume $t\ge s$, we can decompose

$$
\int_0^t e^{-(t-u)}dW(u) = \int_0^s e^{-(t-u)}dW(u) + \int_s^t e^{-(t-u)}dW(u)
$$

The brownian increments from $s$ to $t$ is independent of the increments from 0 to $s$, so the expectations of their product is zero, so we just need to handle the interval from 0 to s only or take $\min(t,s)=s$, so

$$
\mathbb{E}\left[\int_0^t e^{-(t-u)}dW(u)\int_0^s e^{-(s-v)}dW(v)\right] \\= \int_0^s e^{-(t-u)}e^{-(s-u)}du = \int_0^s e^{-(t+s-2u)}du \\
= e^{-(t+s)}\int_0^s e^{2u}du = e^{-(t+s)} \cdot \frac{e^{2s}-1}{2} 
$$

Hence, 

$$
 
\mathbb{E}[F(t)F(s)]= e^{-t-s}+2 \cdot e^{-(t+s)} \cdot \frac{e^{2s}-1}{2} \\= e^{-t-s} + e^{-(t-s)} - e^{-(t+s)} = e^{-(t-s)}
$$

For $s>t$, by the same argument, we obtain $e^{-(s-t)}$, hence

$$
\mathbb{E}[F(t)F(s)] = e^{-|t-s|}
$$

## 3(c)

A continuous stochastic process is said to satisfy the Markov property if

$$
p(x_n, t_n|x_1, \dots, x_{n-1}; t_1, \dots, t_{n-1}) = p(x_n, t_n|x_{n-1}, t_{n-1})
$$

So in a Markov process, the change at time $t$ must only depends on the current state $(X(t),Y(t))$ and current noise increment. 

However, $(X(t), Y(t))$ is not a Markov process because looking at the equation for $Y$, the drift term here 

$$
\int_0^t e^{-(t-s)}Y(s)ds
$$

contain all memory about the past $0 \le s\le t$, so it does not satisfy the Markov property. The exponential term $e^{-(t-s)}$ put weights on the past values that decay exponentially. 

Also, the driving term $F(t)$ is not white noise, it is colored noised with an autocorrelation of $e^{-|t-s|}$.  This mens that the force at time $t$ is correlated with the force at previous time. 

## 4(a)

Given the OU process in vector form 

$$
d\mathbf{X}(t) = \mathbf{A}\mathbf{X}(t)dt + \mathbf{B}d\mathbf{W}(t)
$$

Use integrating factor $e^{-\mathbf{A}t}$

$$
\begin{aligned}d(e^{-\mathbf{A}t} \mathbf{X}(t)) 

&= -\mathbf{A}e^{-\mathbf{A}t}\mathbf{X}(t)dt + e^{-\mathbf{A}t}d\mathbf{X}(t)

\\ &= -\mathbf{A}e^{-\mathbf{A}t}\mathbf{X}(t)dt + e^{-\mathbf{A}t}(\mathbf{A}\mathbf{X}(t)dt + \mathbf{B}d\mathbf{W}(t))

\\&= e^{-\mathbf{A}t}  \mathbf{B}d\mathbf{W}(t)
\end{aligned}
$$

Integrate

$$
e^{-\mathbf{A}t} \mathbf{X}(t) = \mathbf{X}(0) + \int_0^t e^{-\mathbf{A}t'} \mathbf{B}d\mathbf{W}(t') \\
\mathbf{X}(t) = e^{\mathbf{A}t}\bar{\mathbf{x}} + \int_0^t e^{\mathbf{A}(t-t')}\mathbf{B} d\mathbf{W}(t')
$$

Where $\mathbf{X}(0) = \bar{\mathbf{x}}$ 

## 4(b)

Taking expectation on both side

$$
\langle \mathbf{X}(t) \rangle = e^{\mathbf{A}t}\bar{\mathbf{x}} + \int_0^t e^{\mathbf{A}(t-t')}\mathbf{B} \langle d\mathbf{W}(t')\rangle
$$

Since $\langle d\mathbf{W}(t')\rangle=0$, we have

$$
\langle \mathbf{X}(t) \rangle = e^{\mathbf{A}t}\bar{\mathbf{x}}
$$

The centered process is

$$
\mathbf{X}(t)  -  \langle \mathbf{X}(t) \rangle = \int_0^t e^{\mathbf{A}(t-t')}\mathbf{B} d\mathbf{W}(t')
$$

$$
\mathbf{X}(s)  -  \langle \mathbf{X}(s) \rangle = \int_0^s e^{\mathbf{A}(s-u)}\mathbf{B} d\mathbf{W}(u)
$$

$$
(\mathbf{X}(s) - \langle\mathbf{X}(s)\rangle)^\top = \int_0^s d\mathbf{W}(u)^\top\mathbf{B}^\top e^{\mathbf{A}^\top(s-u)}
$$

Hence the correlation function

$$
\mathbf{C}(t,s) = \left\langle\left(\int_0^t e^{\mathbf{A}(t-t')}\mathbf{B}d\mathbf{W}(t')\right)\left(\int_0^s d\mathbf{W}(u)^\top\mathbf{B}^\top e^{\mathbf{A}^\top(s-u)}\right)\right\rangle
$$

For a $d$-dimensional standard Brownian motion, we know that

$$
\mathbb{E}[W_i(t)W_j(s)]=\delta_{i,j}\min\{t,s\} 
$$

$$
\mathbb{E}\left[\int_0^t F(t')d\mathbf{W}(t')\int_0^s d\mathbf{W}(u)^\top G(u)^\top\right] = \int_0^{\min(t,s)} F(u)G(u)^\top du
$$

because the nonoverlapping region simply independent of overlapping region, so the expectations of their product is zero, as explain in question 3b answer, so just take 0 to $\min(t,s)$

$$
\mathbf{C}(t,s) = \int_0^{\min(t,s)} e^{\mathbf{A}(t-t')}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top(s-t')}dt'
$$

## 4(c)

From (b)

$$
\Sigma(t) = \mathbf{C}(t,t) = \int_0^t e^{\mathbf{A}(t-t')}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top(t-t')}dt'
$$

Differentiate with respect $\Sigma(t)$ to $t$

$$
\frac{d\Sigma(t)}{dt} = \frac{d}{dt}\int_0^t e^{\mathbf{A}(t-t')}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top(t-t')}dt'
$$

Since there is no stochastic term, we use Leibniz rule

$$
\frac{d}{dt}\left(\int_0^{b(t)} f(t,u)du\right) = f(t,b(t))b'(t)  + \int_0^{b(t)} \frac{\partial}{\partial t}f(t,u)du
$$

Evaluate upper limit term, sub $t'=t$, 

$$
e^{\mathbf{A}(t-t)}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top(t-t)} = \mathbf{B}\mathbf{B}^\top
$$

Evaluate derivative of the integrand 

$$
\frac{\partial}{\partial t}\left(e^{\mathbf{A}(t-t')}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top(t-t')}\right) \\= \mathbf{A}e^{\mathbf{A}(t-t')}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top(t-t')} + e^{\mathbf{A}(t-t')}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top(t-t')}\mathbf{A}^\top
$$

Now

$$
\frac{d\Sigma(t)}{dt} = \mathbf{B}\mathbf{B}^\top + \int_0^t \left[\mathbf{A}e^{\mathbf{A}(t-t')}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top(t-t')} + e^{\mathbf{A}(t-t')}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top(t-t')}\mathbf{A}^\top\right] dt'
$$

$$
\int_0^t \mathbf{A}e^{\mathbf{A}(t-t')}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top(t-t')}dt' = \mathbf{A}\Sigma(t)
$$

$$
\int_0^t e^{\mathbf{A}(t-t')}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top(t-t')}\mathbf{A}^\top dt' = \Sigma(t)\mathbf{A}^\top
$$

Therefore,

$$
\frac{d\Sigma(t)}{dt} = \mathbf{A}\Sigma(t) + \Sigma(t)\mathbf{A}^\top + \mathbf{B}\mathbf{B}^\top
$$

To show $\Sigma(t) \to \Sigma_0$, let $\tau = t - t'$. Then $d\tau = -dt'$

- When $t' = 0$, $\tau = t$
- When $t' = t$, $\tau = 0$

Substitute these into the integral, we get

$$
\Sigma(t) = \int_0^t e^{\mathbf{A}\tau} \mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top \tau} d\tau
$$

Define the limit as $t\to\infty$

$$
\Sigma_0 = \lim_{t \to \infty} \Sigma(t) = \int_0^\infty e^{\mathbf{A}\tau} \mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top \tau} d\tau
$$

Now do

$$
\mathbf{A}\Sigma_0 + \Sigma_0\mathbf{A}^\top \\= \mathbf{A} \left(\int_0^\infty e^{\mathbf{A}\tau}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top \tau} d\tau\right) + \left(\int_0^\infty e^{\mathbf{A}\tau}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top \tau} d\tau\right) \mathbf{A}^\top
$$

Since $\mathbf{A}$ is constant, we can move inside the integral

$$
= \int_0^\infty \left(\mathbf{A}e^{\mathbf{A}\tau}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top \tau} + e^{\mathbf{A}\tau}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top \tau} \mathbf{A}^\top\right) d\tau
$$

The integrand is the derivative of the term inside the integral by product rule

$$
\frac{d}{d\tau} \left(e^{\mathbf{A}\tau}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top \tau}\right) = \mathbf{A}e^{\mathbf{A}\tau}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top \tau} + e^{\mathbf{A}\tau}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top \tau} \mathbf{A}^\top
$$

Now evaluate the integral

$$
\mathbf{A}\Sigma_0 + \Sigma_0\mathbf{A}^\top = \int_0^\infty \frac{d}{d\tau} \left(e^{\mathbf{A}\tau}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top \tau}\right) d\tau= \left[e^{\mathbf{A}\tau}\mathbf{B}\mathbf{B}^\top e^{\mathbf{A}^\top \tau}\right]_0^\infty
$$

For the upper limit, since the eigenvalues of $\mathbf{A}$ have negative real parts, the matrix exponential $e^{\mathbf{A}\tau}$ must decays to zero as $\tau \to \infty$, so $e^{\mathbf{A}\tau} \to 0$. Term vanish. 

For the lower limit, $\mathbf{I}$, so 

$$
\mathbf{I}\mathbf{B}\mathbf{B}^\top \mathbf{I} = \mathbf{B}\mathbf{B}^\top
$$

Therefore,

$$
\mathbf{A}\Sigma_0 + \Sigma_0\mathbf{A}^\top = 0 - \mathbf{B}\mathbf{B}^\top \\
\mathbf{A}\Sigma_0 + \Sigma_0\mathbf{A}^\top + \mathbf{B}\mathbf{B}^\top = 0
$$

## 4(d)

Rewrite as 

$$
\frac{d\mathbf{X}(t)}{dt} = \mathbf{A}\mathbf{X}(t) + \mathbf{B}\boldsymbol{\xi}(t).
$$

Define the Fourier transform of a function $f(t)$ as 

$$
\tilde{f}(\omega) = \int_{-\infty}^{\infty} f(t) e^{i\omega t} dt
$$

Take Fourier transform of the SDE 

$$
-i\omega \tilde{\mathbf{X}}(\omega) = \mathbf{A}\tilde{\mathbf{X}}(\omega) + \mathbf{B}\tilde{\boldsymbol{\xi}}(\omega).
$$

Rearrange

$$
(-i\omega\mathbf{I} - \mathbf{A})\tilde{\mathbf{X}}(\omega) = \mathbf{B}\tilde{\boldsymbol{\xi}}(\omega)
$$

Substitute the transfer matrix 

$$
\Phi_{ij}(\omega)=-i\omega\delta_{i,j}-A_{ij}
$$

So 

$$
\boldsymbol{\Phi}(\omega)\tilde{\mathbf{X}}(\omega) = \mathbf{B}\tilde{\boldsymbol{\xi}}(\omega)
$$

Invert the matrix 

$$
\tilde{\mathbf{X}}(\omega) = \boldsymbol{\Phi}^{-1}(\omega)\mathbf{B}\tilde{\boldsymbol{\xi}}(\omega)
$$

In component form 

$$
\tilde{X}_i(\omega) = \sum_{j=1}^d \sum_{k=1}^d \Phi_{ij}^{-1}(\omega) B_{jk} \tilde{\xi}_k(\omega).
$$

Consider the covariance of two frequency components of $X(t)$

$$
\langle \tilde{X}_i(\omega)\tilde{X}_i(\omega') \rangle = \left\langle \left( \sum_{j,k} \Phi_{ij}^{-1}(\omega) B_{jk} \tilde{\xi}_k(\omega) \right) \left( \sum_{j',k'} \Phi_{ij'}^{-1}(\omega') B_{j'k'} \tilde{\xi}_{k'}(\omega') \right) \right\rangle
$$

Since $\Phi^{-1}$ and $B$ are deterministic, we move them out of the expectation,

$$
\langle \tilde{X}_i(\omega)\tilde{X}_i(\omega') \rangle = \sum_{j,j'} \sum_{k,k'} \Phi_{ij}^{-1}(\omega) B_{jk} \Phi_{ij'}^{-1}(\omega') B_{j'k'} {\langle \tilde{\xi}_k(\omega) \tilde{\xi}_{k'}(\omega') \rangle}
$$

Calculate noise correlation in the frequency domain using the time-domain properties provided: $\langle \xi_k(t)\xi_{k'}(t') \rangle = \delta_{kk'}\delta(t-t')$

$$
\begin{aligned}
\langle \tilde{\xi}_k(\omega) \tilde{\xi}_{k'}(\omega') \rangle &= \int_{-\infty}^\infty dt \int_{-\infty}^\infty dt' e^{i\omega t} e^{i\omega' t'} \langle \xi_k(t)\xi_{k'}(t') \rangle \\
&= \delta_{kk'} \int_{-\infty}^\infty dt \int_{-\infty}^\infty dt' e^{i\omega t} e^{i\omega' t'} \delta(t-t') \\
&= \delta_{kk'} \int_{-\infty}^\infty dt \, e^{i(\omega + \omega')t} \\
&= \delta_{kk'} 2\pi \delta(\omega + \omega').
\end{aligned}
$$

Substitute back and we get

$$
\langle \tilde{X}_i(\omega)\tilde{X}_i(\omega') \rangle = \sum_{j,j'} \Phi_{ij}^{-1}(\omega) \Phi_{ij'}^{-1}(\omega') \left( \sum_k B_{jk} B_{j'k} \right) 2\pi \delta(\omega + \omega')
$$

Noted that the term $\delta_{kk'}$ forces $k = k'$, s o we get single sum

Since the diffusion matrix term is 

$$
\sum_k B_{jk} B_{j'k} = (\mathbf{B}\mathbf{B}^\top)_{jj'} = D_{jj'}
$$

We now have

$$
\langle \tilde{X}_i(\omega)\tilde{X}_i(\omega') \rangle = \left[ \sum_{j,j'} \Phi_{ij}^{-1}(\omega) \Phi_{ij'}^{-1}(\omega') D_{jj'} \right] 2\pi \delta(\omega + \omega').
$$

The Wiener-Khinchin theorem states:

$$
\langle \tilde{X}_i(\omega)\tilde{X}_i(\omega') \rangle = 2\pi S_i(\omega)\delta(\omega+\omega')
$$

Comparing terms, and noting that the Dirac delta implies that the expression is non-zero only when $\omega' = -\omega$, hence we get

$$
S_i(\omega) = \sum_{j=1}^d \sum_{j'=1}^d \Phi_{ij}^{-1}(\omega)\Phi_{ij'}^{-1}(-\omega)D_{jj'}
$$

## 5(a)

Drfit and diffusion coefficient are

$$
A(x) = -x^3+x, \quad \Sigma(x)=(\sqrt2)^2=2
$$

Generator is

$$
\mathbb{L} = A(x)\partial_x + \frac{1}{2}\Sigma(x)\partial_x^2 = (-x^3+x)\partial_x + \partial_x^2.
$$

Backward Kolmogorov equation for $u(x,t)=\mathbb{E}(f(X(t) \mid X(0)=x)$ is

$$
\frac{\partial u}{\partial t} = \mathbb{L}u= (-x^3+x)\frac{\partial u}{\partial x} + \frac{\partial^2 u}{\partial x^2}
$$

Forward Kolmogorov equation for density $p(x,t)$ is 

$$
\frac{\partial p}{\partial t} = \mathbb{L}^* p = -\frac{\partial}{\partial x}[(-x^3+x)p(x,t)] + \frac{\partial^2 p}{\partial x^2}, \quad p(x,0) = p_0(x).
$$

## 5(b)

$$
m_n(t) = \mathbb{E}[X(t)^n]=\int_\mathbb{R} x^n p(x,t)dx
$$

$$
\frac{d}{dt}m_n(t) = \int_{\mathbb{R}} x^n \frac{\partial p}{\partial t}(x, t) dx
$$

$$
\frac{d}{dt}m_n(t) = -\int_{\mathbb{R}} x^n\frac{\partial}{\partial x}[(-x^3 + x)p] dx + \int_{\mathbb{R}} x^n\frac{\partial^2 p}{\partial x^2} dx=I_1+I_2
$$

Integrate by parts for drift term $I_1$

$$
u = x^n, \quad dv = \partial_x[(-x^3+x)p] dx
$$

$$
du = nx^{n-1}dx, \quad v = (-x^3+x)p
$$

$$
I_1 = -[x^n(-x^3+x)p]_{-\infty}^{\infty} + \int (-x^3+x)p nx^{n-1} dx
$$

assume $p$ vanish sufficiently fast at boundary, so boundary term vanishes

$$
-[x^n(-x^3+x)p]_{-\infty}^{\infty}=0
$$

so

$$
I_1 = n \int_{\mathbb{R}} x^{n-1}(-x^3+x)pdx 
\\= n\mathbb{E}[X^{n-1}(-X^3 + X)] 
\\= n\mathbb{E}[-X^{n+2} + X^n] 
\\= n(-m_{n+2}(t) + m_n(t))
$$

Integrate by parts twice for diffusion term $I_2$

$$
u = x^n, \quad dv = p_{xx} dx
$$

$$
du = nx^{n-1}dx, \quad v = p_x
$$

$$
I_2  = [x^n p_x]_{-\infty}^{\infty} - \int nx^{n-1} p_x dx
$$

assume $p$ and its detivatives decay sufficiently fast as $|x| \to \infty$, so the boundary term vanish

$$
[x^n p_x]_{-\infty}^{\infty} = 0
$$

so

$$
I_2 = -n \int x^{n-1} p_x dx
$$

$$
u = x^{n-1}, \quad dv = p_x dx
$$

$$
du = (n - 1)x^{n-2}dx, \quad v = p
$$

$$
I_2= -n[x^{n-1}p]_{-\infty}^{\infty} +n \int (n - 1)x^{n-2}p dx
$$

Again the boundary term vanishes, so

$$
I_2 = n(n - 1) \int x^{n-2}p(x,t) dx \\
\\= n(n - 1)m_{n-2}(t) 
$$

Combine

$$
\frac{d}{dt}m_n(t)=I_1+I_2= n(-m_{n+2}(t) + m_n(t))+n(n - 1)m_{n-2}(t) 

$$

For $n=0$

$$
\frac{d}{dt}m_0(t)=0
$$

Since $m_0(t)=\mathbb{E}[X^0]=\int p(x,t)dx = \int p_0(x)dx=1$, so

$$
m_0(t)=m_0(0)=1
$$

For $n=1$

$$
\frac{d}{dt}m_1(t)=m_1(t)-m_3(t)
$$

the first moment depends on the third moment

For $n=2$

$$
\frac{d}{dt}m_2(t) = 2(-m_4(t) + m_2(t)) + 2 \cdot 1 \cdot m_0(t) \\= 2(m_2(t) - m_4(t)) + 2m_0(t)
$$

Using $m_0(t) = 1$, this becomes

$$
\frac{d}{dt}m_2(t) = 2(m_2(t) - m_4(t)) + 2
$$

second moment also depends on higher moment term.

## 5(c)

At stationary, $\partial_tp=0$, so 

$$
0=-\frac{d}{d x}A(x) p(x) + \frac{d^2 }{d x^2} p(x)
$$

$$
0= \frac{d}{dx}\left( -A(x)p(x) + \frac{d}{dx}p(x) \right)
$$

$$
\frac{d}{dx}(-A(x)p(x) + p'(x)) = 0
$$

$$
-A(x)p(x) + p'(x) = C
$$

Since $p(x)$ is a probability density on $\mathbb{R}$ that decays (and so does $p'(x)$) as $|x| \to \infty$. Then the LHS goes to 0 as $|x| \to \infty$, so

$$
C = 0
$$

So

$$
\frac{p'(x)}{p(x)} = A(x) 
$$

$$
\frac{d}{dx}(\ln p(x)) = A(x)
$$

Integrate:

$$
\ln p(x) = \int A(x) dx + C_1
$$

$$
p(x) = e^{C_1} \exp\left(\int A(x) dx\right)
$$

Define

$$
V(x) = -\int A(x) dx = -\int (-x^3+x)=\frac{x^4}{4}-\frac{x^2}{2}+C_2
$$

Absorb the constant $C_2$ into $C_1$, so we take

$$
V(x) = \frac{x^4}{4}-\frac{x^2}{2}
$$

Then

$$
p(x) = e^{C_1}e^{-V(x)}
$$

Define normalisation constant such that $\int p(x)dx=1$ 

$$
e^{C_1}=Z^{-1}, \quad  Z= \int_{\mathbb{R}} e^{-V(x)} dx
$$

Hence

$$
p^*(x) = Z^{-1}e^{-V(x)}
$$

$$
p^*(x) = Z^{-1}\exp(-\frac{x^4}{4}+\frac{x^2}{2})
$$

## 5(d)

$$
\mathbb{L}^*(h(x)p^*(x))=0
$$

$$
-\frac{d}{dx}[A(x)h(x)p^*(x)] + \frac{d^2}{dx^2}[h(x)p^*(x)] = 0
$$

Let $Ahp=A(x)h(x)p^*(x)$ and expand derivatives

First term:

$$
-\frac{d}{dx}[h \cdot (Ap)] = -h'(Ap) - h(Ap)'
$$

Second term:

$$
\frac{d}{dx}[hp] = h'p + hp'
$$

$$
\begin{aligned} \frac{d^2}{dx^2}[hp] &= \frac{d}{dx}[h'p + hp'] = (h''p + h'p') + (h'p' + hp'') \\ &= h''p + 2h'p' + hp'' \end{aligned}
$$

Combine:

$$
-h'(Ap) - h(Ap)'+h''p + 2h'p' + hp''=0
$$

Rearrage:

$$
h(x)[-(Ap)' + p''] + h'(x)[-Ap + 2p'] + h''(x)p = 0
$$

This term $[-(Ap)' + p'']$ is $\mathbb{L}^*p$. Since $p=p^*(x)$ is the stationary density, we have $\mathbb{L}^*p=0$ so the first $h(x)$ term vanish. 

Part (c) also shown that for the stationary density $p=p^*(x)$,

$$
-Ap+p'=0
$$

Substitute $p'=Ap$, we get

$$
h'(x)[-Ap + 2Ap] + h''(x)p = 0 \\
h'(x)[Ap] + h''(x)p = 0
$$

Since $p$ is probability density and is strictyly positive, we divide by $p$ and get

$$
A(x)h'(x)+h''(x)=0
$$

Since the generator $\mathbb{L}$ is defined as 

$$
\mathbb{L}=A(x)\partial_x+\partial_x^2
$$

Hence,

$$
\mathbb{L}h(x)=A(x)h'(x)+h''(x)=0
$$

Now multiply by $h(x)p^*(x)$ and integrate

$$
\int_{\mathbb{R}} h(x)p^*(x) [A(x)h'(x) + h''(x)] dx = 0
$$

$$
\int_{\mathbb{R}} h(x)h'(x)A(x)p^*(x)dx+\int_{\mathbb{R}}  h(x)p^*(x)h''(x) dx = I_1+I_2=0
$$

For the first integral, substituite $A(x)p^*(x)=p'^*(x)$

$$
I_1=\int_{\mathbb{R}} h(x)h'(x)p'^*(x)dx
$$

For the second integral, do integration by parts

Let $u = h(x)p^*(x)=hp$ and $dv = h''(x)dx=h''dx$.Then 

$$
du = h'p+hp' \\
v = h'
$$

$$
I_2 = [hph']_{-\infty}^{\infty} - \int_{\mathbb{R}} h' (h'p + hp') dx
$$

Since $p(x)$ is a probability density on $\mathbb{R}$ that decays to 0 as $|x| \to \infty$, so boundary term vanish and we get

$$
I_2 = - \int_{\mathbb{R}} |h'|^2p^*dx - \int_{\mathbb{R}} h'hp'^*dx
$$

Combine $I_1+I_2$

$$
\int_{\mathbb{R}} hh'p'^*dx- \int_{\mathbb{R}} |h'|^2p^*dx - \int_{\mathbb{R}} h'hp'^*dx=0
$$

Hence

$$
\int_{\mathbb{R}} |h'|^2p^*dx=0
$$

We know that the stationary density $p^*(x) = Z^{-1}e^{-V(x)}$ is strictly positive for all $x$ 

Since $|h'(x)|^2 \ge 0$ and $p^*(x) > 0$, the integral can only be zero if the integrand is zero everywhere. This means that $h(x)$ is a constant:

$$
h(x) = C
$$

From part (c) we know $p^*(x)$ is normalised and  so 

$$
h(x)p^*(x) = Cp^*(x)
$$

Since $h(x)p^*(x)$ is a probability density, it must integrate to 1, and $\int p^*(x)dx = 1$ so $C=1$

Hence, we prove that the invariant measure is unique and this means that the process $X(t)$ is ****ergodic.