## Noise in Baseband
$$
/\begin{align}
P_{n_{0}} &= \int^{+W}_{-W} \frac{N_{0}}{2}df \\
&= N_{0}W
\end{align}
$$
## Noise in DSB-SC AM
$$
\begin{align}
r(t) &= u(t) + n(t) \\
&= 
\end{align}
$$
### SNR
$$
\left(\frac{S}{N}\right)_{0}= \frac{{A_{c}^{2}P_{M}}}{2WN_{0}}
$$
- Received power from DSB-SC $P_{R}= \frac{A_{c}^{2}P_{M}}{2}$ 
- This makes it the same as baseband SNR so no advantage.

## Noise of SSB AM
- Exactly the same as before

## Noise of Conventional AM
### SNR 
$$
\begin{align}
\left(\frac{S}{N}\right)_{0_{AM}} &= \frac{{a^{2}P_{M_{n}}}}{{1+a^{2}P_{M_{n}}}}  \left(\frac{S}{N}\right)_{0_{AM}} \\
&= \eta \left(\frac{S}{N}\right)_{0_{AM}}
\end{align}
$$
- $\eta$ is always less then 1, typically $a$ is picked to be 0.8 - 0.9 while $P_M$ around 0.1 this gives factor of -. 075.
- The SNR is much lower than baseband as a lot of power is used to send the carrier component of modulated signal