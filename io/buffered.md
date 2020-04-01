

# Buffered....  

  * 매번 읽을 때매다, 매번 쓸 때마다 디스크에 접근해야 할까?  
  
### 한번에 읽어서 저장해두고, 모았다가 한번에 쓰자  


## This is BUFFER.  


## BufferedOutputStream  

* write 시 메모리 buffer에 저장해두었다가  
 close 혹은 flush 혹은 predefine 된 buffer 크기 꽉차면 그 때서야 write 수행.  

* 디폴트 버퍼 사이즈는 512.  

```java
            File file = new File("to.txt");
            
            FileOutputStream fos = new FileOutputStream(file);
            
            BufferedOutputStream bos = new BufferedOutputStream(fos, 1024);
            
            bos.write("aaaaaaaaaaa".getBytes());
```

## BufferedInputStream  
  * 역시나 한번에 디스크에서 읽어와 메모리에 상주시키고, 메모리에서 읽는다.  
  


## BufferedWriter  
  * 바이트가 아닌, char 단위의 쓰기  
  
```java
            File file = new File("to.txt");
            FileWriter fw = new FileWriter(file);
            BufferedWriter bw = new BufferedWriter(fw);

            bw.write("HEllo world");
            
            bw.close();
```
