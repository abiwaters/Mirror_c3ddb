On c3ddb, software and application environments are often controlled using “modules.” This page will cover the basics of choosing, loading and using modules on the cluster.

**How to view and load modules:**

> module list                             /* List loaded modules
> module avail                            /* List modules available on the system
> module load {module name}               /* add module you need. Default is the latest version
> module load {module name/version}       /* add a specific version of the module
> module rm {module name}                 /* remove module you do not need
> module initadd {module name}            /* add module when you login