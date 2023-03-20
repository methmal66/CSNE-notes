#practical #networking #software #vmware #linux
https://alexsm.com/vmware-fusion-nat-port-forwarding-ssh
https://bytefreaks.net/gnulinux/fedora-25-install-start-enable-ssh-server
https://phoenixnap.com/kb/how-to-enable-ssh-centos-7

###### Configure OpenSSH server in VM
Install OpenSSH server
```Fedora
$ sudo yum install openssh-server ufw
```

```CentOs
$ sudo yum install epel-release
$ sudo yum install --enablerepo="epel" ufw
```

Enable ssh
```Fedora
$ sudo systemctl enable sshd.service
$ sudo systemctl start sshd.service
$ sudo systemctl status sshd.service
```

```CentOs
$ sudo systemctl enable sshd
$ sudo systemctl start sshd
$ sudo systemctl status sshd
```
Make sure that it output as "Active(running)"

###### Configure firewall in VM
```Fedora
$ sudo ufw allow ssh
$ sudo ufw enable
$ sudo ufw status
```

Final command must display an output simillar to this
![[Screenshot 2023-02-24 at 14.02.24.png|450]]

###### Configure NAT port forwarding 
Open NAT configs in an editor
```Mac
$ sudo vim Library/Preferences/VMware\ Fusion/vmnet8/nat.conf
```

Under the line `[incomingtcp]` add a new port forwarding rules similar to this
![[Screenshot 2023-02-24 at 14.10.24.png]]
Any number of rules can be added like this. `2222` in here is the SSH client port in the host os. Close and restart Fusion, then launch the VM.

###### Run in the background
Goto VMware Fusion > Settings. Under General, tick 'Confirm before closing'
![[Screenshot 2023-02-24 at 19.49.49.png]]
When closing a VM, you can select the option to 'Run in Background' from now.
![[Screenshot 2023-02-24 at 19.50.28.png|250]]

###### Connect to SSH server from the guest OS
```Mac
$ ssh -p 2222 methmal@127.0.0.1
```

You will be loged into VM through SSH successfully
![[Screenshot 2023-02-24 at 19.54.53.png]]