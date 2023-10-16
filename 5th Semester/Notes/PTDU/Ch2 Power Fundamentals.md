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

### Line to Line Voltages
$$E_{ab}= E_{an}- E_{bn}$$
- The **clockwise** arrangement of the line to line voltages indicates a **positive sequence**.
- Since a **line to line** voltage vectors form a closed triangle their **sum is always zero**, *even in unbalanced*. $$E_{ab} + E_{bc} + E_{ca} = 0$$
- But for Line to Neutral voltages this is only true for **Balanced**. $$E_{an} + E_{bn} + E_{cn} = 0$$
![[Wye_Phasor_and Voltage_Triangle.png]]

### Line Currents
$$I_{a}= \frac{E_{an}}{Z_{Y}}$$
$$I_{n}= I_{a}+ I_{b}+ I_{c}$$
- If **balanced this neutral current is zero**, because of closed phasor triangle.

## $\Delta$-Delta Connections

### Load Currents
#### $\Delta$-Load Currents
$$I_{AB}=\frac{E_{ab}}{Z_{\Delta}}$$
![[Y-delta Load.png]]
#### Line Currents
$$I_{a}= I_{AB}-I_{CA}$$
$$I_{a}= \sqrt{3}I_{AB}\angle-30\degree$$
#### Properties
- The **sum of the $\Delta$-Load** currents is **zero if balanced**.
- The **sum of the Line** currents is **always zero**.