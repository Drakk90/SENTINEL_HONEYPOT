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

As mentioned above, we can go step by step or we can go ahead by creating our Log Analytics Workspaces. Once inside we click on the Create button.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image10.jpg)

We select our Resource group, name our instance and select the same region we have been working in for our example case West US 3.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image11.jpg)

Here we go, click on the create option and wait.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image12.jpg)

We take our first steps through Sentinel to start working the environment.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image13.jpg)

We are heading to Defender Plans. And Check proceed to give check on Servers if is off.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image14.jpg)

Then we go to Data Collections and click on the option All Events

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image15.jpg)

Look for the Virtual Machines (deprecated) option and double click on it.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image16.jpg)

We connect our machine.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image17.jpg)

It is time to connect to our virtual machine, if you do not know the public IP used, go to the virtual machines section where you can get it.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image18.jpg)

When you log in for the first time, turn off all privacy settings that come with Windows by default. In other words click NO for each of the features and then click Accept.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image19.jpg)

Go to Windows Firewall and turn everything off.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image20.jpg)

Download the ipgeo_ps.ps1 file from the following address.  
 - https://github.com/Drakk90/SENTINEL_HONEYPOT/blob/main/src/ipgeo_ps.ps1
 - Run Power Shell ISE as Administrator, open the newly downloaded file, modify the file by inserting your API key created earlier. Click on the RUN option and watch the magic.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image21.jpg)

As a last step proceed to run Command Prompt on your local machine and verify that you have PING.
 
![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image22.jpg)

By this time your Log Analytics is already created, go to the Tables section.
 
![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image23.jpg)

Click on the Create option, select the New Custom log (MMA-Based) option.
 
![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image24.jpg)

Enter the name of the log, which is being captured in the virtual machine, the name of the file can be found in the file with extension *.ps1
 
![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image25.jpg)

Select the Operating System and enter the path to the file and the file name, please remember this is Case Sensitive so enter it exactly the same.
 
![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image26.jpg)

Give a name to the custom log.
 
![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image27.jpg)

For this proof of concept we are capturing all events of type 4625, if you go to your Event Viewer inside your virtual machine you will be able to check this.
 
![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image28.jpg)

Wait about 10 minutes while your newly created log is displayed in Analytics and run the log you just created.
 
![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image29.jpg)

Some time ago there was the option to make extracts from a log, but that option disappeared, so now we proceed to do it through a query. You can find the query at the following address.
 - https://github.com/Drakk90/SENTINEL_HONEYPOT/blob/main/src/IPGeo_Sentinel.sql
 - Run the query on Analytics.
    
![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image30.jpg)

We go to Microsoft Sentinel and click on the Workbooks section.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image31.jpg)

We edited our Workbook.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image32.jpg)

Remove all elements of the workbook.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image33.jpg)

We paste our previous query.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image34.jpg)

We enter Map Settings and modify some of our elements taking as reference the image shown below.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image35.jpg)

We continue with our settings.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image36.jpg)

Save as.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image37.jpg)

Set the Autorefresh every 5 minutes.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image38.jpg)

We wait a few hours and the results will be as shown below.

![VIRTUALMACHINE](https://raw.githubusercontent.com/Drakk90/SENTINEL_HONEYPOT/main/images/image39.jpg)


## [!] Disclaimer
***This manual is designed to help creating your first project on Azure Sentinel and create your virtual Machine, please remember delete all the created instances on Azure if you want to avoid problems with your monthly billing.***

### This repository is open source to help others. So if you wish to copy, consider giving credit!

## Credits:
Some base codes and templates are from [Josh Madakor](https://github.com/joshmadakor1).

## [~] Find Me on :

- [![Github](https://img.shields.io/badge/Github-Drakk90-purple?style=for-the-badge&logo=github)](https://github.com/Drakk90)

- [![Gmail](https://img.shields.io/badge/Gmail-Drakk90-green?style=for-the-badge&logo=gmail)](mailto:erecinos@gmail.com)

- [![LinkedIn](https://img.shields.io/badge/LinkedIn-Drakk90-blue?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/eduardo-recinos)
