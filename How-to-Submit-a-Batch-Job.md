**How to Submit an Interactive Job using [SLURM](https://support.ceci-hpc.be/doc/_contents/QuickStart/SubmittingJobs/SlurmTutorial.html)**

SLURM is used to help allocate resources for submitted jobs on the cluster. Jobs that require less resources, and take less time, may be scheduled quicker than jobs that are more resource intensive. Your job will not start until all requested resources are available, so it is important to only request the memory, CPU, etc., that is necessary to complete the job. 

`--help` provides a brief summary of options. Note that the command options are all case sensitive.

* **sinfo** will return an overview of the resources offered by the cluster, while the **squeue** command shows to which jobs those resources are currently allocated. **sinfo** lists the partitions, or compute nodes, dedicated to different computing needs

` [username@c3ddb01@mit.edu/]$ sinfo`

>         PARTITION            AVAIL TIMELIMIT   NODES STATE  NODELIST
>         defq                    up 5-00:00:00     18 drain* node[008-018,022,054,077-080,091]
>         defq                    up 5-00:00:00      1   comp node095
>         defq                    up 5-00:00:00     16    mix node[004,020,023-029,033,065,081-083,093,097]
>         defq                    up 5-00:00:00     18  alloc node[006,019,021,030-032,055,069,084-090,092,094,096]
>         defq                    up 5-00:00:00     32   idle node[034-053,056-064,066-068]
>         quicktest*              up      15:00      4   idle node[001-003,005]
>         sched_mem4TB            up 5-00:00:00      1  drain node201
>         sched_mem1TB            up 5-00:00:00      2    mix node[300-301]
>         sched_mem1TB            up 5-00:00:00     24   idle node[302-308,310-326]
>         sched_mem1TB_centos7    up 5-00:00:00      8    mix node[070-076,327]
>         sched_mem1TB_centos7    up 5-00:00:00      5   idle node[098,328-331]

This is an example of the available nodes on c3ddb. When submitting a job, you will have to choose which partition (and therefore the kind of node) your job requires. Full details on these resources are available [here](http://www.mghpcc.org/resources/computer-systems-at-the-mghpcc/c3ddb/resources/). 

A few simple rules for choosing the right partition:

**quicktest** is for running test scripts that do no exceed 15 min. It can be helpful to test job submission scripts here so larger nodes are not used for troubleshooting. 

**defq** is the partition used for most jobs. The _idle_ nodes are not in use, and therefore available for job submission. Be mindful of what resources are available when requesting jobs. If you request more nodes than are currently available, your job will only be started once all resources are idle. 

**sched_mem** nodes are for jobs which require a large amount of RAM (or Main Memory) resources. Unless otherwise specified these nodes run using Centos 6. 

* **sacct** is used to report job or job step accounting information about active or completed jobs

` [username@c3ddb01@mit.edu/]$ sacct`

>            JobID    JobName  Partition    Account  AllocCPUS      State ExitCode
>        ------------ ---------- ---------- ---------- ---------- ---------- --------

_Creating a Job_

A job consists of two parts: resource requests and job steps. Resource requests define a number of CPUs, computing expected duration, amounts of RAM or disk space, etc. Job steps describe tasks that must be done, software which must be run.

The easiest way to submit a job is to create a shell script and submit it with the command **sbatch**

` [username@c3ddb01@mit.edu/]$ sbatch myscript.sh`

Job submission scripts should have the following format **(Note: these are the minimum parameters to run a job, to specify further options see chart here)**:

>           #!/bin/bash
>           #
>           #Select which kind of nodes will be used for job 
>           #SBATCH -p defq
>           #Output file
>           #SBATCH -o slurm.%N.%j.out
>           #Error/log file
>           #SBATCH -e slurm.%N.%j.err
>
>           #The test command
>           srun date



Where **SBATCH** is always at the top, after *#!/bin/bash*. Make sure that any modules needed for your job are loaded at the beginning of the script. 

Additionally, [here](http://www.ceci-hpc.be/scriptgen.html) is a resource for generating slurm headers for your scripts.

 