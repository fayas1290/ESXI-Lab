# Installing VMware ESXI On An HPE Proliant Server And Installing Firmware In VMware ESXI

To begin with, delete previously configured arrays from the sever on System Utilities by going into System Configuration > selecting the appropriate storage controller > Array Configuration > Manage Array > select the Array to delete > Delete Array > Submit Changes
<br>
<br>
![image](https://github.com/fayas1290/ESXI-Lab/assets/157561213/4c0ba2ed-fd81-4f9f-97d7-554e419e07ab)
<br>
<br>
Create New Array by going back to the Array Configuration page > Create Array > select appropriate HDD > select the RAID level  > Submit Changes. Here we can name the logical drive, select stip size and accelerator method
<br>
<br>
![image](https://github.com/fayas1290/ESXI-Lab/assets/157561213/e765e0d5-79eb-4a5a-b7f9-8df6dfe2ccbc)
<br>
<br>
Click Save and Exit (F12)
Reboot the server, meanwhile find the Vmware ESXi ISO and [mount](https://kb.leaseweb.com/products/dedicated-server/remote-management-of-your-dedicated-server/attaching-iso-to-virtual-console-ilo-4) it as a virtual disk in iLO. HPE servers uses custom VMware images loaded with appropriate firmware and drivers, the ISO files can be downlaoded from [here](https://www.hpe.com/in/en/servers/hpe-esxi.html)

While the server reaches the POST screen press F11 to go to the One-Time Boot menu and select iLO virtual USB from the list, the OS installation screen will load.
<br>
<br>
![image](https://github.com/fayas1290/ESXI-Lab/assets/157561213/a7f4b55f-d8bf-40f0-b75e-d9bfbacdce43)
<br>
<br>
Once all the modules are loaded you will be prompted to select the logical disk, keyboard layout and the root password
<br>
<br>
![image](https://github.com/fayas1290/ESXI-Lab/assets/157561213/a0903a0c-a732-4190-b5a9-61cd7c6409c6)
<br>
<br>
Confirm the installation by pressing F11 on the final screen.
Once the OS has been installed boot into the OS by rebooting the server

# Installing Firmware In VMware ESXI
We begin by placing the host in maintenance mode, instructions can be found [here](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html)
<br>
And then we Enable SSH and ESXi Shell so that we can connect to the OS through an app like PuTTY using SSH protocol
<br>
From the VMware ESXi home screen Press F2 to go to the settings<br>
Enter the credentials to log in<br>
Go to Troubleshooting Options<br>
Enable SSH
<br>
<br>
![image](https://github.com/fayas1290/ESXI-Lab/assets/157561213/ad9c0afc-1fa6-4e25-8f1c-e26ad717ce46)
<br>
<br>
We then SSH into the VMware OS using an app like PuTTY<br>
Login as root <br>
Download the required firmware
<img width="938" alt="Screenshot 2024-05-07 114106" src="https://github.com/fayas1290/ESXI-Lab/assets/157561213/8f2230da-0e94-424e-9871-091203b2e792">
<br>
<br>
Note that the firmware file is in ZIP format<br>
Place the Smart Component zip file in a temporary directory. (using FTP client like FileZilla)<br>
We then unzip the file CPXXXXXX.zip downloaded from HPE Support Center using `unzip` command<br>
After extraction, we need to ensure that the CPXXXXXX.vmexe file is executable by using the command
```Shell
chmod +x CPXXXXXX.vmexe
```
From the same directory, execute the Smart Component, using the following command
```Shell
 ./CPXXXXXX.vmexe
```
<br>

![image](https://github.com/fayas1290/ESXI-Lab/assets/157561213/e3021072-1d38-4f97-8368-6c019722be88)
<br>
<br>
Reboot the server as requested and the installiion will be complete

















