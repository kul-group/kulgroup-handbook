---
layout: default
title: BASH Commands & Essentials
parent: 2. Learning the basics
has_children: false
nav_order: 2
has_toc: false
---

# Learning BASH

{: .no_toc }

The following will guide you and point to the nessescary resources to learn the basic BASH commands for use on the terminals and try some basic exercises.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

### Getting Started with Bash: Basic Commands
This is a basic introduction to the most commonly used bash commands. A more detailed tutorial can be found [here](Command_Line.md#command-line). You can practice most of this on your local machine. Essentially, the command line allows you to move around your computer, make new files, edit documents, and run simple programs. While this is easy to do on your local machine using Finder or Anaconda, when using a HPC, almost everything must be done using the command line. To start, open iTerm or other terminal software.

### Moving Around
- See what directory you are in at anytime by typing `pwd` (and then pressing enter)
- See what items are in your current directory by typing `ls`
- Move to one of the subdirectories by typing `cd [directory_name]` for example, in your home directory (the one you start in when you open iTerm) `cd Desktop` will take you to your Desktop, and then typing ```ls``` will show you the same files that you see on your Desktop normally.
- Return to your home directory at anytime by typing `cd ~/` or just `cd`
- Go from your current directory to the one that contains it (or 'above' it) by typing `cd ../`
- Go to a particular directory by typing ```cd path/to/dir``` where 'path/to/dir' is the string you get when you type ```pwd``` in the particular directory you wish to go to

### Moving Files 
 - copy a file from one location to another using `cp path/to/source path/to/destination`
 - copy a folder from one location to another using `cp -r path/to/source path/to/destination`
 - copy a file from one location to another using `mv path/to/source path/to/destination`
 - copy a folder from one location to another using `mv path/to/source path/to/destination`
 - delete a file using `rm filename`. Be careful, there is no way to undo this action!!
 - delete a folder using `rm -r foldername`. Be careful, there is no way to undo this action!!
 
Note that in the previous examples, 'path/to/folder' and 'path/to/file' refer to the file paths you would need to navigate to that item. For example if you wanted to copy 'zeolite.traj' from the Documents folder to the Desktop, you could use `cp ~/Documents/zeolite.traj ~/Desktop/.`. However, if you are already in the Documents folder, you do not need to type the entire path, you can instead write `cp zeolite.traj ~/Desktop/.` since the terminal will automatically copy the file named 'zeolite.traj' in your current folder.

### Opening Files
- make a new file by typing 'vi filename' where filename is the title of the file you want to create. This will open a blank file in the vi editor, more details on using vi in the next section. 
- open and existing file by typing 'vi filename' where filename is the title of the file you want to open. Once again this will open the file in a vi editor.

### Editing Files
The vi editor seems simple but has many important commands. A more thorough list can be found [here](https://www.cs.colostate.edu/helpdocs/vi.html). 
The basic commands are:
- move around using the arrow keys
- edit part of the file by pressing the 'i' key, in the lower left corner you will see the word 'INSERT' indicating that you are in insert mode. Here you can delete characters, write new ones, and add new lines. However, your changes do not automatically save! Get out of insert mode by pressing the escape key.
- quit vi and save your work by holding down the shift key and pressing Z twice (shift + ZZ)

### Run commands on multiple directories
The following one-liners allow you to run a command for multiple directories or folders without retyping the same thing over and over again. And here are a few options to do that. 
- Write simple loops. Here is an example of a for loop. `for each_dir in 00_*; do mv $each_dir/folder1/file1  $each_dir/folder2 ; done`. This one liner allows you to run the 'mv' command only for folders that start with '00_'. Note that the '$' sign needs to be added before 'each_dir'. 
- An alternative way without using loops is to use 'echo'. Here is an example: `echo T1_T1*/ | xargs -n 1 cp vasp_opt.py`, where it will move a Python script called 'vasp_opt.py' into every single folder in the current directory that start with 'T1_T1'
- In the meantime, you can also use control operators to increase flexibility of your one liner since now you are dealing with many directories instead of one. For example, `for each_dir in 00_*; do cp $ each_dir/opt_500/my.traj new.traj || cp each_dir/opt_400/my.traj new.traj ; done`. This means if the sub-directory 'opt_500' does not have 'my.traj' in it, instead of returning an error, it will copy 'my.traj' from a different sub-folder.  The symol '||' is an 'OR' condition which execute the command after '||' if the command before it failed.
- Similarly, you can use operators such as '&&' or '!' as well in your one liner. And one more example would be `mv !(folder1 && folder2) folder1`. This command moves everything in the current directory except folder1 and folder2 into folder1.


