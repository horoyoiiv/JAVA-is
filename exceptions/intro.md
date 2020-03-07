[Ref](https://www.javatpoint.com/exception-handling-in-java)  


## 1. Why handling exceptions needed?  
 * To maintain a normal flow of executions.  


## 2. Hierachy of JAVA Exception classes  
  * **java.lang.Throwable class** is the root class which is inherited by two subclasses;   
 
  ![스크린샷, 2020-03-07 22-12-18](https://user-images.githubusercontent.com/34915108/76144139-c3039280-60c0-11ea-9093-daae365e6b79.png)  
  
  * Exception vs Error  
  
  **1. Error** :  it **cannot get recovered** by any handling methods.  
   ex) java.lang.StackOverflowError, OutOfMemoryError  
   
  **2. Exception** : it can get recovered by using try, catch and throw keywords.  
  
  * 2.1. **checked exception** : are the exceptions **that are checked at compile time.**   
    
    That is, if not properly handle the statement generating exceptions, it cannot be complied.  

```java
    public static void main(String[] args) { 
        FileReader file = new FileReader("C:\\test\\a.txt"); 
        BufferedReader fileInput = new BufferedReader(file); 
          
        // Print first 3 lines of file "C:\test\a.txt" 
        for (int counter = 0; counter < 3; counter++)  
            System.out.println(fileInput.readLine()); 
          
        fileInput.close(); 
    } 
```

Output : 
```
Exception in thread "main" java.lang.RuntimeException: Uncompilable source code - 
unreported exception java.io.FileNotFoundException; must be caught or declared to be 
thrown
```
  FileReader() can throw a checked exception FileNotFoundException.  
  readLine() and close() can throw checked exception IOException.  
  


  * 2.2. **unchecked exception** : are the exceptions that are not checked at compile time.  
  (In C++, all exceptions are unchecked.)  
  
  **The classes which inherit RuntimeException** are known as unchecked exceptions.  
  ex) ArithmeticException, NullPointerException, ArrayIndexOutOfBoundsException  
  
  
  ## 3. Common exceptions  
  
  1) ArithmeticException  
  ```java
  int a=50/0;//ArithmeticException  
  ```
  
  2) NullPointerException  
  ```java
  String s=null;  
  System.out.println(s.length());//NullPointerException  
  ```
  
  3) ArrayIndexOutofBoundsException  
  ```java
  int a[]=new int[5];  
  a[10]=50; //ArrayIndexOutOfBoundsException  
  ```
  
  
  
  
  
  
  
  
