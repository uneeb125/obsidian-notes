# Divergence of Vector Fields
## Cartesian Coordinates
$$\nabla \cdot \mathbf{F} = \frac{\partial F_x}{\partial x} + \frac{\partial F_y}{\partial y} + \frac{\partial F_z}{\partial z}$$


## Cylindrical Coordinates
$$\nabla \cdot \mathbf{F} = \frac{1}{\rho} \frac{\partial}{\partial \rho} (\rho F_\rho) + \frac{1}{\rho} \frac{\partial F_\phi}{\partial \phi} + \frac{\partial F_z}{\partial z}$$


## Spherical Coordinates
$$\nabla \cdot \mathbf{F} = \frac{1}{r^2} \frac{\partial}{\partial r} (r^2 F_r) + \frac{1}{r \sin \theta} \frac{\partial}{\partial \theta} (\sin \theta \, F_\theta) + \frac{1}{r \sin \theta} \frac{\partial F_\phi}{\partial \phi}$$

# Grad of Scalar Fields

## Cartesian coordinates
$$\nabla \times \vec{F} = \left(\frac{\partial F_z}{\partial y} - \frac{\partial F_y}{\partial z}\right) \hat{\bf{a}}_x + \left(\frac{\partial F_x}{\partial z} - \frac{\partial F_z}{\partial x}\right) \hat{\bf{a}}_y + \left(\frac{\partial F_y}{\partial x} - \frac{\partial F_x}{\partial y}\right) \hat{\bf{a}}_z$$

## Cylindrical coordinates  
$$\nabla \times \vec{F} = \left(\frac{1}{\rho} \frac{\partial F_z}{\partial \phi} - \frac{\partial F_\phi}{\partial z}\right) \hat{\bf{a}}_\rho + \left(\frac{\partial F_\rho}{\partial z} - \frac{\partial F_z}{\partial \rho}\right) \hat{\bf{a}}_\phi + \left(\frac{1}{\rho} \frac{\partial(\rho F_\phi)}{\partial \rho} - \frac{1}{\rho} \frac{\partial F_\rho}{\partial \phi}\right) \hat{\bf{a}}_z$$

## Spherical coordinates
$$\nabla \times \vec{F} = \left(\frac{1}{r \sin{\theta}} \frac{\partial (\sin{\theta} F_\phi)}{\partial \theta} - \frac{1}{r} \frac{\partial F_\theta}{\partial \phi}\right) \hat{\bf{a}}_r + \left(\frac{1}{r} \frac{\partial (r F_\phi)}{\partial r} - \frac{1}{r} \frac{\partial F_r}{\partial \phi}\right) \hat{\bf{a}}_\theta + \left(\frac{1}{r \sin{\theta}} \frac{\partial F_\theta}{\partial r} - \frac{1}{r} \frac{\partial F_r}{\partial \theta}\right) \hat{\bf{a}}_\phi$$

# Curl
## Cartesian coordinates
$$\nabla \times \vec{F} = 
\begin{vmatrix} 
\hat{x} & \hat{y} & \hat{z} \\
\frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\
F_x & F_y & F_z
\end{vmatrix}$$

## Cylindrical coordinates
$$\nabla \times \vec{F} =  
\begin{vmatrix}
\frac{1}{{\rho}}a_{\rho} & a_{\phi} & \frac{1}{{\rho}}a_{z} \\
\frac{\partial}{\partial \rho} & \frac{\partial}{\partial \phi} & \frac{\partial}{\partial z} \\ 
F_\rho & \rho F_\phi & F_z
\end{vmatrix}$$

## Spherical coordinates
$$\nabla \times \vec{F} =
\begin{vmatrix}  
\frac{1}{{r^{2}\sin\theta}}a_{r} & \frac{1}{{r\sin}}a_{\theta} & \frac{1}{r}a_{\phi} \
\frac{\partial}{\partial r} & \frac{\partial}{\partial \theta} &  \frac{\partial}{\partial \phi} \
F_r & rF_\theta & r\sin \theta F_\phi  
\end{vmatrix}$$

## Cartesian coordinates
$$ \nabla \times \vec{F} = \hat{x} \left( \frac{\partial F_z}{\partial y} - \frac{\partial F_y}{\partial z} \right) + \hat{y} \left( \frac{\partial F_x}{\partial z} - \frac{\partial F_z}{\partial x} \right) + \hat{z} \left( \frac{\partial F_y}{\partial x} - \frac{\partial F_x}{\partial y} \right)$$

## Cylindrical coordinates 
$$ \nabla \times \vec{F} = \hat{\rho} \left( \frac{1}{\rho} \frac{\partial F_z}{\partial \phi} - \frac{\partial F_\phi}{\partial z} \right) + \hat{\phi} \left( \frac{\partial F_\rho}{\partial z} - \frac{\partial F_z}{\partial \rho} \right) + \hat{z} \left( \frac{1}{\rho} \frac{\partial(\rho F_\phi)}{\partial \rho} - \frac{1}{\rho} \frac{\partial F_\rho}{\partial \phi} \right)$$

## Spherical coordinates
$$ \nabla \times \vec{F} = \hat{r} \left( \frac{1}{r \sin{\theta}} \frac{\partial (\sin{\theta} F_\phi)}{\partial \theta} - \frac{1}{r} \frac{\partial F_\theta}{\partial \phi} \right) + \hat{\theta} \left( \frac{1}{r} \frac{\partial (r F_\phi)}{\partial r} - \frac{1}{r} \frac{\partial F_r}{\partial \phi} \right) + \hat{\phi} \left( \frac{1}{r \sin{\theta}} \frac{\partial F_\theta}{\partial r} - \frac{1}{r} \frac{\partial F_r}{\partial \theta} \right)$$


# Laplacian of Scalar Fields
## Cartesian Coordinates
$$\nabla^2 \phi = \frac{\partial^2 \phi}{\partial x^2} + \frac{\partial^2 \phi}{\partial y^2} + \frac{\partial^2 \phi}{\partial z^2}$$

## Laplacian in Cylindrical Coordinates
$$\nabla^2 \phi = \frac{1}{\rho} \frac{\partial}{\partial \rho}\left(\rho \frac{\partial \phi}{\partial \rho}\right) + \frac{1}{\rho^2} \frac{\partial^2 \phi}{\partial \phi^2} + \frac{\partial^2 \phi}{\partial z^2}$$

## Laplacian in Spherical Coordinates
$$\nabla^2 \phi = \frac{1}{r^2} \frac{\partial}{\partial r}\left(r^2 \frac{\partial \phi}{\partial r}\right) + \frac{1}{r^2 \sin \theta} \frac{\partial}{\partial \theta}\left(\sin \theta \frac{\partial \phi}{\partial \theta}\right) + \frac{1}{r^2 \sin^2 \theta} \frac{\partial^2 \phi}{\partial \phi^2}$$


# Divergence Theorem
$$\int_V \nabla \cdot \vec{F} \, dV = \oint_S \vec{F} \cdot \vec{n} \, dS$$
# Stokes Theorem
$$\oint \vec{F} \cdot dL = \int_{S} (\nabla \times \vec{F}) \cdot  d\vec{S} $$