# Job Submission Tutorial

## Submit your first batch job 

From this directory (".") run the command:
```
sbatch submit_test.sh
```
On a machine that has slurm installed (CU Research Computing for this example).

### Some questions to answer:

- Where does the output go?
- What is your job's ID?

### Anatonmy of a job script:

```
 #!/bin/bash
 
 ## Directives (Resources) 
 #SBATCH --<resource>=<amount> 

 ## Software  (Load in software)
 module load <software>

 ## User commands
 <commands>
 hostname
```

