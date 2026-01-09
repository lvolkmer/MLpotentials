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
