

# final  
  * final keyword is used to restrict the user!!  
  * This is mainly used in three context.  
  
  1) variable : stop value change.    
  2) method : stop method overriding.  
  3) class : stop class inheritance.  
  

## 1. final variable  
  * once it is assigned, it is never changed.  
  * If trying to change this, Compile time error occurs.  
  * final member field can be assigned in a constructor.  
  
```java
class Bike extends Some{
  final String type = "FIXED";
  final String type2;
  Bike(){
    type2 = "FIXED2";
  }
}
```


## 2. final method  
  * final method can not be overrided.  

```java
class animal{
    final void eat(){
        system.out.println("eating...");
    }
}

class dog extends animal{
  @Override
  void eat(){   // CT error  
  
  }
}
```

## 3. final class  
  * final class can not be extended.  
  
```java
final class Bike{

}  
  
class Honda1 extends Bike{  
  void run(){System.out.println("running safely with 100kmph");
}  
```

## 4. final parameter  
```java
void add(final int a){
  a += 2;   // error
}
```

## 5. Uninitialized final variables.  
  * a final variable which is not initialized at the time of declaration  
  is known as blank final variable.  
  * It can be initialized only in constructor.  
  
```java
class Student{
  final int id;
  
  Student(int id){
    this.id = id;
  }
}
```
   * static blank var is only assigned in a static block.  
   
```java
class A{
  static final int data;
  static{
    data = 50;
  }

}
```
