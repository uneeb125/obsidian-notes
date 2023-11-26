# Angle Modulation Systems

## Angle modulation and Types
Generally represented by
$$
u(t)=A_{c}{cos(2\pi}f_{c}t + \phi(t))
$$
The **Instantaneous Frequency is given by**
$$
f_{i}(t)=f_{c}+\frac{1}{2\pi}\frac{d}{dt}\phi(t)
$$
$$
f_{i}(t)-f_{c}=\frac{1}{2\pi}\frac{d}{dt}\phi(t)
$$
### For **PM** we have $m(t)\propto \phi(t)$ 
$$
\phi(t)=k_{p}m(t)
$$
### For **FM** we have $m(t)\propto f_{i}(t)-f_{c}$
$$
f_{i}(t)-f_{c}=k_{f}m(t)=\frac{1}{2\pi}\frac{d}{dt}\phi(t)
$$
### $\phi (t)$ Definition 
$$\phi(t) = \begin{cases}k_{p}m(t),          &\text{PM} \\
\\ 2\pi k_{f}\int^{t}_{-\infty}m(\tau)d\tau, &\text{FM} 
 & \end{cases}$$
### Modulation Index
$$
\begin{align}\beta_{p}&= k_{p}\max[\lvert{m(t)\rvert}], \\
\beta_{f}&= \frac{k_{f}\max[\lvert{m(t)\rvert}}{W}]
\end{align}
$$
## Narrow Band modulation
$$
\begin{align}u_{t}&= A_{c}cos2\pi f_{c}t\space cos\phi(t) -A_{c}sin2\pi f_{c}t\space sin\phi(t), \\
&\approx A_{c}cos2\pi f_{c}t\space -A_{c}\phi(t)sin2\pi f_{c}t\space , \\
\end{align}
$$
- This is just like AM modulated signal except that it modulated with sine.
- Provides no advantage over AM modulation:
	- Same double m(t) bandwidth
	- Same susceptibility to noise.
![[Narroband FM Phasor.png]]

## Spectral Analysis
- u (t) can be represented as:
$$
u(t)= \sum^{\infty}_{-\infty}A_{c}J_{n}(\beta)cos(2\pi(f_{c}+nf_{m})t)
$$
- where $J_{n}(\beta)$ is represented as:
$$
J_{n}(\beta)\approx \frac{\beta^{n}}{2^{n}n!}
$$
Here we have used the approximation of _finite effective bandwidth_ so for small $\beta$ 
### Solution
- Find the modulation index $\beta$ by putting in $m (t)$  into the std expression.
- Use this $\beta$ in spectral $u (t)$ above.
- Then find power which is of the form $\frac{A_{c}J_{n}^{2}(\beta)}{2}$ because of the $cos$ 

## Carson's rule
### Effective Bandwidth
$$
B_{c}=2(\beta+1)W
$$
$$
\beta=\begin{cases}
k_{p}max[\lvert m(t)\rvert] & \text{PM} \\ 
\frac{k_{f}max[\lvert m(t)\rvert]}{W} & \text{FM}
\end{cases}
$$
### Number of Harmonics
$$
M_{c}= 2(\lfloor\beta\rfloor+1)+1=2\lfloor\beta\rfloor+3
$$
## Implementation
### Angle Modulator
The output of angle modulator introduces frequencies not present in the input signal hence they can not be LTI systems, they must be non-linear.
#### Voltage-controlled oscillator
- used a **varactor diode**
- using a **reactance tube**
#### (Indirect) Narrowband Gen $\rightarrow$ Wideband signal
- Generate narrowband by implementing its equation [[#Narrow Band modulation|Narrowband]].
- Frequency multiplier:
	-  Pass through **non-linear element** 
	- Pass through **band-pass**
	Output is $y(t) = A_{c}\cos(2\pi n f_{c}t + n\phi(t))$ 
- Go through mixer that performs up/down conversion then Band-pass
	Output is $y(t) = A_{c}\cos(2\pi(n f_{c}-f_{LO})t + n\phi(t))$ 

### Angle Demodulator
Generate AM signal, whose amplitude is proportional to the instantaneous frequency of FM signal, then use AM demodulators.
#### FM $\rightarrow$ AM $\rightarrow$ m(t)
- FM $\rightarrow$ AM
	- Pass FM through an LTI system having frequency response having straight line in the frequency band of the FM.
$$
\begin{align}
\lvert H(f)\rvert = V_{0}+k(f-f_{c}) \qquad for \lvert f-f_{c}\rvert <\frac{B_{c}}{2}
\end{align}
$$
		Differentiator
		Rising/Falling edge of bandpass.
			Use 2 right next to each other to get larger range

- AM Demodulate
#### FMFB (feedback)



