---
notion-id: 292982ca-e761-80c2-98c7-fab489c0b6de
---
# Adders

<!-- Column 1 -->
Half Adder:

<!-- Column 2 -->
![[lecture-5-full-adders-and-subtractors-01.png]]

<!-- Column 1 -->
Full Adder:

<!-- Column 2 -->
![[lecture-5-full-adders-and-subtractors-02.png]]

<!-- Column 1 -->
Ripple Carry Adder - Slow due to propagation delay

<!-- Column 2 -->
![[lecture-5-full-adders-and-subtractors-03.png]]

It is possible to build a variant that can generate the output in terms of inputs $A_i$ and $B_i$.

The alternative to the Ripple Carry Adder is the Carry-Lookahead Adder.

# Subtractors

Instead of a C_in or C_out for Carry, we use B_in and B_out for borrow

Also the output is D for difference instead of S for sum

Half Subtractor: 

![[lecture-5-full-adders-and-subtractors-04.png]]

You can chain subtractors to make a full subtractor

Really we dont use these we just use two’s complement and add together the numbers.

![[lecture-5-full-adders-and-subtractors-05.png]]

# Sign and Magnitude

MSB indicates sign, other bits hold number, problem with +-0 being different numbers.

1000 and 0000 in 4 bit S&M are the same number.

# Excess-n

S&M but offset by n in binary, so 0000 is -3, 0001 is -2 and so on

# One’s Compliment

The negative numbers are the complement of their positive counterparts, for instance, 0111 is 7, 1000 is -7. 0000 is 0, 1111 is 0 as well. Still has the two 0s problem, but conversion is easy. Adding with one’s complement means you add the numbers like normal but you have to add the carry and the result to make sure it is correct.

# Two’s Complement

The negative of a number in binary is its complement + 1. This offset allows us to store another negative number and removes -0. 
