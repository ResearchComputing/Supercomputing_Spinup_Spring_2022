# Job Submission Tutorial

## Introduction 

This tutorial will introduce you to the concept of "Jobs" in High Performance Computing (HPC), why they are necessary, explore different types of jobs, and provide examples for you to work through.

:warning: **__This tutorial assumes you are using CU Research Computing resources, the following jobs and scripts will ONLY work on the CURC system. Visit [this link](https://curc.readthedocs.io/en/latest/access/logging-in.html) if you need an account and login directions__** :warning:

The basic structure of this tutorial directory follows:

```
README.md 		# *this* tutorial markdown file
scripts			# directory which includes skeleton scripts for tutorial examples
programs		# directory which includes programs our jobs will execute 
solutions 		# directory with solution job scripts for examples
```

We'll start with a brief introduction to jobs and why they are necessary, describe main job types, and work through some examples. All of the examples in this section will require access to a terminal. We'll finish up with some non-traditional job submissions which allow for access to RC hardware via some graphical browser application.

## HPC Jobs

High Performance Computing (HPC) systems are more often than not, environments where many users share/compete for the same resources. Because our HPC clusters are shared resources with many users trying to utilize available compute with their applications, we need a system to divide compute in a simple and fair system.

CU Research Computing uses the resource managment program SLURM (Simple Linux Utility for Resource Management) to manage resources. Through SLURM, users can request allotments of computer resources called "Jobs." Jobs are submitted to a queue where they will wait until resources become available and then run.

Through SLURM, users can request jobs in 2 way:

1) Batch jobs (most common)

2) Interactive jobs

Both types of jobs give a user access to a compute node (hardware where intense computation should be run, visit [link](https://curc.readthedocs.io/en/latest/compute/node-types.html) for description of different node types at CURC). 

### Batch Jobs

The primary method of running applications on Research Computing (and other HPC centers) resources is through a batch job. A batch job is a job that runs on a compute node with little or no interaction with the users

Unlike running an application on your personal machine, you do not call the application you wish to run directly. Instead you create a job script that includes a call to your application. Job scripts are simply a set of resource requests and commands. When a job script is run, all the commands in the job script are executed on a compute node.

__The primary advantage of a batch job is that you don't have to sit around waiting for resources to become avaiable, just submit and wait.__

### Interactive Jobs

As the name would imply, an interactive job is a job that allows users to interact with requested resources in real time. Users can run applications, execute scripts, or run other commands directly on a compute node.

__The primary advantage of an interactive job is that you get real-time access to a compute node. Do note that you will have to wait for resources to become available.__ 


## Submit your first batch job 

Most of our examples are batch jobs as these are the most commmon and often trickest to get familiar with.

We'll start off with simply running a pre-written script to get familiar with the syntax. You run your job script by passing it to the Slurm queue with the `sbatch` command followed by your job script name:
```
sbatch <your-jobscript-name>
```

From this directory run the command:
```
sbatch scripts/submit_test.sh
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

