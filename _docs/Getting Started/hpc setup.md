---
layout: default
title: Using HPC in UC Davis
parent: 1. Getting Started
has_children: false
nav_order: 4
has_toc: false
---

### STEP 1: creating HPC1 and HPC2 account

you will need to create SSH keys
- open the terminal and type `$ ssh-keygen`
- suggestion: empty the passphrase if you dont have one
- you would generate a public key and a private key. keep the private key for yourself safe.
- sent the public key to https://wiki.cse.ucdavis.edu/cgi-bin/engr.pl for hpc1 setup.

once you have done, you can login your hpc1 account through `$ ssh-XY username@hpc1.ucdavis.engr.edu`

useful website for using ssh keys: https://www.youtube.com/watch?v=du-nWMCRkqE&t=209s


### STEP 2: creating .bashrc file on the terminal

create a .bashrc file via `$ vim .bashrc` in your local terminal, copy the text under  

```
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

#hpc2
from_hpc2() {
scp -r username@hpc2.engr.ucdavis.edu:$1 $2
}

to_hpc2() {
scp -r $1 username@hpc2.engr.ucdavis.edu:$2
```


### STEP 3: creating .profile file on the terminal

create a .profile file via `$ vim .profile` in your local terminal, copy the text under  

```
if [ -s ~/.bashrc ]; then
  source ~/.bashrc;
fi
```




