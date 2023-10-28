# Divergence
## Cartesian Coordinates
$$\nabla \cdot \mathbf{F} = \frac{\partial F_x}{\partial x} + \frac{\partial F_y}{\partial y} + \frac{\partial F_z}{\partial z}$$


## Cylindrical Coordinates
$$\nabla \cdot \mathbf{F} = \frac{1}{\rho} \frac{\partial}{\partial \rho} (\rho F_\rho) + \frac{1}{\rho} \frac{\partial F_\phi}{\partial \phi} + \frac{\partial F_z}{\partial z}$$


## Spherical Coordinates
$$\nabla \cdot \mathbf{F} = \frac{1}{r^2} \frac{\partial}{\partial r} (r^2 F_r) + \frac{1}{r \sin \theta} \frac{\partial}{\partial \theta} (\sin \theta \, F_\theta) + \frac{1}{r \sin \theta} \frac{\partial F_\phi}{\partial \phi}$$

# Grad

## Cartesian Coordinates
$$\nabla \phi = \frac{\partial \phi}{\partial x} \mathbf{e}_x + \frac{\partial \phi}{\partial y} \mathbf{e}_y + \frac{\partial \phi}{\partial z} \mathbf{e}_z$$

## Cylindrical Coordinates
$$\nabla \phi = \frac{\partial \phi}{\partial \rho} \mathbf{e}_\rho + \frac{1}{\rho} \frac{\partial \phi}{\partial \phi} \mathbf{e}_\phi + \frac{\partial \phi}{\partial z} \mathbf{e}_z$$

## Spherical Coordinates
$$\nabla \phi = \frac{\partial \phi}{\partial r} \mathbf{e}_r + \frac{1}{r} \frac{\partial \phi}{\partial \theta} \mathbf{e}_\theta + \frac{1}{r \sin \theta} \frac{\partial \phi}{\partial \phi} \mathbf{e}_\phi$$

# Laplacian
## Cartesian Coordinates
$$\nabla^2 \phi = \frac{\partial^2 \phi}{\partial x^2} + \frac{\partial^2 \phi}{\partial y^2} + \frac{\partial^2 \phi}{\partial z^2}$$

## Laplacian in Cylindrical Coordinates
$$\nabla^2 \phi = \frac{1}{\rho} \frac{\partial}{\partial \rho}\left(\rho \frac{\partial \phi}{\partial \rho}\right) + \frac{1}{\rho^2} \frac{\partial^2 \phi}{\partial \phi^2} + \frac{\partial^2 \phi}{\partial z^2}$$

## Laplacian in Spherical Coordinates
$$\nabla^2 \phi = \frac{1}{r^2} \frac{\partial}{\partial r}\left(r^2 \frac{\partial \phi}{\partial r}\right) + \frac{1}{r^2 \sin \theta} \frac{\partial}{\partial \theta}\left(\sin \theta \frac{\partial \phi}{\partial \theta}\right) + \frac{1}{r^2 \sin^2 \theta} \frac{\partial^2 \phi}{\partial \phi^2}$$

