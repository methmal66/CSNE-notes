 #practical  #hardware #vscode #platformio #ES
You must have installed "Platform I/O" vscode extension.
###### Create new Platform I/O project in vscode
![[Screenshot 2023-02-22 at 09.24.01.png]]

###### Complete project wizard
Give a suitable name for the project. Choose the "ATmega328P" board. Then select the project location and finish
![[Screenshot 2023-02-22 at 09.30.36.png]]

It will generate project files similar to below
![[Pasted image 20230222093716.png]]

###### Write the source code
Copy this sample code to the main.cpp
```c
/*
 * toggleProgram.c
 *
 * This program toggles ports B and C.
 *
 * Created: 4/3/2015 4:43:51 PM
 *  Author: Naimi

*/

#include <avr/io.h> #define F_CPU 16000000UL

#include "util/delay.h"
int main(void){
	DDRB = 0xFF;
	DDRC = 0xFF;
	
	while(1){
	       PORTB ^= 0xFF;  //toggle port B
	       PORTC ^= 0xFF; //toggle port C
	       _delay_ms(1000); //wait 1 second
	
	}
}
```

###### Upload to the boad
![[Screenshot 2023-02-23 at 18.15.06.png]]
