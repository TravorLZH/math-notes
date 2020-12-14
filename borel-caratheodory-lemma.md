# Borel-Caratheodory Lemma

In this article, we aim to study the properties of analytic function $f(z)$ satisfying $f(0)=0$ and $\Re f(z)\le M$ on $|z|=R$.

Since $f(z)$ is analytic and $f(0)=0$ we have that

$$
f(z)=\sum_{n=1}^\infty a_nz^n
$$

wherein by Cauchy's integral formula we have

$$
\begin{aligned}
a_n
&={1\over2\pi i}\oint_{|z|=R}{f(z)\over z^{n+1}}\mathrm dz \\
&=\int_0^1f(Re^{2\pi it})R^{-n}e^{-2\pi int}\mathrm dt
\end{aligned}
$$

Because $f(0)=0$ and by Cauchy's integral theorem it directly follows

$$
\int_0^1f(Re^{2\pi it})e^{2\pi int}\mathrm dt=0
$$

whenever $n\in\mathbb N$. Now, let $\theta_n=\arg a_n$ then

$$
{1\over R^n}\int_0^1f(Re^{2\pi it})[1+(e^{2\pi int+i\theta_n}+e^{-(2\pi int+i\theta_n)})/2]=\frac12|a_n|
$$

Reorganizing the terms gives

$$
|a_n|={2\over R^n}\Re\int_0^1f(Re^{2\pi it})[1+\cos(2\pi nt+\theta_n)]\mathrm dt\le{2M\over R^n}
$$

As a result, whenever $|z|\le r<R$, we have

$$
|f(z)|\le\sum_{n=1}^\infty|a_n|r^n\le2M\sum_{n=1}^\infty{r^n\over R^n}={2Mr\over R-r}\tag1
$$

If we were to take the derivative, then

$$
|f'(z)|\le{2M\over R}\sum_{n=1}^\infty n\left(\frac rR\right)^{n-1}={2MR\over(R-r)^2}\tag2
$$

Since the lemma itself appears to be weird, we'd better have a look at its application.

## Application: logarithmic derivative of analytic functions

Let $f(z)$ be some functions analytic in an open set containing the closed ball $|z|\le R$, $M$ be its maximum modulus within $|z|\le R$, and $z_1,z_2,\dots,z_m$ be its zeros within $|z|\le r<R<1$. Then we can define $g(z)$ analytic and zeroless within $|z|\le r$ by

$$
f(z)=g(z)\prod_{k=1}^mB_{z_k}(z)\tag3
$$

where $m$, by Jensen's inequality, has a loose bound:

$$
m\le{\log M/|f(0)|\over\log1/R}\ll\log{M\over|f(0)|}
$$

Now, taking logarithms on both side of (3), we get

$$
\log|f(z)|=\log|g(z)|+\sum_{k=1}^m\log|B_{z_k}(z)|
$$

By the maximum modulus principle, the maximum of both side is achieved on $|z|=R$, meaning

$$
\log|g(z)|+\sum_{k=1}^m\log|B_{z_k}(z)|\le\log|f(z)|\le\log M
$$

Now, define

$$
h(z)=\log{g(z)\over g(0)}=\int_0^z{g'\over g}(s)\mathrm ds
$$

so we have

$$
\Re h(z)\le\log{M\over|g(0)|}
$$

Moreover, by the definition we have

$$
|f(0)|=|g(0)|\prod_{k=1}^m\left|{z_k\over R}\right|\le|g(0)|
$$

Thus this bound becomes in in terms of $f(z)$:

$$
\Re h(z)\le\log{M\over|f(0)|}
$$

Applying Borel-Caratheodory lemma to this inequality gives

$$
|h'(z)|=\left|{g'\over g}(z)\right|\le{2R\log M/|f(0)|\over(R-r)^2}=\mathcal O\left(\log{M\over |f(0)|}\right)
$$

However, by (3) we have

$$
{g'\over g}(z)={f'\over f}(z)-\sum_{k=1}^m{1\over z-z_k}+\sum_{k=1}^m{1\over z-R^2/\overline z_k}
$$

in which the last sum can be approximated by

$$
\sum_{k=1}^m{1\over z-R^2/\overline z_k}\le{m\over R-r}=\mathcal O\left(\log{M\over|f(0)|}\right)
$$

Therefore, by the bounds for $(g'/g)(z)$ we deduce

$$
{f'\over f}(z)=\sum_{k=1}^m{1\over z-z_k}+\mathcal O\left(\log{M\over|f(0)|}\right)
$$