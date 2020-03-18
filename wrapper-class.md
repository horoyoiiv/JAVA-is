

# Wrapper class  

  * Wrapper class is a class whose **object wraps or contains a primitive data types**.  
  * That is, we can store the primitive data type into a wrapper class object.  
  * **AND These are immutables....!**  
  
```java
int n = 123;

// Deprecated API
Integer i1 = new Integer(n);
Integer i2 = new Integer(123);

// Autoboxing
Integer i3 = n;

System.out.println(i3);   // 123
```


  * **Autoboxing** :  The automatic conversion of primitive type into its corresponding wrapper class is known as autoboxing.  
  byte -> Byte  
  int -> Integer  
  long -> Long  
  float -> Float  
  boolean -> Boolean  
  double -> Double  
  short -> Short  
  
  ```java
  // it means that you can just use it like bellow.  
  int a = 123;
  Integer = 133; or a
  ```
  
  * **unboxing** : Conversion of wrapper class object into primitive type variable.  
  
  ```java
  Integer n = 123123;
  
  // int ni = n.intValue();
  int ni = n;   // compiler will write n.intValue() automatically  
  ```
  
  
  ## immutable  
  
    * When the value is setted into the object, it is impossible to change.  
    * **아래의 경우 A에 +1을 하지만 **새로운 Integer 객체가 생성된 것이었다...!**  
  
  ```java
  Integer A = 123;
  A++;
  
  System.out.println(A); // 124
  ```
  
  ### example  
    
  ```java
  Integer a = 123;
  Integer b = a;    // 래퍼런스 a 와 b는 동일한 힙 객체(123)를 가르킴
    
  a = a + 1000;     // a에 대한 뮤테이션 시도 후 래퍼런스 a는 a+1000 연산 결과를 포함하는 새로운 객체를 가르킴.  
  
  System.out.println(a);    // 1123
  System.out.println(b);    // 123 
  ```
  
  
  
