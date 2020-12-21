# Merten's Formula

In this article, we are going to derive Merten's asymptotic formula that

$$
\prod_{p\le x}\left(1-\frac1p\right)\sim{e^{-\gamma}\over\log x}\tag1
$$

## An elementary estimate for reciprocal sum

Due to Merten's first theorem that

$$
g(x)=\sum_{p\le x}{\log p\over p}=\log x+h(x)
$$

wherein $h(x)=\mathcal O(1)$, we have

$$
\begin{aligned}
\sum_{p\le x}\frac1p
&=\sum_{p\le x}{1\over\log p}\cdot{\log p\over p}=\int_{2-\varepsilon}^x{\mathrm dg(t)\over\log t} \\
&={g(x)\over\log x}+\int_2^x{g(t)\over t\log^2t}\mathrm dt \\
&=1+\int_2^x{\mathrm dt\over t\log t}+\int_2^x{h(t)\over t\log^2t}\mathrm dt+\mathcal O\left(1\over\log x\right) \\
&=\log\log x\underbrace{-\log\log2+1+\int_2^\infty{h(t)\over t\log^2t}}_{B_1}+\mathcal O\left(1\over\log x\right) \\
\end{aligned}
$$

Thus we obtain an asymptotic formula for the reciprocal sum of prime numbers:

$$
f(x)=\sum_{p\le x}\frac1p=\log\log x+B_1+\mathcal O\left(1\over\log x\right)\tag1
$$

where $B_1$ is called **Merten's constant**.

## Euler product and convergence

From the above justification, it is not difficult for us to deduce that the reciprocal sum of prime numbers diverge. However, there is still little information known about $B_1$ since specific behaviors of $h(x)$ are not known. Therefore, we have to approach this problem by some other means. For example, why not consider Euler product

$$
P(x,s)=\prod_{p\le x}{1\over1-p^{-s}}
$$

Taking logarithms on both side gives

$$
\begin{aligned}
\log P(x,s)
&=\sum_{p\le x}\left[-\log\left(1-{1\over p^s}\right)\right] \\
&=\sum_{p\le x}{1\over p^s}+\sum_{p\le x}\left[\log\left({1\over1-p^{-s}}\right)-{1\over p^s}\right]
\end{aligned}
$$

Since

$$
\log\left(1\over1-p^{-1}\right)=\log\left(1+{p^{-1}\over1-p^{-1}}\right)\le{1\over p-1}
$$

we have

$$
\begin{aligned}
\sum_{p>x}\left[\log\left({1\over1-p^{-1}}\right)-\frac1p\right]
&\le\sum_{p>x}\left[{1\over p-1}-\frac1p\right] \\
&\ll\sum_{n\ge x}^\infty\left[{1\over n-1}-\frac1n\right]=\mathcal O\left(\frac1x\right)
\end{aligned}
$$

Thus, this series actually converges to a constant less than one. Moreover, if we were to denote the infinite sum as $C$ then

$$
\sum_{p\le x}\left[\log\left({1\over1-p^{-1}}\right)-\frac1p\right]=C+\mathcal O\left(\frac1x\right)\tag2
$$

## Riemann zeta function

If we were to expand Euler product in to Dirichlet series, we have

$$
\prod_{p\le x}{1\over1-p^{-s}}=\sum_{n=1}^\infty{\varepsilon_n\over n^s}
$$

where $\varepsilon_n=1$ if all prime factors of $n$ are $\le x$ and zero otherwise. In addition, for $x\ge2$, $\prod_{p\le x}p\ge x$, so we get

$$
\sum_{n\le x}{1\over n^s}\le\prod_{p\le x}{1\over1-p^{-s}}\le\zeta(s)
$$

By letting $x\to\infty$, we can see that whenever $\Re(s)>1$ the product converges and equals to $\zeta(s)$, which is consistent with our observation while studying $f(x)$. In addition, due to the alternative representation that

$$
\zeta(s)={s\over s-1}-s\int_1^\infty{\{x\}\over x^{s+1}}\mathrm dx
$$

we can obtain an asymptotic formula near $s=1$:

$$
\zeta(s)={1\over s-1}+\gamma+o(1)
$$

## $\zeta(s)$ near $s=1$

Similar to how we study $P(x,s)$, we take logarithm on $\zeta(1+\delta)$ to get

