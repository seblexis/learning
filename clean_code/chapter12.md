## Chapter 12: Emergence 

* Template method (p. 174):
  * A method for removing duplication. 
  * Can be applied when you have lots of different functions doing the same thing, but for example on different objects
  * Old code (taken from [chapter 14](https://github.com/seblexis/notes/new/master/clean_code/chapter14.md), p. 231)
  ```
class ArgumentMarshaller {
    getBoolean()
    getString()
    getInteger()
  }
getArgument(ArgumentMarshaller m) {
  if (m instanceof BooleanArgumentMarshaller)
    m.getBoolean()
  else if (m instanceof StringArgumentMarshaller)
    m.getInteger()
  else if (m instanceof IntegerArgumentMarshaller)
    m.getInteger()
}
  ```
  * Problem: The get getArgument is a **type-case**. It's ugly. We can get rid of it by applying the Template method pattern. We abstract
    ArgumentMarshaller, give it an abstract get method and create subclasses that implement those get methods.
  * New code: Applying template method
  ```
  **abstract** class ArgumentMarshaller {
      abstract get()
  }
  class BooleanArgumentMarshaller extends ArgumentMarshaller {
    void get() {
      getBoolean()
    }
  }
  class StringArgumentMarshaller extends ArgumentMarshaller {
    void get() {
      getString()
    }
  }
  class IntegerArgumentMarshaller extends ArgumentMarshaller {
    void get() {
      getInteger()
    }
  }
  ```
