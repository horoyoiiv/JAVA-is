  
  
  
 # DataInputStream & DataOutpuStream  
 
 
 ## Before  
  * java.io 객체들은 데코레이터 패턴으로 구현되어 있다.  
  


#### 1. 먼저 파일 객체를 생성한다.  
```java
File file = new File("text.txt);
```

#### 2. 이 파일 객체를 fos에 넘겨준다.  


```java
File file = new File("text.txt);

FileOutputStream fos = new FileOutputStream(file);
```

fos 객체를 대상으로 **바이트 단위의 쓰기**가 가능하다.  
```java
fos.write(65);
```

실제로 이 수준의 클래스는 아래와 같은 메서드만 제공  
```java
int read(): Reads the next byte of data from this input stream.
int	read​(byte[] b)	: Reads up to b.length bytes of data from this input stream into an array of bytes.
int	read​(byte[] b, int off, int len)

```

#### 3. DataOutStream  
 * 바이트 단위의 쓰기를 넘어서 **자바의 Primitive 형의 쓰기**까지 지원해주는 클래스  

### 그래서 데코레이터 패턴이다. 기능이 제한된 객체를 다른 객체의 생성 시점에 넘김으로써 새로운 기능이 동적으로 추가됨...!  


 * readInt()와 같이 primitive 타입을 바로 읽을 수 있는 메서드를 제공.  
 
```java
File file = new File("text.txt");

FileInputStream fis = new FileInputStream(file);

DataInutStream dis = new DataInputStream(fis);

dis.readInt();
dis.readBoolean();
dis.readUTF();
등등...
```


```java
int	read​(byte[] b)	
int	read​(byte[] b, int off, int len)	
boolean	readBoolean()	
byte	readByte()	
char	readChar()	
double	readDouble()	
float	readFloat()	
int	readInt()	
String	readLine()	Deprecated.
long	readLong()	
short	readShort()	
int	readUnsignedByte()	
int	readUnsignedShort()	
String	readUTF()	
```
 
 * 실제로의 동작방식  
 
```java
DataOutStream dos = ~;
dos.writeInt(77);
```
 dos는 FileOutputStream을 감싸고 있기에 write()을 사용하여,  
 Int 4byte이므로 4번 byte를 쓴다.  
 
 


## 4. ObjectOutputStream  

  * 기본형에서 더 나아가 객체 자체를 저장한다.  
  
  
  * 이 경우 쓰려고 하는 객체는 serializable을 구현해야 한다.  
  
```java
            File file2 = new File("to.txt");
            
            FileOutputStream fos = new FileOutputStream(file2);
            
            ObjectOutputStream oos = new ObjectOutputStream(fos);

            oos.writeObject(user);

```

```java
            File f3 = new File("to.txt");
            FileInputStream fis3 = new FileInputStream(f3);
            
            ObjectInputStream ois3= new ObjectInputStream(fis3);

            User u2 = (User)ois3.readObject();

```

