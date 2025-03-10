<h1>Active Directory Home Lab</h1>


<h2>Description</h2>
In this project, I built an Active Directory Home Lab environment using Oracle VirtualBox. I started by setting up a Domain Controller (DC) running Windows Server 2019, where I installed and configured Active Directory. This included setting up network adapters, IP addressing, and the domain. To enable internet access for clients on the internal network, I implemented NAT and routing through the DC. Additionally, I configured DHCP on the DC to automatically assign IP addresses to client machines.

To simulate a real-world enterprise environment, I used a PowerShell script to generate 1,000 Active Directory user accounts.

Next, I created a Windows 10 virtual machine to act as a client system within the lab. This machine was connected to the private VirtualBox network and joined to the Active Directory domain. As a result, it could authenticate and log in using any of the 1,000 user accounts created by the PowerShell script.


<br />


<h2>Tools Used</h2>

- <b>Active Directory</b> 
- <b>PowerShell ISE</b>
- <b>Oracle Virtual Box</b>

<h2>Environments Used </h2>

- <b>Windows 10 </b> 
- <b>Server 2019</b>

<h2>Walk-through:</h2>

<p align="center">
Set up an empty VM with no ISO installed. Navigate to settings and configure its network to have two network adapters. One will connect to the external public internet: <br/>
<img src="https://i.imgur.com/1uQj4La.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The other will connect to the internal private network.:  <br/>
<img src="https://i.imgur.com/5Y7Qb7w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install Server 2019 ISO on the VM: <br/>
<img src="https://i.imgur.com/EHzKDeE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to Settings > Network & Internet > Change adapter options. Then rename the network adapter that connects to the external internet “INTERNET”, then name the other adapter which will connect to the internal network “internal”:  <br/>
<img src="https://i.imgur.com/fsHfdB7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Assign internal an IP address and subnet mask. Assign the DNS server to a loopback address.:  <br/>
<img src="https://i.imgur.com/6ZH5d6M.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install Active Directory Domain Services:  <br/>
<img src="https://i.imgur.com/Q9gbuk5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a domain:  <br/>
<img src="https://i.imgur.com/0IxLS4k.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 Create and sign into a domain admin account:  <br/>
<img src="https://i.imgur.com/b6gJ04m.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
 Now we will set up routing and NAT to enable clients to connect to the internet through the Domain Controller. Install Routing and Remote Access on Server Manager:  <br/>
<img src="https://i.imgur.com/BTrlt7f.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure and enable Routing and Remote Access with NAT. Choose the network adapter you named INTERNET:  <br/>
<img src="https://i.imgur.com/zHSBTlt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next, Install DHCP on Server Manager:  <br/>
<img src="https://i.imgur.com/NHMfwBW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In DHCP, set your IP range and subnet mask:  <br/>
<img src="https://i.imgur.com/r6zDEvU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Use your DC’s IP address as the router and use your DC as a DNS server:  <br/>
<img src="https://i.imgur.com/ydBFrGw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open PowerShell ISE and run a script that generates 1000 random users.:  <br/>
<img src="https://i.imgur.com/4quRdiG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Go back to Oracle VB and create an empty VM called client. Navigate to settings and change its network adapter to connect to the internal network. :  <br/>
<img src="https://i.imgur.com/JmisgxJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install Windows 10 ISO:  <br/>
<img src="https://i.imgur.com/ZrhnTkc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
After installing Windows 10, add the client to your domain:  <br/>
<img src="https://i.imgur.com/ZurQdaN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
You can now sign into this client using any of the generated user accounts:  <br/>
<img src="https://i.imgur.com/GEbZy0t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
First user:  <br/>
<img src="https://i.imgur.com/9OJ13Tz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
