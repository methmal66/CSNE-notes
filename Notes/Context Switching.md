#software #os

> [[CPU]] switching from one [[Process]] to another.

![[Screenshot 2023-02-26 at 19.07.55.png|500]]

###### How context switching works?
When CPU switches to another process, system saves the state of the current process and load the state from the new process.

###### What is used to represent the context of a process?
[[PCB]]

###### Why context swtching time should be close to zero?
Because CPU does nothing during that time. So, minimizing the time spend helps to reduce the resource wastage

