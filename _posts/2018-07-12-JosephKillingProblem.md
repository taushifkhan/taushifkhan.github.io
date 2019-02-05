---
title: "Mathematics of how Joseph survived !"
date: 2018-01-27
tags: [Fun]
header:
    #image: "/assets/images/404Page.jpg"
excerpt: "How to stay alive with Mathematics"

---
Joseph Killing Problem :camel: :rocket:

A group of Jews are surrounded by Roman solders. 
The Jews do not want to get capture or surrender to the Roman.
 They plan to kill each other and the last surviving will commit suicide. 
 > (A historical opinion was that Joseph knew the winning seat and did not commit suicide as last man surviving). 
 
The setting arrangements were done in a circle with a rule that in each circle of killing event, only a person to the left gets killed.

A very cool mathematical connection can be drawn and learned form the systematic study of this problem,

Lets start with a smaller number n = 3; and the symbol > represent person at position i kills person at position j. Where i and j are sitting position in n=3. Now let the killing start,
```
n=3; 1>2; 3>1 : w(n) = 3
n=4; 1>2 3>4; 1>4 : w(n) = 1
n=5; 1>2 3>4 5>1; 3>5 w(n) = 3
n=6; 1>2 3>4 5>6; 1>3 5>1 : w(n) = 5
n=7; 1>2 3>4 5>6 7>1; 3>5 7>3: w(n) = 7
n=8: 1>2 3>4 5>6 7>8; 1>3 5>7 ; 1>5 = 1
```

* observation 1: all even position are get killed at one cycle here on we will start with odd positions only
```
n=9: 9>1 3>5 7>9; 3>7 w(n) = 3
n=10: 1>3 5>7 9>1; 5>9 w(n) = 5
n=11: 11 >1 3>5 7>9  11>3; 7>11; w(n) = 7
```
* similarly carrying out the work for n= 12, 13 , 14, 15, 16
```
n=12:   w(n) = 9
n=13;   w(n) = 11
n = 14; w(n) = 13
n= 15: w(n) = 15
n= 16: w(n) = 1
```

* Now we have seen following observations,

Repeatation of odd surviving seats.
A relation between number of people and order of last surviving seat.

From second observation, we can say that, when the number of seats are absolute power of 2 (n= 2,4,8,16.. ); winning seat is 1 (w(n)=1).

§ if n= 2^a ; w(n) =1

§ if there is remainder (l) from the biggest binomial of 2; winning seat number can be 2l+1

*  now lets try, for the original problem of Joseph killing, suppose there were 41 jews lest on the table.
41 = 2^5 + 9
hence, the possible last surviving seat is 2*9+1 = 19. Joseph would be sitting on the 19th position from the killing to start.

### A cool solution : Jumping the binary.

Every number can be written in the binary system where each position represent the power of 2. for example,
```
3 = 2^1 + 2^0 = 11 
4 = 2^2 + 0*2^1 + 0*2^0 = 100
5 = 2^2 + 0*2^1 +1*2^0 = 101
```
— henceforth

now, w(n) can be estimated by jumping the binary of right most to the left most position and reevaluation seat number. so, if n =5 ; Binary(n) =  101 ; Jumping Binary (w(n)) = 011 = 3

for illustration, 41 = 32+9 = 32+8+1 = 2^5 +0*2^4+1*2^3+0*2^2+0*2^1+1*2^0 = 101001

w(n) = 010011 = 16+2+1 = 19  (= 2*9+1 ).
