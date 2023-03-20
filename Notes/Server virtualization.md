#software #os 
Dividing physical server into multiple virtual servers where each VM can be used for a seperate application server. Virtualization layer applies in the hardware level. [[Bare metal hypervisor]] is used

###### which kind of application servers can be run as a VM?
- [[Proxy server]]
- [[Mail server]]
- [[DNS server]]
- [[File server]]

###### How to access an app uniquely when connected them using 

###### what are the benifits?
- Performace 
	- VMs can run at the native hardware speed
	- Kernel is optimized for hardware
- Security
	- Any vulnerability in the hypervisor wont affect the VMs
- Scalability
	- Enterprise level hypervisors support the creation of large VM clusters
- Manageability
	- Vendors provide a management console where VMs can be managed in a single place


###### What are the drawback?
- Cost
	- Hypervisors are more expensive
	- Requires dedicated hardware to run
- Complexity
	- Has a substantial learning curve associate with


###### 
![[Pasted image 20230214213930.png]]
