---
title: Java Collection 源码阅读1
date: 2017-06-01 20:48:48
tags:
- 技术
- Java
---

## How fast-fail happened in non-synced collections

(why modCount is not volatile: [http://www.jianshu.com/p/d9ee4b075d5a](http://www.jianshu.com/p/d9ee4b075d5a) )

## Differences between Iterator and ListIterator

-   Methods of Iterator (for list and set):
    
    -   hasNext()
        
    -   next()
        
    -   remove()
        

- Methods of ListIterator (only for list):

  -   add(E e)
    
  -   hasNext()
    
  -   hasPrevious()
    
  -   next()
    
  -   nextIndex()
    
  -   previous()
    
  -   previousIndex()
    
  -   remove()
    
  -   set(E e)
    

## ReentrantLock and synchronized

ReentrantLock has bettern performance and can cross method.

But synchronized is simple. So use it unless it is proven to be a problem.

## Enumeration and Iterator

Enumeration is faster than Iterator since Iterator may check fast fail while Enumeration don't. Iterator also support modification. Enumeration is usually used in synced collection.

## Queue

- Non-blocking

  - Dequeue (LinkedList and ArrayDeque are its children)
    
  - PriorityQueue (maintains a binary heap)
    

- Blocking (see notes on Concurrency)

  - ArrayBlockingQueue
    
  - LinkedBlockingQueue
    
  - PriorityBlockingQueue
    
  - DelayedWorkQueue (in ScheduledThreadExecutor, this is actually also a binary heap)
    
  - DelayQueue (very similar to DeplayedWordQueue)
    

## Set

HastSet 和 TreeSet  是Set的两个实现类。  
HashSet依赖于HashMap，它实际上是通过HashMap实现的。HashSet中的元素是无序的。  
TreeSet依赖于TreeMap，它实际上是通过TreeMap实现的。TreeSet中的元素是有序的。

## Synchronized collections

CopyOnWriteArrayList

Vector/Stack

HashTable

ConcurrentHashMap

Collections.synchronizedXXX()

## Difference between HashTable, ConcurrentHashMap and Collections.synchronizedMap
![](/images/collection.png)
The "scalability issues" for Hashtable are present in exactly the same way in Collections.synchronizedMap(Map) \- they use very simple synchronization, which means that only one thread can access the map at the same time.
