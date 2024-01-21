# Computing-and-data-analysis

<img src="FEM_wavepropagation.gif" alt="Image 2" width="5555cm">
**Wavefront propagation using the Finit element method**


## Project Summary

The objective of this project is to model the propagation of wavefronts in the Ionosphere by employing convolution with a Dirac function on the Total Electron Content (TEC) signal received from a satellite. Additionally, the Finite Element Method is applied to simulate the impact on the pressure field in the ionosphere during natural hazards, such as earthquakes. Specifically, the focus is on replicating wave propagation in Turkey, considering the earthquake that occurred on February 6, 2023. The TEC data during the earthquake is sourced from CDDIS Earthdata NASA.\\

To go into a comprehensive understanding of the ionosphere and extract vital information, I initially opted for a straightforward simulation approach. Understanding the ionosphere is crucial, particularly in monitoring natural hazards on Earth. When events like earthquakes happen, they generate atmospheric waves that travel the sky and reach the ionosphere, situated approximately 50 km to 1000 km above the Earth's surface. These events perturbate the total electron content in the ionosphere, 

## Theory :  Mathematical Equations and Methods

# Convolution with Dirac Delta Function

The convolution operation is represented mathematically as:

$$
(f * g)(t) = \int_{-\infty}^{\infty} f(\tau)g(t - \tau) d\tau \quad \text{(1)}
$$

where \(f\) is the TEC signal and \(g\) is the Dirac delta function. The Dirac delta function, \(\delta(t - \tau)\), is used to model an impulse at a specific point in time.

## Finite Element Method (FEM)

FEM is a numerical technique used for solving partial differential equations (PDEs) by dividing the domain into small elements. The TEC signal propagation can be modeled using the wave equation 

$$
\frac{\partial^2 u}{\partial t^2} = c^2 \nabla^2 u \quad
$$

$$\textit{(Reference: Ludovic Metivier & Romain Brossier lecture on Full waveform inversion)}$$

where \(u\) is the displacement field and \(c\) is the wave speed. To achieve this, we need to discretize the domain into elements and solve for the displacement field at each node using finite element approximations. Boundary conditions, such as the absorption boundary condition, can also be implemented to capture the TEC signal wavepacket behavior.

The FEM is based on expressing the partial differential equation (PDE) to be solved in its variational or weak form. The first step is to approximate the second-order temporal derivative in the wave equation by its backward finite difference:

$$
\frac{\partial^2}{\partial t^2} p(\mathbf{x}, t) \approx \frac{p(\mathbf{x}, t) - 2 p(\mathbf{x}, t - T) + p(\mathbf{x}, t- 2 T)}{T^2} \quad \text{(2)}
$$

where $(T)$ is the sampling interval.

By adding this approximation into the wave equation and rearranging terms, we get:

$$
c^2 T^2 \Delta p(\mathbf{x}, t) - p(\mathbf{x}, t) = - 2 p(\mathbf{x}, t - T) + p(\mathbf{x}, t- 2 T) - c^2 T^2 q(\mathbf{x}, t)
$$




## Getting Started

## Usage



