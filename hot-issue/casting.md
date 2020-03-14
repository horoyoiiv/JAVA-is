
[Ref](https://mommoo.tistory.com/51)  

# Casting  
  * 캐스팅은 자식 객체를 부모 타입 래퍼런스로 가르키게 한다는 것이 아닌,  
  * 자식 타입의 래퍼런스를 부모 타입의 래퍼런스로 **바꾼다**라는 형 변환의 개념이다.  
  * 실제 객체와는 무관하게, 참조변수 간의 변환이 관심사인 것.  
  

# Upcasting  
  * 자식클래스 타입의 객체를 부모클래스 타입의 래퍼런스로 가리키게 하는 것.  
  
```java
Aniaml ani = new Dog();
```

# Downcasting  
  * 부모클래스 타입의 객체를 자식클래스 타입의 래퍼런스로 가리키게 하는 것.  
  
```java
Dog dog = new Animal(); // compile error  
```

```java
Dog dog = (Dog)new Animal();  // runtime error : classCastException
```

 * **다운캐스팅은 바꾸고자 하는 래퍼런스 타입의 객체가 먼저 업캐스팅이 발생한 후에 가능**  
```java
Animal anim = new Dog();

Dog dog = (Dog)anim;   // downcating
```
```java
Animal anim = new Animal();

Dog dog = (Dog)anim;    // runtime error 
```


# JAVA에서의 method 는 "C++과 달리" JVM에 의해 자동으로 Polymorphism이 적용된다.  
  * But compiler uses the runtime polymorhpism **only for methods.**  
  * member varaible is not the target.  
  
```java
class Parent{
  String val = "Parent!!";
  void hello(){
      System.out.println("Parent hello");
  }
}

class Child extends Parent{
  String val = "Child!!";
  void hello(){
      System.out.println("Child hello");
  }
}
```

  * Polymorphism which is the runtime dynamic binding applys only to method.  
```java
Parent p1 = new Child();

p1.val;         // Parent!!
p1.hello();     // Child hello;
```

# instaceof :  
  * 특정 래퍼런스 변수가 가르키는 실제 객체의 타입을 확인하기 위하여.  
  * 업캐스팅된 실제 객체의 맴버 변수에 접근하고 싶은 경우.  
  * reference varaible이 null이면 false 반환.  
  
### example    
```java
Parent p1 = new Child();
p1.val;         // Parent!!
p1.hello();     // Child hello;
```
  * 이 경우 val의 값에 대하여 child의 값을 가지고 오고 싶은 경우  

```java
Parent p1 = new Child();
p1.val;         // Parent!!
if(p1 instanceof Child){
  ((Child)p1).val;    // Child!!
}
```


```java
Parent p1 = new Child();
p1.val;         // Parent!!
// 물론 아래와 같이 해도 되지만, 아무래도 위험하다. - runtime error 나올 수 있음.
((Child)p1).val;    // Child!!
```


** A parent class data member is accessed when a referece of a parent type refers  
to a child object.**  
We can access child memeber data using type casting with help of instaceof.  


