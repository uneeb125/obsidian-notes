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
S_{X}(f) = \
$$
### Cyclostationary
## Power Spectra of LTI
## Power Spectral Density of a Sum process
## Gaussian Processes
## White Processes
## Filtered Noise Processes
## Noise Equivalent Bandwidth
