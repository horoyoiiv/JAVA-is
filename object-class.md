

# object class in java  


  * present in **java.lang** package  
  * Every class in java is directly or indirectly derived from **Object class**.  
  * Why is this needed ?  
  

## Methods of Object class  
  * This means every class in java can use these method directly or override it.  
  

### 1. toString()  
  * Convert an object to String.  
  * output : Classname + @ + unique id(hashcode) of the generated object.  

```java
    public String toString() {
        return getClass().getName() + "@" + Integer.toHexString(hashCode());
    }
```

* Example  
**It is always recommended to override toString() to get our own string**  



### 2. hashCode()  
  * For every object, JVM generates a unique number which is hashcode.  
  * This is not an address, but using the address to generate the hashdoe.  
  * **hashCode() method is native cus it is impossible to find address of the object**  
  * **So it uses native languages like C/C++ to find the address of object.**  
  
  
```java
public native int hashCode();
```


### 3. equals(Object ojb)  
  * This is simply comparing two obejcts based on the address.  
  * check the obejct references.  
  
  
```java
    public boolean equals(Object obj) {
        return (this == obj);
    }
```
#### ==  vs equals  
  
  * **==** : just address based comparision.  
  * **equals** : comparision based on how it is implemented.  
  * **equals를 그대로 쓰면 ==와 동일하다, 주소값 비교연산**  
  * **하지만 각 클래스가 이를 overriding한다면 그것에 따라 결과가 달라진다.**  
  
  
  
  

### 4. getClass()  


### 5. finalize()  

