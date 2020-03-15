
# inner class   



## 1. Annoymous inner class  
  * A class that has no name is known as annoymous inner class.  
  * It can be used when overriding is needed.  
  * by two ways  
  
```java
    button1.setOnClickListener(new Button.OnClickListener() {
        @Override
        public void onClick(View view) {
            // TODO : click event
        }
    });
```

#### 1.1. extend of class  

```java
abstract class Person{
    abstract void eat();
}
```


```java
        Person p = new Person();  // 만 하면 compile 안됨.
        Person p = new Person(){
                @Override
                void eat(){
                    System.out.println("Eatting.....");
                }
            };
        
        
        p.eat();


```

**annoymous class is generated at runtime**  
```java
static clas Person$1 extends Person{
  void eat(){
    // what you've written...
  }
}
```


#### 1.2. implement of interface  

```java
class Button{
    
    private Clickable clickable;
    
    void setOnClickListener(Clickable clickable){
        this.clickable = clickable;
    }

    void click(){
        clickable.click();
    }

    
    interface Clickable{
        void click();
    }
}
```

```java
         Button btn1 = new Button();
         
         btn1.setOnClickListener(new Button.Clickable(){
                @Override
                public void click(){
                    System.out.println("Button is clicked...!");
                }
             });

         Button btn2 = new Button();
         
         btn2.setOnClickListener(new Button.Clickable(){
               @Override
               public void click(){
                    System.out.println("Red button is clicked.....??");   
               }
         });
         

         ArrayList<Button> btnList = new ArrayList<Button>();
         btnList.add(btn1);
         btnList.add(btn2);

         for(Button b : btnList){
            b.click();
         }
    }

```
