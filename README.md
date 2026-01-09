# MLpotentials
This repo contains MLIPs trained for property-prediction of Al-Alloys 

# Software required
- any DFT code (if you want to create training structures on your own)
- MD simulation software, e.g. LAMMPS, VASP or ASE (if you want to run directly my trained ML model)

# How to use 
Run the MD dynamics simulation for your case of application. The ML model is accurate enough in energies and forces such that it gives good result for optimization and equilibration. DO NOT use it for thermodynamic stability considerations, i.e. Convex Hull or Gibbs free energy scheme.
The ML model has high accuracy for prediction of stress tensors. Always use the average of the last $N$ time steps in your MD simulation. 
