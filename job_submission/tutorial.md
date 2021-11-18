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
## Write your first batch job

### Create and run a batch job that has the following:

1) The job will run on 1 core of 1 node
2) We will request a 1 minute wall time
3) Run on the shas-testing partition
4) Set the output file to be named “sleep.%j.out”
5) Name your job “sleep”
Bonus: Email yourself when the job ends
6) Contains the following commands
```
echo "Running on host" $(hostname)
echo "Starting Sleep"
sleep 30
echo "Ending Sleep. Exiting Job!"
```

> Note: A [brief list](https://curc.readthedocs.io/en/latest/running-jobs/job-resources.html#slurm-resource-flags) of slurm directives/flags.

### Solutions

For solutions go to the `./solutions` directory, solutions are prefixed with "answer"

