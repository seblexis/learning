## Chapter15: JUnit Internals
*Refactoring on the example of JUnit code*

### Hidden temporal coupling 
Code smell. When the error-free running of the code depends on two (or more) methods being called in a temporal order without this being obvious.  

**Example** 
```
var var1;
var var2;
method1() {
  var1 = 0;
}
method2() {
  var2 = 4;
  var1 + var2
}
method1()
method2()
```
method1 needs to be tun before method2 because var1 needs to be defined to be added to var2.  

**Problem**: This isn't clear from the code. If somewhere were to change the order of the function they would get an error and then spent a lot of time debugging. 

**Solution**: Incorporate method1 into method2 and rename method2
```
supermethod() {
  method1();
  var2 = 4;
  var1 + var2;
}
supermethod();
``` 
This way, we make sure that method1 is called before what used to be the core functionality of method2 (adding var 1 and var2).

### Unencapsulated conditional 
*Code smell. Extensive conditional statement that could be wrapped into method*  
**Example**  
```
if (expected == null | actual == null | areStringsEqual() ) {}
```
**Problem:** Readability  
**Solution**  
```
if (shouldNotCompact()) {}
Boolean shouldNotCompact() {
  return (expected == null | actual == null | areStringsEqual() )
}
```


