---
tag: software linux centos practical networking CSA 
---

FInd out the current dhcp server used by the VM
```
sudo journalctl -r | grep -m1 DHCPACK
```

Download DHCP package
```
sudo yum install dhcp -y
```

Find the network interface which required to setup dhcp in 
```
ifconfig
```

