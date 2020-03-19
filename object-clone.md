

# Clone method    

 * Object cloning refers to creation of **exact copy of an object**.  
 * It creates a new instance of the class of current object.  
 * and initializes all its fields with **exactly the contents of the corresponding fields of this object.  
 
 
## 0. Assignment operator  
  * In java, there is no operator to create copy of an object.  
  * Unlike C++, if we use assignment operator, this will create a copy of **reference variable**.  
  
```java
Test ob1 = new Test();
ob1.x = 100;

Test ob2 = ob1;
ob2.x = 123;
 
System.out.println(ob1.x); // 123
System.out.println(ob2.x); // 123
```



## 1. Clone()  

#### 1. clone() method is defined in Object class.  

```java
class Object{
  
  protected native Object clone() throws CloneNotSupportedException;

}
```

#### 2. how to use  

  1. implements cloneable interface  
  * Cloneable이 없으면, clone() 호출 시 CloneNotSupportedException 발생  
  
```java
class Test implements Cloneable{

}
```

  2. @Override the clone method  
  
```java
public Test clone() throws CloneNotSupportedException{
  return (Test)super.clone();
}
```


  3. example
  
```java
class Test implements Cloneable{
    int a;
    int b;

    Test(int a, int b){
        this.a = a;
        this.b = b;
    }

    public Test clone() throws CloneNotSupportedException{
        return (Test)super.clone();
    }
}
```

```java
        Test a1, a2 = null;
        
        a1 = new Test(1, 2);
        a1.a = 123;

        try{
            a2 = a1.clone();
        }catch(Exception e){
            System.out.println(e);
        }
        
        a2.a = 444;
        System.out.println(a1.a);    // 444
        System.out.println(a2.a);    // 123     
```


#### 3. 깊은 복사 vs 얇은 복사  

1. clone호출 시 기본적으로 각 필드를 복사하는데  
그 필드가 참조형인 경우 참조형의 값을 복사하기에 **얇은 복사**  
 * super.clone() 은 default swallow copy  
 

```java

class Test implements Cloneable{
    int a;
    int b;
    int[] arr = new int[3];

    Test(int a, int b){
        this.a = a;
        this.b = b;
    }

    void setArr(int a, int b, int c){
        arr[0] = a;
        arr[1] = b;
        arr[2] = c;
    }
    
    void getArr(){
        System.out.println(arr[0]);
    }

    public Test clone() throws CloneNotSupportedException{
        return (Test)super.clone();
    }
}
```


```java
        Test a1, a2 = null;
        
        a1 = new Test(1, 2);
        a1.a = 123;
        a1.setArr(1,2,3);

        try{
            a2 = a1.clone();
        }catch(Exception e){
            System.out.println(e);
        }
        
        a2.a = 444;
        a2.setArr(10,20,30);

        System.out.println(a1.a);
        System.out.println(a2.a);          
        
        a1.getArr();  // 10 20 30
        a2.getArr();  // 10 20 30
    }
```


2. 깊은 복사를 위해서 clone() 메서드 안에서 새로운 필드 객체를 만들어서 반환  

```java
    public Test clone() throws CloneNotSupportedException{
        Test copyObj = (Test)super.clone();
        
        copyObj.arr = new int[3];    // 새로운 객체 생성
        for(int i=0; i < 3; i++){
            copyObj.arr[i] = arr[i];
        }

        return copyObj;
    }
```


