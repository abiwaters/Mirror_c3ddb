**How to Submit an Interactive Job using [SLURM](https://github.com/mghpcc-projects/rc_howtos/blob/master/general/SlurmSummary.pdf)**

SLURM is used to help allocate resources for submitted jobs on the cluster. Jobs that require less resources, and take less time, may be scheduled quicker than jobs that are more resource intensive. Your job will not start until all requested resources are available, so it is important to only request the memory, CPU, etc., that is necessary to complete the job. 
* **sinfo** will return an overview of the resources offered by the cluster, while the **squeue** command shows to which jobs those resources are currently allocated.

` [username@c3ddb01@mit.edu/]$ sinfo`

>         PARTITION AVAIL TIMELIMIT NODES STATE  NODELIST
>         batch     up     infinite     2 alloc  node[8-9]
>         batch     up     infinite     6 idle   node[10-15]
>         debug*    up        30:00     8 idle   node[0-7]


 

>        salloc -N 1 -n 16 -p {partition name} --time=1:00:00 -exclusive
>        where:
>                -N # : number of nodes
>                -n # : number of CPU cores
>                -p <name> : specific partition
>                --time=<hh:min:sec> : run time
>                —-exclusive : using all 16 cores on a single node
>        cat <
>        myjob.slurm
>        #!/bin/bash
>        #SBATCH --gres=gpu:1
>        #SBATCH -N 1
>        #SBATCH -n 16
>        #SBATCH --time=1:00:00
>        #SBATCH --exclusive
>        . /etc/profile.d/modules.sh
>        module add gcc
>        module add mvapich2/gcc
>        /cm/shared/apps/cuda55/sdk/current/1_Utilities/deviceQuery/deviceQuery
>        sbatch myjob.slurm

**Non-interactive batch jobs** are submitted with the qsub command. The general form of the command is:

scc % **qsub** _[options] command [arguments]_

For example, to submit the printenv command to the batch system, execute:

scc % **qsub** -b y printenv
Your job _#jobID_ ("printenv") has been submitted

The option -b y tells the batch system that the following command is a binary executable. The output message of the qsub command will print the job ID, which you can use to monitor the job's status within the queue. While the job is running the batch system creates stdout and stderr files in the job’s working directory, which are named after the job with the extension ending in the job’s number, for the above example printenv.o#jobID and printenv.e#jobID. The first one will contain the output of the command and the second will have the list of errors, if any, that occurred while the job was running.

When running a program that requires arguments and passes additional options to the batch system, it quickly becomes useful to save them in a script file and submit this script as an argument to the qsub command. For example, the following script script.sh will execute a simple MATLAB job:

#!/bin/bash
 
#program name or command and its options and arguments
matlab -nodisplay -singleCompThread -r "n=4, rand; exit"

**Note:** To be processed correctly, the script must contain a blank line at the end of the file.

To submit this script.sh file to the batch system, execute:

scc % **qsub** script.sh
Your job _#jobID_ ("script.sh") has been submitted

For other batch script examples, please see Batch Script Examples.

**Software Versions and the Module Command:**
The default versions of many applications (like MATLAB, R, Python, gcc compiler, etc.) are old. To get access to newer versions of the software, please use Modules. When a **module** command is used in a bash script, the first line of the script must contain the “**-l**” option to ensure proper handling of the module command:

#!/bin/bash -l
 
#Specify the version of MATLAB to be used
module load matlab/2016b
 
#program name or command and its options and arguments
matlab -nodisplay -singleCompThread -r "n=4, rand; exit"

**General Job Submission Directives:**
There are a number of directives (options) that the user can pass to the batch system. These directives can either be provided as arguments to the **qsub** command or embedded in the job script. In a script file the lines containing these directives begin with the symbols **#$** – here is an example:

#!/bin/bash
 
#$ -l h_rt=24:00:00   # Specify the hard time limit for the job
#$ -N myjob           # Give job a name
#$ -j y               # Merge the error and output streams into a single file
 
printenv


Below is the list of some of the most commonly used directives:

**General Directives:**

**Directive:**

* **-l** _h_rt=hh:mm:ss_ : Hard run time limit in _hh:mm:ss_ format. The default is 12 hours.
* **-P** _project_name_ : Project to which this jobs is to be assigned. This directive is mandatory for all users associated with any Med.Campus project.
* **-N** _job_name_ : Specifies the job name. The default is the script or command name.
* **-o** _outputfile_ : File name for the stdout output of the job.
* **-e** _errfile_ : File name for the stderr output of the job.
* **-j y** : Merge the error and output stream files into a single file.
* **-m** _b|e|a|s|n_ : Controls when the batch system sends email to you. The possible values are – when the job begins (b), ends (e), is aborted (a), is suspended (s), or never (n) – default.
* **-M** _user_email_ : Overwrites the default email address used to send the job report.
* **-V** : All current environment variables should be exported to the batch job.
* **-v** _env=value_ : Set the runtime environment variable _env_ to _value_.
* **-hold_jid** _job_list_ : Setup job dependency list. job_list is a comma separated list of job ids and/or job names which must complete before this job can run. 

**Resource Usage and Limits:**
The Sun Grid Engine (SGE) allows a job to request specific SCC resources necessary for a successful run, including a node with large memory, multiple CPUs, a specific queue, or a node with a specific architecture. The Technical Summary contains hardware configuration for all SCC nodes. The Advanced Batch System Usage page contains examples of running jobs which require parallel environments (OMP, MPI, GPU).

The following table lists the most commonly used options to request resources available on the SCC:

**Directives to request SCC resources:**

**Directive**
* **-l h_rt**=_hh:mm:ss_ : Hard run time limit in _hh:mm:ss_ format. The default is 12 hours.
* **-l mem_total** =_#G_ : Request a node that has at least this amount of memory. Current possible choices include 94G, 125G, 252G, 504G, and 1000G
* **-l mem_per_core** =_#G_ : Request a node that has at least this amount of memory per core. Current possible choices include 3G, 4G, 8G, 12G, 16G, 18G and 28G
* **-pe omp** _N_ : Request multiple slots for Shared Memory applications (OpenMP, pthread). This option can also be used to reserve a larger amount of memory for the application. N can vary 1-28, 36.
* **-pe mpi_#_tasks_per_node** _N_ : Select multiple nodes for an MPI job. Number of tasks can be 4, 8, 12, 16, or 28 and Nmust be a multiple of this value. 
* **-t** _N_ : Submit an Array Job with N tasks. N can be up to 75,000. 
* **-l cpu_arch**=_ARCH_ : Select a processor architecture (broadwell, haswell, ivybridge, …). 
* **-l cpu_type**=_TYPE_ : Select a processor type (X5650, X5670, X5675, etc.) 
* **-l gpus**=_G/C_ : Requests a node with GPUs. G/C specifies the number of GPUs per CPU requested and should be expressed as a decimal number. 
* **-l gpu_type**=_GPUMODEL_ : Current choices for _GPUMODEL_ are M2070, K40m, and P100.
* **-l gpu_c**=_CAPABILITY_ : Specify minimum GPU capability. Current choices for _CAPABILITY_ are 2.0, 3.5, and 6.0


The following table summarizes the wall-clock runtime limits for different jobs based on their type:

**Run time limits for shared nodes:**

Type of the job / Time limit on shared nodes: 

* Single processor job / 720 hours (30 days)
* OMP / 720 hours (30 days)
* MPI / 120 hours (5 days)
* GPU / 48 hours (2 days)

**SGE Environment Variables:**
When the job is scheduled to run, a number of environment variables are set and may be used by the program:

**Batch System Environment:**

Environment Variable:
* JOB_ID : Current job ID
* JOB_NAME : Current job name
* NSLOTS : The number of slots requested by a job
* HOSTNAME : Name of execution host
* SGE_TASK_ID : Array Job task index number
* SGE_TASK_STEPSIZE : The step size of the array job specification
* SGE_TASK_FIRST : The index number of the first array job task
* SGE_TASK_LAST : The index number of the last array job task
* TMPDIR : The absolute path to the job’s temporary working directory
