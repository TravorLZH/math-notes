# Bernoulli Numbers and Its Associated Polynomials

As they are defined, the following generating function characterized **Bernoulli numbers**:

$$
{x\over e^x-1}=\sum_{n=0}^\infty{x^n\over n!}B_n\tag1
$$

To further study the properties of this function, we set $x$ to $-x$, resulting in

$$
{-x\over e^{-x}-1}={xe^x\over e^x-1}=x+{x\over e^x-1}
$$

which implies that the function

$$
{x\over e^x-1}+\frac12x
$$

is even. Hence, according to (1) we have $B_1=-\frac12$ and $B_{2k+1}=0$ for all $k\ge1$. By this intuition, it also follows that

$$
{xe^x\over e^x-1}-{x\over e^x-1}=x\tag2
$$

wherein by Cauchy product, we have

$$
\begin{aligned}
{xe^x\over e^x-1}
&=e^x\cdot{x\over e^x-1} \\
&=\sum_{m=0}^\infty{x^m\over m!}\sum_{k=0}^\infty{x^k\over k!}B_k \\
&=\sum_{n=0}^\infty x^n\sum_{r=0}^n{B_r\over r!(n-r)!} \\
&=\sum_{n=0}^\infty{x^n\over n!}\sum_{r=0}^n\binom nrB_r
\end{aligned}
$$

and by observing (1) and (2), it can be concluded that for all $n\ne1$ the following identity holds

$$
\sum_{r=0}^n\binom nrB_r=B_n\tag3
$$

which leads to the discovery of a recursive relation:

$$
B_n=-{1\over n+1}\sum_{r=0}^{n-1}\binom{n+1}rB_r
$$

## Analytic closed form for Bernoulli numbers

Recursive relations are still not satisfactory, why don't we consider using some complex analysis on (1)?

> Except for $B_1$, Bernoulli numbers of odd order are always zero, so we only care about the evaluation of even Bernoulli numbers.

To begin with, we first use Cauchy's integral formula to obtain

$$
{B_{2n}\over(2n)!}={1\over2\pi i}\int_{(0+)}{z^{-2n}\over e^z-1}\mathrm dz
$$

Because evaluating a residue with high order is difficult and uninteresting, let's look at the integrand's properties. Due to the properties of complex exponential, we observe that except for origin, the function has poles at

$$
z=\pm2r\pi i\quad r=1,2,3,\dots
$$

Accordingly, let's define a contour $\Gamma_N:|z|=(2N+1)\pi$ so that $z=\pm2N\pi i$ are contained within $\Gamma_N$. As a result, we have

$$
{1\over2\pi i}\oint_{\Gamma_N}{z^{-2n}\over e^z-1}\mathrm dz={B_{2n}\over(2n)!}+\sum_{k\ne0,-N\le k\le N}\operatorname{Res}(f,2\pi ik)\tag4
$$

in which

$$
\begin{aligned}
\operatorname{Res}(f,2\pi ik)
&=\lim_{z\to2\pi ik}{z^{-2n}(z-2\pi ik)\over e^z-1} \\
&=(-1)^n(2\pi k)^{-2n}\lim_{z\to2\pi ik}{z-2\pi ik\over e^{z-2\pi ik}-1} \\
&=(-1)^n(2\pi)^{-2n}k^{-2n}
\end{aligned}
$$

Plugging these results into (4), we get

$$
{1\over2\pi i}\oint_{\Gamma_N}{z^{-2n}\over e^z-1}\mathrm dz={B_{2n}\over(2n)!}+(-1)^n2(2\pi)^{-2n}\sum_{k=1}^N{1\over k^{2n}}
$$

As $N\to\infty$, we deduce that the integral on the left vanishes, leaving us

$$
{B_{2n}\over(2n)!}={2(-1)^{n+1}\over(2\pi)^{2n}}\sum_{k=1}^\infty{1\over k^{2n}}
$$

## Bernoulli polynomials and its algebraic properties

In order for us to further investigate the properties of Bernoulli numbers, let's move our attention to a generalization: the **Bernoulli polynomials**.

$$
{xe^{tx}\over e^x-1}=\sum_{n=0}^\infty{x^n\over n!}B_n(t)\tag5
$$

Similar to how we deduce (3), we can perform subtraction to get

$$
{xe^{(t+1)x}\over e^x-1}-{xe^{tx}\over e^x-1}=xe^{tx}=\sum_{m=1}^\infty{x^m(mt^{m-1})\over m!}
$$

which implies

$$
B_n(t+1)-B_n(t)=nt^{n-1}
$$

so that Bernoulli polynomials can be used to sum consecutive powers of integers:

$$
\sum_{k=1}^Nk^n={B_{n+1}(N+1)-B_{n+1}\over n+1}
$$

