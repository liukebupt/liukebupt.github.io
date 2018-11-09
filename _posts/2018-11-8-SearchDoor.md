---
layout:     post
title:      Search Door Problem
subtitle:   
date:       2018-11-8
author:     Ke Liu
header-img: img/post-bg-ios9-web.jpg
catalog: 	 true
tags:
    - Algorithm
---

Imagine that you are facing a high wall that stretches infinitely in both directions. There is a door in the wall, but you don't know how far away is the door or in which direction. It is pitch dark, but you have a very dim lighted candle that will enable you to see the door when you are right next to it.   

1. Show an algorithm that enables you to find the door by walking at most $$O(n)$$ steps in the worst case, where $$n$$ is the number of steps that you would have taken if you knew where the door is and walked directly to it (note that your algorithm does **not** know the value of $$n$$ in advance)

2. What is the constant multiple in the worst-case analysis for your algorithm?

3. Observe that if you knew $$n$$, you could trivially solve the problem in $$3n$$ steps in the worst case (since you do not know the direction of the door); an interesting question (beyond the scope of this problem) is: what the minimum constant $$c>3$$ that can be achieved by a linear-time algorithm (in the worst case)?

## Q1  
We have three approaches for this problem.  

1. 
```
a=1
while not find door:
     walk left a steps
     a*=2
     walk right a steps
     a*=2
```

2. 
```
a=1
while not find door:
     walk left to positoin a
     a*=2
     walk right to positoin a
     a*=2
```

3. 
```
a=1
while not find door:
     walk left to positoin a
     walk right to positoin a
     a*=2
```

## Q2
First, calculate some values after $$k^{th}$$ iteration.
### Approach 1
1. $$a_k$$  
`a` doubles twice after each iteration, so that $$a_k=4^k$$.  
2. $$T_k$$  
$$T_k$$ is the steps we move after $$k^{th}$$ iteration. For each iteration, we move left $$a_{k-1}$$ steps and then move right $$2a_{k-1}$$ steps. So that $$T_k=\sum^k_{i=1}3a_{k-1}=\sum^k_{i=1}\frac{3}{4}\cdot4^k=\frac{3}{4}\cdot4\cdot\frac{4^k-1}{4-1}=4^k-1$$.  
3. $$p_k$$  
$$p_k$$ is the current position after $$k^{th}$$ iteration. We assume that the left side of the starting point is negative, and right side is positive. Similarly to $$T_k$$, $$p_k=\sum^k_{i=1}a_{k-1}=\frac{1}{3}T_k=\frac{4^k-1}{3}$$.
4. $$L_k$$
$$L_k$$ is the furthest checked position checked on the left after $$k^{th}$$ iteration. Notice that, we can see the positions next to us using the candle. $$L_k=p_{k-1}-a_{k-1}-1=\frac{1}{3}(4^{k-1}-1)-4^{k-1}-1=-\frac{2}{3}(4^{k-1}+2)$$.
5. $$R_k$$
Similarly to $$L_k$$, $$R_k$$ is the furthest checked on the right after $$k^{th}$$ iteration. $$R_k=p_{k-1}+a_{k-1}+1=\frac{4}{3}(4^{k-1}+\frac{1}{2})$$.

After kth iteration  

|          |n         |current position|furthest checked position left|furthest checked position right|
| :------: | :------: | :------: | :------: | :------: |
|approach 1|$$4^k-1$$ |$$4^k-1$$|          |          |
|approach 2|          |          |          |          |
|approach 3|          |          |          |          |
