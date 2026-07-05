<div align="center">
  <h1>🌊 Soliton Dynamics</h1>
  <p><strong>A Comprehensive Mathematical Exploration & Computational Solver for the KdV and sine-Gordon Equations</strong></p>
  
  <p>
    <img src="https://img.shields.io/badge/Mathematics-Mathematical%20Physics-blue?style=flat-square" alt="Math Physics">
    <img src="https://img.shields.io/badge/Equations-Nonlinear%20PDEs-orange?style=flat-square" alt="Nonlinear PDEs">
    <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License MIT">
  </p>
</div>

<hr />

## 📑 Table of Contents
<ul>
  <li><a href="#introduction">Introduction to Solitons</a></li>
  <li><a href="#kdv-equation">The Korteweg-de Vries (KdV) Equation</a></li>
  <li><a href="#sine-gordon-equation">The sine-Gordon Equation</a></li>
  <li><a href="#comparative-analysis">Comparative Analysis</a></li>
  <li><a href="#numerical-methods">Numerical Implementation</a></li>
  <li><a href="#getting-started">Getting Started</a></li>
</ul>

<hr />

<div id="introduction"></div>
## 🌌 Introduction to Solitons

<p>
  A <strong>soliton</strong> is a self-reinforcing solitary wave packet that maintains its shape while propagating at a constant velocity. Unlike standard waves in linear media, which inevitably dissipate and spread out due to dispersion, solitons owe their permanent existence to a delicate, exact cancellation between two competing physical phenomena:
</p>

<blockquote>
  <strong>Nonlinear Effects:</strong> Which act to steepen the wave front.<br>
  <strong>Dispersive Effects:</strong> Which act to broaden and flatten the wave front.
</blockquote>

<p>
  First observed experimentally by John Scott Russell in a Scottish canal in 1834, solitons are now recognized as foundational elements in fiber-optic communications, plasma physics, crystal lattices, and quantum field theories.
</p>

<hr />

<div id="kdv-equation"></div>
## 🏄 The Korteweg-de Vries (KdV) Equation

<p>
  Formulated in 1895 to model long, shallow water waves, the <strong>KdV equation</strong> is a third-order nonlinear partial differential equation. It serves as the archetypal system for studying mathematical solitons and integrability.
</p>

<h3>Mathematical Form</h3>
<p>
  For a spatial coordinate <em>x</em> and time variable <em>t</em>, the evolution of the wave profile <em>u(x, t)</em> is governed by:
</p>

<pre><code>  &part;u/&part;t + 6u(&part;u/&part;x) + &part;³u/&part;x³ = 0</code></pre>

<p>Where:</p>
<ul>
  <li><code>&part;u/&part;t</code> represents the time evolution of the wave.</li>
  <li><code>6u(&part;u/&part;x)</code> is the convective nonlinear term causing the wave front to steepen.</li>
  <li><code>&part;³u/&part;x³</code> is the linear dispersion term causing different wavelengths to travel at different speeds.</li>
</ul>

<h3>Key Characteristics</h3>
<ul>
  <li><strong>Amplitude-Velocity Coupling:</strong> Taller KdV solitons travel strictly faster and are narrower than shorter ones.</li>
  <li><strong>Elastic Collisions:</strong> When two solitons collide, they interact nonlinearly, undergo a clean phase shift, and emerge entirely unscathed with their original shapes and velocities intact.</li>
</ul>

<hr />

<div id="sine-gordon-equation"></div>
## 🌀 The sine-Gordon Equation

<p>
  The <strong>sine-Gordon equation</strong> is a nonlinear hyperbolic partial differential equation that features relativistic invariance. It emerges natively in differential geometry, the physics of Josephson junctions (superconducting devices), dislocations in crystals, and mechanical torsion pendulums.
</p>

<h3>Mathematical Form</h3>
<p>
  The fields &phi;<em>(x, t)</em> evolve according to the following wave-like equation modified by a nonlinear periodic potential:
</p>

<pre><code>  &part;²&phi;/&part;t² - &part;²&phi;/&part;x² + sin(&phi;) = 0</code></pre>