To find a closed form expression, we apply Cauchy product to (5) so that Bernoulli polynomials can now be associated with Bernoulli numbers.

$$
B_n(t)=\sum_{r=0}^n\binom nrB_rt^{n-r}\tag6
$$

For example, setting $n=1$ in (6) gives

$$
B_1(t)=t-\frac12
$$

Immediately by (3) we also see that for $n\ne1$ this identity holds

$$
B_n(1)=B_n(0)=B_n
$$

Having analyzed the algebraic properties of Bernoulli polynomials, let's move onto some calculus.

## Analytic properties of Bernoulli polynomials

By (6) it follows that

$$
{\mathrm d\over\mathrm dt}B_n(t)=nB_{n-1}(t)
$$

By this relationship, we also obtain a neat integral representation for sum of consecutive powers:

$$
\sum_{k=1}^Nk^n=\int_0^{N+1}B_n(t)\mathrm dt
$$

and by the properties of $B_n(1)=B_n(0)$ for all $n>1$ we can define $P_n(t)=B_n(\{t\})$ as the periodic Bernoulli polynomials, which will be proved to be powerful in the next section.

## Euler-Maclaurin formula

With everything ready, let's begin our main course, where we aim to study the sum

$$
\sum_{k=a}^bf(k)
$$

where $a,b\in\mathbb Z^+$ and $f$ is a function defined on $[a,b]$ such that its $m$'th derivative is continuous. As a result, we are allowed to use Riemann-Stieltjes integration to get

$$
\begin{aligned}
\sum_{k=a}^bf(k)
&=f(a)+\int_a^bf(t)\mathrm d\lfloor t\rfloor \\
&=f(a)+\int_a^bf(t)\mathrm dt-\int_a^bf(t)\mathrm d\left(\{t\}-\frac12\right) \\
&=\int_a^bf(t)\mathrm dt+f(a)+{f(b)-f(a)\over2}+\int_a^b\left(\{t\}-\frac12\right)f'(t)\mathrm dt \\
&=\int_a^bf(t)\mathrm dt+{f(a)+f(b)\over2}+\int_a^bP_1(t)f'(t)\mathrm dt
\end{aligned}
$$

Now, by repeated integration by parts, we can expand the latter integral:

