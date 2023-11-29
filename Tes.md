Here is the explanation in Markdown format:

# Question 6.5

1) The signal power $P_R$ at the output of the noise-limiting filter is calculated by integrating the squared signal over one period T and taking the limit as T goes to infinity. This gives:

$P_R = 10^{-6} (1 + \alpha^2/2) = 56.25 \times 10^{-6}$

The noise power at the output $P_{n,o}$ is half the input white noise power over the filter bandwidth (2500 Hz), which gives:  

$P_{n,o} = 0.5 P_n = 0.5 N_0^2 \times 2 \times 2500 = 25 \times 10^{-10}$

2) When the signal is multiplied by $2\cos(2\pi f_c t)$, there are double frequency terms created that are filtered out by the lowpass filter (LPF). So the output of the LPF is:

$v(t) = 10^{-3}[1 + \alpha\cos(2\pi f_m t)] + n_c(t)$

Blocking the DC component, the signal power $P_o$ is:  

$P_o = (10^{-6}/2) \times 0.5^2 = 0.125 \times 10^{-6}$

The output noise power is the same as before over the LPF bandwidth (1000 Hz), giving:

$P_{n,o} = 40 \times 10^{-10}$

Therefore, the output SNR is:  
SNR = $0.125 \times 10^{-6} / 40 \times 10^{-10} = 31.25 = 14.95$ dB