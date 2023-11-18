Here is the table with LaTeX math expressions in a code block:


| Time Domain (x(t)) | Frequency Domain (X(f)) |
|-|-|
| $\delta(t)$ | 1 |  
| 1 | $\delta(f)$ |
| $\delta(t - t_0)$ | $e^{-j2\pi ft_0}$ |
| $e^{j2\pi f_0t}$ | $\delta(f - f_0)$ |  
| $\cos(2\pi f_0t)$ | $\frac{1}{2}\delta(f - f_0) + \frac{1}{2}\delta(f + f_0)$ |
| $\sin(2\pi f_0t)$ | $-\frac{1}{2}j\delta(f + f_0) + \frac{1}{2}j\delta(f - f_0)$ |
| $u(t) = \begin{cases}1, & \lvert t \rvert < \frac{1}{2} \\ \frac{1}{2}, & t = \pm \frac{1}{2} \\ 0, & \text{otherwise} \end{cases}$ | $\mathrm{sinc}(f)$ |
| $\mathrm{sinc}(t)$ | $u(f)$ |
| $v(t) = \begin{cases}t + 1, & -1 \leq t < 0 \\ -t + 1, & 0 \leq t < 1 \\ 0, & \text{otherwise} \end{cases}$ | $\mathrm{sinc}^2(f)$ |  
| $\mathrm{sinc}^2(t)$ | $v(f)$ |
| $e^{-\alpha t}u^{-1}(t), \alpha > 0$ | $\frac{1}{\alpha + j2\pi f}$ |
| $te^{-\alpha t}u^{-1}(t), \alpha > 0$ | $\frac{1}{(\alpha + j2\pi f)^2}$ |
| $e^{-\alpha\lvert t \rvert}, \alpha > 0$ | $\frac{2\alpha}{\alpha^2 + (2\pi f)^2}$ |
| $e^{-\pi t^2}$ | $e^{-\pi f^2}$ |
| $\mathrm{sgn}(t) = \begin{cases}1, & t > 0 \\ -1, & t < 0 \\ 0, & t = 0\end{cases}$ | $\frac{1}{j\pi f}$ |  
| $u^{-1}(t)$ | $\frac{1}{2}\delta(f) + \frac{1}{j2\pi f}$ |
| $\delta'(t)$ | $j2\pi f$ |
| $\delta^{(n)}(t)$ | $(j2\pi f)^n$ |
| $\frac{1}{t}$ | $-j\pi \mathrm{sgn}(f)$ |
| $\sum\limits_{n=-\infty}^{\infty} \delta(t - nT_0)$ | $\frac{1}{T_0}\sum\limits_{n=-\infty}^{\infty} \delta(f - \frac{n}{T_0})$ |
