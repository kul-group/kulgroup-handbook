---
layout: default
title: Being Organized
parent: 3. Effective tips & strategies
has_children: false
nav_order: 4
has_toc: false
---

# Being organized
* Directory naming scheme should be consistent and descriptive. 
* 



# Organizing Files on HPC's

It is important to keep directory structures consistent across the clusters.
Only important files should be saved in the home directory. 


# Organizing Files on your computer

# Backing up files
Most important files should be backed up on your UCD box. 
The python submission script, optimized traj file, and the tar.gz zipped vasprun.xml should be saved for each run. 


# General workflow
## Preparing scripts and structures for running jobs
When preparing submission scripts or generating structures for jobs, it is best to do this within and IDE (ex) PyCharm) on your local machine. Job preparation is best done locally because...
* An IDE provides debugging tools and enables error detection when generating python scripts
* ASE GUI runs much faster locally. It is painfully slow on the clusters.

## Transfering data/scripts to and from the cluster
Check out rsync documentation online.  
* ex) transfering from local to HPC2: rsync -aP local_path <username@hpc2address>:hpc2_path 

## Locations for running jobs on cluster
Depending on the cluster you have various locations where you can run jobs and store data.
* ex) Cori
  * projectdirs
  * SCRATCH (This is short term storage. Can run jobs here and then transfer most important files to a projectdir or local for long term storage.
  * Local (only most important files should be stored here as there is limited space) 

## Box
Box should be utilized for long term storage of...
* submission scripts
* any relevant python scripts
* project data (see backing up files above)


Ask people in the group for helpful python scripts.
