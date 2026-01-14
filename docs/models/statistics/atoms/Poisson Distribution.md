---
sticker: lucide//atom
---
### Poisson Distribution

“The Poisson distribution: the classical example of a Poisson process is radioactive decay. Observing a piece of radioactive material over a time interval T shows that:” (Kardar, p. 42)

“(a) The probability of one and only one event (decay) in the interval t t + dt is proportional to dt as dt → 0. (b) The probabilities of events at different intervals are independent of each other.” (Kardar, p. 42)

$$
\tilde p(k) = (pe^{-ik}+q)^n = \lim_{dt \rightarrow 0}[1+\alpha dt(e^{-ik}-1)]^{T/dt} = \exp[\alpha(e^{-ik}-1)T]
$$
The Poisson PDF is obtained from the inverse Fourier transform as:
$$
p(x) = \int_{-\infty}^\infty \frac{dk}{2\pi}\exp[\alpha(e^{-ik}-1)T + ikx] = e^{-\alpha T}\int_{-\infty}^\infty \frac{dk}{2\pi} e^{ikx}\sum_{M=0}^\infty\frac{(\alpha T)^M}{M!}e^{ikM}
$$
Using the power series for the exponential. The integral over $k$ is 
$$
\int_{-\infty}^\infty \frac{dk}{2\pi}e^{ik(x-M)} = \delta(x-M)
$$
leading to 
$$
p_{\alpha T}(x) = \sum_{M=0}^\infty
e^{\alpha T}\frac{(\alpha T)^M}{M!}\delta(x-M)
$$
“This answer clearly realizes that the only possible values of $x$ are integers $M$. The probability of M events is thus $p_{\alpha T}(M) = e^{-\alpha T}(\alpha T)^M/M!$ . The cumulants of the distribution are obtained from the expansion” ([Kardar, p. 42](zotero://select/library/items/M9RXQI74)) ([pdf](zotero://open-pdf/library/items/WDMIC9R3?page=54&annotation=AH4UUE3X))

$$
\ln \tilde p_{\alpha T} (k) = \alpha T (e^{-ik}-1) = \alpha T \sum_{n=1}^\infty \frac{(-ik)^n}{n!}\Rightarrow \left\langle M^n\right\rangle_c = \alpha T
$$All cumulants have the same value, and the moments are obtained in the form below
$$
\left\langle M\right\rangle  = (\alpha T),  \ \ \ \left\langle M^2 \right\rangle = (\alpha T)^2 + (\alpha T), \dots
$$