$$
\begin{aligned}
\int_a^bP_1(t)f'(t)\mathrm dt
&=\left.{P_2(t)\over2}f'(t)\right|_a^b-\frac12\int_a^b{P_2(t)}f''(t)\mathrm dt \\
&=\left[{B_2\over2}f'(t)-{P_3(t)\over3!}f''(t)\right]_a^b+{1\over3!}\int_a^bP_3(t)f'''(t)\mathrm dt \\
&=\left.\sum_{r=2}^m{(-1)^rB_r\over r!}f^{(r-1)}(t)\right|_a^b+{(-1)^{m+1}\over m!}\int_a^bP_m(t)f^{(m)}(t)\mathrm dt
\end{aligned}
$$

Because $B_{2k+1}=0$ for all $k\ge1$, the $(-1)^r$ term can be ignored for even powers of negative numbers are always positive. Now, by plugging this result into the above expansion, we obtain the final version of **Euler-Maclaurin formula**:

$$
\sum_{k=a}^bf(k)=\int_a^bf(t)\mathrm dt+{f(a)+f(b)\over2}+\left.\sum_{r=2}^m{B_r\over r!}f^{(r-1)}(t)\right|_a^b+{(-1)^{m+1}\over m!}\int_a^bP_m(t)f^{(m)}(t)\mathrm dt\tag7
$$

## Application: Stirling's formula for Gamma function

Prior to this article, I have applied Euler-Maclaurin formula to factorials, and today I will present to you a more inclusive version of Stirling's formula that can be used for continuous factorial. According to its definition, the Gamma function can be represented by

$$
\Gamma(s+1)=\lim_{N\to\infty}{N^sN!\over(s+1)(s+2)\cdots(s+N)}\triangleq\lim_{N\to\infty}\Gamma_N(s+1)
$$

Now, taking logarithms converts this equation into a sum:

$$
\Gamma_N(s+1)=s\log N+\log N!-\sum_{k=1}^N\log(s+k)\tag8
$$

First, to elmininate the factorial term, let's first apply (7) to $\log N!$ and the latter sum so that

$$
\begin{aligned}
\log N!
&=\left(N+\frac12\right)\log N-N+1+\int_1^N{P_1(t)\over t}\mathrm dt \\
&=\left(N+\frac12\right)\log N-N+\underbrace{1+\int_1^\infty{P_1(t)\over t}\mathrm dt}_C-\int_N^\infty{P_1(t)\over t}\mathrm dt
\end{aligned}
$$

$$
\begin{aligned}
\sum_{k=1}^N\log(s+k)
&=\int_1^N\log(s+t)\mathrm dt+{\log(s+N)+\log(s+1)\over2}+\int_1^N{P_1(t)\over s+t}\mathrm dt \\
&=\left(s+N+\frac12\right)\log(s+N)-(s+N) \\
&-\left(s+1-\frac12\right)\log(s+1)+(s+1)+\int_1^N{P_1(t)\over s+t}\mathrm dt \\
&=s\log(s+N)+\left(N+\frac12\right)\log(s+N) \\
&-N-\log\left(s+\frac12\right)\log(s+1)+1+\int_1^N{P_1(t)\over s+t}\mathrm dt
\end{aligned}
$$

As a result, subtraction gives

$$
\begin{aligned}
\log N!-\sum_{k=1}^N\log(s+k)
&=-s\log(s+N)-\left(N+\frac12\right)\log\left(1+\frac sN\right) \\
&+\left(s+\frac12\right)\log(s+1)+C-1 \\
&-\int_N^\infty{P_1(t)\over t}\mathrm dt-\int_1^N{P_1(t)\over s+t}\mathrm dt
\end{aligned}
$$

Plugging this back to (8), we have

$$
\begin{aligned}
\log\Gamma_N(s+1)
&=-\left(s+N+\frac12\right)\log\left(1+\frac sN\right) \\
&+\left(s+\frac12\right)\log\left(s+1\right)+C-1 \\
&-\int_N^\infty{P_1(t)\over t}\mathrm dt-\int_1^N{P_1(t)\over s+t}\mathrm dt
\end{aligned}
$$

Due to the asymptotic relation that

$$
N\log\left(1+\frac sN\right)\sim N\cdot\frac sN=s
$$

we obtain the following formula when $N\to\infty$:

$$
\begin{aligned}
\log\Gamma(s+1)
&=\left(s+\frac12\right)\log(s+1)-s+C-1-\int_1^\infty{P_1(t)\over s+t}\mathrm dt \\
&=\left(s+\frac12\right)\log(s+1)-s+C-1+\int_0^1{t-\frac12\over s+t}\mathrm dt-\int_0^\infty{P_1(t)\over s+t}\mathrm dt \\
\end{aligned}
$$

wherein due to discrete Stirling's formula $C=\frac12\log2\pi$ the integral evaluates to

$$
\begin{aligned}
\int_0^1{t-\frac12\over s+t}\mathrm dt
&=\int_0^1{t+s-\left(s+\frac12\right)\over s+1}\mathrm dt \\
&=1-\left(s+\frac12\right)\log\left(1+\frac1s\right)
\end{aligned}
$$

Plugging this and $C=\frac12\log2\pi$ that comes from discrete Stirling's formula in gives us the continuous version of Stirling's formula:

$$
\log\Gamma(s+1)=\left(s+\frac12\right)\log s-s+\frac12\log2\pi-\int_0^\infty{P_1(t)\over s+t}\mathrm dt\tag9
$$

and by the properties of Bernoulli polynomials, we have

$$
\begin{aligned}
-\int_0^\infty{P_1(t)\over s+t}\mathrm dt
&=\left.-{P_2(t)\over2(s+t)}\right|_0^\infty \\
&-\frac12\int_0^\infty{P_1(t)\over(s+t)^2}\mathrm dt \\
&=\mathcal O\left(\frac1s\right)
\end{aligned}
$$

Exponentiating (9) gives us the product version of Stirling's approximation:

$$
\Gamma(s+1)=\sqrt{2\pi s}\left(\frac se\right)^s\left[1+\mathcal O\left(\frac1s\right)\right]
$$

## Application: Riemann zeta function

It is well-known that the Riemann zeta function's original definition converges at which $\Re(s)>1$, but Euler-Maclaurin formula offers a way to expand the domain of $\zeta(s)$. Particularly, we first let $\Re(s)>1$ and obtain

$$
\begin{aligned}
\sum_{k=M+1}^\infty{1\over k^s}
&=\int_M^\infty{\mathrm dt\over t^s}-{M^{-s}\over2}-s\int_M^\infty{P_1(t)\over t^{s+1}}\mathrm dt \\
&={M^{1-s}\over s-1}-{M^{-s}\over2}-s\int_M^\infty{P_1(t)\over t^{s+1}}\mathrm dt \\
\end{aligned}
$$

As a result, Riemann zeta function can be calculated by

$$
\zeta(s)=\sum_{k=1}^M{1\over k^s}+{M^{1-s}\over s-1}-{1\over2M^s}-s\int_M^\infty{P_1(t)\over t^{s+1}}\mathrm dt
$$

and this formula is proven useful to evaluate values of $\zeta(s)$ numerically.