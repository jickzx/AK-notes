---
notion-id: 292982ca-e761-8096-ae79-c7bb5c5d2374
---
```assembly
		B main

; define your strings here
verses  DEFW 4 
line1   DEFB " men went to mow\n",0
meadow  DEFB "Went to mow a meadow\n",0
spot    DEFB "and his dog, Spot\n",0
man    DEFB " man ",0
men     DEFB ' men, ',0

		ALIGN



main
verseloop
		MOV R1,  verses ; Use R1 as the lineloop iterator equal to verses
		MOV R0, verses
		SWI 4 ; prints the verses number
		ADRL R0,line1
		SWI 3 ; prints " men went to mow\n"

		ADRL R0,meadow
		SWI 3 ; prints "Went to mow a meadow\n"

		CMP R1,#1
		BGT lineloop
		lineloopend 

		;1 man and his dog, Spot\n Went to mow a meadow
		MOV R0,#1
		SWI 4

		ADRL R0, man
		SWI 3

		ADRL R0, spot
		SWI 3

		ADRL R0,meadow
		SWI 3

		MOV R0, #10 ; Prints newline
		SWI 0
		
		SUB verses, verses, #1
		CMP verses, #0
		BGE verseloop

SWI 2

lineloop ; prints 4 men, 3 men, 2 men, 
		MOV R0,R1
		SWI 4

		ADRL R0, men
		SWI 3

		CMP R1, #2
		SUB R1, R1, #1
		BNE lineloop

		B lineloopend
```

Fibb

```assembly
        B   main

fibbEnd DEFW    13
fibbOld   DEFW    1
fibbNew   DEFW    0
strng   DEFB    "Fibonacci number ",0
is      DEFB    " is ",0

        ALIGN
main
        MOV R5 ,#1
loop    
        ADRL R0, strng
        SWI 3 ; "Fibonacci number "
        MOV R0, R5
        SWI 4 ; prints the iteration number
        ADRL R0, is
        SWI 3  ; " is "
        LDR R2, fibbNew ; store fibbNew in a temporary register
        LDR R3, fibbNew
        LDR R4, fibbOld
        ADD R3, R3, R4 ; fibbNew += fibbOld
        STR R2, fibbOld
        STR R3, fibbNew

        LDR R0, fibbNew
        SWI 4

        MOV R0, #46 ; Prints .
        SWI 0

        MOV R0, #10 ; Prints newline
	SWI 0

        ADD R5, R5, #1
        CMP R5, #13
        BLE loop 

SWI 2


```