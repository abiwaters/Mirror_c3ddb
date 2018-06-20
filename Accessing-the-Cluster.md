All access to the c3ddb is done through SSH (Secure SHell) client. SSH instructions will vary based on your operating system, but all systems will require your private SSH key downloaded when you submitted a request and your passphrase. 

Connecting to the SCC from Microsoft Windows
There are multiple SSH clients available for Microsoft Windows, each will connect to the SCC using the same protocol. These instructions are based on MobaXterm because this application provides functionality you may find useful for other tasks.

**Using MobaXterm to Connect to the SCC:**
1. Download and Install [MobaXterm](https://mobaxterm.mobatek.net/download-home-edition.html). You can also watch this [MobaXterm Demonstration Video](https://mobaxterm.mobatek.net/).
2. Launch MobaXterm and start a “New Session”:
3. Select “SSH” as the session type:
4. Specify “c3ddb01.mit.edu” as the remote host and click “OK”:
5. Your connection will be saved on the left sidebar, so the next time you can start your session by clicking the “c3ddb01.mit.edu [SSH]” link. In the terminal window you will get a prompt to enter your login information and password _(Note that the characters in your password will not be displayed when you type them as a security precaution):_
 
6. Alternatively, open the MobaXterm terminal and type:                     
ssh -i ‘PATH-TO-\c3ddb-key.ppk' -l USERNAME c3ddb01.mit.edu
7. Enter passphrase when prompted.
 
Connecting to the SCC from Apple OS X
The Secure SHell (SSH) is built into the Apple OS X operating system. To connect to the SCC, we will leverage this utility using the Terminal application.
Using Terminal to Connect to the SCC
Open the Terminal application, which is found in Applications >> Utilities >> Terminal. Alternatively, press <command> and <space> simultaneously to open Spotlight, search for Terminal and press <return>.
In the terminal, type ssh username@ c3ddb01.mit.edu.
Enter your passphrase when requested. Note that the characters in your password will not be displayed when you type them as a security precaution. 
Type exit in the terminal when you are done working on the SCC.
Connecting to the SCC from Linux
The Secure SHell (SSH) is built into the Linux operating system. To connect to the SCC, we will leverage this utility using the Terminal application.
Connecting to the SCC
Open a Terminal. This can be done by opening the terminal application in Systems >> Accessories >> Terminal or by using the hot-key Ctrl + Alt + T
Use ssh to connect to the SCC with your login credentials, using a command similar to this example:
your_local_machine% ssh yourLoginName@ c3ddb01.mit.edu
Enter your passphrase when prompted. Note that the characters in your password will not be displayed when you type them as a security precaution.
When finished, type exit to close the session.
