# Lab 3: NMAP

## Section 1

Nmap Ping scan  



Figure 81- Output of the ping Scan



Single Host Scan 



Figure 82 -Single Host Scan Output



Multi host scan 



Figure 83 - Output of multi Host scan

Subnet Scan 



Figure 84 - Output of Subnet Scan



The output for most scans shows the host is up, the amount of closed ports, name of open ports and the mac address. Below is a table containing the differences between each scan.



| Ping Scan | Single Host | Multi Host | Subnet |
| --- | --- | --- | --- |
| Used to check if host is up | Used for scanning 1 host at a time | Good for scanning multiple Hosts at once | Must add the subnet at the end of the IP address |
| No port scan | Scans ports | Scans ports | Scans ports |

## Section 2

TCP Connect scan



Figure 85 - Output of TCP Connect Scan



SYN scan



Figure 86 - SYN Scan



Port Range SCAN



Figure 87 - Output of Port Range Scan



Scan Specific ports 



Figure 88 - Scan Specific Ports



## Comparison Table

| TCP Connect Scan | SYN Scan | UDP Scan | Port range scan | Scan Specific Ports |
| --- | --- | --- | --- | --- |
| sT | sS  | sU | P  | P- |
| Faster than SYN but more detectable | Slower Than TCP but more stealthy | Used for discovering  UDP Ports | Used to define a range of ports to scan | Used to scan specific ports |



## Section 3 -Software Version detection



Figure 89-Software Version Detection Output



## Section 4 – Operating system detection



Figure 90- OS Detection Output



## Section 5 – Aggressive Scan



Figure 91 - Aggressive Scan



## Section 6:

1: Vulnerability Script 

to check for weaknesses in a systems configuration:



Figure 92 - Output of vulnerability Script





Figure 93 - Output of vulnerability Script

2: Specific Script by Name

Runs a http-enum script for listing common web directories, open ports, paths or apps on a http service



Figure 94 - Output of specific Script



3: Combine Version and OS Detection

Combines service detection, OS detection and the default NSE Script to give a more detailed scan that gathers service info and runs common safe scripts for more detail



Figure 95 - Output



## Section 7: Output Options

1: Save Scan results to text file

Saves the output of scan results to output.txt so it can stored for later use



Figure 96 - Output.txt Output

2: Saves output results as a xml file



Figure 97 - Output Results XML FILE



3: Saves Output in a Greppable Format 

Used for quick filtering or scripting



Figure 98 - Greppable Format Output



## Section 8: Advanced Scanning Techniques

1: Avoid Firewall Detection (Decoys)

Uses decoys by adding random spoofed addresses to hide the real source of a scan



Figure 99 - Decoys Output



2: Fragmentation

Used to avoid packet filters



Figure 100 - Avoid Packet filter



3: Spoof Mac Address

Used to disguise a scanner’s network identity (ERROR)



Figure 101- Spoof Mac Address output



4: Randomize Host Order

Disable random port order for predictable scanning



Figure 102 - Randomize Host order Output



5: Idle Scan (Stealthy and Spoofed)

(ERROR)



Figure 119 - Nmap idle scan error output



6: Timing Options

