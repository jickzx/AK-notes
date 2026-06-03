---
notion-id: 27f982ca-e761-8089-9704-fa2592432e80
---

[[Lecture 1 VN Architecture & Address Decoding]]

[[Lecture 2 Representing Information]]

[[Lecture 3 Boolean Logic]]

[[Lecture 4 Adders n shit]]

[[Lecture 5 Full Adders and Subtractors]]

```vhdl
CHIP ShiftR8 {
    IN in[8], load;
    OUT out[8];

    PARTS:
    // Flip-flops
    DFF(in=x0, out=y0);
    DFF(in=x1, out=y1);
    DFF(in=x2, out=y2);
    DFF(in=x3, out=y3);
    DFF(in=x4, out=y4);
    DFF(in=x5, out=y5);
    DFF(in=x6, out=y6);
    DFF(in=x7, out=y7);

    // Right-shift Mux network
    Mux(a=in[0], b=y1, sel=load, out=x0);
    Mux(a=in[1], b=y2, sel=load, out=x1);
    Mux(a=in[2], b=y3, sel=load, out=x2);
    Mux(a=in[3], b=y4, sel=load, out=x3);
    Mux(a=in[4], b=y5, sel=load, out=x4);
    Mux(a=in[5], b=y6, sel=load, out=x5);
    Mux(a=in[6], b=y7, sel=load, out=x6);
    Mux(a=in[7], b=false, sel=load, out=x7);

    Mux(a=in[0], b=y1, sel=load, out=out[0]);
    Mux(a=in[1], b=y2, sel=load, out=out[1]);
    Mux(a=in[2], b=y3, sel=load, out=out[2]);
    Mux(a=in[3], b=y4, sel=load, out=out[3]);
    Mux(a=in[4], b=y5, sel=load, out=out[4]);
    Mux(a=in[5], b=y6, sel=load, out=out[5]);
    Mux(a=in[6], b=y7, sel=load, out=out[6]);
    Mux(a=in[7], b=false, sel=load, out=out[7]);

}
```