
## 1. try catch  
  * try block is used to enclose the statements that might occur an exception.  
  * try block should be followed by catch or finally block.  
  
```java
        try{  
            int data=50/0; 
        } 
        catch(ArithmeticException e){  
            System.out.println(e);  
        }  
        System.out.println("rest of the code");  
        }  
```
  
## 2. Examples  

  * ArithmeicException extends RuntimeException class which also extends Exception class.  
  
```
java.lang.Object
    java.lang.Throwable
          java.lang.Error
              java.io.IOError      
          java.lang.Exception
                java.lang.RuntimeException
                     java.lang.ArithmeticException
```  


##### 1. 
```java
int a = 10;
int b = 0;

try{
  System.out.println(a/b);
}catch(Exception e){
  System.out.println(e);
}
```

```java
try{
  System.out.println(a/b);
}catch(RuntimeException e){
  System.out.println(e);
}
```

```java
try{
  System.out.println(a/b);
}catch(ArithmeticException e){
  System.out.println(e);
}
```

##### 2. handling the exception with a different type of exception class.  
  * Then, it is terminated by the exception.  
```java
try{
  System.out.println(a/b);
}catch(ArrayIndexOutOfBoundsException e){
  System.out.println(e);
}
```  


## 3. What if not handle the exception?  
  * First JVM checks whether the exception is handled or not.  
  If not handled, a default exception handler works.  
  
  1) prints out exception description.  
  2) prints the **stack trace** (Hierachy of methods where the exception occured)  
  3) causes the program to terminate.  
  
```java

Exception in thread "main" java.lang.ArithmeticException: / by zero // descriptions 
	at ExceptionLEGO.method_boo(ExceptionLEGO.java:21)                // stack trace 
	at ExceptionLEGO.method_foo(ExceptionLEGO.java:13)
	at ExceptionLEGO.main(ExceptionLEGO.java:8)
```
  
  
## 4. multiple catch blocks.  
  * **At a time, only one excetion occurs and only one catch block is executed.**  
  * All catch blocks must be ordered from most specific to most general.  
  
#### 4.1. Examples  
```java
           try{    
                int a[]=new int[5];    
                a[5]=30/0;    
               }    
               catch(ArithmeticException e)  
                  {  
                   System.out.println("Arithmetic Exception occurs");  
                  }    
               catch(ArrayIndexOutOfBoundsException e)  
                  {  
                   System.out.println("ArrayIndexOutOfBounds Exception occurs");  
                  }    
               catch(Exception e)  
                  {  
                   System.out.println("Parent Exception occurs");  
                  }        

```

Output :
```
Arithmetic Exception occurs
rest of the code
```

#### 4.2. If not provie the corresponding exception type.  
```java
           try{    
                String s=null;  
                System.out.println(s.length());  
               }    
               catch(ArithmeticException e)  
                  {  
                   System.out.println("Arithmetic Exception occurs");  
                  }    
               catch(ArrayIndexOutOfBoundsException e)  
                  {  
                   System.out.println("ArrayIndexOutOfBounds Exception occurs");  
                  }    
               catch(Exception e)  
                  {  
                   System.out.println("Parent Exception occurs");  
                  }             
               System.out.println("rest of the code");    
    }  
```

#### 4.3. Not complied examples  
```java
        int a = 10;
        int b = 0;

        try{
            int[] arr = new int[5];
            arr[10] = a / b;

        }catch(Exception e){
            System.out.println("exectpion ");
        }
        catch(ArithmeticException e){
            System.out.println(e);
        }
        catch(ArrayIndexOutOfBoundsException e){
            System.out.println(e);
        }
 
```
