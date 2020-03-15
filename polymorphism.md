
[Ref](https://www.geeksforgeeks.org/polymorphism-in-java/)  

# Polymorphism  
  * means having many forms.  
  * 동일한 코드조각이 그떄그때 다르게 행동하는 것.  
  
  * two types of; complie time polymorphism and runtime polymorphism.  
  * **complie time polymorphism** : achieved by **overloading**  
  * **runtime polymorphism** : achieved by **overriding**  

## Why is it needed?  

```java
ArrayList<Human> humanList = ~~~;

for(Human h : humanList){
    h.run();
}
```

## complie time polymorphism  

  * method overloading  
  * same method name with different numbers of parameters or types.  
  
## runtime polymorphism  
  * If subclass has the same method as declared in the parent class, it is method overrideing.  
  * **method overriding is used for runtime polymorphism.**  
  
### method overriding  
  * static method can not be overrided.  
  
  
## Static method overriding.  
  * It doesn't work because statics are resolved at compile time.  
  
```java
class Parent{

  static void hello(){
    System.out.println("Hello Parent");
  }
}

class Child extends Parent{

  static void hello(){
    System.out.println("Hello Parent");
  }
}
```

```java
Parent p = new Child();
p.hello();     // Hello Parent'
```

  
  
 
 
