# Getting Started
Clone the following repository to the HPC1, HPC2, and CORI.
* https://github.com/kul-group/kultools

# VASP Test
Instructions
1. add `module load vasp/5.4.4` to your `.bashrc` file and reload it or reconnect 
2. run file `00_make_molecule.py` by running `python3 00_make_molecule.py`
3. verify that the file `start.traj` was created
4. Verify that the correct header is being used for each cluster. 
5. run the second file with slurm by typing `sbatch 01_submit_job.py` (you might need a __init__.py file for kultools.py to be recognized as a module). 
6. Check the `job.out` and `job.err` files for errors

# Adjusting parameters in submission script
Kultools creates an object which contains all the relevant information needed to successfully run a DFT calculation using vasp. Below are some attributes of the KT class which can be adjusted for your specific system.

## Material type
When creating and instance of the KT class, a structure_type must be specified. Available types. 
* zeo
* mof
* metal
* gas-phase

These structure type tags are helpful in setting vasp parameters that are appropriate for your system of choice

