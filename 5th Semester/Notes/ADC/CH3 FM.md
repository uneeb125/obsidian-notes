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

Using Fourier analysis, it can be shown that the spectrum of an angle-modulated signal contains an infinite number of sidebands spaced at multiples of the message frequency.

For small modulation indices:

- Bandwidth of FM signal ≈ 2 (Δf + f_m) 
    - where Δf is the peak frequency deviation and f_m is the highest frequency in the modulating signal

- Bandwidth of PM signal ≈ 2Δf

## Effect of Modulation Parameters

Increasing the message amplitude increases the bandwidth of both FM and PM signals by increasing the deviation Δf.

Increasing the message frequency f_m:

- Increases FM signal bandwidth proportionally
- Has little effect on PM signal bandwidth

## Implementation

Narrowband FM signals can be generated using a voltage-controlled oscillator (VCO) in a phase-locked loop (PLL). 

FM demodulation can be performed using a PLL with a frequency discriminator.

## Applications

FM and PM are used in radio broadcasting and communications when high noise immunity is required. Narrowband FM is used to sacrifice bandwidth for noise performance.