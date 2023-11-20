- **Realization of a function or Sample function**: The deterministic time function $x(t;\omega_{i})$ given when you pick an $\omega_{i}$. 
- At any time instance the value of a random process is a random variable predicated on $\omega_{i}$ 
- The Random process can be described as a vector of random variables. 
	- if we pick a **t** we just get a random variable 
	- if we pick a value for random variable 
$$
\begin{bmatrix}
X(t_1) \\ X(t_2) \\ X(t_3) \\ . \\ X(t_{n})
\end{bmatrix}
$$

## Statistical Averages
### Mean
$$
E[X(t_{0})]=m_{X}(t_{0})=\int^{\infty}_{-\infty}xf_{xt_0}(x)dx
$$
### Auto-correlation
$$
R_{X}(t_{1},t_{2}) = E[X(t_1)X(t_2)]
$$
$$
R_{X}(t_{1},t_{2}) = \int^{\infty}_{-\infty}x_{1}x_{2}f_{X(t_1)}f_{X(t_2)}(x_1,x_2)dx_{1}dx_{2}
$$
## Wide-Sense Stationary
- WWS has teh following properties
	1. $m_{X}(t)=E[X(t)]$ is independent of t
	2. $R_{X}(t_{1}, t_{2})$ depends only on the difference $t_1 - t_2$ not $t_1$ and $t_2$ individually.
- If process is stationary then $R_X (\tau) = R_X (-\tau)$ 
### Cyclostationary
$$
m_{X}(t+T_{0})=m_{X}(t)
$$
$$
R_{X}(t+\tau+T_{0}, t+T_{0}) = R_{X}(t+\tau,t)
$$
- **Average autocorrelation function** $\bar{R}_{X}(\tau)$ as average of over one period
$$
\bar{R}_{X}(\tau) = \frac{1}{T_{0}}\int^{T_{0}}_{0}R_{X}(t+\tau,t)dt
$$
## Multiple Random Processes
This means if one input can result in many Random variables
- If random process input into an LTI then output y also random process of random variable Y(t). So now we have 2 Random processes.
### Independence
- $X (t)$ and $Y(t)$ are independent if for all m and n for t1, t2, .... ,tn and similarly tau. the random vectors are independent. Similarly the random processes are uncorrelated if the two random vectors are uncorrelated.
### Cross-correlation
$$
R_{XY}(t_1,t_2)=E[X(t_1)Y(t_2)]
$$
$$
R_{XY}(t_1,t_2)=R_{YX}(t_2,t_1)
$$
### Joint-Stationary
- They must be:
	- Individually stationary 
	- Cross-correlation depends only on $\tau$ .
## Random Processes and Linear Systems
- The input and output process of an LTI system are jointly stationary.
==You have not shown this==
## Power Spectral Density of Stationary Processes
- Power as a function of frequency
### Stationary
$$
S_{X}(f) = \mathcal{F}[R_{X}(\tau)]
$$
### Cyclostationary
$$
S_{X}(f) = \mathcal{F}[\bar{R}_{X}(\tau)]
$$
## Power Spectra of LTI
- Input stationary output stationary
$$
m_{Y}= m_{X} \int^{\infty}_{-\infty}h(t)dt
$$
$$
R_{Y}(\tau) = R_{X(\tau)}\star h(\tau)\star h(-\tau)
$$
- Jointly stationary with cross-correlation
$$
R_{XY}(\tau)= R_{X}(\tau)\star h(-\tau)
$$
- In **Frequency Domain** 
- Since Mean of random process is its DC value, so mean of reponse only depends on $H (f)$ at $f=0$ 
$$
m_{Y}= m_{X} H(0)dt
$$
- For power spectrum the phase of $H (f)$ is irrelevant
$$
S_{Y}(f) = S_{X}(f)\lvert H(f) \rvert ^2
$$
## Power Spectral Density of a Sum process
Additive noise added to the transmitter signal
$$
R_{Z}(\tau) = R_{X}(\tau) + R_{Y}(\tau) + R_{XY}(\tau) + R_{YX}(\tau)
$$
$$
S_{Z}(\tau) = S_{X}(\tau) + S_{Y}(\tau) + S_{XY}(\tau) + S_{YX}(\tau)
$$
$$
S_{YX}(\tau) = S^*_{YX}(\tau)
$$
- if $X(t) , Y(t)$ are uncorrelated 
$$
R_{XY}(\tau) = m_{X}m_{Y}
$$
- if one has mean 0
$$
S_{Z}(f) = S_{X}(f) +S_{Y}(f)
$$
## Gaussian Processes
- A random process X (t) is a Gaussian process if for all n all (t1, t2 , . . . , tn), the random variables have a jointly Gaussian density function.
### Jointly Gaussian
- $X (t)$ and $Y(t)$ are jointly Gaussion if for all m and n for t1, t2, .... ,tn and similarly tau. the random vectors is distributed according to an n+m dimensions jointly Gaussian distributions. 

### Properties
1. If Gaussian process X (t) is passed through an LTI system then out put is a Gaussian process. Also they are jointly Gaussian processes.
2. For jointly Gaussian processes, uncorrelatedness and independence are equivalent.
## White Processes
### Definition
All frequencies appear with equal power i.e. power spectral density is a constant.
- a wide range of processes used to describe a variety of information sources can be modeled as the output of LTI systems driven by a white process.
### Actual modelling (Thermal noise)
$$
S_{n}(t)=\frac{hf}{2(e^{\frac{hf}{kT}}-1)}
$$
- h is the Plank's constant
- k is Boltzmann's constant
- T is temperature in Kelvins
It gets its max value at $f=0$ having value $\frac{kT}{2}$ 
- say $kT=N_0$ so in general $S_n(f)$ 
$$
S_{n}(f) =\left[\frac{N_{0}}{2}\right]
$$
$$
R_{n}(\tau) = \mathcal{F}^{-1} \left[\frac{N_{0}}{2}\right]=\left[\frac{N_{0}}{2}\right]\delta(\tau)
$$
- For white process $R_n(\tau)=0$ for all $\tau\neq 0$ 

### Properties of Thermal noise
1. Stationary process
2. Zero-mean process
3. Gaussian process
4. Thermal noise is specific while process where $S_{n}(f)=\frac{kT}{2}$ 

- Thermal noise increases with temperature
## Filtered Noise Processes
Noise from one stage can get filtered by another stage.
## Noise Equivalent Bandwidth
- Gaussian White noise after filter in still Gaussian but not white
	The filter characteristics change the spectral properties.
$$
S_{y}(f) = S_{X}(f) \lvert H(f) \rvert^{2}= \frac{N_{0}}{2} \lvert H(f) \rvert^{2}
$$
$$
P_{y} = \int^{\infty}_{-\infty}S_{Y}df = \frac{N_{0}}{2}\int^{\infty}_{-\infty} \lvert H(f) \rvert^{2}df
$$
$$
B_{neq}= \frac{\int^{\infty}_{-\infty}\lvert H(f)\rvert ^2df}{2H_{max}^{2}}
$$
$$
\begin{align}
P_{y} &= \frac{N_{0}}{2}\int^{\infty}_{-\infty} \lvert H(f) \rvert^{2}df \\
&= \frac{N_{0}}{2} \times 2B_{neq}H_{max}^{2}\\
&= N_{0}B_{neq}H_{max}^{2}
\end{align}
$$