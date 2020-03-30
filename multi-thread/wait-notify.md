

# wait and nofify in JAVA

## 1. Without these two.  

  * 특정 조건을 만족하느냐에 대한 쓰레드 간의 커뮤니케이션에서 Polling( spin-wait )이 초래됨.  
  * Polling이란 while을 계속 돌면서 특정 조건이 참이 되었는지 지속적으로 확인하는 것.  
  이는 CPU cycle을 낭비시킴.  
  


## 2. wait, notify, notifyAll  
  * 이러한 polling을 회피하기 위하여 자바에서는 위의 메서드를 제공.  
  * Condition variable을 직접적으로 제공해준다고 볼 수 있다.  
  
```c
pthread_cond_wait();
pthread_cond_signal();
pthread_cond_broadcast();
```

#### 이들은 조건에 대한 동기화 기법이다.  


## 3. Methods  

1) **wait()** : It tells the calling thread to give up the lock and go to sleep until some other thread enters the same monitor and calls notify().  

2) **notify()** : It wakes up one single thread that called wait() on the same object. It should be noted that calling notify() does not actually give up a lock on a resource.  
3) **notifyAll()** : It wakes up all the threads that called wait() on the same object.  



## 4. Example  

[코드 리뷰](https://www.geeksforgeeks.org/inter-thread-communication-java/)  

```java
import java.util.Scanner;

public class test{

    
    public static void main(String[] args) 
                                throws InterruptedException{
        
        final PC pc = new PC();

        Thread t1 = new Thread(new Runnable(){
            
            @Override
            public void run(){
            
                try{
                    pc.produce();
                }catch(Exception e){}

            }
        });


        Thread t2 = new Thread(new Runnable(){
           
           @Override
           public void run(){
                
                try{
                    pc.consume();
                }catch(Exception e){}
           }
               
        });
        
        t1.start();
        t2.start();

        t1.join();
        t2.join();
    }

    public static class PC{
        public void produce() throws InterruptedException{
            
            synchronized(this){ // c의 mutex lock과 달리, Object 자체에 lock을 걸어
                System.out.println("producer thread running");
                wait(3000);
                System.out.println("Resumed");
            }
        }

        public void consume() throws InterruptedException{
            
            Thread.sleep(1000);
            Scanner s = new Scanner(System.in);

            synchronized(this){
                System.out.println("Waiting...");
                s.nextLine();
               

                notify();
                Thread.sleep(2000);
                System.out.println("release the key");
            }
        }

    }
}
```
