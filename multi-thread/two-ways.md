

## Thread in java  

* Threads can be created by using two ways :  

#### 1. Extends the Thread class  
#### 2. Implementing the Runnable interface  



## 1. Extends Thread  

  * java.lang.Thread  
  * override the **run** method.  
  * call **start** method to run the thread.  
  
  
```java

class Test extends Thread {
    int id;

    Test(int i){
        this.id = i;
    }

    @Override
    public void run(){
        
        for(int i=0; i < 100; i++){
            System.out.println(id + " : "+i );   
            
            try{
                //Thread.sleep(1000);
            }catch(Exception e){}
        }
    }
}

```


* use the start method to start the         thread.  
```java
Test t1 = new Test(1);
Test t2 = new Test(2);

t1.start();
t2.start();         
```

## Why run() and start() ?  

 * When we call the start() method, internally run method is called.  
 [Ref](https://javarevisited.blogspot.com/2012/03/difference-between-start-and-run-method.html)  
 
 
 * When program call the **start()**, a **new thread** is created and run() method is executed in new thread.  
 * While if you call the **run()**, no new thread is created and run() is executed on **Curren thread**.  
 
 
 
### So the result of below code is...    
 ```java
Test t1 = new Test(1);
Test t2 = new Test(2);

t1.run();
t2.run();   
 ```
 
 **Sequential Execution....!**  
 
 
 
 
 
 ## 2. Implements Runnable interface  
 
  * java.lang.Runnable    
  * override the **run** method.  
  * call **start** method to run the thread.  
 
#### Difference with Extends Thread  

 * a class which implements the interface should be passed into **Thread class**.  
 * Then, the Thread object call the start() method.  
 
 
 ```java
 
class Test implements Runnable {
    int id;

    Test(int i){
        this.id = i;
    }

    @Override
    public void run(){
        
        for(int i=0; i < 100; i++){
            System.out.println(id + " : "+i );   
            
            try{
                //Thread.sleep(1000);
            }catch(Exception e){}
        }
    }
}

 ```

```java
        Test t1 = new Test(1);
      
        Thread thread1 = new Thread(t1);
        Thread thread2 = new Thread(new Test(2));
        
        
        thread1.start();
        thread2.start();
 ```
 
 
 
 
 ## Thread vs Runnable  

[Very good web-site](https://techdifferences.com/difference-between-thread-class-and-runnable-interface-in-java.html)  
 
 #### 1) When we extend Thread class, then we can not extend any other class.  
 * Because java doesn't allow multiple inheritance.  
 
 #### 2) When we extends Thread class, we can use another inbuilt method like yield(), interrupt() etc.  
 
 
 #### 3) Loose coupling :  
 
   * Using the runnable, the object is passed to the Thread class.  
   * So **Composition** relation is created.  
   * **the Thread code itself is separted from the job of the thread**.  
    - the job here is MyDoing class which implements runnable.  
    
 ```java

// when using the interface.
Thread t1 = new Tread(new MyDoing());
t1.start();

// when using the thread class.
MyDoing mydoing = new MyDoing();
mydoing.start();
```
 
 #### 4) Memory Efficiency  
 
   * Multiple threads share the same object...!  
   
   * Only one MyDoing object is created.
```java
//When using runnable 

MyDoing mydoing = new MyDoing();

Thread t1 = new Thread(mydoing);
Thread t2 = new Thread(mydoing);
Thread t3 = new Thread(mydoing);
Thread t4 = new Thread(mydoing);

t1.start();
t2.start();
t3.start();
t4.start();
```
   
 * If using thread class, each thread creates a unique object.  
 
```java
//When using runnable 

MyDoing t1 = new MyDoing();
MyDoing t2 = new MyDoing();
MyDoing t3 = new MyDoing();
MyDoing t4 = new MyDoing();

t1.start();
t2.start();
t3.start();
t4.start();
```



