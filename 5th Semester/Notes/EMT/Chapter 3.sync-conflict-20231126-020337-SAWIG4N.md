# Electric Flux Density
-  Electric flux produced by a charge is equal to the charge enclosed.
$$\Psi = Q$$
## For a Point Charge 
### Electric flux Density
$$\textbf{D} = \frac{Q}{4\pi r^{2}} \textbf{a}_r$$
### Electric charge intensity
$$\textbf{E}= \frac{Q}{4\pi \epsilon_{0}r^{2}}\textbf{a}_r$$
### Flux density and Electric intensity
$$\textbf{D} = \epsilon_0 \textbf{E}$$
## For Volume Charge
### Electric flux Density
$$\textbf{D} =\int_{vol} \frac{\rho_{v}dv}{4\pi R^{2}} \textbf{a}_R$$
### Electric charge intensity
$$\textbf{E} =\int_{vol} \frac{\rho_{v}dv}{4\pi \epsilon_{0}R^{2}} \textbf{a}_R$$

# Gauss's Law
$$\oint_{S}\textbf{D}_{s}\cdot d\textbf{S} = \int_{vol}\rho_{v}dv$$
## Application on symmetrical charge distribution

### Spherical Cover (Point Charge)
$$
\begin{align}
Q &= \oint_{S} \textbf{D}_{s}\cdot d\textbf{S}\\
&= 4 \pi r^{2}D_{s}
\end{align}
$$
#### Electric Flux Density
$$\textbf{D} = \frac{Q}{4\pi r^{2}} \textbf{a}_r$$
#### Electric Charge intensity
$$\textbf{E}= \frac{Q}{4\pi \epsilon_{0}r^{2}}\textbf{a}_r$$
### Cylindrical Cover (Line and Coaxial Charge)
- Ideal for line charge density.
#### Electric Flux density
$$\mathbf{D_\rho} = \frac{\rho_{L}}{2\pi  \rho}a_{\rho}$$
#### Electric Charge intensity
$$\mathbf{E_{\rho}} = \frac{\rho_{L}}{2\pi \epsilon_{0} \rho}a_{\rho}$$
## Application on Volume Element
$$\oint_{S}\mathbf{D}\cdot d \mathbf{S}= \int_{front} +  \int_{back} + \int_{left} + \int_{right} + \int_{top} + \int_{bottom} $$
$$\oint_{S}\mathbf{D}\cdot d \mathbf{S}= \left(\frac{\partial D_{x}}{\partial x} + \frac{\partial D_{y}}{\partial y} + \frac{\partial D_{z}}{\partial z} \right) \Delta v $$
# Divergence and Maxwell's First Equation
$$\text{Divergence of } \mathbf{A} = \text{div } \mathbf{A} = \lim_{\Delta v \rightarrow 0} \frac{\oint_{S}\mathbf{A}\cdot d \mathbf{S}}{\Delta v} = \rho_{v}$$
# The Vector Operation and Divergence Theorem
## The Del Operator (nabla)
$$\nabla = \frac{\partial}{\partial x}\mathbf{a}_x + \frac{\partial}{\partial y}\mathbf{a}_y + \frac{\partial}{\partial z}\mathbf{a}_z$$
## The Divergence Theorem
$$\oint_{S}\mathbf{D} \cdot d \mathbf{S} = \int_{vol} \nabla \cdot \mathbf{D} dv$$