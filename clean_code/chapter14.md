## Chapter 14

* Arguments/functions: 
  * When looping through an array and then calling a function in the loop, it's dirty to pass the array and the current index. (p. 231)
  * Example: 
  ```int currentArgument = 0;
     String[] arr = ["a", "b"];
     for (i in arr) {
       function(list, currentArgument)
     }
     function(list, currentArgument) {
        //some code using both list and currentArgument
     }
  ```
  * Better: Use iterators
  * Example:
  ```List<String> arrList = new List<>();
     Iterator<String> currentArgument;
     for (currentArgument = arrList.iterator(); currentArgument.hasNext()) {
      function(currentArgument); 
     }
     function(currentArgument) {
        //some code using both list and currentArgument
        //we can now jump back and forth in the list without needing both index and list, simply using currentArgument.next()
     }
