# Real-Time Coding on Isca (interactive nodes)
You can run jobs line-by-line on computational nodes of ISCA as you would in an R console or any other terminal. 
A computational node is one designed for computing, as opposed to the login node that most users connect to when they log in to Isca. 
They offer more computing power, and coding on these doesn't slow things down for everyone else. 

When you start an interactive session, you schedule it in the similar way to how you would submit a script through slurm.

## Starting an interactive session
There's a simple command to start an interactive session. You will need to be logged in to Isca to use it. 

You can modify this and enter it into the terminal.

`srun -p pq --time=4:00:00 --pty bash -i `

- **srun** submits a job to slurm.
- **-p** is a flag which specifies a partition, or queue, that you want to use on Isca.
- **pq** is Isca's standard partition. Others include high-mem, which allocates you more processing power.
- **--time=** specifies a duration of the job, in the hh:mm:ss format. Here we ask for 4 hours. ***Warning!*** After the time specified finishes, your interactive session will be killed, and ongoing processes stopped.
- **-pty** asks for a pseudo-terminal. This is effectively what keeps the job open in your terminal and lets you interact with it.  ***Warning!*** Closing the pseudo-terminal will probably kill your job and any ongoing processes will be stopped.
- **bash -i** starts a bash shell. **-i** is a flag telling it you'd like to interact with bash. 

After running that code, you will be asked to wait for a few moments, and then told your job was allocated resources.
Then your job will begin and you can start using the interactive session. 

**Because this is a job on the slurm scheduler, running a command which cancels all your ongoing jobs will cancel this one**

E.g. **scancel -u <isca_username>**


## Also good to know
I often use interactive nodes to run R in the terminal.

To do this, I usually purge modules to prevent conflicts, load my desired R version and then initiate it by simply entering R.

```
module purge
module load R/4.1.0-foss-2021a

R
```
This will turn the terminal into an R terminal. 
If you want to use a different version of R, you can look at what is available on Isca using `module avail R`
