


## FileInputStream

 * ~~stream 에 대한 read 연산은 하나의 byte씩 읽어온다.  
 
 
```java
            FileInputStream fis = new FileInputStream("hello.txt");
            
            int d = fis.read(); // read a byte of data
            
            System.out.println((char)d);
            
            d = fis.read(); // read a next byte of data
            System.out.println((char)d);
            
```

 * EOF 시 -1을 반환  
 * int type으로 반환되면 char로 캐스팅  
 * byte 가 int로 반환되고, 이를 char로 캐스팅  
 
```java
            int r = 0;
            
            while( (r = fis.read()) != -1){
                System.out.println((char)r);              
            }
```


## Read and Wrtie bytes  
  * fis에서 한 바이트씩 읽어 fos에 한 바이트씩 쓴다.  
  
```java
            FileInputStream fis = new FileInputStream("from.txt");
            FileOutputStream fos = new FileOutputStream("to.txt");

            int r = 0;

            while( (r = fis.read()) != -1 ){
                fos.write((byte)r);                
            }
            
            fis.close();
            fos.close();
```


## FileReader  

 * byte가 아닌, char로 스트림을 다룬다.  
 
```java
             FileReader fr = new FileReader("hello.txt");
            

             char[] c = new char[13];

             fr.read(c);

             System.out.println(String.valueOf(c));
```


## FileInputStream 과 FileReader  
 * **InputStream** 과 **Reader**는 거의 동일하지만 전자는 byte, 후자는 char** 단위로 처리한다.  
 
```java
                     byte [] b = new byte[10];

 

                     try{

                                fis = new FileInputStream("r.txt");     

                                fis.read(b);

                                System.out.println(new String(b));
```

```java
                    char [] c = new char[10];

                    

                     try{

                                fr = new FileReader("r.txt");

                                fr.read(c);

                                System.out.println(new String(c));
```


## 데코레이터  

 * FileInputStream / FileReader  
 다음과 같이 단조로운 read 함수만 제공한다.  
![스크린샷, 2020-04-01 20-34-14](https://user-images.githubusercontent.com/62331555/78132928-870de400-7458-11ea-814c-e4404c306f15.png)  

 * FileOutputStream / FileWriter  
 다음과 같이 단조로운 write 함수만 제공한다.  
![스크린샷, 2020-04-01 20-34-48](https://user-images.githubusercontent.com/62331555/78132932-88d7a780-7458-11ea-9b45-8c18bdf6e7a2.png)


