

## finally block  

  * finally block is always executed whether exception occurs or not.  
   and exception is handled or not.  
   
  * **If you don't handle the exception, before terminating the program,  
  JVM executes the finally block**.  
  
  * It is used for closing the connection or file; cleanup  
  
#### examples  

```java
  try{  
   int data=25/5;  
   System.out.println(data);  
  }  
  catch(NullPointerException e){System.out.println(e);}  
  finally{System.out.println("finally block is always executed");}  
    System.out.println("rest of the code...");  
  }  
```

2. when exception occcurs and not handled  
  * finally block is executed and the program is terminated.  
  
```java
  try{  
   int data=25/0;  
   System.out.println(data);  
  }  
  catch(NullPointerException e){System.out.println(e);}  
  finally{System.out.println("finally block is always executed");}  
  System.out.println("rest of the code...");  
  }  
```

Output :  
```
finally block is always executed
Exception in thread main java.lang.ArithmeticException:/ by zero
```



#### finally examples  
  **the return statement in finally block means that the function is no problem.  
  
##### 1. return statement in a finally block **override** the result.  

```java
    System.out.println("result : "+getString());
    
    public static String getString(){
        String name;

        try{
            int data = 25 / 0;
            name = "try";            
            return name;
        }catch(NullPointerException e){
            System.out.println("catch ----");
        }finally{
            System.out.println("finally----");
            name = "finally";
            return name;
        }       
    }
```

Output :  
```
finally----
result : finally
```

##### 2. 

```java
    System.out.println("result : "+getString());
    
    public static String getString(){
        String name;

        try{
            int data = 25 / 0;
            name = "try";            
            return name;
        }catch(NullPointerException e){
            System.out.println("catch ----");
        }finally{
            System.out.println("finally----");
            name = "finally";
        }       
    }
```

Output :  
```
finally----
Exception in thread "main" java.lang.ArithmeticException: / by zero
	at ExceptionLEGO.getString(ExceptionLEGO.java:18)
	at ExceptionLEGO.main(ExceptionLEGO.java:9)
```
