
[Ref](https://www.codejava.net/java-core/the-java-language/what-is-upcasting-and-downcasting-in-java)
  

# upcating 과 downcating이 왜 필요한가...?

  * upcating : 다형성을 활용하여, 코드를 general하게 사용할 수 있게 된다. 또 쓸 수 있는 것 / 계속 추가 안해도 되는 것.  
  * downcating : upcasting하여 사용하는 도중에, subclass에서만 추가된 특정 메서드나, 멤버변수에 접근하고자 할 때,  
  

```java
package com.horoyoii.zoo;

public interface Mammal{
    public void eat();
    
    public void move();

    public void sleep();
}
```

```java
package com.horoyoii.zoo;

import com.horoyoii.zoo.Mammal;

public abstract class Animal implements Mammal{
    public void eat(){
        System.out.println("Eating...");
    }

    public void move(){
        System.out.println("Moving...");
    }   

    public void sleep(){
        System.out.println("Sleeping...");
    }
    
    public abstract void run();
}
```

```java
package com.horoyoii.zoo.model;

import com.horoyoii.zoo.Animal;

public class Dog extends Animal{
    public void bark(){
        System.out.println("dog bark...");
    }

    @Override
    public void eat(){
        System.out.println("Dog is eating...");
    }

    @Override
    public void run(){
        System.out.println("Dog is running away...");
    }

}
```

```java
package com.horoyoii.zoo.model;

import com.horoyoii.zoo.Animal;

public class Cat extends Animal{
    public void meow(){
        System.out.println("Cat is meeeeooow...");
    }

    public void run(){
        System.out.println("cat is running up");
    }

}
```



```java
package com.horoyoii.zoo;

import java.util.ArrayList;
import com.horoyoii.zoo.model.*;

class application{

    public static void main(String[] args){
        System.out.println("application is running");
        
        Dog dog = new Dog();
        Animal anim = dog;
        anim.eat();

        Mammal mam = anim;
        mam.eat();

        test_one();
        System.out.println("-------------------");
        test_two(new Dog());
        test_two(new Cat());
    }

    static void test_two(Animal anim){
        anim.eat();
        anim.move();
        anim.run();

        if(anim instanceof Dog){
            ((Dog)anim).bark();
        }else if(anim instanceof Cat){
            ((Cat)anim).meow();
        }
    }

    static void test_one(){
        ArrayList<Animal> aList = new ArrayList<Animal>();
        aList.add(new Dog());
        aList.add(new Cat());
        
        for(Animal anim : aList){
            anim.eat();
            anim.move();
            anim.sleep();
            anim.run();
        }

    }

}
```


