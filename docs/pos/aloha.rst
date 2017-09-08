Aloha Setup
===========

**Step 1**

Download and place setup on desktop, then run setup.

https://posservice.takeouttech.com/setup/generic/setupQ.zip



**Step 2**

There are 2 POSIntegrationClient.exe.config files that you will need to edit. 

# Open the file [installation path]\POSIintegrationClient.exe.config

 * change the site id to _______.


# Open the file is under [installation path]\TakeOut Technologies POS Integration Service\POSIintegrationClient.exe.config

 * Where you see  value=”DEMO”, change it to value=“________” 


# under [installation path]\TakeOut Technologies POS Integration Service

 * In this folder you will also need add the iber.bat file. 


**Step 3**

Right click on the Windows icon, select "run", then, type in services.msc

  * Go to services and right click on  “TakeOut Technologies POS integration”
  * Right click to bring up properties
  * Go to the tab for Recovery and change the first two boxes down to show Restart the program
  * Go back to the general tab and make sure the client shows startup as “Automatic” (will fail if on manual) 
  * Click Apply 
  * Click Start 
