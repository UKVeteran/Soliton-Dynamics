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


