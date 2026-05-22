---
notion-id: 27d982ca-e761-8004-9b0d-e4c545479784
---
glpat--ISIhI0rXaEoI567W_csC286MQp1Ojd5awk.01.0z0xeyx2i

[[PENULTIMATE ASM NOTES]]

[[Lecture 2 Hello World or something idk]]

We use ARM32 and Komodo Emulator

```assembly

        B main

string  DEFB        "Hello World\n", 0

        ALIGN       
main    ADRL        R0, string          ; take data from string into R0
        SWI         3                   ; SWI = software interrupt, SWI 3 is print
        SWI         2                   ; SWI 2 is stop

```

[[Lecture 3 Branching]]

[[Notes on Mock Exam]]

[[Meadow 2 & Fibb]]
