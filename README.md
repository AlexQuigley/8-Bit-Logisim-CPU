# 8-Bit-Logisim-CPU
This is an 8 Bit logisim CPU built for fun while in my Digital Logic class  

**CU INSTRUCTION CODES:**  
The control unit breaks up the instruction register into 3-4 segments based on what operation its running.   

For Loading and Storing operations the instruction register is decoded into these 3 segments:  

00 00 0000  
^  ^   ^  
|  |   |  
|  |   L This is the target address for the CU to Load/Save from  
|  L This is the target CU register that is being Loaded/Saved to/from     
L This is the instruction choosing if we are loading or saving.   

For ALU operations the layout for the 4 lowest bit changes, the ALU instructions look like this:  

00 00 00 00  
^  ^  ^  ^  
|  |  |  |  
|  |  |  L Register the ALU will get its B input from  
|  |  L Register the ALU will get its A input from (Also will be the register the ALU saves the output to)  
|  L ALU op code (see below)  
L ALU Select (will always be 00)  


**REGISTER CODES:**  
R0	     00  
R1	     01  
R2	     10  
R3	     11  

**INSTRUCTION CODES:**  
ALU      00	  
Load	   01  
Store	   10  
Jump	   11	-Not operational atm  

**ALU OP CODES:**  
Add 	   00  
Subtract 01  
Multiply 10  
Divide	 11  
 

A basic example of a program to add two numbers together, save the output to memory, then load the output into R2:  

**_0_**  0000	  0100 1000  	LOAD  R0 ADDR-8  
**_1**  0001	  0101 1001  	LOAD  R1 ADDR-9  
**_2**  0010	  0000 0001	  ADD   R0 R1  
**_3**  0011	  0000 0001	  -ALU SAVE-  
**_4_**  0100	  1000 1010	  STORE R0 ADDR-10  
**_5_**  0101	  0110 1010	  LOAD  R2 ADDR-10  
**_6_**  0110	  0000 0000  
**_7_**  0111	  0000 0000  
**_8_**  1000	  1111 0110  
**_9_**  1001	  1101 1000  
**_10_** 1010	  0000 0000  
**_11_** 1011	  0000 0000  
**_12_** 1100	  0000 0000
**_13_** 1101	  0000 0000
**_14_** 1110	  0000 0000
**_15_** 1111	  0000 0000

