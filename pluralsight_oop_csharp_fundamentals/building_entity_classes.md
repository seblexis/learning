### Building Entity classes  

**Layering the application**  

Layers:  
* User Interface  
* Business Logic  
* Data Access  

All of these should be independent projects in .NET  

**Classes**  

Classes are types  

Accessibility: internal is accessible to the component within it is defined, e.g., project.  

Autoimplemented property: public PropertyName { get; set; } --> use if there is no code needed for get or set  

**Tests**  

Best way to run .dll classes: Tests!

Arrange // Act // Assert  

When using another class (for example for testing)  
* Add reference  
* *And* using ...
