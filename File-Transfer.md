# File Transfer

To download/upload files from a local computer, there are a number of software options. [Cyberduck](https://cyberduck.io/) or the **SFTP** function of MobaXTerm will allow for user-friendly download/upload to local machines. 

Many researchers use publicly available datasets. To download directly onto c33db from the internet, you will have to login to a globus node and submit the download script.

`[username@c3ddb01@mit.edu/]$ ssh c3ddb-globus`

>        Last login: Wed Jul 25 12:33:18 2018 from login003.cm.cluster

The command **logout** will close the globus-node connection

`[username@c3ddb01@mit.edu/]$ logout`

>        Connection to c3ddb-globus closed.

Any process when downloading/uploading to c3ddb is best done through an ethernet connection instead of wifi. When downloading with the globus node, think carefully about how much data actually needs to be downloaded at once. It is helpful to batch jobs, so that resources on the globus node are not used for extended periods of time. 

It is also important to note that while HPC is an excellent resource for large datasets, downloading/uploading data may be a time consuming process. 