$$
\log\zeta(1+\delta)=\sum_p{1\over p^{1+\delta}}+\sum_p\left[\log\left({1\over1-p^{-1-\delta}}\right)-{1\over p^{1+\delta}}\right]\tag3
$$

where the left hand side equals to

$$
\begin{aligned}
\log\zeta(1+\delta)
&=\log\left[\frac1\delta+\gamma+o(1)\right] \\
&=\log{1\over1-e^{-\delta}}+\log{1-e^{-\delta}\over\delta}+\log(1+\gamma\delta+o(1)) \\
&=\sum_{n=1}^\infty{e^{-\delta n}\over n}+\log{1-e^{-\delta}\over\delta}+o(1) \\
&=\int_{1-\varepsilon}^\infty e^{-\delta t}\mathrm dH(t)+o(1)
\end{aligned}
$$

in which $H(x)$ denotes

$$
H(x)=\sum_{n\le x}\frac1n=\log x+\gamma+\mathcal O\left(\frac1x\right)\tag4
$$

Thus, using integration by parts, we get

$$
\begin{aligned}
\log\zeta(1+\delta)
&=e^{-\delta t}H(t)|_0^\infty-\int_0^\infty H(t)\mathrm d(e^{-\delta t})+o(1) \\
&=\delta\int_0^\infty H(t)e^{-\delta t}\mathrm dt+o(1)
\end{aligned}
$$

For the right hand side, we have

$$
\begin{aligned}
\sum_p{1\over p^{1+\delta}}
&=\int_0^\infty u^{-\delta}\mathrm df(u) \\
&=\lim_{u\to\infty}f(u)u^{-\delta}+\delta\underbrace{\int_1^\infty f(u)u^{-\delta}\cdot u^{-1}\mathrm du}_{u=e^t} \\
&=\delta\int_0^\infty f(e^t)e^{-\delta t}\mathrm dt
\end{aligned}
$$

Plugging these results back into (3) gives

$$
\delta\int_0^\infty[H(t)-f(e^t)]e^{-\delta t}\mathrm dt=\sum_p\left[\log\left({1\over1-p^{-1-\delta}}\right)-{1\over p^{1+\delta}}\right]+o(1)\tag5
$$

Now, using (1) and (3), the left hand side becomes

$$
\begin{aligned}
LHS
&=\delta\int_0^\infty\left[\log t+\gamma-\log\log(e^t)-B_1+\mathcal O\left(1\over\log e^t\right)\right]\mathrm dt \\
&=(\gamma-B_1)\delta\int_0^\infty e^{-\delta t}\mathrm dt+\mathcal O\left(\delta\int_0^\infty{e^{-\delta t}\over t+1}\mathrm dt\right)
\end{aligned}
$$

For the latter part, we have

$$
\begin{aligned}
\delta\int_0^\infty{e^{-\delta t}\over t+1}\mathrm dt
&=\left.{-e^{-\delta t}\over t+1}\right|_0^\infty+\int_0^\infty e^{-\delta t}\mathrm d\left(1\over t+1\right) \\
&=1+\int_0^\infty e^{-\delta t}\mathrm d\left(1\over t+1\right)
\end{aligned}
$$

Obviously, this goes to zero as $\delta\to0$. Plugging this back to the (5), we obtain

$$
\gamma-B_1=\sum_p\left[\log\left({1\over1-p^{-1-\delta}}\right)-{1\over p^{1+\delta}}\right]+o(1)
$$

Finally, taking the limit $\delta\to0^+$ gives us a better formula for $B_1$:

$$
B_1=\gamma+\sum_p\left[\log\left(1-\frac1p\right)+\frac1p\right]\tag6
$$

## Proof of Merten's formula

With every prerequisite being ready, plugging (2) and (6) back into (1) gives

$$
\sum_{p\le x}\frac1p=\log\log x+\gamma+\sum_{p\le x}\left[\log\left(1-\frac1p\right)+\frac1p\right]+\mathcal O\left(1\over\log x\right)
$$

Manipulating this algebraically, we get

$$
\sum_{p\le x}\log\left(1-\frac1p\right)=-\gamma-\log\log x+\mathcal O\left(1\over\log x\right)\tag7
$$

By exponentiating and employing $e^a=1+\mathcal O(a)$, we deduce Merten's formula:

$$
\prod_{p\le x}\left(1-\frac1p\right)={e^{-\gamma}\over\log x}\left[1+\mathcal O\left(1\over\log x\right)\right]\tag{$x\ge2$}
$$