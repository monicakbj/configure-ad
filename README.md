# configure-ad
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create VM's foer Windows server 2022 and Windows 10
- Downloading Active Directory
- Restart 
- Disable/Enable/Passwords

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/BlcmGFd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
You will log in to microsoft azure and create a resource group and two virtual machines. One virtual machine will be the domain controller using windows server 2022, and the other virtual machine will be using windows 10. You will have to make sure to set the NIC in the domain controllerprivate IP address to static. By clicking on networking, then click on the number and letters that are highlighted next to network interface. Then select IP configurations and scroll down to IPconfig1 and click on it. Scroll down to assignment, click on static and save.
</p>
<br />

<p>
<img src="https://i.imgur.com/GSK8QPb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log into domain controller through remote desktop connection the server manager screen should be up. Go to add roles and features to install active directory domain services and add features and click install. The software should now be installed and then click close a yellow hazard sign with an exclamation click on this and it should say "promote this server toa domain controller". By clicking this it now turns the server into the domain controller this finishes the installation. Add a new forest and choose your domain name with ".com". The system will log you off once the installation is complete so you must use remote desktop connection to reconnect to the domain controller windows 2022 by utilizing your domain credentials that you set up.
</p>
<img src="https://i.imgur.com/t0hqomV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/R3IiOD1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now when you are able to log in, go to tools click on active directory users and computers to create an admin user and organizational units. Click on your domain name click on new after that click organizatinal unit to create your folders. Next you are going to join windows 10 vm to our domain controller by setting windows 10 DNS settings to our DC private IP address and then we will restart windows 10 vm.
<p>

<img src="https://i.imgur.com/WGJHHLn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/WDc2uxv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to windows 10 vm> networking> click network interface> DNS servers> click custom. Now place in the DC private IP address and save, afterwards go to overview in your windows 10 vm and press restart. Log in to windows 10 vm with its new DNS settings by using remote desktop contoller.

</p>
<p>
<img src="https://i.imgur.com/Et4u2zP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now will join windows 10 to DC server by going to settings> system> about> rename this PC(advanced)> change> domain. This will restart and be joined with the domain account. Log back into windows 10 vm using your domain login credentials. 
<p>
</p>
<p>

<img src="https://i.imgur.com/AWFUSIT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<img src="https://i.imgur.com/A6aj7SA.png" width="80%" alt="Disk Sanitization Steps"/>
</p>

For you to allow other domain users to utilize your domain you must go to settings> about> remote desktop> select users that can remotely access this PC and add names. You can log out of your windows 10 vm and try to log in now using one of the users credentials that you may have set up. If an account becomes locked click on the  user name> properties> account> unlock account. You can unlock password/ disable account/ reenable account/ and reset password for this tab.
</p>
<br />
