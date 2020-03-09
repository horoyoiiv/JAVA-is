
## Exception propagation.  

  * An exception is first thrown from the top of stack fram and **if it is not caught,**  
  **it drops down the call stack to the previos method.**  
  If not caught there, the exception again drops down to the previous method.  
  UNTIL it is caught.  
  
#### By default, unchecked exceptions are forwarded into calling chain.  



```java
    public static void main(String[] args){

        goo();
        System.out.println("result");
    }

    
    static void foo(){
        System.out.println("foo start");
        int data = 50 / 0;
        System.out.println("foo end");
    }

    static void boo(){
        System.out.println("boo start");
        foo();
        System.out.println("boo end");
    }

    static void goo(){
        System.out.println("goo start");
        try{
            boo();
        }catch(Exception e){
            System.out.println(e);
        }
        
        System.out.println("goo end");
    }
```

Output :  
```
goo start
boo start
foo start
java.lang.ArithmeticException: / by zero
goo end
result
```