<h3>Topological Solitons (Kinks & Antikinks)</h3>
<p>
  Because of the periodic <code>sin(&phi;)</code> term, the solutions shift between different discrete, stable vacuum states (multiples of 2&pi;). This gives rise to unique topological configurations:
</p>

<ul>
  <li><strong>Kink Soliton:</strong> A smooth transition from 0 to 2&pi; as <em>x</em> spans from negative to positive infinity. It behaves like a relativistic particle.</li>
  <li><strong>Antikink Soliton:</strong> A smooth transition downward from 2&pi; to 0.</li>
  <li><strong>Breather Mode:</strong> A bound kink-antikink pair that oscillates periodically in time while remaining localized in space.</li>
</ul>

<hr />

<div id="comparative-analysis"></div>
## 📊 Comparative Analysis

<table width="100%">
  <thead>
    <tr>
      <th align="left">Property</th>
      <th align="left">Korteweg-de Vries (KdV)</th>
      <th align="left">sine-Gordon</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Physical Origin</strong></td>
      <td>Shallow water waves, acoustic waves</td>
      <td>Relativistic fields, Josephson arrays</td>
    </tr>
    <tr>
      <td><strong>Equation Order</strong></td>
      <td>1st order in time, 3rd order in space</td>
      <td>2nd order in time, 2nd order in space</td>
    </tr>
    <tr>
      <td><strong>Soliton Type</strong></td>
      <td>Nontopological (pulse shape)</td>
      <td>Topological (Kinks, Antikinks, Breathers)</td>
    </tr>
    <tr>
      <td><strong>Relativistic Behavior</strong></td>
      <td>No (Galilean invariant)</td>
      <td>Yes (Lorentz invariant, velocity bounded by c=1)</td>
    </tr>
    <tr>
      <td><strong>Asymptotic Boundaries</strong></td>
      <td>Approaches 0 at infinity</td>
      <td>Approaches multiples of 2&pi; at infinity</td>
    </tr>
  </tbody>
</table>

<hr />

<div id="numerical-methods"></div>
## 💻 Numerical Implementation

<p>
  Because both equations are completely integrable, they can be solved analytically using the Inverse Scattering Transform (IST). However, for multi-soliton interactions on arbitrary initial profiles, this repository implements high-order numeric solvers.
</p>

<details>
  <summary>🔍 View Mathematical Discretization Details</summary>
  <br>
  <h4>KdV Solver: Pseudo-Spectral Method</h4>
  <p>
    We approximate the spatial derivatives using the Fast Fourier Transform (FFT). Because spatial dispersion is linear in the Fourier domain, it can be integrated exactly:
  </p>
  <pre><code>  U_k(t + &Delta;t) = U_k(t) * exp(i * k³ * &Delta;t) + Nonlinear_Corrections</code></pre>

  <h4>sine-Gordon Solver: Fourth-Order Runge-Kutta (RK4)</h4>
  <p>
    The second-order time derivative is split into a system of coupled first-order equations by defining an auxiliary conjugate momentum field <code>&psi; = &part;&phi;/&part;t</code>, then solved via an explicit spatial finite-difference grid.
  </p>
</details>

<hr />

<div id="getting-started"></div>
## 🚀 Getting Started

<h3>Prerequisites</h3>
<p>Ensure you have a modern scientific environment set up with your chosen runtime wrapper (Python, MATLAB, or C++):</p>
<pre><code>pip install numpy scipy matplotlib</code></pre>

<h3>Running a Simulation</h3>
<p>To launch the interactive multi-soliton collision visualizer, run the main simulation file:</p>
<pre><code>python simulate_solitons.py --equation kdv --solitons 2</code></pre>

<br>

