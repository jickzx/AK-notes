---
notion-id: 299982ca-e761-80cb-9e6c-f75d7da1fc98
---
String is array of chars with null terminator on end, you can do 

```c
char *s[2] = {"Orange", "Black"}
```

which is an arr of pointers to strings stored in read-only memory

referring to name of an array returns the address of the first element

```c
char s[6] = "hello" //has a null terminator

s == &s[0]
```
