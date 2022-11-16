---
layout: default
title: Atomic Simulation Environment
parent: 2. Learning the basics
has_children: false
nav_order: 4
has_toc: false
---

# Atomic Simulation Environment

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

Familiarize yourself with this package throughly. 

### Learning ASE
ASE is a python package using for setting up, manipulating, visualizing and analyzing atomic structures. 

Detailed documentation can be found here: [ASE](https://wiki.fysik.dtu.dk/ase/#)

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
- Detailed instruction: [File Reading](https://wiki.fysik.dtu.dk/ase/ase/io/io.html)


### Indexing
need to add more

```
indice_H = [atom.index for atom in atoms if atom.symbol=='H']
```

### Adding and deleting atoms
atoms.append thing 

You can combine two atoms objects using the + operator: combined_atoms = atoms1 + atoms2. 'combined_atoms' will have the unit cell shape of atoms1, so order of addition matters!

So, for example, you can add a hydrogen atoms using:
```
from ase import Atom
h_atom = Atom('H', (1, 1, 1)) # Creates an H atom at the (1, 1, 1) position
structure_with_hydrogen = structure + h_atom  # new atoms object which has all the atoms in 'structure' and an H atom at (1, 1, 1)
```

You can make a molecule using:
```
from ase.build import molecule
ch3oh = molecule('CH3OH')
```

You can build a metal surface slab using:
```
from ase.build import surface
s1 = surface('Au', (2, 1, 1), 9)  # makes a gold surface along the [2 1 1] plane with 9 layers
s1.center(vacuum=10, axis=2)  # centers the slab in the unit cell with 10 angstroms of vacuum along the y-axis
```


### Moving and rotating atoms
talk about translate and wrap

Move a set of atoms using atoms.translate([x,y,z]) where x,y,z are the amounts to move in x/y/z direction (in angstroms).

Rotate a set of atoms using:
```
atoms.rotate(90, 'z')  # rotates atoms 90 degrees around z-axis
atoms.rotate(90, (0, 0, 1))  # rotates atoms 90 degrees around (0, 0, 1) vector (The z-axis)
atoms.rotate('x', 'y')  # rotates the x-axis into the y-axis
atoms.rotate((1, 0, 0), (0, 1, 0))  # rotates the (1, 0, 0) axis into the (0, 1, 0) axis
```

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

[ASE Tutorials](https://wiki.fysik.dtu.dk/ase/tutorials/tutorials.html)





