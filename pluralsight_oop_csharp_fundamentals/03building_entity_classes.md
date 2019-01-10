### Building Entity classes  

**Layering the application**  

Layers:  
* User Interface  
* Business Logic  
* Data Access  

All of these should be independent projects in .NET  

**Classes**  

* Classes are types  
* Accessibility: internal is accessible to the component within it is defined, e.g., project.  
* Autoimplemented property: public PropertyName { get; set; } --> use if there is no code needed for get or set  

**Tests**  
* Best way to run .dll classes: Tests!  
* Arrange // Act // Assert  
* When using another class (for example for testing)  
  * Add reference  
  * *And* using ...  
* Test not only for valid conditions, but also for invalid ones  

**Objects**  
* use ```var``` where type is obvious  
* Reference type vs value type    
  * variables of reference types: store reference to their data. Example: var customer = new Customer()  
  * variables of value types: store the data itself. Examples: int num = 5;  
  * Consequence:  
    ```
    int num1 = 1; 
    int num2 = 2; 
    num2 = num1; 
    ==> num1 == 1
    ```
    ```
    var customer1 = new Customer; 
    customer1.Name = "Seb"; 
    var customer2 = customer1; 
    customer2.Name = "Skai"; 
    ==> customer1.Name == "Skai" //customer2 is now referencing what customer1 is referencing to.  

