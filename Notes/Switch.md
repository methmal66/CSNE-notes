#networking #hardware #NF #RS #AI
A switch is a hardware component working in the [[Data link layer]] of the [[OSI model]] in network infrastructure that performs the switching process. It connects end devices to the network

# MAC address learning process of a switch/ switching
1. [[CAM table]] is empty when a switch is turned on for the first time. It does not know about [[MAC address]]es of the interfaces it has connected to.
2. When there is an incoming frame, switch records the source MAC address corresponding to the interface it was recieved, if it is not already available in the CAM table.
3. If the destination address cannot be found from the CAM table, switch broadcasts the frame and find the destination interface through the responding frame.
4. When source address and destination address is already avilable in the CAM table, switch will simple forward the frame through the corresponding interface, rather repeating the above process.

# Switch types
Based on hardware form factors to consider when buying a new device
1. [[Managed switch]]
2. [[Unmanaged switch]]
3. [[Modular switch]]
4. [[Fixed-configuration switch]]
5. [[Stackable switch]]
6. Non-stackable switch

# Switch platforms
Based on implementation differences
1. [[Campus LAN switch]]
2. [[Cloud managed switch]]
3. [[Data center switch]]
4. [[Service provider switch]]
5. [[Virtual switch]]

# Methods of managing switch platforms
- Cloud host management
- Browser based management

# Consideration of buying a switch
- Port density
	- Number of ports avaible in a single switch
	- Modular switches can support very high-port densities
	- Large networks require high density, modular switches to make the best use of space and power
- Forwarding rates
	- Overall processing capability of a switch
	- Measured by Gbps
	- Forwarding rate = number of ports x rate of a port x 2(full duplex)
	- Switch product lines are classified by forwarding rates.
	- Entry-level switches have lower forwarding rates, they can be used as [[Access switch]]es
	- Swiches with higher rates must be chosen for distribution and core layer
- Power over ethernet (PoE)
	- Delivering power through an already available ethernet link
	- Used with IP phones and access points as they can be installed at anywhere 
- Multilayer switching
	- Build a routing table, support a few routing protocols, and forward IP packets at a rate close to that of Layer 2 forwarding.
	- Deployed in the core or distribution layer
	- Almost all switches support routing nowadays





