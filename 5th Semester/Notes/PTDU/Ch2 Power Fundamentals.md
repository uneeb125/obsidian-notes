# Phasor Representation
$$v(t) = V_{max}\cos(wt+\delta)$$
$$V = \frac{V_{max}}{\sqrt{2}}$$
$$
\begin{align}
v(t) &= \Re{[V_{max}e^{j(wt+\delta)}]}\\
&=\Re{[\sqrt{2}(Ve^{j\delta})e^{jwt}]}
\end{align}
$$
$$\tilde{V} = Ve^{j\delta}= V\angle \delta$$
# Instantaneous Power
$$p(t) = v(t)i(t)$$
## Purely Resistive 
$$p_{R}(t)=VI_{R}\{1+\cos[2(wt+\delta)]\}$$
## Purely Inductive
$$p_{L}(t)=VI_{L}\sin[2(wt+\delta)]$$
## Purely Capacitive
$$p_{C}(t)=-VI_{C}\sin[2(wt+\delta)]$$
## General RLC
$$p(t)=VI_{R}\{1+\cos[2(wt+\delta)]\} + VI_{x}sin[2(wt+\delta)]$$
$$p(t) = p_{R}(t) +p_{X}(t)$$
# Complex power
$$S = VI^{*}= [V\angle \delta][I\angle \delta]^{*} = VI\angle \delta - \beta$$

# Balanced 3-Phase
## Y-Connections
- **Balanced** if load impedance on each line is equal.
- 