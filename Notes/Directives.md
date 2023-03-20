#ES #software #programming 

> Instructions for the [[Assembler]] which helps automating the assembly process and imporve the program readability

Not translated into [[Mnemonics]]. There are not for the execution of CPU.

###### What are the common directives used in 8bit AVR?
- `.equ`
	- Define constants
	- Ex:
		- `.equ max, 100  ;max = 100`
		- `.equ min, 0   ;min = 0`
- `.set`
	- Set local variables
	- Ex:
		- `.set x, 10.  ;x = 10`
		- `.set y, 12  ;y = 12`
- `.include`
	- Include definition files (.inc ex) in to source code
	- Definition files contains the constants specific to the MCU
	- For ATmega328 : `.include "m328def.inc"`
- `.org`
	- Defines from where the specific parts of the machine code get stored in the memory
	- Ex:
		- `.org 0`
		- `.org 0x7`