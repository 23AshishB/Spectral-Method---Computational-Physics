# Spectral Method | EP4210 (Computational Physics)

Solving a wave equation with spatially varying wave speed using a spectral (Fourier–Galerkin) method.

$$
\frac{\partial^2 f}{\partial t^2} = \cos^2(x)\,\frac{\partial^2 f}{\partial x^2}
$$

---

## Wave Evolution (Animation)
<p align="center">
  <img src="https://github.com/user-attachments/assets/22042620-60df-4ca0-8dc3-7f3e0590707e" width="70%">
</p>


### What the animation shows

- **PDE:**  $$f_{tt} = \cos^2(x)\, f_{xx}$$ on $$[0, 2\pi]$$ with periodic BCs  
- **Spectral method (space):**
  - $$K = \mathrm{diag}(k^2)$$ (spectral Laplacian from FFT)
  - $$C$$ is the Fourier convolution matrix of $\cos^2(x)$  
    $$C_{k,k} = \frac12, \qquad C_{k,k\pm2} = \frac14$$

- **Implicit time-stepping:**
  $$(C + \Delta t^2 K)\,\hat{f}^{\,n+1}
  = 2C\,\hat{f}^{\,n} - C\,\hat{f}^{\,n-1}$$

- **Initialization:**
  $$f^1 = f^0 + \frac{1}{2}\Delta t^2\,( \cos^2 x )\, f_{xx}^0$$

  Second derivative computed via FFT:
  $$f_{xx}^0 = \mathcal{F}^{-1} \big( -k^2 \, \mathcal{F}(f^0) \big)$$
