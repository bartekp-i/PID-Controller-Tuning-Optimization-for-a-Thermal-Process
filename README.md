# PID Controller Tuning Optimization for a Thermal Plant

## Overview

This project compares two optimization techniques for tuning a PID controller of a first-order thermal plant with transport delay:

* Nelder-Mead Simplex (`fminsearch`)
* Particle Swarm Optimization (PSO)

The goal is to automatically find the PID parameters that provide the best temperature control performance while minimizing tracking error and overshoot.

---

## Thermal Plant Model

The controlled system is modeled as a first-order thermal process with:

* Static gain
* Time constant
* Transport delay

The delay is approximated using a third-order Padé approximation to enable simulation and controller design in MATLAB.

---

## PID Controller

The PID controller output is calculated from:

- Proportional term (Kp × current error)
- Integral term (Ki × accumulated error)
- Derivative term (Kd × rate of change of error)
A first-order filter is applied to the derivative term to reduce sensitivity to measurement noise.

---

## Optimization Objective

The PID parameters ((K_p, K_i, K_d)) are optimized by minimizing a cost function composed of:

* **ISE (Integral of Squared Error)** – measures tracking accuracy.
* **Overshoot penalty** – discourages excessive temperature overshoot.

---

## Optimization Methods

### Nelder-Mead

A derivative-free local optimization algorithm that iteratively modifies a simplex in the search space to find better PID parameters.

**Advantages**

* Simple implementation
* Fast convergence near a good solution

**Limitations**

* May converge to a local optimum
* Sensitive to the initial parameter guess

---

### Particle Swarm Optimization (PSO)

A population-based optimization algorithm inspired by swarm behavior.

Each particle represents a candidate PID parameter set and moves through the search space based on:

* Its own best solution
* The swarm's global best solution

**Advantages**

* Better global search capability
* Less dependent on initial conditions

**Limitations**

* Higher computational cost
* Requires tuning of swarm parameters

---

## Results

### Step Response Comparison

> Insert simulation result graph here.

![Results Graph](images/results.png)

The graph should compare:

* Manual PID tuning
* Nelder-Mead optimized PID
* PSO optimized PID

Performance metrics include:

* ISE
* IAE
* Overshoot (%)
* Settling Time (s)

---

## Conclusion

This project demonstrates how optimization algorithms can automatically tune PID controllers for thermal systems. The performance of a classical local optimizer (Nelder-Mead) is compared with a global optimization technique (PSO), allowing evaluation of control quality and optimization effectiveness.
