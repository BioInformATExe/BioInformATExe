# How to create your own shortcuts (aliases) in a bash command shell (including on ISCA)

You can create your own shortcuts to use on ISCA, or any bash terminal, which can massively speed up your work. 

Examples of shortcuts I use often:
- .. is as though I'd done cd ..
- ... is the equivalent of cd ../.. - and .... is cd ../../.. etc. which speeds up navigation
- **squ** is the equivalent of squeue -u <username> (which lists my active jobs)
- **mine** - if I type this into bash, it takes me to my directory within my groups project directory, instead of the home directory I reach when I log in. This is as though I did cd /lustre/projects/Research_Project-TXXXXXX/user
- **stop** - this stops all jobs I'm running on the slurm scheduler, as though I'd typed scancel -u <username>


## How do you do this?
To add your own shortcuts, you need to modify your **.bashrc** file. This is located in your home directory, but it is normally hidden. A . at the start of a file name indicates a hidden file.

Hidden files don't usually show up with the `ls` command, but you can view hidden files using `ls -a` 
  
Edit your .bashrc file with caution. Try not to make shortcuts which are similar to common commands.

```
cd ~ # go to your home directory
nano .bashrc # open and edit your .bashrc file. 
  
```

Inside your .bashrc file, you will find a section called **# User specific aliases and functions**
Under these, you can begin adding aliases. An alias is basically a different way of saying a command. 

The format to add an alias is:
`alias <shortcut>='full command'

e.g.
  
`alias ...='cd ../..'`
  
`alias mine='cd /lustre/projects/Research_Project-TXXXXXX/ali'`  #Ali is my name and this path is to a subdirectory I set up in my group's research project directory on Isca. You will want to modify this one!
  

Once you've added the aliases you want (each on a new line), save your .bashrc, close Isca and log back in to use your new shortcuts. 
  
  
## Here's a list of shortcuts I use, already formated for the .bashrc file. 
```
alias ll='ls -lhtr' # list files and info with human readable file sizes in order of most recent
alias squ='squeue -u <userID>' # replace <userID> with your isca username. Shows your active jobs in the slurm queue
alias stop='scancel -u <userID>' # cancel all of your scheduled and running jobs. 
alias mine='cd /lustre/projects/Research_Project-<your_project!>/<subdirectory_of_your_choice>' # go to that directory
alias ..='cd ..' # go up to the directory containing current directory
alias ...='cd ../..' # go up two levels
alias ....='cd ../../..' # go up 3 levels
alias .....='cd ../../../..' # up 4 levels
alias cd..='cd ..' # as above but for an alternate quickly typed in format
alias cd...='cd ../..'
alias cd....='cd ../../..'
alias cd.....='cd ../../../..'
  
```
  
### Why have both alias ...='cd ../..' and alias cd...='cd ../..' ?
Because cd is so commonly used, it just becomes part of your muscle memory and I sometimes find I've typed it and others not. You could even add an alias for cd ...#'cd ../..' in case you automatically type the space as well. 
  
  
  
## About the .bashrc file
This is a configuration file for bash which is personal to you as a user. It can be used to contain aliases, but it can also be used for other important purposes, such as allowing you to easily initialise conda and similar tools which let you install your own modules and packages.
