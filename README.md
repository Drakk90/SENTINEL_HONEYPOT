<h1 align="center">Sentinel HoneyPot</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Version-1.0-green?style=for-the-badge">
  <img src="https://img.shields.io/github/stars/Drakk90/pyphisher?style=for-the-badge&color=orange">
  <img src="https://img.shields.io/github/forks/Drakk90/pyphisher?color=cyan&style=for-the-badge&color=purple">
  <img src="https://img.shields.io/github/watchers/Drakk90/pyphisher?color=cyan&style=for-the-badge&color=purple">
  <img src="https://img.shields.io/github/issues/Drakk90/pyphisher?color=red&style=for-the-badge">
  <img src="https://img.shields.io/github/license/Drakk90/pyphisher?style=for-the-badge&color=blue">
<br>
<br>
  <img src="https://img.shields.io/badge/Author-Drakk90-purple?style=flat-square">
  <img src="https://img.shields.io/badge/Open%20Source-Yes-cyan?style=flat-square">
  <img src="https://img.shields.io/badge/Made%20in-Guatemala-green?colorA=%23ff0000&colorB=%23017e40&style=flat-square">
  <img src="https://img.shields.io/badge/Written%20in-PowerShell-blue?style=flat-square">
</p>


<h1 align="center">Steps to Follow</h1>
 - Main idea is the deploy of a HoneyPot with Visualization in Azure. 
 - Deploy a virtual machine in Azure leaving it unprotected on purpose to be seen by any attacker.
 - Run PowerShell ISE Script to be used inside the virtual machine to detect attacks.
 - Log Analytics WorkSpace where we will tell it which is the machine we want to extract the data and where the logs are located.
 - Run the query to be used on Sentinel within the Analytics Workspace.
 - Deploy SIEM within Azure Sentinel.
 - Review of the attacks received in Azure.


<h1 align="center">Sentinel Honey Pot</h1>

![Sentinel](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/Sentinel.svg)


## [!] Let's go...
As a first step we will create an account within ipgeolocation. Once created, we access the dashboard where the API Keys section will appear, which is what we will copy later to our script inside the virtual machine in Azure.
Go to https://app.ipgeolocation.io/login

![IPGEOLOCATION](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image01.jpg)

 - If you do not have a Microsoft Azure account go to the following address. https://portal.azure.com/
 - Microsoft will welcome you with an initial credit of $200.00, which is valid for 30 days (Friendly reminder, always remember to delete your labs).

Follow the instructions shown in the following images.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image02.jpg)

For this exercise remember to set a very strong password with a strong complexity.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image03.jpg)

Leave the default values until you reach the Networking section.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image04.jpg)

Once in the networking section, click on the NIC network security group section and select the Advanced option. Click on the create new option.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image05.jpg)

In the Create a Network Security Group section, enter the name of the group as you want it. In the Incoming Rules section delete the incoming rule you will see there.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image06.jpg)

It is time to create an inbound rule, for this purpose, in the Destination port ranges section we will place asterisk (*). In the Priority section we will put 1000 and in the Name section we will give the name to the rule as we want it to appear.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image07.jpg)

This is how our newly created rule should look like.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image08.jpg)

Finally we will create our virtual machine and we can wait or continue with the next section while it is up.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image09.jpg)




## [!] Disclaimer
***This manual is designed to help creating your first project on Azure Sentinel and create your virtual Machine, please remember delete all the created instances on Azure if you want to avoid problems with your monthly billing.***

### This repository is open source to help others. So if you wish to copy, consider giving credit!

## Credits:
Some base codes and templates are from [Josh Madakor](https://github.com/joshmadakor1).

## [~] Find Me on :

- [![Github](https://img.shields.io/badge/Github-Drakk90-purple?style=for-the-badge&logo=github)](https://github.com/Drakk90)

- [![Gmail](https://img.shields.io/badge/Gmail-Drakk90-green?style=for-the-badge&logo=gmail)](mailto:erecinos@gmail.com)

- [![LinkedIn](https://img.shields.io/badge/LinkedIn-Drakk90-blue?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/eduardo-recinos)
