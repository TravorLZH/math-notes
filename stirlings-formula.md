# Stirling's Formula

To further study the property of factorial, we take logarithm of this operation because logarithm can convert a problem involving multiplication into a summatory problem, in which many tools are available for approximation:

$$
\log N!=\sum_{k=1}^N\log k
$$

By rewriting this sum into Riemann-Stieltjes integral, we get

$$
\begin{aligned}
\log N!
&=\log1+\int_1^N\log t\mathrm d\lfloor t\rfloor \\
&=\int_1^N\log t\mathrm dt-\int_1^N\log t\mathrm d\{t\} \\
&=t\log t-t|_1^N-\int_1^N\log t\mathrm d\left(\{t\}-\frac12\right) \\
&=N\log N-N+1-\left.\left(\{t\}-\frac12\right)\log t\right|_1^N \\
&+\int_1^N\left(\{t\}-\frac12\right)\mathrm d\log t \\
&=\left(N+\frac12\right)\log N-N+1+\int_1^N{\{t\}-\frac12\over t}\mathrm dt
\end{aligned}
$$

If we were to define $P_n(x)=B_n(\{x\})$, the Bernoulli polynomials, then $P_1(x)=\{x\}-\frac12$, and this is why the one-half term appears in the calculation:

$$
\begin{aligned}
\int_1^N{\{t\}-\frac12\over t}\mathrm dt
&=\int_1^N{P_1(t)\over t}\mathrm dt \\
&=\left.{P_2(t)\over2t}\right|_1^N+\frac12\int_1^N{P_2(t)\over t^2}\mathrm dt \\
&=\left[{B_2\over2t}+{P_3(t)\over2\cdot3t^2}\right]_1^N+\frac13\int_1^N{P_3(t)\over t^3}\mathrm dt \\
&=\left[{B_2\over2t}+{B_4\over3\cdot4t^3}\right]_1^N+\frac14\int_1^N{P_4(t)\over t^4}\mathrm dt \\
&=\sum_{m=1}^r\left.{B_{2m}\over2m(2m-1)t^{2m-1}}\right|_1^N+{1\over2r}\int_1^N{P_{2r}(t)\over t^{2r}}\mathrm dt
\end{aligned}
$$

If we were to combine these results, we get

$$
\log N!=\left(N+\frac12\right)\log N-N+\log C+\sum_{m=1}^{r-1}{B_{2m}\over2m(2m-1)N^{2m-1}}+\mathcal O\left(1\over N^{2r-1}\right)\tag1
$$

where $C$ is just a constant obtaind from absorbing constant terms from the above integral. Exponentiating both side gives

$$
N!\sim C\left(\frac Ne\right)^N\sqrt N\tag2
$$

As a result, all we need is to figure out the constant

## Wallis product

According to the Weierstrass factorization theorem, we have

$$
{\pi x\over\sin(\pi x)}=\prod_{k=1}^\infty\left(1-{x^2\over k^2}\right)^{-1}
$$

Setting $x=\frac12$, we get

$$
\begin{aligned}
\frac\pi2
&=\prod_{k=1}^\infty{(2k)^2\over(2k+1)(2k-1)} \\
&=\lim_{N\to\infty}{[(2N)!!]^2\over[(2N-1)!!]^2(2N+1)} \\
&=\lim_{N\to\infty}{[(2N)!!]^4\over[(2N)!]^2(2N+1)} \\
&=\lim_{N\to\infty}{2^{4N}(N!)^4\over[(2N)!]^2(2N+1)}
\end{aligned}
$$

Now, plug in (2) so that

$$
\begin{aligned}
\frac\pi2
&\sim{2^{4N}C^4(N/e)^{4N}N^2\over C^2(2N/e)^{4N}(2N)(2N+1)} \\
&\sim{C^22^{4N}(N/e)^{4N}\over2^{4N}(N/e)^{4N}4} \\
&={C^2\over4}
\end{aligned}
$$

As a result, we obtain

$$
C^2=2\pi\Rightarrow C=\sqrt{2\pi}
$$

Plugging this into (2), we obtain **Stirling's approximation** for factorials:

$$
N!\sim\sqrt{2\pi N}\left(\frac Ne\right)^N\tag3
$$

Taking logarithm on (3) and plugging into (1), we deduce this powerful formula for factorials:

$$
\log N!=\left(N+\frac12\right)\log N-N+\frac12\log2\pi+\sum_{m=1}^r{B_{2m}\over2m(2m-1)N^{2m-1}}+\mathcal O\left(1\over N^{2r+1}\right)
$$