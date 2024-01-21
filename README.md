# Computing-and-data-analysis

<img src="FEM_wavepropagation.gif" alt="Image 2" width="5555cm">
*Wavefront propagation using the Finit element method*

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

Multiplying by the test function \(v(\mathbf{x}, t)\), integration over the domain \(V\), and application of Green's first identity yields:

\[
- \int_V \left( c^2 T^2  \nabla p(\mathbf{x}, t) \cdot \nabla v(\mathbf{x}, t) + p(\mathbf{x}, t) v(\mathbf{x}, t) \right) \mathrm{d}x = \int_V \left( - 2 p(\mathbf{x}, t - T) + p(\mathbf{x}, t- 2 T) - c^2 T^2 q(\mathbf{x}, t) \right) v(\mathbf{x}, t) \mathrm{d}x

\]

where \(v(\mathbf{x}, t) = 0\) on \(\partial V\) where \(p(\mathbf{x}, t)\) is known (e.g., due to fixed boundary conditions), either in case of a pure Dirichlet boundary condition or \(\frac{\partial}{\partial n} p(\mathbf{x}, t) = 0\) on \(\partial V\) in case of a pure Neumann boundary condition. It is common to express the integral equation above in terms of the bilinear \(a(P, V)\) and linear \(L(V)\) forms:

\[
a(P, V) = \int_V \left( c^2 T^2  \nabla p(\mathbf{x}, t) \cdot \nabla v(\mathbf{x}, t) + p(\mathbf{x}, t) v(\mathbf{x}, t) \right) \mathrm{d}x
\]

\[
L(V) = \int_V \left( 2 p(\mathbf{x}, t - T) - p(\mathbf{x}, t- 2 T) + c^2 T^2 q(\mathbf{x}, t) \right) v(\mathbf{x}, t) \mathrm{d}x
\]

where

\[
a(P, V) = L(V)
\]





## Project Summary

This goal of this project is to try and simulate the wavefront propagation in the Ionosphere using the convolution with a dirac and the Finit element method.

## Getting Started

## Usage



