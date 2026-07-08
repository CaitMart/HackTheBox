# Meow 

You can take the IP address of your current target from the Starting Point
lab's page and paste it into your terminal after typing in the ping command as illustrated below.

<img width="1053" height="907" alt="image" src="https://github.com/user-attachments/assets/bb2b8deb-bdf1-4c77-b8b1-7405f26d13b1" />


In order to start the scanning process, we can use the following command with the
nmap script.Others might be non-standard, which is why we will be using the service detection flag -sV to
determine the name and description of the identified services. 

<img width="1054" height="910" alt="image" src="https://github.com/user-attachments/assets/ab1bb32d-05ec-454c-8c07-d2b1fa55ef61" />

telnet is an old service used for remote management of other hosts on the network. Since the target is running this service, it can
receive telnet connection requests from other hosts in the network (such as ourselves). Usually, connection
requests through telnet are configured with username/password combinations for increased security.

<img width="1053" height="910" alt="image" src="https://github.com/user-attachments/assets/a92ef9b5-685e-4d1e-b64a-128b3443507f" />

Sometimes admin accounts are left with default credentials or have no password attactched to it. You can 
brute force the login to see if any combinations work, which root did with no password 
<img width="818" height="591" alt="image" src="https://github.com/user-attachments/assets/8e7575f2-d5fe-43ee-bfd6-c4616bb46c82" />

you can list the files or folders in the current directory and from there read the flag.txt file by using
the cat command. From there  you get the hash that is the flag for the lab. 

<img width="1054" height="910" alt="image" src="https://github.com/user-attachments/assets/bb75999c-19c7-4494-95b2-e174799f0bfd" />


## Lab Questions 
1. What tool do we use to test our connection to the target with an ICMP echo request? Ping
2. What is the name of the most common tool for finding open ports on a target? nmap
3. What service do we identify on port 23/tcp during our scans? telnet
4. What username is able to log into the target over telnet with a blank password? root
5. Submit the flag located in root's home directory. flag was submitted!
