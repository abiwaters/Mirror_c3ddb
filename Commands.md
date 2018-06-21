Once logged into c3ddb, you will see a command prompt. The text prompt displayed to you is called the “terminal” and the program you interact with is called a “shell“. Inside each shell, you will communicate with the operating system and filesystem using “commands“. 

**Command Prompt:**                                                                                                     
After connecting to the Shared Computing Cluster, you will be presented with a command prompt. This can look different depending on the shell. The default shell is “bash” and for most users it will look as follows.               
[username@ c3ddb01.mit.edu ~]$

Regardless of your shell, your interaction with the cluster will be nearly identical. This prompt lets you type in Linux commands to the system, to create directories, list files, and do more complex things like run applications. Make sure to hit the “Enter” key after typing in any of the commands shown on this page.

If you are completely new to bash, we recommend some tutorials below to orient you to the shell language. This is not an exhaustive list by any means: 
Videos:
PDF Tutorials:
Interactive Websites:

                                                                                                                         
**Commands, Arguments and Options:**

**Commands** are issued to the system by typing in the terminal; some are straightforward and are entered as is.
*  #whoami simply returns the username of the current user.
* [username@ c3ddb01.mit.edu ~]$ whoami 
username

**Arguments** are given to some commands to specify what the command should do something to or with. Often arguments are filenames (that the command will work with) or text (that the command will use).
* #_echo takes an "argument" and returns it to the screen (stdout).
* [username@ c3ddb01.mit.edu ~]$ echo "Hello" 
Hello

**Options** instruct a command to perform a task in different ways. To use these expanded functions, you use the same command and specify different “options.” Options are usually preceded by a dash (-) or double-dash (–) if a full word is used.
* #_hostname returns the name of the system you are currently using. The -f "option" returns the full name.
* [username@ c3ddb01.mit.edu ~]$ hostname -f 
c3ddb01.mit.edu

Most commands have a manual page that can be accessed using the “man” command.

* [username@ c3ddb01.mit.edu ~]$ man hostname
Note: “q” quits the manual pager.