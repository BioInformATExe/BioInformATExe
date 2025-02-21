# How to run a jupyter notebook on ISCA.
Assumptions:
- You have conda installed (e.g. as miniconda) - you don't need to have it in your .bashrc however.
- You have an environment you want to open the notebook in
- That environment has jupyter installed

## ssh into isca with this code in a terminal
```
ssh -L 8890:localhost:8890 username@login.isca.ex.ac.uk

```

## Navigate to the directory with your notebook in and connect to an interactive node. Note the name of the compute node you connect to
```
cd path/to/directory/

# You can also use -p highmem for high memory nodes.
# --time is in the format of hh:mm:ss so change appropriately
srun -p pq --time=4:00:00 --pty bash -i

```
## Activate your environment and start jupyter notebook
You can avoid the source step if conda is in your .bashrc

```
# I'm using miniconda3 so you may need to change this part:
source /lustre/home/yourusername/miniconda3/bin/activate  
conda activate your_environment

jupyter notebook --no-browser --ip=0.0.0.0 --port=8890
```
**Keep this terminal open**

## In a new terminal, ssh back into the login node
```
ssh -L 8890:localhost:8890 username@login.isca.ex.ac.uk

```
## In the same terminal, ssh from the login node into your compute node
If you don't know your login node, it should be shown in the other terminal or you can run `squeue` to see it.

```
ssh -L 8890:localhost:8890 computenode

## E.g. ssh -L 8890:localhost:8890 comp021

```

## Then open a browser and go to:
```
http://localhost:8890
```
This should open your notebooks. 
