# School-cloud-mini-project

# Sentinel SIEM

 ### [I am also doing Security Awareness](https://www.facebook.com/profile.php?id=100086563703368&mibextid=ZbWKwL)

<h2>Architecture:</h2>

![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/81f28326-239c-434f-8fcb-dccfbf313cdb)
 

Performing the lab.
1.	Create an Azure account (it can be free or pay as you go)
 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/fa36d5ab-48d0-48be-b3a3-c154a3b8e905)

So, you sign up using your Microsoft account or if you do not have, create one and proced
 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/81268f44-6e41-4859-9797-baadbea8d4aa)

After signing up you navigate to this https://portal.azure.com and it will look like the following:
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/6e5e714a-5360-4a8f-a012-4612efdb9903)


<h2>2.	Create the virtual machine (windows virtual Machine) that we named in our case Honeypot-VM</h2>

 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/9ed48b5b-74c7-481b-8816-6051dd50695b)

Virtual machine overview
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/7493499f-9d4b-4e4b-9730-0096c2b5daae)


We have created inbound traffic rule in such as away that we make the machine very vulnerable. It will be visible and any one can interact with.
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/588f4f65-bba9-4a92-a7e5-8a29467f6efe)
 

Use remote desktop (RDP) to connect to the virtual machine. To do so you just need to copy the public ip of the VM.
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/18791348-eb44-4c10-877d-46055005d020)

 
Paste the ip and provide the VM’s username and Password and you are good to go.
 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/9acc3d25-6c37-4b6a-9770-8fca0c10c1ed)


We then disable the VM’s Firewall

 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/100c2fc8-f88f-4d4d-af84-44771e65fe1b)


<h2>3.	Create Log analytics workspace</h2>

![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/84dba91a-c309-402e-bb4e-ce0081b35cf4)


![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/c89fd770-2c49-423b-9e1f-d723104613e8)

 
 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/1defaa98-cdfb-4f31-b8bd-bb496905adb8)

 

<h2>4.	Go to Microsoft Defender for cloud enable the defender plan giving the ability to gather the logs</h2>

•	Enable the plans
 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/c5d85d8d-49b3-4b62-af09-3f8ba4b529b1)

•	Selected the collection options
 
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/924e66ad-5152-413e-b8e4-e14bfdbf989d)

 
<h2>5.	Go to log analytics workspace to connect the virtual machine.</h2>
   
 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/b7402f70-0be4-4493-878b-043b9ec31251)

The screenshot below indicates that it is connected successfully.
 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/f7d5728e-6774-40d8-960f-8d1def5e9132)

<h2>6.	Setting up Microsoft sentinel the SIEM tools that will be used to visualize the attack data.</h2>
Here we added our workspace that we create previously in the sentinel. 

![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/bacce1eb-4c59-4538-902c-93dc3fc4ecb6)


<h2>7.	Open the PowerShell ISE in the VM, paste and run the log exporter:</h2>

1.	First sign up to ipgeolcation site (https://app.ipgeolocation.io/) and the API Key that will be used in the PowerShell code.
The idea behind the ip_geolocation api key is to customize the collected the RDP login attempt in the following format:

 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/4dea8f3e-8e9e-4be4-9ce0-3fbb6c4d4c29)


so, once login to ipgeolocation.io we go to the dashboard and copy the API that will be paste in the PowerShell code:
 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/68807bc3-46ef-4736-899c-dcd1ad44c465)

2. Now, incorporate the API key and run the PowerShell code to programmatically collect the failed RDP log and save it into a file that we can name “failed_rdp.log” and will later on used it to train the Microsoft Sentinel.
 
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/2320bad4-e2c0-4854-8f73-909279045264)

The content of the failed_rdp.log saved:
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/e27a8bde-0328-4331-a7d3-3ff840650a3c)

 
8.	Custom log creation and training
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/3a685ef9-3668-4a82-9b1d-4089fb7a2c23)
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/d731a080-058f-4710-8e2a-8b8a201002f5)
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/86f22eba-3b6c-4225-8e04-300612acf32a)
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/3c19d401-0652-444f-9b09-102e5fa97fef)
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/935d75e7-4fce-453b-88dd-89e2ef63836f)
 
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/dc4cddcc-abe0-4c1a-829b-23bd24b1bdae)
 
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/a18fe1bb-0f9a-4f60-bb6f-82550de43ca2)

 
 
 
 
 

Now, we can query the VM security event logs
![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/72d6d718-efc5-4f4b-9834-f19c7effd820)
 

Filtering a particular event is its ID (example ID 4625 for login attempt failure)

![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/e7b749b9-1b8c-4f55-894f-940ac2c80453)


<h2>9.	Go back to the Microsoft sentinel to finalize things
Overview of sentinel</h2> 

 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/e1217107-81dc-4353-b42f-96fcfe0fc03e)

A workbook is created to map to the attack sources or failed_rdp location.

 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/b5664891-5322-4a0e-a603-fd4416115433)

We used log query code to plot the data on the map:

 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/410b5f60-f7ef-4f9e-b278-5d23476a7154)


Set the map setting accordingly to our preference.

 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/5273806a-67a9-493f-ae80-2563a743a9eb)


The map 
 ![image](https://github.com/CyberWorld-kam/School-cloud-mini-project/assets/157485250/d14c0567-7573-4a66-a9fb-71208444c085)


As we can see the mapping, the are people trying to login or attacking the machine from different country and different continents like:<br/>
•	India ==> 12 attempts<br/>
•	Egypt ==> 744 attempts<br/>
•	Indonesia ==> 3.1k attempts…


