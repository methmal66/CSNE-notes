A memory structure in which the processor is connected to two independent memory banks for data and instructions via two independent sets of [[Bus]]es

![[Pasted image 20230215081216.png]]
###### What are the two buses?
- Data bus
- Address bus

###### What are the pros?
- CPU can fetch data and instructions without conflicts
- Instruction size is independent from data size
- Easy memory addressing for processors with a small RAM

###### What are the cons?
- Control unit is expensive to design and develop
- Two buses cannot be used interchangeably

###### Why is it prefered for microcontrollers?
Having two seperate buses make it ideal for digital signal processing. But modern microcontrollers use a modern version of this architecture 