(Sets up a faster timing template to speed up scans on reliable networks but this increases noise and the risk of missed results



Figure 103 - Timing Options Output



## Section 9: Other Useful Commands

1: Trace Route

Performs a Trace Route to the target and is used for seeing the path a packet travels through



Figure 104 – Trace Route Output



2: IPV6 Scanning



Figure 105 - Output of ipv6 Scanning



3: Scan using TCP ACK Packets

Used for mapping firewall rules and determining if ports are filtered instead of finding open ports directly.



Figure 106 - TCP ACK Packets



4: Scan Only hosts with Open ports

Used to find Hosts that Host Services



Figure 107 - Output of hosts with open ports



## WEEK 3 Lab: SSH 

Secure Shell Host is a protocol that secures communications with another system over an unsecured network by encrypting all transmitted data to prevent any sensitive data from being intercepted.



## Section 1: SSH Connection Basics

1: Connect to a remote server using ssh 

This is used to remotely control a remote server from your local machine using the remote servers ip address and logs in as a user that is already registered on the host machine. The output shows a successful login and information about the remote server. In the terminal the name of the user has changed from kali@kali to student@wordpress.



Figure 108 - ssh output



Specify A port:



Figure 109 - Output for port 22



## Section 2: SSH Authentication and Key Management

Generate a 4096-bit RSA SSH key pair 

Enables logging in without a password. The output shows SHA256 encrypted key has been created and saved.



Figure 110 - Output of key Generation



Copy public key to remote server 

Used to login without password on the remote machine. Output shows the key was successfully copied.



Figure 111 - Copy Key to remote server



Passwordless Login



Figure 112 - No Password Login



## Section 3: Managing SSH SESSIONS

Log out using the “exit” command

### Output shows the username has reverted to kali@kali



Figure 113 - Log out output



Remote commands 

Used to log into the remote server using ssh and execute “ls -la” to list files in the student users directory.



Figure 114 - Ls-la SSH Output



## Section 4: File Transfer With SCP

Copy a File from Local to Remote 

Uses Secure Copy Protocol to copy files.txt from the local machine to the specified remote directory using ssh to ensure transferred data is encrypted. The output shows the file has been located and transferred to the remote directory



Figure 115 - SCP Output









Copied file.txt to the remote directory



Figure 120 - SCP upload of file.txt to the remote Documents directory



Copy from remote to local



Figure 121 - SCP command to copy a file from the remote server to the local machine



### Output the file has been copied to kali



Figure 122 - Local Documents folder showing the file copied from the remote server



## Section 5: Secure File Transfers with SFTP

Connect to a Remote Server using SFTP 

SSH file transfer protocol is an alternative to SCP where you can do CRUD operations directly from the terminal and is reliable alternative to scp if the connection is unstable. The output shows we have successfully connected to the remote server using SFTP



Figure 123 - SFTP connection established to the remote Ubuntu WordPress server



SFTP LS 

Lists the file on the remote machine



Figure 124 - SFTP ls output listing the documents directory on the remote server

Download a File from the Remote Ubuntu Wordpress server with SFTP 

Using the get command along with the working remote directory path of the file we want to download



Figure 125 - SFTP get command downloading file.txt from the remote server



### Output of the file we copied from the remote server to kali



Figure 126 - Downloaded file shown in the local Documents folder



### Comparison between STFP and SCP

| SFTP | SCP |
| --- | --- |
| Best used if connection is unstable | Best used with a stable connection |
| Do commands inside the terminal | Do commands outside the terminal. |
| Used to manage Files remotely | Used to copy files from one host to another. |



## Section 6: Tunneling with SSH

Local Port Forwarding on Port 8080 to Remote Host Port 80 using the -L flag 

Used for securing port forwarding methods by tunnelling TCP/IP packets through a SSH link to make the data obscure and protecting the link from attacks.



Figure 127 - Local port forwarding from local port 8080 to remote host port 80



Remote Port Forwading using the -R flag 

Requests on remote server port 9090 should be forwarded to local host at port 80. If we make a request to the server on port 9090 you would get a reply from local host



Figure 128 - Remote port forwarding from remote port 9090 to local host port 80



## Section 7: MultiPlexing and Persistent Connections



MultiPlexing and Persistent connections (This command creates a persistent connection 60 seconds after the session ends)



Figure 129 - SSH multiplexing command using persistent connection options



### Output



Figure 130 - Output of the multiplexed persistent SSH connection



## Section 8: Advanced SSH Options

Logging in with a different key 

Connects using a specified private key file instead of the default key



Figure 131 - SSH login using a specified private key file



SSH Debug (Verbose Mode)

Enables verbose mode and verbose output which can be used for diagnosing issues



Figure 132 - Verbose SSH session output used for debugging





Figure 133 - Additional verbose SSH debug output during the session

Logging out in verbose mode (Prints out how many bytes were used and exit status before closing the connection)



Figure 134 - Verbose logout output showing bytes transferred and exit status



### Difference between verbose mode and Normal Mode

| Normal SSH Mode | Verbose Mode |
| --- | --- |
| Only prints out the results of the connection attempt. | Prints debugging information such as port number used, file path of the pubkey. |
| Only prints “logout” when logging out. | Prints how many bytes were used every second and the exit status when logging out. |
| Used for logging in. | Used for Identifying bugs in SSH Configuration. |



Limiting Bandwith speed with SCP



Figure 135 - SCP bandwidth limiting command output



Lab 3 Reflection

Lab 3 has taught how Nmap is used to identify live machines, scanning ports, detecting the OS a machine is using and creating custom scripts to detect vulnerabilities or check performance. Using every scan type has revealed that no scan is perfect, but each scan is built for a specific purpose as each scan involves a trade-off between coverage, speed, stealth and the required access level like the Syn scan which is faster and stealthier than the TCP scan, but the downside is that it requires root access. The NSE Vulnerability script revealed that NMAP could be converted from a reconnaissance tool, into a vulnerability scanner that returned findings including exposed WordPress paths, potential CSRF Vulnerabilities and username Enumeration which compliment the WPscan exercise very well.



Strengths and Weaknesses

Nmap NSE Scripting capabilities makes it highly adaptable as this port scanner can run targeted checks for CVE’s, enumerate http directories or test database configurations. The range of output formats makes it suitable for both manual review and automatic pipeline integration. Nmap becomes unreliable when firewalls are active on the target machine due to ports becoming filtered and being unable to detect the Operating System. This suggests that Nmap’s effectiveness depends on the network environment and should not be treated as the ultimate tool in securely configured networks.


