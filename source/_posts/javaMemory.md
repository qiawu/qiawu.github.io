---
title: Java 内存知识
date: 2017-05-01 21:37:06
tags:
- 技术
- Java
---
1.  Integer contains meta data, not only the int value. The size is usually 4 times of int. An array is bigger since it needs to store the length
    
2.  HashSet is a wrapper of HashMap. An empty HashSet/HashMap already contains 16 objects (default size) and the size is more 100 bytes. Everytime we do "put", it will create new object "Entry".
    
3.  HashTable is synchronized and HashMap is not. Vector (also Stack) is synchronized and ArrayList is not.
    
<!--more-->
4.  Overhead of collections:
![](/images/javaMemory1.png)

5. Java application memory
![](/images/javaMemory2.png)

6. Compressed reference/compressed OOPs could reduce java heap usage when migrate from 32 bit to 64 bit platform. But it doesn't do the same for java native heap
    
7.  How heap and stack work together:
![](/images/javaMemory3.png)
