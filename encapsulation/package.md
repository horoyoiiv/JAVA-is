
# Encapsulation  
  * Encapsulation is one of the properties of OOP.  
  * It has two aspects.  
  1) Binding the related data and behavior together in a single unit.  
  2) Hiding details.  
  

# package  

  * to encapsulate a group of classes, sub packages and interfaces.  
 
 
## 1. package names are similiar with directory structure.  

```java
package university.skku;

public class Student{
    public static void main(String args[]){
        System.out.println("Hello WOrld");
    }
}
```

```
javac -d . Student.java
```
The -d switch specifies the destination where to put the genearated **class file**.  


![스크린샷, 2020-03-11 19-18-42](https://user-images.githubusercontent.com/34915108/76406499-29442a00-63cd-11ea-96e2-8062c90d180f.png)
  

Run :  
```
java university.skku.Student
```


## 2. complie the package  

```
javac -d . *.java
```

![스크린샷, 2020-03-11 19-18-42](https://user-images.githubusercontent.com/34915108/76406499-29442a00-63cd-11ea-96e2-8062c90d180f.png)  


## 3. sub package  
  * package inside the package is called the subpackage.  
  
```java
package java.lang.~~~
```
 lang is a sub package of java package.  
 
 
## 4. access to the package  

#### 1. import package.*; or import package.classname;   
  * all the classes and interfaces are accessible but **not subpackage**.  
  
```java
package animal;

import university.*;

public class Dog{
  Student std;
  Dog(Student std){
    this.std = std;
  }
```
This is an example of compile time error.

```java
package animal;

import university.skku.*;
or
import university.skku.Student;

public class Dog{
  Student std;
  Dog(Student std){
    this.std = std;
  }
```

## 5. Types of packages  

### 1. built-in package  
  
  
### 2. user-defined package  
  
 
