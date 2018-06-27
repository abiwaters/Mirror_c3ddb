**My institution is not an option when I try to request access:**

You should communicate with your organization's information technology services or resources for high performance computing. If your organization does not already have an existing agreement with MGHPCC, they may be able to facilitate one. 

**My SSH key is not working:** 

First, make sure you are using the private key (ends with .ppk) and not the public key. 
Next, make sure that the read permissions are set appropriately with  
[username@ c3ddb01.mit.edu ~]$ chmod 777 SSHKEY.ppk
  
**I lost my passphrase or SSH key:** 

If you have forgotten your passphrase or deleted your SSH key, you will need to contact System Admins and generate a new private SSH key. Based on your operating system, this will differ. 
Once you have generated a new one, System Admins will be able to assist you in resetting your password. 

**Collaborators cannot view my output:**

Consider making a publicly readable folder by changing the permissions. You can move the information you want public into that folder and other users on the cluster will be able to read it. Do not share your log-in information with other users.

 
