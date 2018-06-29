This page describes the filesystem structure on c3ddb as well as commands for basic navigation and file manipulation on the system. 

**Filesystem Structure:**

The Linux filesystem starts at the “**root**” (/) and extends forward into directories that can contain both subdirectories and files. A series of decending directories can be strung together separated by slash characters (“/”) to indicate a location on the filesystem. This string of folders is called a “**path**” and will look like _/project/projectname/subfolder/file._  This structure is much like that on other common operating systems. 

_/username_ : Each user has a “home directory,” this is the directory you are put in when you first log in each session.

_/scratch/users/username_ : Directory for jobs and intermediate files in stages of processing. In order to facilitate research projects, the scratch space has few limits placed on storage. However, it is not supposed to be used for long term storage. After processes are complete, data should be moved out of scratch space.  

Working with Files/Directories

Below are some simple examples of basic Linux commands for accessing and changing your files and directories. For all of these commands, you can run **man** _command_name_ to see the manual page (system documentation) on the command, including explanation of available command line options.

Show the current “full path”, the directory you are in with its parent and all levels of grandparents up to the root directory (/):

* C3ddb% pwd
* /usr2/collab/adftest2

Create a file:

C3ddb% touch _myfile_

This command will create a blank file named _myfile_. You will also want to be able to use an editor to create or modify an existing text file. A simple graphical editor to use is gedit, but more complex editors like emacs and vi are also available.

Create a new directory:

C3ddb% **mkdir** newdir

List the files, including other directories, in the current directory:

* C3ddb% **ls** newdir
* newdir

There are many options to the **ls** command such as **ls** **-l** to list the files in the current directory in “long” (verbose) format such as:
C3ddb% **ls -l** newdir
total 0
drwxr-xr-x 3 adftest2 adftest 512 Oct 28 16:03 newdir

The letters on the left (“drwxr-xr-x”) indicate the “permissions” of this file/directory. The “d” indicates that it is a directory. The next 9 characters indicate that is is “readable”, “writable”, and “executable” by you and “readable” and “executable” by both the members of your project group and the world. The commands you can use to change these “permissions” are chmod and umask.

Move and/or rename a File:

* c3ddb% **mv** _myfile newdir/newfilename_

This command will move the file _myfile_ into the directory _newdir_ and simultaneously rename it to be called _newfilename_.

Move to a different directory:

* c3ddb% **cd** _newdir_

Move to the newly created _newdir_ directory. You can also specify a “full path” (a path that starts with a /) such as **cd /usr/local/bin**. Typing just **cd** (or **cd .**) by itself will always take you to your home directory.

Copy a file:

* c3ddb% **cp** _newfilename filecopy_

This command will make a copy of _newfilename_ in the file _filecopy_. You can copy entire directories by using the **-r** (recursive) option.

Delete a file:

* c3ddb% **rm** _filecopy_
* rm: remove regular empty file `filecopy'? y

By default you will be asked to confirm that you want to remove a file by typing y when asked. You could avoid this by using the command line option **-f** but then you must be much more careful. Empty directories are removed using the command **rmdir** _directory_name_. Full directories can be removed by again using the **-r**(recursive) option to **rm**.