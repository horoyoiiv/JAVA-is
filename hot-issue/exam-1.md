
# Exam one  

```java
class Parent{
    String val = "Parent Value";

    void hello(){
        System.out.println("Hello from parent");
    }
}


class Child extends Parent{
    String val = "Child value";

    @Override 
    void hello(){
        System.out.println("Hello from child");
    }

}
```


## expect the outputs.  

```java
Child c = new Child();
c.val;
c.hello();
```
<details>  

Child value  
hello from child

</details>


```java
Parent c = new Child(); // 업캐스팅 - (Parent)new Child() 생략된 것.
c.val;
c.hello();
```
<details>  

Parent value  
hello from child

</details>


```java
Child c = new Parent();
c.val
c.hello();
```

<details>  

Compile error 

</details>


```java
Child c = (Child)new Parent();  
c.val
c.hello();
```

<details>  
Child c = (Child)new Parent()에서 다음 에러 발생  
Runtime error : java.lang.ClassCastException  

</details>

```java
Parent p = new Child();
Child c = (Child)p;

c.val;
c.hello();
```

<details>  

Child value
hello from child
</details>

```java
Parent p = new Parent();
Child c = (Child)p;

c.val;
c.hello();
```

<details>  

Runtime Exception : java.lang.ClassCastException  
</details>


```java
Parent p = new Parent();
if(p instanceof Child){
  Child c = (Child)p;
  c.val;
  c.hello();
}
```

<details>  

nothing...  
</details>
