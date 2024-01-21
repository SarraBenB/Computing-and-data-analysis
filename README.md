# Simulation Of The Wavefront Propagation In The Ionosphere 


<img src="FEM_wavepropagation.gif" alt="Image 2" width="5555cm">

***Wavefront propagation of the pressure field using the Finit element method***

Done by Sarra Ben Brahim and supervised by **Pierre Boué** for the Computing and Data analysis project.

## Project Summary

The objective of this project is to model the propagation of wavefronts in the Ionosphere by employing convolution with a Dirac function on the Total Electron Content (TEC) signal received from a satellite and solving in order to solve a simple forward problem. Additionally, the Finite Element Method (FEM) is applied to simulate the impact on the pressure field in the ionosphere during natural hazards, such as earthquakes. Specifically, the focus is on replicating wave propagation in Turkey, considering the earthquake that occurred on February 6, 2023. The TEC data during the earthquake is sourced from CDDIS Earthdata NASA.

To go into a comprehensive understanding of the ionosphere and extract vital information, I initially opted for a straightforward simulation approach. Understanding the ionosphere is crucial, particularly in monitoring natural hazards on Earth. When events like earthquakes happen, they generate atmospheric waves that travel the sky and reach the ionosphere, situated approximately 50 km to 1000 km above the Earth's surface. These events perturbate the total electron content in the ionosphere and can be detect it faster with real-time GNSS station than traditional GNSS station (GUARDIAN project).

## Theory :  Mathematical Equations and Methods

### Convolution with Dirac Function

The convolution operation is represented mathematically as:

$$
(f * g)(t) = \int_{-\infty}^{\infty} f(\tau)g(t - \tau) d\tau \quad \text{(1)}
$$

where $$(f)$$ is the TEC signal and $$(g)$$ is the Dirac delta function. The Dirac delta function, $$\delta(t - \tau)$$, is used to model an impulse at a specific point in time.

### Finite Element Method (FEM)

FEM is a numerical technique used for solving partial differential equations (PDEs) by dividing the domain into small elements. The TEC signal propagation can be modeled using the wave equation 

$$
\frac{\partial^2 u}{\partial t^2} = c^2 \nabla^2 u \quad
$$

where $(u)$ is the displacement field and $(c)$ is the wave speed. To achieve this, we need to discretize the domain into elements and solve for the displacement field at each node using finite element approximations. Boundary conditions, such as the absorption boundary condition, can also be implemented to capture the TEC signal wavepacket behavior.***(Reference: Ludovic Metivier & Romain Brossier lecture on Full waveform inversion)***


The FEM is based on expressing the partial differential equation (PDE) to be solved in its variational or weak form. The first step is to approximate the second-order temporal derivative in the wave equation by its backward finite difference:

$$
\frac{\partial^2}{\partial t^2} p(\mathbf{x}, t) \approx \frac{p(\mathbf{x}, t) - 2 p(\mathbf{x}, t - T) + p(\mathbf{x}, t- 2 T)}{T^2} \quad \text{(2)}
$$

where $(T)$ is the sampling interval.

By adding this approximation into the wave equation and rearranging terms, we get:

$$
c^2 T^2 \Delta p(\mathbf{x}, t) - p(\mathbf{x}, t) = - 2 p(\mathbf{x}, t - T) + p(\mathbf{x}, t- 2 T) - c^2 T^2 q(\mathbf{x}, t)
$$




## Reference

[1] GUARDIAN Project: Martire, L., Krishnamoorthy, S., Vergados, P., Romans, L. J., Szilágyi, B., Meng, X., Anderson, J. L., Komjáthy, A., Bar-Sever, Y. E. (2023) The GUARDIAN system - a GNSS upper atmospheric real-time disaster information and alert network, GPS Solutions 27(32), DOI 10.1007/s10291-022-01365-6.
[2] Ludovic Metivier & Romain Brossier lecture on Full waveform inversion
[3] Near-real-time TEC data from GUARDIAN are available through the NASA Crustal Dynamics Data Information System (CDDIS) 

