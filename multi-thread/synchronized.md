  


# Synchronized  

 * 공유 자원에 대한 여러 쓰레드의 접근을 제어  
 * synchronized block  
 * synchronized method  
 * **synchronized keyword**는 자바에서 임계 영역에 대한 상호 배제를 제공해주는 키워드.  
 
 
# Base  
 
 * 모든 Object는 lock을 가진다.  


## synchronized method  
  * 이 메서드가 호출되면, 그 쓰레드는 이 메서드의 오브젝트에 대한 락을 획득.  
  * 메서드 종료 시 락을 반환.  
  

```java

class test{
    public static void main(String arg[]){
        Table obj = new Table();          // shared object - monitor object.

        MyThread1 t1 = new MyThread1(obj);
        MyThread2 t2 = new MyThread2(obj);
        t1.start();
        t2.start();

        try{
            t1.join();
            t2.join();
        }catch(Exception e){}
        
        obj.result();
      
    }

}


class MyThread1 extends Thread{
    Table t;
    MyThread1(Table t){
        this.t = t;
    }
    
    @Override
    public void run(){
        t.printTable(50000);
    }
}


class MyThread2 extends Thread{
    Table t;
    MyThread2(Table t){
        this.t = t;
    }
    
    @Override
    public void run(){
        t.printTable(100000);
    }

}


class Table{
    int cnt = 0;

    synchronized void printTable(int n){  
        for(int i=1; i <= n; i++){
            cnt ++;
        }  
    }
    
    void result(){
        System.out.println(cnt);
    }
}
```
 * obj 객체의 printTable은 T1, T2에 의해 동시에 호출되나,  
 synchronized method에 의해 한명 씩 실행 가능해진다.  
 
 
## Syncrhonized block  

  * synchronized method는 method 전체를 임계영역으로 지정.  
  * method의 50줄 중 5줄만 보호하고 싶다면 그 범위를 줄일 수 있는 것이 block.  
  
```java
class Table{
    int cnt = 0;

    void printTable(int n){
        System.out.println("work start!!"); // 

        synchronized(this){
            for(int i=1; i <= n; i++){
                cnt ++;
            }  

            try{
                Thread.sleep(1000);
            }catch(Exception e){}
        }

        System.out.println("Wake up");
    }

}
```


## Tips  

  * 한 객체에 대하여 lock을 걸었다고 해서  
  syncrhonized method가 아닌 메서드의 호출까지 막히는 것은 아니다.  
  * 아래의 코드에서  
  * T1이 synchronized block을 실행하기 위해 lock을 획득해도,  
  이 블락을 실행하고 싶은 T2는 막히지만, result() 메서드를 실행할 T3는 막히지 않는다.  
  
```java
class Table{
    int cnt = 0;

    void printTable(int n){
        synchronized(this){
            for(int i=1; i <= n; i++){
                cnt ++;
            }  

        }
    }
    
    void result(){
        System.out.println(cnt);
    }
}
```


  * syncrhonized block에 this 객체 사용하고 감싼 코드의 범위가 메서드 전체라면  
  syncrhonized method와 차이가 없다.  
  
```java
class Table{
    int cnt = 0;

    void printTable(int n){
        synchronized(this){
            for(int i=1; i <= n; i++){
                cnt ++;
            }  

        }
    }
```

```java
class Table{
    int cnt = 0;

    synchronized printTable(int n){
            for(int i=1; i <= n; i++){
                cnt ++;
            }  
    }
```


* 다른 쓰레드에 의해 printTable 과 printTable2가 각각 호출되어도,  
monitor 객체가 동일하다면 lock 메커니즘이 동작한다.  

```java
    void printTable(int n){
        System.out.println("work start!!");

        synchronized(this){
            for(int i=1; i <= n; i++){
                cnt ++;
            }  
        }

        System.out.println("Wake up");
    }
    

    void printTable2(int n){
        System.out.println("work start!!");

        synchronized(this){
            for(int i=1; i <= n; i++){
                cnt ++;
            }  
        }

        System.out.println("Wake up");
    }    

```


* 반면, monitor 객체가 다르다면, lock 메커니즘은 동작하지 않는다.  

```java
    TempObject tmp = new TempObject();
    
    
    void printTable(int n){
        System.out.println("work start!!");

        synchronized(this){
            for(int i=1; i <= n; i++){
                cnt ++;
            }  
        }

        System.out.println("Wake up");
    }
    

    void printTable2(int n){
        System.out.println("work start!!");

        synchronized(tmp){
            for(int i=1; i <= n; i++){
                cnt ++;
            }  
        }

        System.out.println("Wake up");
    }    

```

* static method의 경우 객체가 없기에, class를 기준으로 lock을 사용.  
