CONTACT FOR SYSTEM ADMIN: c3ddb-admin@techsquare.com

**My institution is not an option when I try to request access:**

You should communicate with your organization's information technology services or resources for high performance computing. If your organization does not already have an existing agreement with MGHPCC, they may be able to facilitate one. 

**My SSH key is not working:** 

First, make sure you are using the private key (ends with .ppk) and not the public key. 
Next, make sure that the read permissions are set appropriately with  
`[username@ c3ddb01.mit.edu ~]$ chmod 777 SSHKEY.ppk`
  
**I lost my passphrase or SSH key:** 

If you have forgotten your passphrase or deleted your SSH key, you will need to contact System Admins and generate a new private SSH key. Based on your operating system, this will differ. 
Once you have generated a new one, System Admins will be able to assist you in resetting your password. 

**Collaborators cannot view my output:**

Consider making a publicly readable folder by changing the permissions. You can move the information you want public into that folder and other users on the cluster will be able to read it. Do not share your log-in information with other users.

**What is the space limit for home directory and scratch space?**

User home directory space is limited. It is intend for users to save their code, documents and small tests and it is not for large data storage.

The scratch space is for storing computational data and it is on a much faster Lustre system. Since the space is shared among all cluster users, please be considerate and clean up your unwanted or unneeded data as often as you can.

**How much memory is on each node?**

It depends on which partition you are requesting. Be aware of the specific needs of your jobs and only request what you need. 

**What is the time limit for job runs?**

Depends on the partition. Some partitions may offer 12 hours for normal job run and 15 minutes for a quick test. Others may offer different times. Sometimes special arrangements can be made depending on the requirements.

**Can I log into the computing nodes?**

Users can only log into a compute node if the users owns a job running on the node.
