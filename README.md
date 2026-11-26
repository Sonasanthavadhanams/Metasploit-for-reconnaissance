# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:

<img width="1456" height="1088" alt="Updated terminal username – 26 Nov 2026, 8 59 am" src="https://github.com/user-attachments/assets/f17c6858-38fe-4503-982a-9a7010745c24" />

Invoke msfconsole:
## OUTPUT:

<img width="1680" height="944" alt="Updated terminal username – 26 Nov 2026, 9 02 am" src="https://github.com/user-attachments/assets/7388f79f-0876-43a5-b197-050edc10f35f" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:

<img width="1920" height="922" alt="image" src="https://github.com/user-attachments/assets/1512409c-5043-41fa-8e53-32f85f9e6b0c" />


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="956" height="443" alt="image" src="https://github.com/user-attachments/assets/3ef9806d-88b5-4536-9e29-e95d877a4daf" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="1456" height="1088" alt="Updated terminal username – 26 Nov 2026, 9 04 am" src="https://github.com/user-attachments/assets/199d63c6-2be8-4663-8241-af4566803844" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="1920" height="923" alt="image" src="https://github.com/user-attachments/assets/f1809e71-89ac-4fe7-b0dc-de783339d00e" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="1920" height="923" alt="image" src="https://github.com/user-attachments/assets/be2893a4-3b8d-44db-aed2-f3743deeb2d4" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="1071" height="206" alt="image" src="https://github.com/user-attachments/assets/b0d094c5-89f5-4071-95e5-0cc4bd8cb453" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="1707" height="682" alt="image" src="https://github.com/user-attachments/assets/f31f9852-9746-4457-af35-2d3d504a4747" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="796" height="433" alt="image" src="https://github.com/user-attachments/assets/cb54dc20-c5e9-40c9-b85e-b18507d38fad" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="897" height="147" alt="image" src="https://github.com/user-attachments/assets/7fc56108-c03c-4aef-8c1b-09106f8185ed" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="1517" height="675" alt="image" src="https://github.com/user-attachments/assets/41dabb38-37e2-458b-be56-e4f783796986" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:



<img width="1028" height="921" alt="image" src="https://github.com/user-attachments/assets/e2546fae-1078-4eba-af87-a8584946b798" />



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
