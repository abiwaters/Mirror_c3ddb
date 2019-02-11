**How to Submit an Interactive Job using [SLURM](https://support.ceci-hpc.be/doc/_contents/QuickStart/SubmittingJobs/SlurmTutorial.html)**

SLURM is used to help allocate resources for submitted jobs on the cluster. Jobs that require less resources, and take less time, may be scheduled quicker than jobs that are more resource intensive. Your job will not start until all requested resources are available, so it is important to only request the memory, CPU, etc., that is necessary to complete the job. 

`--help` provides a brief summary of options. Note that the command options are all case sensitive.

* **sinfo** will return an overview of the resources offered by the cluster, while the **squeue** command shows to which jobs those resources are currently allocated. **sinfo** lists the partitions, or compute nodes, dedicated to different computing needs

` [username@c3ddb01@mit.edu/]$ sinfo`

>         PARTITION AVAIL TIMELIMIT NODES STATE  NODELIST
>         batch     up     infinite     2 alloc  node[8-9]
>         batch     up     infinite     6 idle   node[10-15]
>         debug*    up        30:00     8 idle   node[0-7]

* **sacct** is used to report job or job step accounting information about active or completed jobs

` [username@c3ddb01@mit.edu/]$ sacct`

>            JobID    JobName  Partition    Account  AllocCPUS      State ExitCode
>        ------------ ---------- ---------- ---------- ---------- ---------- --------

_Creating a Job_

A job consists of two parts: resource requests and job steps. Resource requests define a number of CPUs, computing expected duration, amounts of RAM or disk space, etc. Job steps describe tasks that must be done, software which must be run.

The easiest way to submit a job is to create a shell script and submit it with the command **sbatch**

` [username@c3ddb01@mit.edu/]$ sbatch myscript.sh`

Job submission scripts should have the following format:

>           #!/bin/bash
>           #
>           #SBATCH -p general # partition (queue)
>           #SBATCH -N 1 # number of nodes
>           #SBATCH -n 1 # number of cores
>           #SBATCH --mem 100 # memory pool for all cores
>           #SBATCH -t 0-2:00 # time (D-HH:MM)
>           #SBATCH -o slurm.%N.%j.out # STDOUT
>           #SBATCH -e slurm.%N.%j.err # STDERR
>           for i in {1..100000}; do
>           echo $RANDOM >> SomeRandomNumbers.txt
>           donesort SomeRandomNumbers.txt



Where **SBATCH** is always at the top, after *#!/bin/bash*. Make sure that any modules needed for your job are loaded at the beginning of the script. 


 