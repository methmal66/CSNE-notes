#linux #practical  #software #CSA #networking 

###### Pre requirements
- [[Create a vlan switch in Fusion]]
- [[Create a VM in Fusion]]

###### Setup network adapters
You need to network adapters
1. Share internet from the host OS
2. Connect to the vlan
You can always add new devices to your VM from the top right button.
![[Screenshot 2023-02-23 at 18.29.45 1.png]]
Resume the VM and configure the first adapter to share internet with the host
![[Screenshot 2023-02-23 at 18.35.24.png]]
Then setup the other adapter to use the custom vlan we created. Now run the VM

###### FInd out the interface
Execute `ifconfig` and observe the output carefully
![[Screenshot 2023-02-24 at 10.49.05.png]]

The first interface `ens160` is connected to the internet with a IP address using NAT. The last interface `lo` means our localhost. But interface `ens256` does not has a IPv4 address assigned with it. Because it is the one we should configure with the our custom vlan.

###### Assign a temporary IP
Replace the interface, subnet mask, default gateway and IP address as your senario
```bash
$ sudo ifconfig ens256 up 10.0.1.2 netmask 255.255.255.0
$ sudo route add default gateway 10.0.1.1
```

Then execute `ifconfig` again to make sure that configs are success
![[Screenshot 2023-02-24 at 11.08.36.png]]
You can see that new interface is assigned with the IP address.

Now restart the VM and you will see that the IP we assigned to the interface is not there anymore. Because that was a temporary IP address. It get removed everytime when the VM is restarted.

###### Assign a permenant IP
A permenant IP address can be assigned using `nmtui` too. Run it from the terminal. Then select 'Edit a connection'.
![[Screenshot 2023-02-24 at 11.50.20.png|250]]

Enter into the correct interace and do the configureration.
![[Screenshot 2023-02-24 at 11.53.00.png|500]]

Optionally, connection names can be changed to identify them easily
![[Screenshot 2023-02-24 at 11.54.04.png|250]]

Now quit from the nmtui tool.
![[Screenshot 2023-02-24 at 11.54.28.png|250]]

Then run again `ifconfig` and note an IP has been assigned. Finally, restart the VM and see that the IP does not get removed or changed. Because we have assigned a static IP this time. Add a note to the VM so you dont have to run `ifconfig` everytime when you need to find the IP.

