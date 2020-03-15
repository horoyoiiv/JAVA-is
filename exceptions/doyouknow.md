
#### 1. What is the difference between checked and unchecked exceptions?  

 

#### 2. What happens behind the code int data=50/0;?  

#### 3. Why use multiple catch block?  

#### 4. Is there any possibility when finally block is not executed?  
 
  If using the "System.exit(0)"  

#### 5. What is exception propagation?  

#### 6. What is the difference between throw and throws keyword?  

#### 7. What are the 4 rules for using exception handling with method overriding?  

#### 8. What happens if there is no handler for the runtime exceptions?  
(Decribe the work flow of JVM)  
 
 
#### 9. What is the result of the following codes.  
 compile error; general exception class should be positioned at the end.  
 
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

#### 10. Can static method be overridden in JAVA?  


