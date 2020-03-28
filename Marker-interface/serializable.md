

# Serializable  


## What  

  * Convert the state of an object into a byte stream.  

## Why?  

  * We can send the serialized data over the network.  
  * We can save this byte stream in DB or as file.  
  
## How  
  * implement the **java.io.Serializable**  
  

## Points  

#### 1. Only non-static member is serialized.  
#### 2. Static member and transient member is not serialized.  
#### 3. Constructor is never called when an object is deserialized.  


## Do it  

```java
class User implements Serializable {
    private String name;
    private int age;
    private transient int password;
    //private Pocket;

    User(){
        this.name = "hello";
        this.age = 123;
        this.password = 44444;
        
    }

    public String toString(){
        return name+", "+age+ ", "+password; 
    }
}

```


* **FileOutputStream** and **ObjectOutputStream** are used.  
* Especially, ObjectOutputStream.writeObject(Object obj) and ObjectInputStream.readObject() are used.  

```java
        User user = new User();

        System.out.println(user);
        
        String filename = "data.ser";
        FileOutputStream fos;
        ObjectOutputStream oos;
        try{
        
            fos = new FileOutputStream(filename);
            oos = new ObjectOutputStream(fos);

            oos.writeObject(user);
            
            oos.close();
            fos.close();
        }catch(FileNotFoundException e){
            e.printStackTrace();
        }catch(Exception e){

        }


```

## If Serializable interface is not implemented, the file created is corrupted.  
![스크린샷, 2020-03-29 03-22-15](https://user-images.githubusercontent.com/62331555/77830673-7403c700-716d-11ea-9cb5-6d3a0960793e.png)  


## When success  
![스크린샷, 2020-03-29 03-22-35](https://user-images.githubusercontent.com/62331555/77830671-723a0380-716d-11ea-8814-812d39831164.png)  





## Reversing  

```java
        try{
            FileInputStream fis = new FileInputStream(filename);
            ObjectInputStream ois = new ObjectInputStream(fis);

            user = (User)ois.readObject();

            ois.close();
            fis.close();
            
            System.out.println(user);

        }catch(Exception e){

        }
```


## If the member of an object is also from other class, the class should be implemented by Seri....  



```java
class User implements Serializable {
    private String name;
    private int age;
    private transient int password;
    private Pocket p;
```

```java

class Pocket implements Serializable{
    int money;
    String name;

    Pocket(){
        this.money = 123;
        this.name = "mooooney";
    }
}
```

