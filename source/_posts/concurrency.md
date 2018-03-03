---
title: Java Collection 源码阅读2
date: 2017-07-10 21:40:38
tags:
- 技术
- Java
---

## Happen before

[https://stackoverflow.com/questions/14329064/synchronized-and-the-scope-of-visibility](https://stackoverflow.com/questions/14329064/synchronized-and-the-scope-of-visibility)

## Atomic

[http://www.jianshu.com/p/0f1b4ae625e5](http://www.jianshu.com/p/0f1b4ae625e5)

## Monitor/Condition

1.  Object, wait, notify, notifiyAll (the last two must be called when we get the object lock)
    
2.  ReentranceLock, Condition (the later one must be called when we get the reentrance lock). The condition use "LockSupport.park and unpark" to suspend thread and wakeup thread
    

## Lock and Sync

See [http://www.cnblogs.com/wanly3643/p/3835839.html](http://www.cnblogs.com/wanly3643/p/3835839.html)

Lock ---->  AbstractQueuedSynchronizer ---> setState to communicate between threads, put waiting threads to a waiting list, use park to suspend threads and unpark to wake up threads

ReentrantLock ----\> Sync/FairSync/NonFairSync

ReentrantReadWriteLock ---\> ReadLock/WriteLock, Sync/FairSync/NonFairSync

Semphore --\> Sync/FairSync/NonFairSync, allow limit number of share locking

## ConcurrentHashMap

[http://www.cnblogs.com/wanly3643/category/437878.html](http://www.cnblogs.com/wanly3643/category/437878.html)

1.  Use volatile
    
2.  Sync only in one bucket
    

## BlockingQueue

1.  They are using ReentrantLock and Condition to do syncing
    
2.  BlockingQueue use lock and condition to implement the consumer and producer scenario
    
3.  ArrayBlockingQueue needs one lock while LInkedBlockingQueue needs two
    
4.  See notes in "Collection and Map" for all BlockingQueue classes
    

## Thread State:

[https://www.geeksforgeeks.org/lifecycle-and-states-of-a-thread-in-java/](https://www.geeksforgeeks.org/lifecycle-and-states-of-a-thread-in-java/)

## Executor
![](/images/concurrency.png)
1.  How ThreadPoolExecutor controls the threads:

[http://www.jianshu.com/p/65da61177eed](http://www.jianshu.com/p/65da61177eed)

	Submit process:

	Submit(Runnable) ---> execute(FutureTask(runnable)) --> threadpool call runWorkers() --> FutureTask.run --\> FutureTask.finish --\> unpark(waiting client threads) --> worker thread continue to take task from workQueue

	ClientThread --\> FutureTask.get --> awaitDone --\> park(client thread), waiting to be unparked by FutureTask.finish

2.  How ScheduledThreadPoolExecutor works:

	Same as ThreadPoolExecutor, but use a DelayWorkQueue as workQueue, which as deplay polling task.

	DelayWorkQueue contains ScheduleFutureTask, which is a FutureTask that will can check the delayTime before each run and add itself back to workQueue if it is set to repeatly run.

	DelayWorkQueue is actually similar to PriorityQueue, which maintains a binary heap, which compare by each element's delay time.

## ForkJoinPool

See [http://www.bijishequ.com/detail/520567?p=37](http://www.bijishequ.com/detail/520567?p=37) for implementation detail

Some tips:

1.  The pool maintains an array of WorkQueue
    
2.  Each workQueue contains a ForkJoinThread, which is actually a thread can run to steal jobs and run its own taskQueue
    
3.  Each taskQueue is an array of ForkJoinTask, which is a FutureTask
    
4.  Each ForkJoinThread will get its own job from its queue using FILO, but steal job from other thread's queue using FIFO
