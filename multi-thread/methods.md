

# sleep  

```java
public static void sleep(long miliseconds) throws InterruptedException  
```

```java
@Override
public void run(){
  try{
    Thread.sleep(1000);
  }catch(InterruptedException e){
    e.printStackTrace();
  }
}
```


# start twice  
  * It is never legal to start a thread more than once.  
  
```java
Thread t1 = new Thread(new Do());
t1.start();
t1.start();
```

```java
java.lang.IllegalThreadStateException
```


# Join  
  * wait until the specific thread is terminated.  
  
```java
        Thread t1 = new Thread(new Test(1));
        Thread t2 = new Thread(new Test(2));
        Thread t3 = new Thread(new Test(3));
        

        t1.start();
        t2.start();
        try{
            t1.join();
            t2.join();
        }catch(Exception e){}
        // execute after t1, t2 are dead.  
        t3.start();

```
 


