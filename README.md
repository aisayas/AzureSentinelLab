<h1>Azure Sentinal HoneyPot Lab</h1>

 ### [YouTube Demonstration]()

<h2>Description</h2>
In this lab, I setup Azure Sentinel (SIEM) and connect it to a live virtual machine acting as a honey pot. We will observe live attacks (RDP Brute Force) from all around the world. We will use a custom PowerShell script to look up the attackers Geolocation information and plot it on the Azure Sentinel Map!
<br />


<h2>Tools and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Azure Sentinel</b>
- <b>Azure VMs</b>
- <b>ipgeolocation.io</b>

<h2>Environments Used </h2>

- <b>Windows 10 Pro</b> (22H2)

<h2>Program walk-through:</h2>
<p align="center">
Create VM and set firewall to allow all connections as well as a Log Analytics workstation for later: <br/>
<img src="https://i.imgur.com/RE3rpZr.png" height="80%" width="80%" alt="1"/>
<br />
<br />
Connect to the VM using Remote Desktop Connection:  <br/>
<img src="https://i.imgur.com/R0OYYPI.png" height="80%" width="80%" alt="Azure Sentinel Steps"/>
<br />
<br />
Create an ipgeolocation account to get an API Key:  <br/>
<img src="https://i.imgur.com/Z7fNDaD.png" height="80%" width="80%" alt="Azure Sentinel Steps"/>
<br />
<br />
On the VM, open Windows Powershell ISE and create log exporting script and run it:  <br/>
<img src="https://i.imgur.com/sqdXf5S.png" height="80%" width="80%" alt="Azure Sentinel Steps"/>
<br />
<br />
After running the script, the following log should be exported:  <br/>
<img src="https://i.imgur.com/bSuS1Vl.png" height="80%" width="80%" alt="Azure Sentinel Steps"/>
<br />
<br />
With each failed login attempt, the log should update (as well as the Windows Powershell ISE terminal) :  <br/>
<img src="https://i.imgur.com/Wm4c29H.png" height="80%" width="80%" alt="Azure Sentinel Steps"/>
<br />
<br />
Copy that log from the VM to your host machine and create a custom log in Azure Cloud named FAILED_RDP_WITH_GEO:  <br/>
<img src="https://i.imgur.com/T6oeysJ.png" height="80%" width="80%" alt="Azure Sentinel Steps"/>
<br />
<br />
Create a new querie under you Log Analytics Workstation to view the logs of your VM:  <br/>
<img src="https://i.imgur.com/b3LTohg.png" height="80%" width="80%" alt="Azure Sentinel Steps"/>
<br />
<br />
I added a few more lines of code to properly parse through the incoming data (such as longitude and latitude):  <br/>
<img src="https://i.imgur.com/cA2wwTb.png" height="80%" width="80%" alt="Azure Sentinel Steps"/>
<br />
<br />
Copy that log from the VM to your host machine and create a custom log in Azure Cloud named FAILED_RDP_WITH_GEO:  <br/>
<img src="https://i.imgur.com/T6oeysJ.png" height="80%" width="80%" alt="Azure Sentinel Steps"/>
<br />

 
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
