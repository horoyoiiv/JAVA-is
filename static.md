

## static  

  * The static keyword is used for **memory management**.  
  * apply it with variables, methods, blocks.  
    
## static variable    
  * static variable gets memory only once in the class at the time of class loading.  
  * It save memory space.  
  * static varialbe is allocated in **class area**.  
  
```java
Student{
  static String university = "SKKU";
  static int num = 0;
  
  Student(){
     num++;
  }
}
```
 
## static method  

  * a static method belongs to the class rather than the object.  
  * Invoked without the need for creating an instance.  
  * Static method only can access static varialbes.  
  
```java
class math{
  public static int add(int a, int b){
    return a + b;
  }
}

~~
math.add(1, 2);
```

  * this and super keywoards do not be used in static methods.  
  
  
