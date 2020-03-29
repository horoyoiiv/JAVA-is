

## Life cycle of Thread  


#### 1. New  
  * When an instance of Thread class is created but before the invocation of start() method.  
  
#### 2. Runnable  
  * After invocation of start() method, but the **thread scheduler** has not selected it to be the running.  
  
#### 3. Running  
  * The thread scheduler has selected it.  

#### 4. Block  
  * The thread is still alive, but is currently not eligible to run.  
  
#### 5. 
  * run() method exits.  
  
  
