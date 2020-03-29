

# Thread pool in JAVA   


* Since the thread is already existing when the request arrives, the delay introduced by thread creation is eliminated.  

* JAVA provides **ThreadPoolExecutor** so one only has to implement the Runnable objects and send them to the executor to execute.  

* A object of **ExecutorService** is needed.  


# ExecutorService  


## 1. newFixedThreadPool  
  * creates a fixed size thread pool.  
  * if all threads are being currently run by the executor, then the peding tasks are placed in a queue.  
  * and are executed when a thread becomes idle.  
  

```java
import java.util.concurrent.ExecutorService; 
import java.util.concurrent.Executors; 


        // creates five tasks 
        Runnable r1 = new Task("task 1"); 
        Runnable r2 = new Task("task 2"); 
        Runnable r3 = new Task("task 3"); 
        Runnable r4 = new Task("task 4"); 
        Runnable r5 = new Task("task 5");       
          
        // creates a thread pool with MAX_T no. of  
        // threads as the fixed pool size(Step 2) 
        ExecutorService pool = Executors.newFixedThreadPool(3);   
         
        // passes the Task objects to the pool to execute (Step 3) 
        pool.execute(r1); 
        pool.execute(r2); 
        pool.execute(r3); 
        pool.execute(r4); 
        pool.execute(r5); 

```
![스크린샷, 2020-03-30 02-04-08](https://user-images.githubusercontent.com/62331555/77855337-c525c080-722a-11ea-8f82-557030bef6b4.png)  
