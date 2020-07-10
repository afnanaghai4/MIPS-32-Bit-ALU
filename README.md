# MIPS-32-Bit-ALU

##	Overview:
The project that has been attached in this file is a 32 bit ALU. ALU (Arithmetic Logic Unit) carries out all the arithmetic and logical operations in the CPU and is the third component of CPU.

##	Components:
ALU has various components including logical and arithmetic operators.
It contains:

1.	EQUALS COMPONENT:

![Stack overflow](/images/1.jpg)

Component compares every bit of both inputs. Bits first goes into XOR to check if they are equal and then goes into AND gate to see if all the results are 1, if so then it generates a 1 which is extended to 32 bits and the output is shown.


2.	NOT EQUALS COMPONENT:

![Stack overflow](/images/2.jpg)

Not equals component checks if both the inputs entered are not equal. So it uses Equal as subcomponent and then uses a NOT gate on the LSB to invert the output. So if equal generates a 1, NOT gate changes it to 0 and hence it shows they are equal.


3.	GREATER THAN COMPONENT

![Stack overflow](/images/3.jpg)	
  
This component checks if the input entered is greater than 1 or not. So it starts by checking MSB which is also the sign bit, if it is 1 then it gives output 0 which then is extended to 32 bits. But if sign bit is 0, then it checks the remaining bits if they are equal to 0. So all the bits are XNOR’ed with 31 0’s and then they are sent into an AND gate to check if every single bit after comparison gives a 1. If so, it generates a 0, otherwise it gives out a 1.


4.	LESS THAN COMPONENT:

![Stack overflow](/images/4.jpg)

Less than component just uses greater than as a sub component and then only inverts the LSB so that it automatically inverts the whole result of greater than component. Now, if greater than sends a 1, then output will be a 0 due to NOT gate.


5.	ADDER/SUBTRACTOR COMPONENT:

![Stack overflow](/images/5.jpg)

This component works both as an adder and a subtractor depending on the Carry in bit. B input is XOR’ed with carryin. So, if carry in is 1, then it changes the B to its two’s complement form and then it works as a subtractor. When carry in is 0, XOR gate does not change anything and B is normally added into A, so it now works as an adder.


6.	SHIFTER COMPONENT:

![Stack overflow](/images/6.jpg)

This component works on the logical side of the ALU. It carries out 3 operations depending on the opcode which is coming; shift right, shift left and shift right arithmetic. Shift left means that A’s bits are shifted towards the left and the bits that they are shifted with is also an input known as carry. MUX’s input ports 1st and 2nd carries out this function. If carry is 1 and shift left is to be done 1 time and input is 010, then output will be 011.shift right shifts A’s bits towards the right and replace the bits that have been shifted with a carry. MUX’s input port 3 carries out this operation. So whenever opcode comes in the form 0100, it does a shift right because MUX’s 3rd port input is selected .shift right arithmetic is basically similar to shift right. The only difference is that the MSB bit remains constant throughout shifting of the bits towards the right. MUX’s port 4 does this operation.  


7.	GATES COMPONENTS:
 
![Stack overflow](/images/7.jpg)

This picture is from the ALU component because if I would have made a separate circuit for every Gate, complexity of the circuit would have increased and it would be counted as a poor design. Gates operation are straightforward, inputs come in and according to the gate, a suitable output is generated.


## ALU(ARITHMETIC AND LOGIC UNIT):
 
![Stack overflow](/images/8.jpg)

I have divided my ALU into 4 parts according to the opcode.
Arithmetic part includes addition, subtraction and shifting operations. So when the opcode is 3rd bit is a 1, alu knows that addition or subtraction or shifting is to be done. Alu knows this through a mux which is enabled when the 2nd bit of opcode is 1.  If after this, opcode’s 2nd bit is a 1, alu now comes to know that subtraction is to be done, since this bit is connected with the carry port of addsub component. If it was a 0, then it would have done addition. Now if the opcode’s 3rd bit is a 1, and its 1st is also 1, then alu knows that shifter component is to be used for shift right arithmetic. Now the next part is logical one in which decisions are made if the input entered is greater than 0 or less than 0 or if both inputs are equal or not. ALU recognizes if any of this operation is to be done by checking the 2nd and 3rd bit of the opcode. If they are both 1, both mux’s on the downside are enabled and now ALU only needs to see the remaining bits of the opcode to check which operation is to be carried out. The output of these operations is sent into a mux which is only enables when the 1st bit of opcode is 1 which is also the case for the mux’s on the downside too. V is overflow which only works during addition and subtraction operation. This is so because sometimes the output after either addition or subtraction, is out of the range of the signed numbers so it might give a wrong answer, so to avoid it an overflow is connected to indicate whenever the answer is out of the range.

##	EVALUATION:

ALU works fine on all the opcodes and with any sort of inputs. Complexity is kept to the minimum and it is always tried to keep it simple as much as possible.
