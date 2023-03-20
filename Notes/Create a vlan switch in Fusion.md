#practical #networking #software #vmware #CSA 
https://spin.atomicobject.com/2017/04/03/vmware-fusion-custom-virtual-networks

###### Edit networking config files
Close fusion. Open the file using vi or any editor
```
vi /Library/Preferences/VMware \Fusion/networking
```

Append the following lines to that file
```
answer VNET_2_HOSTONLY_NETMASK 255.255.255.0 
answer VNET_2_HOSTONLY_SUBNET 10.0.1.0 
answer VNET_2_VIRTUAL_ADAPTER yes 
```

###### Select the adapter option
Then open Fusion again and go to the settings of a any VM. Select network adapter form there. You will see the virtual network we just created under the adapter options.
![[Screenshot 2023-02-24 at 10.32.11.png]]
