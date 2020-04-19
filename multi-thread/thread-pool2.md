

## Thread pool  

#### How to use a thread pool in java  

```java
        ExecutorService executorService = Executors.newSingleThreadExecutor();
        
        executorService.execute(new Runnable(){            
            @Override
            public void run(){
                System.out.println("task1");
            }
        });

        executorService.shutdown();
```


1. Executors 클래스에서 static factory 생성자를 통해 만들고자 하는 유형의 ThreadPool을 생성한다.  

#### 1. public static ExecutorService newSingleThreadExecutor()   
하나의 worker thread를 가진 thread pool을 반환  

#### 2. public static ExecutorService newFixedThreadPool(int nThreads)   
재사용 가능한 nThreads 개수의 워커 쓰레드를 가지는 풀을 반환.  

1. 모든 쓰레드가 사용 중인 경우 task는 queue에 들어간다.  
2. 모든 쓰레드는 **shutdown()**이 호출되기 전까지 살아있다.  

#### 3. public static ExecutorService newCachedThreadPool()  

1. 필요한만큼 쓰레드가 생성된다.  
2. 60초 동안 idle하면 pool에서 제거된다.  
3. 그전에 다시 사용할 수 있다.  


#### 4. public static ExecutorService newWorkStealingPool()  

1. 실제 parallelism 정도에 따라(CPU 수) 쓰레드를 생성한다.  
2. **여러 개의 task 큐**를 사용하여, 경합을 줄임.  
3. 그렇기에 순서는 보장되지 않는다.  























