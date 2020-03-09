
## 1. An Object in Java  
  * An entity that has **state** and **behavior** is known as an object.  
  * **new keyword** is used to allocate memory at runtime.  
  * All objects in JAVA get memory in HEAP memory area.  
  * Reference type variable to indicate the object in HEAP is allocated in STACK.  
  
  
## 2. Constructor  
  * This method is used to **initialize the object**.  
  * Every time an object is created using the new() keyword, at least one constructor is called.  
  * If there is no constructor, **Java complier** provides **default constructor** at compile time.  
  
  
#### 2.1. No return value  
  * If there is a return statement in a contructor, compile error.  
  
#### 2.2. Copy constructor  
  * There is no copy contructor like c++ in java.  
  * But there are many ways to do so.  
  
  **1. By contructor**  

```java
class Student{
  int age;
  String name;
  
  Student(Student s2){
    this.age = s2.age;
    this.name = s2.name;
  }
  
}

~~~
Student s1 = new Student();
Student s2 = new Student(s1);
```
  
  **2. By clone()**  
  
  
  
