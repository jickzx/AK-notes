---
notion-id: 28b982ca-e761-80c0-9597-d8a51cf640bc
---
The B instruction is for branching. Use as a goto.

```assembly
        B       main                ; jump to the function main

press   DEFB    "Press any key\n",0 ; Defines a string called "press", terminates at the 0
youpress DEFB   "You pressed :",0   ; Defines a string called "youpress", terminates at 0

        ALIGN                       ; Keeps strings saved as four characters per memory location

main                                ; The function main begins
        ADRL    R0, press           ; Places "press" string into memory location R0
        SWI     3                   ; Prints the string contents of R0 

        SWI     1                   ; Takes a keyboard character input into R0

        ADRL    R0, youpress        ; Same as before but with "youpress" this time
        SWI     3                   ;

        SWI     0                   ; Prints the character contents of R0
        MOV     R0, #10             ; Loads the literal '10' into R0 which is a newline in ASCII
        SWI     0                   ; prints the newline in R0

        SWI     2                   ; exits program

```

Now if we add B we can use it as branching

```assembly
        B       main                ; jump to the function main

press   DEFB    "Press any key\n",0 ; Defines a string called "press", terminates at the 0
youpress DEFB   "You pressed :",0   ; Defines a string called "youpress", terminates at 0

        ALIGN                       ; Keeps strings saved as four characters per memory location

main                                ; The function main begins
        ADRL    R0, press           ; Places "press" string into memory location R0
        SWI     3                   ; Prints the string contents of R0 

        SWI     1                   ; Takes a keyboard character input into R0

        ADRL    R0, youpress        ; Same as before but with "youpress" this time
        SWI     3                   ;

        SWI     0                   ; Prints the character contents of R0
        MOV     R0, #10             ; Loads the literal '10' into R0 which is a newline in ASCII
        SWI     0                   ; prints the newline in R0

        SWI     2                   ; exits program

```

DEFB puts a single byte in memory, DEFW puts 4 bytes into memory, DEFW is better for handling larger numbers

All instruction are 4 bytes

ALIGN shifts the next part of code to be stored in an address that is a multiple of 4

ADRL loads an ADDRESS into memory, LDR loads DATA AT AN ADDRESS into memory

```assembly
		B main

table		DEFW	5
is		DEFB " is ",0

		ALIGN

main
;;	You'll need to enter code here to initialise any registers before the loop




;; These two lines load R3 and R4 with some initial values so that the code below works -- you will probably want to delete these two lines 
		MOV	R3,#0
		LDR R4, table

;; This code currently prints out the result of multiplying the numbers in the registers R3 and R4
;; Remember we have to use R0 to print anything (integers, strings or characters) so we sometimes need to move values into R0 
;; so we can print them

loop    
		MOV	R0,R3
		SWI	4

		MOV	R0, #'x'
		SWI	0

		MOV	R0,R4
		SWI	4

		ADRL	R0, is
		SWI 3

;; Multiply R3 and R4, and put the result in R0 ready to be printed
		MUL	R0,R3,R4
		SWI	4
		
		MOV 	R0, #10		; A linefeed character
		SWI	0

		CMP R3, R4
		ADD R3, R3, #1

		BNE loop

;; You'll need to add code here to implement the loop

		
;; End program	
		SWI 	2
	

```
