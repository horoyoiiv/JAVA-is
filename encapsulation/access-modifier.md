
# Default  

  * when no access modifier is specified for a class, method or member, 
  default is a default.  
  
  * Only accessable within a same package.  
  
# private  

  * Only accessable within a class.  
  * even the child class is not accessable.  
  
# protected  
  * accessable within a same package and a subclass of different package.  
  
# public  
 * from everywhere.  
 
 
# Conclusion.  
 * private : only a class  
 * public : everywhere  
 * default : only in a same package    
 * protected : default + subclass in a different package.  
 
 |modif|default|private|protected|public|
 |---|----|----|----|----|
 |same class| OK | OK | OK | OK |
 |subclass in same package | OK | NOO | OK | OK |
 |non-subclass in same pacakage| OK | NOO | OK | OK |
 |subclass in other package| NOO| NOO | OK | OK |
 |non-subclass in other package| NOO | NOO| NOO | OK |
 