## 🐍 The KdV Multi-Soliton Simulation Script
```python
import numpy as np
from scipy.integrate import solve_ivp
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

# =====================================================================
# 1. Spatial Domain & Discrete Grid Setup
# =====================================================================
L = 50.0      # Computational domain width (periodic boundaries)
N = 256       # Number of Fourier modes (power of 2 for fast FFT execution)
x = np.linspace(-L/2, L/2, N, endpoint=False)
dx = x[1] - x[0]

# Generate the wavenumber vector (k) properly mapped to FFT frequencies
k = 2 * np.pi * np.fft.fftfreq(N, d=dx)

# =====================================================================
# 2. Initial Condition: Constructing Two Solitons
#    Analytical 1-soliton: u(x,t) = (c/2) * sech^2( sqrt(c)/2 * (x - c*t) )
# =====================================================================
c1 = 9.0   # Velocity/Amplitude parameter of the fast, heavy soliton
c2 = 2.5   # Velocity/Amplitude parameter of the slow, light soliton

x1 = -15.0 # Starting position of the fast trailing soliton
x2 = -2.0  # Starting position of the slow leading soliton

u0 = (c1/2.0) * (1.0 / np.cosh(np.sqrt(c1)/2.0 * (x - x1)))**2 + \
     (c2/2.0) * (1.0 / np.cosh(np.sqrt(c2)/2.0 * (x - x2)))**2

# =====================================================================
# 3. Defining Governing PDE Dynamics in Fourier Space
#    Transforming u_t + 3*(u^2)_x + u_xxx = 0  ==>  d(u_hat)/dt
# =====================================================================
def kdv_fourier_rhs(t, u_hat):
    # Transform back to real space to compute the nonlinear squaring term
    u = np.fft.ifft(u_hat).real
    u_squared_hat = np.fft.fft(u**2)
    
    # Spatial derivatives become algebraic multiplications in Fourier space:
    # d/dx -> i*k  |  d3/dx3 -> (i*k)^3 = -i * k^3
    nonlinear_term = -3j * k * u_squared_hat
    dispersive_term = 1j * (k**3) * u_hat
    
    return nonlinear_term + dispersive_term

# Transform our physical initial wave packet into Fourier space
u0_hat = np.fft.fft(u0)

# =====================================================================
# 4. Time Integration (Adaptive Runge-Kutta 45)
# =====================================================================
t_span = (0.0, 5.0)
t_frames = np.linspace(t_span[0], t_span[1], 250)

print("Solving nonlinear system trajectory...")
sol = solve_ivp(kdv_fourier_rhs, t_span, u0_hat, t_eval=t_frames, method='RK45')

# Reconstruct the real physical waveform out of the ODE solutions array
u_history = np.fft.ifft(sol.y, axis=0).real

# =====================================================================
# 5. Interactive Animation Setup
# =====================================================================
fig, ax = plt.subplots(figsize=(9, 5.5))
line, = ax.plot(x, u_history[:, 0], color='#007acc', lw=2.5, label='Wave Profile $u(x,t)$')

ax.set_xlim(-L/2, L/2)
ax.set_ylim(-0.5, np.max(u_history) * 1.1)
ax.set_title("KdV 2-Soliton Elastic Collision Sandbox", fontsize=12, fontweight='bold')
ax.set_xlabel("Spatial Coordinate (x)", fontsize=10)
ax.set_ylabel("Amplitude (u)", fontsize=10)
ax.grid(True, linestyle=':', alpha=0.6)
ax.legend(loc="upper right")

# Frame update driver function for matplotlib animation engine
def update_frame(frame_idx):
    line.set_ydata(u_history[:, frame_idx])
    return line,

anim = FuncAnimation(fig, update_frame, frames=len(t_frames), interval=25, blit=True)
plt.show()
```

