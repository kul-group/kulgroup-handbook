---
layout: default
title: Atomic Simulation Environment
parent: 2. Learning the basics
has_children: false
nav_order: 4
has_toc: false
---

# Learning ASE
ASE is a python package using for setting up, manipulating, visualizing and analyzing atomic structures. 

Detailed documentation can be found here: https://wiki.fysik.dtu.dk/ase/#

## Table of contents
- Installation
- Reading and Writing file
- Indexing
- Adding and deleting atoms
- Moving and rotating atoms
- Neighbors
- ASE GUI
- Working examples
- Practices

### Installation
- Make sure you have already have python 3.6 or newer, Numpy downloaded.
- The simplest way to install ase: `$ pip install --upgrade --user ase`
- Before running the test, be sure that you enable ase in your conda environment.
- A detailed instruction for installation can be found here: https://wiki.fysik.dtu.dk/ase/install.html


### Reading and writing file
- Use the `read()` and `write()` in `ase.io` module
- Example:
```
from ase.io import read, write

structure = read('atoms_file.cif')  # create atoms object named 'structure' by reading the file named atoms_file.cif
write('new_file.traj', structure)  # write a new file of the structure with the name new_file.traj
```
- Detailed instruction: https://wiki.fysik.dtu.dk/ase/ase/io/io.html


### Indexing
indice_H = [atom.index for atom in atoms if atom.symbol=='H']


### Adding and deleting atoms
atoms.append thing 


### Moving and rotating atoms
talk about translate and wrap


### Neighbors
Obtain the indicies of the neighbors of a particular atom using:
```
from ase.neighborlist import NeighborList, natural_cutoffs
nl = NeighborList(natural_cutoffs(atoms), self_interaction=False, bothways=True)
nl.update(atoms)  # rerun this line anytime atoms in structure move
neighbors = nl.get_neighbors(atom_index)[0] # list of neighbor indicies around the atom at atom_index. the '[0]' is important!
```


### ASE GUI
ASE GUI is used to visualize and manipulate atoms. It can also be used to visualize atoms on an HPC, but this is slow.

To use ASE GUI on the terminal, navigate to the file you want to view on the command line, then type ase gui [FILENAME] and hit enter. A window should pop up.

#### Useful Commands
- two finger click and drag will allow you to rotate the atoms object.
- press '1': view from the x axis
- press '2': view from the y axis
- press '3' or '=': view from the z axis 
- press 'Cntl+B': toggles between bond view and atom view, bond view is more useful
- Click an atom: displays atom properties (#index, element, position...)
- Select Multiple atoms: 1-finger click and drag to highlight atoms, or Cntl + click to select individual atoms
- Move: 'Cntl+M' will allow you to move selected atoms using your arrow keys. Viewing direction changes what your arrow keys do.
- Rotate: 'Cntl+R' will allow you to rotate selected atoms using your arrow keys. Viewing direction changes what your arrow keys do.

#### Manipulate atoms manually through ASE GUI
- change atoms: Select atom(s)-> Edit-> Modify-> change it to the desired atom(s) 
- add atoms: Edit-> Add atoms, you can select chemical symbol or formula to add and also assign its position
- delete atoms: select atom(s)-> press the 'delete' key (Note that you can make use of invert selection under edit to delete the atoms that are not within your selection)
- repeat the structure: View-> Repeat
- If you want to save this manipilated structure, make sure to Cntl + S

Detailed instruction: https://wiki.fysik.dtu.dk/ase/ase/gui/gui.html?highlight=ase%20gui#module-ase.gui


### Working examples



### Practices





