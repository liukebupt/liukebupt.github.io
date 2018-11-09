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
After kth iteration
|          |n         |          |          |
| :------: | :------: | :------: | :------: |
|approach 1|$$4^k-1$$ |          |          |
|approach 2|          |          |          |
|approach 3|          |          |          |

