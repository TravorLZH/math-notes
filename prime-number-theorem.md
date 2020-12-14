# The Asymptotic Distribution of Prime Numbers

## Elementary Domain

In number theory, the following three prime-counting functions are frequently studied by people:

$$
\pi(x)=\sum_{p\le x}1
$$
$$
\vartheta(x)=\sum_{p\le x}\log p
$$
$$
\psi(x)=\sum_{n\le x}\Lambda(n)
$$

Though they look very different from each other, it is not difficult for us to associate them:

$$
\begin{aligned}
\pi(x)
&=\int_{2-\varepsilon}^x{\mathrm d\vartheta(t)\over\log t} \\
&=\left.{\vartheta(t)\over\log t}\right|_{2-\vartheta}^x+\int_{2-\varepsilon}^x{\vartheta(t)\over t\log^2t}\mathrm dt \\
&={\vartheta(x)\over\log x}+\int_2^x{\vartheta(t)\over t\log^2t}\mathrm dt
\end{aligned}
$$

$$
\begin{aligned}
\psi(x)
&=\sum_{p^k\le x}\log p \\
&=\sum_{k\le\log_2x}\sum_{p\le x^{1/k}}\log p \\
&=\vartheta(x)+\sum_{2\le k\le\log_2x}\vartheta(x^{1/k}) \\
&=\vartheta(x)+\mathcal O\left(\vartheta(x^{1/2})\log x\right) \\
&=\vartheta(x)+\mathcal O(\sqrt x\log^2x)
\end{aligned}
$$

In fact, due to the property of big O notation, we also have

$$
\vartheta(x)=\psi(x)+\mathcal O(\sqrt x\log^2x)
$$

### Analytic Domain

Up to now, we have associated $\pi(x)$ with $\psi(x)$, a function that is much easier to work with. By Perron's formula, we have that when $x$ is noninteger and $c>1$

$$
\psi(x)={1\over2\pi i}\int_{c-i\infty}^{c+i\infty}\sum_{n=1}^\infty{\Lambda(n)\over n^s}{x^s\over s}\mathrm ds
$$

Provided that the elementary relationship

$$
\Lambda(n)=\sum_{d|n}\mu(d)\log\frac nd
$$

we see that

$$
\begin{aligned}
\sum_{n=1}^\infty{\Lambda(n)\over n^s}
&=\sum_{m=1}^\infty{\mu(m)\over m^s}\cdot\sum_{k=1}^\infty{\log k\over k^s} \\
&={1\over\zeta(s)}\cdot-\zeta'(s) \\
&=-{\zeta'\over\zeta}(s)
\end{aligned}
$$

As a result, we get a connection between zeta functions and the prime-counting function:

$$
\psi(x)={1\over2\pi i}\int_{c-i\infty}^{c+i\infty}\left[-{\zeta'\over\zeta}(s)\right]{x^s\over s}\mathrm ds
$$

In order to go deeper, we first integrate this function, and I will explain the reasoning behind this operation. First, define

$$
f(x)\triangleq\int_0^x\psi(t)\mathrm dt
$$

so that

$$
f(x)={1\over2\pi i}\int_{c-i\infty}^{c+i\infty}\left[-{\zeta'\over\zeta}(s)\right]{x^{s+1}\over s(s+1)}\mathrm ds
$$

By the property of the integral formula, we obtain

$$
{1\over2\pi i}\int_{c-i\infty}^{c+i\infty}{x^{s+1}\over s(s+1)}\mathrm ds=x-1
$$
$$
{1\over2\pi i}\int_{c-i\infty}^{c+i\infty}{x^{s+1}\over s(s+1)(s-z)}\mathrm ds={x^{z+1}\over z(z+1)}+{1\over z+1}-\frac xz
$$

Now, due to

$$
-{\zeta'\over\zeta}(s)={s\over s-1}+\sum_{k=1}^\infty\left[{1\over2k}-{1\over s+2k}\right]-\sum_\rho\left[{1\over s-\rho}+\frac1\rho\right]-{\zeta'\over\zeta}(0)
$$

we obtain

$$
-{\zeta'\over\zeta}(s)={s\over s-1}-\frac12+\sum_{k=1}^\infty\left[{1\over2k-1}-{1\over s+2k}\right]-\sum_\rho\left[{1\over s-\rho}+{1\over1+\rho}\right]-{\zeta'\over\zeta}(-1)
$$

Thus

$$
\begin{aligned}
f(x)
&={1\over2\pi i}\int_{c-i\infty}^{c+i\infty}{x^{s+1}\over(s+1)(s-1)}\mathrm ds-{x-1\over2}+
\end{aligned}
$$