#AI #networking #practical #packettracer #cisco 

##### Initial setup
![[Pasted image 20230222114154.png]]

![[Pasted image 20230222114456.png]]

###### BRANCH1 Router
```cisco
hostname BRANCH1
!
interface FastEthernet0/0
ip address 172.16.0.1 255.255.254.0
duplex auto
speed auto
no shutdown
!
interface FastEthernet0/1
ip address 172.16.2.1 255.255.254.0
duplex auto
speed auto 
no shutdown 
! 
interface Serial0/0/0
ip address 209.165.200.226 255.255.255.252
clock rate 64000
no shutdown 
!
router rip
passive-interface FastEthernet0/0
passive-interface FastEthernet0/1
network 172.16.0.0
network 209.165.200.0
!
line con 0
line vty 0 4
login 
! 
end
```
######  BRANCH2 Router
```cisco
hostname BRANCH2
!
interface FastEthernet0/0
ip address 172.16.4.129 255.255.255.128 
duplex auto  
speed auto  
no shutdown
!
interface FastEthernet0/1
ip address 172.16.4.1 255.255.255.128
duplex auto
speed auto
no shutdown
!
interface Serial0/0/0
ip address 209.165.200.230 255.255.255.252
no shutdown 
!
router rip
version 2
passive-interface FastEthernet0/0
passive-interface FastEthernet0/1
network 209.165.200.0
!
line con 0
line vty 0 4
login 
!
end
```

###### HQ Router
```cisco
hostname HQ
!
interface FastEthernet0/0
ip address 192.168.1.1 255.255.255.128
duplex auto
speed auto
no shutdown
!
interface FastEthernet0/1
ip address 192.168.1.129 255.255.255.192 
duplex auto  
speed auto  
no shutdown
!
interface Serial0/0/0
ip address 209.165.200.225 255.255.255.252
no shutdown 
!
interface Serial0/1/0  
ip address 209.165.200.229 255.255.255.252 
no shutdown
!  
router rip
version 2
passive-interface FastEthernet0/0
passive-interface FastEthernet0/1
network 192.168.1.0
network 209.165.200.0
!
line con 0
line vty 0 4
login 
!
end
```