## 🌀 The sine-Gordon Kink-Antikink Simulation Script
```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

# =====================================================================
# 1. Spatial Grid & Relativistic Parameters Setup
# =====================================================================
L = 40.0        # Domain length spanning from -L/2 to L/2
N = 400         # Number of spatial grid points
x = np.linspace(-L/2, L/2, N, endpoint=False)
dx = x[1] - x[0]

v = 0.6         # Velocity of the solitons (fraction of speed of light c=1)
gamma = 1.0 / np.sqrt(1.0 - v**2)  # Lorentz contraction factor
x0 = 8.0        # Initial displacement from the center for both solitons

# =====================================================================
# 2. Time Discretization & Stability (CFL) Check
# =====================================================================
dt = 0.04       # Time step size
# CFL condition check: dt/dx must be strictly less than 1 for stability
assert dt / dx < 1.0, "System unstable: Decrease dt or increase dx."

t_max = 25.0    # Total simulation run time
time_steps = int(t_max / dt)

# =====================================================================
# 3. Analytical Initial Conditions (t = 0)
#    Kink:     4 * arctan( exp( gamma * (x + x0) ) )
#    Antikink: -4 * arctan( exp( gamma * (x - x0) ) )
# =====================================================================
# Superposition creates a stable localized 2*pi plateau/bubble
phi_kink = 4.0 * np.arctan(np.exp(gamma * (x + x0)))
phi_antikink = -4.0 * np.arctan(np.exp(gamma * (x - x0)))
phi_0 = phi_kink + phi_antikink

# Analytical time derivative (velocity field) at t=0
# Shifting the profiles inward requires precise initial momentum mapping
phi_dot_kink = -2.0 * gamma * v / np.cosh(gamma * (x + x0))
phi_dot_antikink = -2.0 * gamma * v / np.cosh(gamma * (x - x0))
phi_dot_0 = phi_dot_kink + phi_dot_antikink

# =====================================================================
# 4. Memory Allocation & Second-Order Time Stepping
# =====================================================================
# We store the full history grid to feed the animation engine
phi_history = np.zeros((N, time_steps))
phi_history[:, 0] = phi_0

# Construct the very first time step (t = dt) using a Taylor expansion:
# phi^1 = phi^0 + dt * phi_dot_0 + (dt^2 / 2) * (phi_xx^0 - sin(phi^0))
phi_xx_0 = (np.roll(phi_0, 1) - 2.0 * phi_0 + np.roll(phi_0, -1)) / (dx**2)
phi_history[:, 1] = phi_0 + dt * phi_dot_0 + (dt**2 / 2.0) * (phi_xx_0 - np.sin(phi_0))

# Main loop using explicit central differences for t > dt
print("Simulating relativistic topological field trajectory...")
for n in range(1, time_steps - 1):
    phi_curr = phi_history[:, n]
    phi_prev = phi_history[:, n - 1]
    
    # Second spatial derivative using a 3-point central stencil
    # np.roll handles periodic boundaries cleanly at the grid edge
    phi_xx = (np.roll(phi_curr, 1) - 2.0 * phi_curr + np.roll(phi_curr, -1)) / (dx**2)
    
    # Solve explicitly for the next step: phi^{n+1} = 2*phi^n - phi^{n-1} + dt^2 * (phi_xx - sin(phi^n))
    phi_history[:, n + 1] = 2.0 * phi_curr - phi_prev + (dt**2) * (phi_xx - np.sin(phi_curr))

# =====================================================================
# 5. Animation Canvas Configuration
# =====================================================================
fig, ax = plt.subplots(figsize=(9, 5.5))
line, = ax.plot(x, phi_history[:, 0], color='#cc0052', lw=2.5, label=r'Field Profile $\phi(x,t)$')

ax.set_xlim(-L/2, L/2)
ax.set_ylim(-1.0, 7.5)
ax.set_title("sine-Gordon Relativistic Kink-Antikink Collision", fontsize=12, fontweight='bold')
ax.set_xlabel("Spatial Coordinate (x)", fontsize=10)
ax.set_ylabel(r"Field Amplitude ($\phi$)", fontsize=10)

# Mark the stable vacuum states (0 and 2*pi) with dashed guide lines
ax.axhline(0, color='gray', linestyle='--', alpha=0.5)
ax.axhline(2 * np.pi, color='gray', linestyle='--', alpha=0.5, label='Vacuum Boundary ($2\pi$)')
ax.grid(True, linestyle=':', alpha=0.6)
ax.legend(loc="upper right")

# Downsample history frames slightly to keep animation rendering snappy
frame_stride = 3
frames_to_render = range(0, time_steps, frame_stride)

def update_frame(frame_idx):
    line.set_ydata(phi_history[:, frame_idx])
    return line,

anim = FuncAnimation(fig, update_frame, frames=frames_to_render, interval=30, blit=True)
plt.show()
```
