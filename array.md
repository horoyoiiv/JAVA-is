
# Array  

  * an array in java is an **object**.  
  * an array is a collection of simlilar type of elements which have a contiguous memory location.  
  * Unlike C/C++, we can get the length of array using the **length** member.  
  * Unlike C/C++, an array in JAVA is a **dynamically generated class**.  
  * But not dynamic array.  
  * **array inherits the Object class**  
  * implements **Serializable** and **Cloneable**.  
  
  
## Examples  

```java
int[] arr = new int[5];
System.out.println(arr.length);
```

```java
int[] arr = {1,2,3,4,5};
```

### Passing array to method 
```java

void sum(int[] arr){

}

sum(new int[]{12,3,4,5}); // anonymous array 
```

### Multidimensional  

```java
int[][] arr = new int[3][3];
```
