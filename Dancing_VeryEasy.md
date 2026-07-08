# Dancing Lab 
There are different ways to transfer files on a computer and one way is using SMB. SMB is a communication 
protocol that provides shared access to files, printers, and serial ports between endpoints. This protocol 
is most common on Windows machines and uses port 445. It runs at the application or presentation layer and
relies on lower level protocols for transportation. 

If SMB allows clients to create, edit,
retrieve, and remove files on a share, there is a clear need for an authentication mechanism. At a user level,
SMB clients are required to provide a username/password combination to see or interact with the contents
of the SMB share.Despite having the ability to secure access to the share, a network administrator can sometimes make
mistakes and accidentaly allow logins without any valid credentials or using either guest accounts or
anonymous log-ons.

You start by scanning the target to see all ports and versions that are currently open. 
-sV: Probe open ports to determine service/version info 

<img width="957" height="897" alt="image" src="https://github.com/user-attachments/assets/1cdf3cd9-970f-4771-9844-bd76274f2adf" />

Once you see that SMB is up and running, you can use a script called smbclient to enumerate share content
on the remote system. I installed it using the following command so that we were able to run the script. 

<img width="963" height="901" alt="image" src="https://github.com/user-attachments/assets/c9a8df75-621f-4358-b08b-3ee7049822e7" />

Since we are trying to access the target ip, I call the script we installed and use the target ip 
[-L|--list=HOST] : Selecting the targeted host for the connection request.

<img width="967" height="902" alt="image" src="https://github.com/user-attachments/assets/ac989d0c-a78b-4062-becf-65da7d0b3ab6" />

After running the command you are able to see that there are shares that we can potentially access. 
Listed below are the shares and their meaning to the system:

1. ADMIN$ - Administrative shares are hidden network shares created by the Windows NT family of
operating systems that allow system administrators to have remote access to every disk volume on a
network-connected system. These shares may not be permanently deleted but may be disabled.
2. C$ - Administrative share for the C:\ disk volume. This is where the operating system is hosted.
3. IPC$ - The inter-process communication share. Used for inter-process communication via named
pipes and is not part of the file system.
4. WorkShares - Custom share.

Since we do not have a password, we can try to enter null passwords to see if any of the shares were
misconfigured. We can see that not entering a password for WorkShares worked and we were able to get 
into the share

<img width="966" height="901" alt="image" src="https://github.com/user-attachments/assets/c6f6e5cb-b161-4a43-ace5-56f3b6a52172" />

We can enter "help" into the terminal to view what commands we can actually use. 

<img width="963" height="897" alt="image" src="https://github.com/user-attachments/assets/12031781-1a1d-4f3d-a9ca-8e76e0caa7f2" />

After we can then list what is in the current directory using the "ls" command. From here we see the Amy and James
directories, and we can go into them using "cd". once we go into both of them we can see each has a .txt 
file and we can download to our system using "get". After we can exit the smb client since we obtained the
two files. 

<img width="971" height="901" alt="image" src="https://github.com/user-attachments/assets/42acd220-0ae0-46a5-8f9d-9ca3bd8c28e1" />

Now that we have exited the smb client, we can list the files in our own directory to see the
flag.txt and worknotes.txt files we downloaded from the share we accessed. We can view the contents
using "cat" and we get the flag to complete the lab. 

<img width="966" height="900" alt="image" src="https://github.com/user-attachments/assets/5e23d279-fd23-4ca0-94f3-91ad86781b21" />

## Questions 
1. What does the 3-letter acronym SMB stand for? Server Message Block
2. What port does SMB use to operate at? 445
3. What is the service name for port 445 that came up in our Nmap scan? microsoft-ds
4. What is the 'flag' or 'switch' that we can use with the smbclient utility to 'list' the available SMB shares on Dancing? -L
5. How many shares are there on Dancing? 4
6. What is the name of the share we are able to access in the end with a blank password? WorkShares
7. What is the command we can use within the SMB shell to download the files we find? get
   
