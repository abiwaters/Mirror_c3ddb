**How to Submit an Interactive Job using [SLURM](https://support.ceci-hpc.be/doc/_contents/QuickStart/SubmittingJobs/SlurmTutorial.html)**

SLURM is used to help allocate resources for submitted jobs on the cluster. Jobs that require less resources, and take less time, may be scheduled quicker than jobs that are more resource intensive. Your job will not start until all requested resources are available, so it is important to only request the memory, CPU, etc., that is necessary to complete the job. 
* **sinfo** will return an overview of the resources offered by the cluster, while the **squeue** command shows to which jobs those resources are currently allocated. **sinfo** lists the partitions, or compute nodes, dedicated to different computing needs

` [username@c3ddb01@mit.edu/]$ sinfo`

>         PARTITION AVAIL TIMELIMIT NODES STATE  NODELIST
>         batch     up     infinite     2 alloc  node[8-9]
>         batch     up     infinite     6 idle   node[10-15]
>         debug*    up        30:00     8 idle   node[0-7]


 