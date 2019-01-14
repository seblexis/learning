## Dependency Injection  
[Google Talk by Misko Hevery: Global State and Singletons](https://www.youtube.com/watch?v=-FRm3VPhseI&list=PL693EFD059797C21E&index=2)  
[Misko Hevery: My main() method is better than yours](http://misko.hevery.com/2008/08/29/my-main-method-is-better-than-yours/)  

* Don't initialise in the constructor  
* Instead, initialise and pass in as constructor arguments  
* But where should initialising happening? Options  
  * very top, in main()  
  * Initialise class B right before you initialise class A, which is dependent on B.
  ```
  var a = new A()  
  var b = new B(a)  
  ```  
* Misko:  
> As you can see we have a clear separation of the object graph construction responsibility from the application logic code. If you were to examine the code in more detail you would find that all of the new operators have migrated from the run-phase  to creation-phase ( ... ) And that is very important. New operator in application code is enemy of testing, but new in tests and factories is your friend. (The reason is that in tests we want to use test-doubles which are usually a subclass or an implementation of the parent class. If application code calls new than you can never replace that new with a subclass or different implementation.) **The key is that the object creation responsibility and the the application code are two different responsibilities and they should not be mixed.** Especially in the main method!

  
