
Key Differences Between Thread and Runnable in Java


1) Each thread created by extending the Thread class creates a unique object for it and get associated with that object. On the other hand, each thread created by implementing a Runnable interface share the same runnable instance.  
2) As each thread is associated with a unique object when created by extending Thread class, more memory is required. On the other hand, each thread created by implementing Runnable interface shares same object space hence, it requires less memory.  
3) If you extend the Thread class then further, you can inherit any other class as Java do not allow multiple inheritance whereas, implementing Runnable still provide a chance for a class to inherit any other class.  
4) One must extend a Thread class only if it has to override or specialise some other methods of Thread class. You must implement a Runnable interface if you only want to specialise run method only.  

5) Extending the Thread class introduces tight coupling in the code as the code of Thread and job of thread is contained by the same class. On the other hand, Implementing Runnable interface introduces loose coupling in the code as the code of Thread is seprate from the job assigned to the thread.  


[Ref](https://techdifferences.com/difference-between-thread-class-and-runnable-interface-in-java.html)  

