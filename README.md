# MLpotentials
This repo contains MLIPs trained for property-prediction of Al-Alloys 

# Software required
- any DFT code (if you want to create training structures on your own)
- MD simulation software, e.g. LAMMPS, VASP or ASE (if you want to run my trained ML models directly)

# How to use 
Run the MD dynamics simulation for your case of application. The ML model is accurate enough in energies and forces such that it gives good result for optimization and equilibration.
The ML model has high accuracy for prediction of stress tensors. Always use the average of the last $N$ time steps in your MD simulation, where $N$ is determined by the absence of fluctuations in other relevant quantities (e.g. temperature fluctuation should be very small) 

| usable| not usable |
|----------|----------|
|Optimization 0K | Convex Hull  | 
|Dynamics up to 400K (including heating, cooling) | Gibbs free energy stability| 
|Stress tensor | any other than NPT and NVT ensemble  | 
|Al + Mg + Zr + Si (low concentration regime) | other elements or non-fcc structures| 


VASP MLFF can be used only in VASP, MACE neural network model can be used in LAMMPS, ASE and many others. 

# Calculation of polycrystal constants 
Apply a change of shape and size to the box defined by the distortion matrix $ D_{ij} = \delta_{ij} + \varepsilon_{ij}$ . Then run MD simulation and get $\tau$ as an average for $N$ time steps. This results in one data point. Do this multiple time and then fit 
From $\tau_{ij} = C_{ijkl} \varepsilon_{kl}$ to derive the stiffness matrix $C_{ijkl}$ . Depending on the symmetry of your system, you need different matrix entries, i.e. need to run different distortions. 
You can calculate the polycrystalline constants $B,G,E, \nu$ from the stiffness matrix, respecting the symmetry of the system. For an isotrope material there exist only two independent constants, so e.g. $\nu = \nu(B,G)$ and $E= E(B,G)$. 
