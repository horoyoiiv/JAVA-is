

# static block  

  * It is used to initialize the **static data member**.  
  * Is is excuted before the main method, at the time of classloading.  
  -> So Non-static variable is not used in this block.  
  
  
```java
class test{
    static int a;
    int b;
    static{
        a = 120;
        // b = 123; compile error 
        System.out.println("HEEEE"); // this is called before the main method runs.  
    }
    public static void main(String[] args){
        System.out.println("Hello World");
    }
}
```
