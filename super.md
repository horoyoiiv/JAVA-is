 
 
# super keyword  

  * **super** is a reference varible like a **this** keyword.  
  * It is used to indicate immediate parent class object.  
  

## 1. used to refer immediate parent class instance variable.  
  * If parent and child have same name field.  
  * because of priority, to access the parent property, we need to use super.  
  
```java
class Animal{
  String color = "white";
}

class Dog extends Animal{
  String color = "black";
  
  void printColor(){
    System.out.println(color);        // blacok
    System.out.println(super.color);  // white
  }
}

```

## 2. used to invoke parent class method.  
  * If the child method is overriding the parent method.  
  
```java
class Animal{  
  void eat(){System.out.println("eating...");}  
} 

class Dog extends Animal{  
  void eat(){
    super.eat();
    System.out.println("eating bread...");
  }  
```
  
  
## 3. super() is used to invoke the parent class constructor  
  * reusing the parent constructor  
  * **super() is automatically added by compiler**  
```java
class Bike extends Some{
  Bike(){
  
  }
}

class Bike extends Some{
  Bike(){
    super();    // by compiler   
  }
}
```


```java
class Person{
  int id;  
  String name;  
  Person(int id,String name){  
    this.id=id;  
    this.name=name;  
  }  
}

class Emp extends Person{
  float salary;
  Emp(int id, String name, float salary){
    super(id, name);                      
    this.float = float;
  }
}
```
