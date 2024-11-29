<h1>Networking</h1>

<h2>Description</h2>
Creating a workplace network environment using VM's. 
<br />


<h2>Scripting languages & Platform</h2>

- <b>PowerShell</b>
- <b>VirtualBox</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Walk-through:</h2>

<p align="center">
The Goal of this project is to create simulated workplace environment. With a private domain, NAT and DHCP that allows thousands of users connection to the internet and managment in active directory: <br/>
<img src="https://imgur.com/tkNhRhA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We use the password we created to access our admin account after installing VirtualBox and setting up our primary domain controller:  <br/>
<img src="https://imgur.com/fE6RtSI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We name our home router as the "internal" internet for our simulated workplace network: <br/>
<img src="https://imgur.com/VZ1m6j4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Fill in IP Adress, Subnet mask, and DNS based on workplace requirements:  <br/>
<img src="https://imgur.com/5MYRe5Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
To manage our users we need to install active directory:  <br/>
<img src="https://imgur.com/CcgKnT1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install active directory:  <br/>
<img src="https://imgur.com/fftBKvP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The alert sign indicates we are missing a domain, click it:  <br/>
<img src="https://imgur.com/JsXWZaG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Name and configure domain:  <br/>
<img src="https://imgur.com/qtqobp7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/QpwZUB6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br />
<br />
After installation your DC should show the name of your primamry domain:  <br/>
<img src="https://imgur.com/z1wZh0x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Let's create a main admin account in our DC (to simulate the head of IT in a workplace environment) Start by creating an Admin OU in Active Directory:  <br/>
<img src="https://imgur.com/9DiMCDR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Right click the new "ADMIN" OU and create a new user, prefix "a-" to indicate admin user:  <br/>
<img src="https://imgur.com/2VLipeG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/RB84Tgj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br />
<br />
After creating account right click on propertis and give admin priviledges by adding user is Domain admins group:  <br/>
<img src="https://imgur.com/KGBVFiH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/UNqC2bg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://imgur.com/cwlKRP8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sign in with new user credentials:  <br/>
<img src="https://imgur.com/EkOfUvg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install remote adressing to configure NAT that allows our clients access to the internet through our private IP address:  <br/>
<img src="https://imgur.com/1GhNEZu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After setting up remote addressing install NAT:  <br/>
<img src="https://imgur.com/Xk4woKV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Green arrow pinting up indicates NAT has been installed:  <br/>
<img src="https://imgur.com/iyzd1Xc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install DHCP to give clients public IP addresses to browse the internet:  <br/>
<img src="https://imgur.com/DVgJbjy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Set scope for DHCP, the range of IP addresses your clients can recieve:  <br/>
<img src="https://imgur.com/PHrGNLI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Set Scope...: <br/>
<img src="https://imgur.com/RPxwLZZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Complete DHCP configuration: <br/>
<img src="https://imgur.com/FQahXFh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 Utilized Script:  <br/>
<img src="https://imgur.com/76QG10U.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
All users will use "Password1" as Password: <br/>
<img src="https://imgur.com/PFVdM6Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Utilize auto-generated names in file "names.txt. to created user list:  <br/>
<img src="https://imgur.com/3CiROsg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
"ConvertTo-SecureString" converts the plain text password users input (Password1) into an "object" PowerShell can use during user creation:  <br/>
<img src="https://imgur.com/6lmvSmw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Creates a new "folder" in active directory Called USERS, unticks prevent accidental deletion box:  <br/>
<img src="https://imgur.com/A6ygND7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Loop: will run following code for all new users accounts created:  <br/>
<img src="https://imgur.com/OHkk1Fm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Splits the full name into first(name) and last(surname):  <br/>
<img src="https://imgur.com/laJAB2r.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Takes first character on first(name) adds it to last(surname) in lowercase:  <br/>
<img src="https://imgur.com/rZsG0qX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Creates new users in active directory: <br/>
<img src="https://imgur.com/EYKtigq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Execute script and check new users: <br/>
<img src="https://imgur.com/jm1f1lm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
With our client we ping Goolge and our domain to see if our networking works, we recieve replies on both: <br/>
<img src="https://imgur.com/9nEPksy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
