# Angle Modulation Systems

### Angle modulation
Generally represented by
$$
u(t)=A_{c}{cos(2\pi}f_{c}t + \phi(t))
$$
The **Instantaneous Frequency is given by**
$$
f_{i}(t)=f_{c}+\frac{1}{2\pi}\frac{d}{dt}\phi(t)
$$

## Types

### Frequency Modulation (FM)

The instantaneous frequency f (t) of the angle-modulated signal is varied proportional to the message signal m (t):

$$ f(t) = f_c + K_f m(t) $$

where $f_c$ is the carrier frequency and $K_f$ is the frequency deviation constant. 

The angle-modulated FM signal can be expressed as:

$$ s(t) = A_c \cos\left(2\pi \int_0^t f(\tau) d\tau \right) $$

### Phase Modulation (PM)  

The instantaneous phase $\phi(t)$ of the angle-modulated signal is varied proportional to the message signal: 

$$ \phi(t) = K_p m(t) $$

where $K_p$ is the phase deviation constant.

The angle-modulated PM signal can be written as: 

$$ s(t) = A_c \cos(2\pi f_c t + K_p m(t)) $$

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