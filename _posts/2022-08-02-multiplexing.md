---
layout: post
section-type: post
has-comments: true
title: "Multiplexing"
category: network
---

<aside>
💡 The sharing of a medium or bandwidth. It is the process in which multiple signals coming from multiple sources are combined and transmitted over a single communication/physical line.

</aside>
<br>
## Frequency Division Multiplexing

The bandwidth of a single physical medium is divided into a number of smaller, independent frequency channels. 

## **Time Division Multiplexing**

All signals operate with the same frequency (bandwidth) at different times. 


## Code Division Multiplexing

Assign a m-bit chip to each user, and all chips are orthogonal(正交).

- For example, m = 8 and S = 00011011.
    - When user transmit bit 1, send original chip.
    - When user transmit bit 0, send reverse code S’ 11100100.
    
    00011011 ⇒ (-1 -1 -1 +1 +1 -1 +1 +1)
    
    $1/m·S·S=1$      
    
    $1/m·S·S'=-1$
    
    When receiver use S to calculate received data:
    
    - Result 0 ⇒ data from other users
    - Result 1 ⇒ sender sends bit 1
    - Result -1 ⇒ sender sends bit 0