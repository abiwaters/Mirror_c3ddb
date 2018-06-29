On c3ddb, software and application environments are often controlled using “modules.” This page will cover the basics of choosing, loading and using modules on the cluster.

**Start Application Without Modules:**

Some applications on the Shared Computing Cluster do not require modules. Notable examples are **matlab** and **sas**. To run these applications and basic system commands, simply type the application name.                         
[username@c3ddb ~]$ **matlab**



[username@c3ddb ~]$ **sas**

**Note**: Both MATLAB and SAS have graphical user interfaces. X Forwarding is required to use either of these applications.

**Start Applications With Modules:**

Modules set the appropriate environment variables for the application and prevent version and other application conflicts from occurring on the cluster. Applications should be loaded and unloaded as needed.

To list your loaded modules:

* [username@c3ddb ~]$ module list
* Currently Loaded Modulefiles:
*   1) pgi/13.5

Most applications will not run without being loaded.

* [username@c3ddb ~]$ **merlin**
* -bash: merlin: command not found

To list available packages use the module command with the “avail” argument

* [username@c3ddb ~]$ module avail
* ---------------------------- /share/etc/modulefiles ----------------------------
* BEAGLE/BEAGLE-3.3.2_jar_x86_64           locuszoom/1.2
* CASAVA/CASAVA_v1.8.2_gnu446              log4perl/v1.43
* CPAT/CPAT-1.2.1_Python-2.7.3_gnu446      mach/mach-1.0.18.c_gnu446
* DELLY/0.0.11                             merlin/merlin-1.1.2_gnu446
* EIGENSOFT/EIGENSOFT-4.2_gnu447           metal/metal_2011-03-25_gnu447
* ...                                   ...

To load an application, invoke the module command with the “load” argument.

* [username@c3ddb ~]$ **module load** merlin

To run the application, type the application command.

* [username@c3ddb ~]$ **merlin** --help
 
* MetaAnalysis Helper - (c) 2007 - 2009 Goncalo Abecasis
This version released on 2011-03-25
 
* #This program facilitates meta-analysis of genome-wide association studies.
* #Commonly used commands are listed below:
* #Options for describing input files ...
* #SEPARATOR        [WHITESPACE|COMMA|BOTH|TAB] (default = WHITESPACE)
* #COLUMNCOUNTING   [STRICT|LENIENT]            (default = 'STRICT')
* #MARKERLABEL      [LABEL]                     (default = 'MARKER')

To unload a module, invoke the module command with the “unload” argument.

* [username@c3ddb ~]$ module unload merlin