---
layout: default
title: HPC Tricks
parent: 2. Learning the basics
has_children: false
nav_order: 5
has_toc: false
---

### STEP 1: creating HPC1 and HPC2 account

Once you have created your HPC accounts (details [here](_docs/../../1.%20Getting%20Started/HPC%20&%20Workstation%20Setup.md)) you can login your hpc1 account through

```bash
ssh-XY username@hpc1.ucdavis.engr.edu
ssh-XY username@hpc2.ucdavis.engr.edu
```

### STEP 2: creating .bashrc file on the terminal

create a .bashrc file via `$ vim .bashrc` in your local terminal, copy the text under

```bash
# COLORS
export LSCOLORS=Exfxcxdxbxegedabagacad
export CLICOLOR=1
PS1="[Local: \W]\\$ "

# Alias
alias g='grep'
alias ag='ase gui'

# Accounts
alias hpc1=' ssh -XY username@hpc1.engr.ucdavis.edu'
alias hpc2=' ssh -XY username@hpc2.engr.ucdavis.edu'
alias cori=' ssh -XY -l username@cori.nersc.gov'

# Download/ uploads
#hpc1
from_hpc1() {
scp -r username@hpc1.engr.ucdavis.edu:$1 $2
}

to_hpc1() {
scp -r $1 username@hpc1.engr.ucdavis.edu:$2
}

#hpc2
from_hpc2() {
scp -r username@hpc2.engr.ucdavis.edu:$1 $2
}

to_hpc2() {
scp -r $1 username@hpc2.engr.ucdavis.edu:$2
}
```

### STEP 3: creating .profile file on the terminal

create a .profile file via `$ vim .profile` in your local terminal, copy the text under

```bash
if [ -s ~/.bashrc ]; then
  source ~/.bashrc;
fi
```
