# README

## Experiments Overview

This repository contains the first two experiments performed using **OpenFOAM** for CFD simulation and **PINNs** (Physics-Informed Neural Networks) for solving fluid flow problems.

---

## **Experiment 1: 2D Channel Flow (OpenFOAM)**

### **Objective**

To simulate laminar flow inside a 2D rectangular channel using OpenFOAM (with a thin 3D extrusion and `empty` boundary condition).

### **Domain Description**

* Channel size: **0.4 m (length) × 0.3 m (height)**
* Extruded to 3D using **0.01 m** thickness
* Mesh divided into **5 horizontal blocks**

  * Top and bottom regions: **40 mm** each
  * Central channel region divided further

### **Boundary Conditions**

* **Inlet:** Located at **x = 0** over entire height
* **Outlet:** Located at **x = 0.4 m** over entire height
* **Top & Bottom Walls:** No-slip
* **Front & Back (z-direction):** `empty` (2D simulation)

### **Solvers Used**

* `icoFoam` for incompressible laminar flow

### **Files Provided**

* `blockMeshDict`
* `fvSchemes`
* `fvSolution`
* `controlDict`
* `physicalProperties`

---

## **Experiment 2: PINNs for Navier–Stokes (2D & 3D)**

### **Objective**

To simulate fluid flow using **Physics-Informed Neural Networks** by solving:

* **Continuity:** ∇·U = 0
* **Momentum:** ∂U/∂t + ∇·(UU) = −1/ρ ∇p + ν∇²U

### **Model Details**

* Used a custom MLP architecture for 2D and extended to **3D flow** with variables:

  * **u(x,y,t)**, **v(x,y,t)**, **w(x,y,t)**, **p(x,y,t)**
* PDE loss formulation includes:

  * Momentum equations in x, y, and z
  * Incompressibility constraint
  * Initial & boundary condition losses

### **Performance Comparison**

You tested:

* Simple ANN baseline
* PINN with MLP
* **FPINN (best performance)**

### **Outputs**

* Loss plots
* Velocity field predictions
* Pressure distribution

---
