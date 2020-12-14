# Dirichlet Series and Its Properties

In number theory, let $a(n)$ be some arithmetic function, $A(x)$ its summatory function such that

$$
A(x)=\sum_{n\le x}f(n)
$$

and we call the following quantity the **Dirichlet series** associated with $a(n)$:

$$
D(s;a)=\int_0^\infty x^{-s}\mathrm dA(x)=\sum_{n=1}^\infty{a(n)\over n^s}
$$

Before moving into the arithmetic properties of this series, we first need to look at its analytic properties:

## Convergence of Dirichlet series

### Uniform convergence over half plane

It can be shown that convergence of $D(s;a)$ at one point implies convergence over a plane to the right of certain line:

For instance, let's say $D(s_0;a)$ converges with $\Re(s_0)=\sigma_0$, then if we were to define the following quantities for convenience:

$$
R(u)=\sum_{n>u}{a(n)\over n^{s_0}}
$$

then due to the convergence of $D(s_0;a)$, we know that for all $\varepsilon>0$ there exists an $M$ such that for all $u>M$ we have $|R(u)|<\varepsilon/4$, and using this fact we can learn more information about the convergence of $D(s;a)$ in general. Let $N>M$ be some arbitrary integer, so

$$
\begin{aligned}
\left|\sum_{n=M+1}^N{a(n)\over n^s}\right|
&=\int_N^M x^{s_0-s}\mathrm dR(x) \\
&=\left|M^{s_0-s}R(M)-N^{s_0-s}R(N)+\int_M^N R(x)\mathrm d(x^{s_0-s})\right| \\
&<\frac12\varepsilon(M^{\sigma_0-\sigma}+N^{\sigma_0-\sigma})
\end{aligned}
$$

As long as $\sigma\ge\sigma_0$, the formula above can be simplified into

$$
\left|\sum_{n=M+1}^N{a(n)\over n^s}\right|<\varepsilon
$$

which, by Cauchy's criterion, implies the uniform convergence of $D(s;a)$ for all $\sigma\ge\sigma_0$.

### Determining the abscissa of convergence $\sigma_c$

If $A(x)=o(x^{\kappa+\varepsilon})$ for all $\varepsilon>0$, then whenever $\sigma>\kappa>0$:

$$
\begin{aligned}
\left|\int_0^\infty x^{-s}\mathrm dA(x)\right|
&=\left|s\int_0^\infty A(x)x^{-s-1}\mathrm dx\right| \\
&\le\sigma\int_0^\infty Kx^{\kappa-\sigma-1}\mathrm dx<\infty
\end{aligned}
$$

This indicates a formula to calculate the abscissa of convergence for $D(s;a)$:

$$
\sigma_c=\lim_{x\to\infty}\sup{\log|A(x)|\over\log x}
$$

For instance, when $a(n)=1$, we have $A(x)=\lfloor x\rfloor$, which gives

$$
\lim_{x\to\infty}\sup{\log|x+\mathcal O(1)|\over\log x}=1
$$

Accordingly, we know that the Riemann zeta function $\zeta(s)$ converges uniformly whenever $\Re(s)>1$