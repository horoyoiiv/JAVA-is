


[jvm all in one](https://www.youtube.com/watch?v=ZBJ0u9MaKtM)  
[html](https://www.guru99.com/java-virtual-machine-jvm.html)  


# JVM  
  
  * provides runtime environment for java applications.  
  * Converts Java bytecode into machine languages.  
  
  * This is mainly composed of subsystems like **Class loader**, **Memory Area** and **Excution Engine.**  
  
## Befroe JVM works  

  * 1) Java code is compiled into **bytecode** by **javac command.**  
  * 2) Bytecode which is **.class file** is loaded by **class loader.**  


# Class loader   

### 1. Linking between files is performed at runtime by JVM's class loader.  
  * C/C++과 달리, javac를 통해선 링킹이 되기 전 상태의 bytecode가 생성된다.  
  ![스크린샷, 2020-03-17 14-45-57](https://user-images.githubusercontent.com/34915108/76825734-0e0a6c00-685e-11ea-822f-be5f8fa27ae7.png)
  
  * 그리고 이 바이트코드는**Symbolic references**를 통해 이후의 링킹정보를 나타낼 뿐이다.  
  
  * used for loading class files.  
  * three steps : **load**, **linking** and **initialization**.  
  
  ![스크린샷, 2020-03-17 14-55-00](https://user-images.githubusercontent.com/34915108/76826239-4cecf180-685f-11ea-9922-93814f62a62b.png)  
  

### 1. Loading stage   
  * import문 등으로 클래스가 동적으로 로드되는 것이 아닌,  
  * 실제로 그 코드가 실행되는 시점에 class 정보가 필요하면 그 때 동적인 로딩이 실행된다.  
  * 어플리케이션 실행 시, 사용자의 bytecode만 로드하는 것이 아닌, rt.jar과 같은 라이브러리도 같이 load한다.  
  * **rt.jar** stands for **r**un**t**ime JAR and contains the bootstrap classes, I mean all the classes from Core Java API.  
  
  * Read the bytecode from file system and load it into **method area.**  
  * method area : stores class structure like the code for methods.  


### 2. Linking stage  

  * verify :  
  * prepare : static varibles are allocated into memory.   
  * resolve : resolve the symbolics for actual linking.  
  
### 3. Initialization  
  * memory allocated static variables are initialized with actual values.  
  
  

# Method area  

 
### 1) Method area 
  * 클래스가 로드되면, 이 영역에 프로그램의 흐름을 구성하는 바이트코드가 저장.  
  * Runtime Contant Pool :  
  * 저장되는 정보 : 필드(이름/타입/접근제어자), 메서드(이름, 리턴타입, 매개변수, 접근제어자)  
  
  
### 2) Heap area  
  * 생성된 객체를 저장하는 공간  
  * new연산자를 통해 생성된 객체 혹은 배열이 저장되는 곳  
 
### 3) Stack area  
  * 각 쓰레드마다 가지는 고유한 영역  
  * 기본적인 메모리 동작 방식에서 stack frame과 동일하다.  
  * 매개변수, 지역변수 등등이 저장  
  
### 4) PC Register  
  * 각 쓰레드마다 Program counter를 저장한다.  

### 5) Native Method stack  
  * 자바언어가 아닌 다른 언어에서 제공되는 메서드를 저장  
  


# Execution Engine  
![스크린샷, 2020-03-17 16-29-56](https://user-images.githubusercontent.com/34915108/76832400-98f26300-686c-11ea-85f1-8c858c2a7b1c.png)  
  
  * Interpreter : It interprets the bytecode line by line then executes.  
  
  * JIT(Just-In-Time Compiler) : 여러번 수행되는 코드(메서드)인 경우 매번 인터프리팅하는 것이 비효율적이다.  
  * **JVM 내부적으로 해당 메서드가 얼마나 자주 수행되는지 체크한 후 일정 정도를 넘을 때만 네이티브 코드로 컴파일을 수행한다.**  
  * 이후 그 코드는 인터프리팅을 거치지 않고 바로 네이티브 코드로서 실행된다.  
  *
  
  
  
  
  
  
 
