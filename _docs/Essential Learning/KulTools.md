---
layout: default
title: KulTools
parent: 2. Learning the basics
has_children: false
nav_order: 6
has_toc: true
---

# KulTools

{: .no_toc }

Clone the following repository to the HPC1, HPC2, and CORI.
* https://github.com/kul-group/kultools

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

### VASP Test
Instructions
1. add `module load vasp/5.4.4` to your `.bashrc` file and reload it or reconnect 
2. run file `00_make_molecule.py` by running `python3 00_make_molecule.py`
3. verify that the file `start.traj` was created
4. Verify that the correct header is being used for each cluster. 
5. Verify that the sys.path.insert() is set to wherever your kultools directory lives.
6. run the second file with slurm by typing `sbatch 01_submit_job.py` (you might need a __init__.py file for kultools.py to be recognized as a module). 
7. Check the `job.out` and `job.err` files for errors

See below for making adjustments to the 01_sumbit_job.py script. 



### Adjusting parameters in submission script
Kultools creates an object which contains all the relevant information needed to successfully run a DFT calculation using vasp. 
Below are some attributes of the KT class which can be adjusted for your specific system.

### Gamma point
If you need to run a gamma point calculation, set gamma_only = True when creating an instance of the kT class.

### Material type
When creating and instance of the KT class, a structure_type must be specified. 

Available types:
* zeo
* mof
* metal
* gas-phase

These structure type tags are helpful in setting vasp parameters that are appropriate for your system of choice.
See kultools.py to see the parameters set for each material type. 
See the 01_submit_job.py script for an example of how to set the structure_type.

### Job type
When running a DFT calculation in vasp, a calculation type must be specified.

The following job types are available in the .set_calculation_type() module:
* opt
* opt_fine
* vib
* spe
* md
* solv
* nebs and dimer will be available soon

See the 01_submit_job.py script for an example of how to set the calculation type.

### Structure selection

See the 01_submit_job.py script for an example of how to set the structure.
Make sure periodic boundary conditions are set. 
* atoms = io.read('start.traj')
* atoms.pbc=True
* kt.set_structure(atoms)

### Additional parameters

Any VASP parameters can be specified by using the .set_overall_vasp_params() module.
Potential parameters that the user may want to specificy include but are not limitied to:
* xc (the functional you wish to use)
* ivdw (set this tag to include van der waals corrections, our group typically uses ivdw = 12)
* nsw (number of steps)
* kpts
* encut

See vasp wiki for more information on various paramaters.

### Kultools directory output
The current naming scheme for the directory created from your vasp run with kultools is as follows:

directory = dir_name + '_' + str(func_for_dir) + '_' + str(encut_for_dir) + '_' + str(kpts_for_dir)

where,

* dir_name = the name of the calculation type (such as opt or spe)
* func_for_dir = whatever functional you set for xc ( such as PBE)
* encut_for_dir = whatever your encut value was set to 
* kpts_for_dir = whatever your kpts were set to 

Ex) opt_PBE_400_221/




