# COA(Computer organization and Architecture)
## GNU8085 MICROPROCESSOR
   N/BThe actual code can be found above you can download and run it

### Finding the smallest number in an array of Data
#### Question A

![image](https://user-images.githubusercontent.com/64952843/126161720-4c2ecc45-edea-4a1e-94ff-f23b593baa14.png)
#### CODE
        ;<Program title>
          jmp start
          ;data
          ;Algorithm
          ;Load the address of the first element  of the array in HL pair
          ;Move the count to B_reg
          ;Increment the pointer 
          ;Get the first data in A_reg
          ;Decrement the counter
          ;Increment the pointer
          ;Compare the content of the memory  address by HL pair with that of A_reg
          ;If carry = 1, go to step 10, if carry =0 go to step 9
          ;Move the content of Memory address by HL to A_reg
          ;Decrement the count
          ;Check for zero of the count.if ZF=0 go to step 6 or if ZF=1 go to the next step
          ;Store the smallest data in memory
          ;Terminate the program


          ;code
          start: nop
          LXI H,2400 ; PC has 8 now here when you execute
          MOV B,M ;PC has 9 now here
          INX H ;PC has 10 now here
          MOV A,M ;PC has 11 now here
          DCR B ;There is an S flag of 1 and p flag of 1
          LOOP: INX H
          CMP M
          JC AHEAD
          MOV A,M
          AHEAD: DCR B
          JNZ LOOP
          STA 2407
          HLT
#### Screenshot of GNU8085
![image](https://user-images.githubusercontent.com/64952843/126166080-4e6ccbd8-e108-4da1-8181-30b8caa134a0.png)

#### Observation 
       After following the algorithm, we find out that when we initialize an array of any size then we store the result of the smallest number in any memory address the algorithm is able to store the smallest number of the element  


### Arranging the array in ascending order
#### Question B
![image](https://user-images.githubusercontent.com/64952843/126162319-6783af6f-8222-4ab7-a682-0ad631f27b87.png)

#### CODE

         ;<Program title>
          jmp start
          ;data
          ;Algorithm
          ;Initialize HL pair as memory pointer
          ;Get the count at 4200 into C - register
          ;Copy it in D - register (for bubble sort (N-1) times required)
          ;Get the first value in A - register
          ;Compare it with the value at next location
          ;If they are out of order, exchange the contents of A - register and Memory
          ;Decrement D - register content by 1
          ;Repeat steps 5 and 7 till the value in D - register become zero
          ;Decrement C - register content by 1
          ;Repeat steps 3 to 9 till the value in C - register becomes zero

          ;code
          start: nop
          LXI H,4200
          MOV C,M
          DCR C
          REPEAT: MOV D,C
          LXI H,4201
          LOOP: MOV A,M
          INX H
          CMP M
          JNC SKIP
          MOV B,M
          MOV M,A
          DCX H
          MOV M,B
          INX H
          SKIP: DCR D
          JNZ LOOP
          DCR C
          JNZ REPEAT
          HLT


#### Screenshot GNU8085

![image](https://user-images.githubusercontent.com/64952843/126166241-b516feb4-c3c1-4dfe-8780-4b5275d936ba.png)

#### Observation
        After following the algorithm given, I found out that when initializing an array of any size and putting specific element in the array when executing the array will be arranged from the largest to the smallest
