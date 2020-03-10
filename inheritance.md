

# Inheritance In JAVA  

  * Inheretance is a mechanism in which one object acquires all the **properties** and **behaviors** of a parent object.  
  * you can create new classes that are built upon existing classes.  
  * **reuse** the code or even add new code.  
  
  * Mainly for **reusability**.  

## No multiple inheritance  
  * to eliminate the **Ambiguity**.  
   
```java
class A{
  void msg(){}
}

class B{
  void msg(){
}

class C extends A, B{
}

~~~
C c = new C();
c.msg();        //  which msg method would be invoked?

```
