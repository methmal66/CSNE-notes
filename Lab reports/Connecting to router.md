#networking #NF #hardware #practical #cisco #packettracer 

![[Pasted image 20230319195348.png]]
![[connecting to router.pkt]]

| Device | Interface | IP address   | Default gateway |
| ------ | --------- | ------------ | --------------- |
| R      | fa0/0     | 192.168.1.1  | -               |
| "      | fa1/0     | 192.168.1.9  | -               |
| PC1    | fa0       | 192.168.1.3  | 192.168.1.1     |
| PC2    | fa0       | 192.168.1.11 | 192.168.1.9     |

# Direct connection using console cable (out-of-band)
```embed
title: 'Secure Shell (SSH) configuration on a switch and router in Packet Tracer'
image: 'https://computernetworking747640215.files.wordpress.com/2018/07/ssh-switch-pc-authentication.png'
description: 'Welcome to this tutorial! Here, we’ll have an overview of Secure Shell (SSH) protocol, then see how to configure it on a switch and a router in Packet Tracer. An overview of SSH Secure Shell,…'
url: 'https://computernetworking747640215.wordpress.com/2018/07/05/secure-shell-ssh-configuration-on-a-switch-and-router-in-packet-tracer/'
```

Go to PC -> Desktop -> Terminal and OK for the default settings to open the terminal emulator in packettracer.
![[Pasted image 20230319175244.png]]
Configure interfaces in the router to build the network topology
```cisco
R1(config-if)#int fa0/0
R1(config-if)#ip add 192.168.1.1 255.255.255.248
R1(config-if)#no shutdown
R1(config-if)
R1(config-if)#int fa1/0
R1(config-if)#ip add 192.168.1.9 255.255.255.248
R1(config-if)#no shut
```

Set domain name, username and password
```cisco
R1(config)#ip domain name admin
```
[[Set username and password for a switch or router]]

Generate ssh key for SSH. Give modulus bits as `1024`.
```cisco
R1(config)#crypto key generaten rsa
```

Specify the ssh version (option)
```cisco
R1(config)#ip ssh version 2
```

Enter into virtual line configuration mode
```cisco
R1(config)#line vty 0 4
```
VTY is a virtual port and used to get Telnet or SSH access to the device. VTY is solely used for inbound connections to the device. These connections are all virtual with no hardware associated with them. The abstract “0 – 4” (recommended) means that the device can allow 5 simultaneous virtual connections.

Enable login through SSH
```cisco
R1(config-line)#transport input ssh
```

Make SSH required both username and password
```cisco
R1(config-line)#login local
```

# Remote connection using SSH (in-band)
After setting the SSH connetion as above, console cable is not needed anymore, remove it. Go to any device(PC/router/switch) and login to the devices which you have enabled ssh

Enter into the router using ssh and enter the password. In order to enter into the golbal config mode, the other password must be also given.
```
ssh -l admin 192.168.1.1
```
![[Pasted image 20230319184840.png]]
`
<iframe width="550" height="315" scroll="no" style="overflow:hidden" src="https://gist.github.com/Albert-W/e37d1c4fa30c430c37d7b1b1fe9b60d8"/>

<body><script src="https://gist.github.com/Albert-W/e37d1c4fa30c430c37d7b1b1fe9b60d8.js"></script></body>

