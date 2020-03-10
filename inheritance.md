

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

# Has-a  

  * If a class has a entity reference as a member field, it is known as Has-a relationship.  
  * ojbect의 lifetime동안 IS-A 관계가 유지되지 않는다면 HAS-A 관계로 사용.  
  * 어쩋거나 둘 다 코드의 재사용 을 위함.  
  
  
  

## Assosication  
  * composition and aggregation are two forms of association.  
  * composition is much stronger than aggregation.  
  0.325
## Composition  
  *  
  
```java
class A{
 B b;
 A(){
   b = new B();
 }
}
```
  
## Aggregation  
  * both the entities can survive indivisually.  
  
```java
class A {
 B b;
 A(B b){
   this.b = b;
 }
}

```
  
