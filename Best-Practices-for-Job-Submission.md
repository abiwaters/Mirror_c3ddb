C3ddb is a multi-user environment and it is important for all users to respectfully share the cluster to ensure the best possible experience for everyone. The guidelines below help with this:

The scratch space is intended to be used for intermediate storage while processing. It has a large limit to facilitate involved processes, but it is important that once a process is finished files are either downloaded or moved out of scratch space. 

Before submitting a large number of jobs (or tasks), run a small test case to make sure it works as expected.
Request jobs with the minimum number of processors needed, as it will make your job submission process faster. For example, if you only need three processors, but request 6 “just in case”, you will have to wait for 6 processors to be available at one time. 

Use checkpoints! If there are breaks in your workflow, save the current state to a checkpoint file. This will allow you to restart your job from the last successful state instead of rerunning it from the beginning in case the job failed due to an error or failed to complete before the hard time limit.

Use a job array instead of submitting many individual jobs when possible.

Do not submit many short jobs. If your jobs take just a few minutes combine them into a single script – this will reduce the workload on the system and will help to avoid generating tons of tiny files, which are a problem for the system and generally annoying for the user. 

Try to avoid creating many (thousands+) tiny files when possible. It is better for the system to have a smaller number of larger files. If you do need to have a very large number of files, you should store them in /XXXX to avoid a high cost on the system to back them up.
