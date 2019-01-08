## Chapter16: Refactoring Serial Date  

### Abstract factory pattern (p. 273)  
**Definition**: A method to encapsulate a group of different factories with a common theme, but different implementation.  
**Use case**: 
* You want to create a Windows or Mac button, dependent on the OS used.  
* You have an abstract ButtonFactory class  
* You have WinButtonFactory and OSButtonFactory, which implement ButtonFactory 
* To create button, you evaluate a conditional (Mac or Windows), and then create *factory*, either an instance of either WinButtonFactory or OSButtonFactory
* You then call the create method on *factory*  

**Example**  
```
interface IButton
{
    void Paint();
}

interface IGUIFactory
{
    IButton CreateButton();
}

class WinFactory : IGUIFactory
{
    public IButton CreateButton()
    {
        return new WinButton();
    }
}

class OSXFactory : IGUIFactory
{
    public IButton CreateButton()
    {
        return new OSXButton();
    }
}

class WinButton : IButton
{
    public void Paint()
    {
        //Render a button in a Windows style
    }
}

class OSXButton : IButton
{
    public void Paint()
    {
        //Render a button in a Mac OS X style
    }
}

class Program
{
    static void Main()
    {
        var appearance = Settings.Appearance;

        IGUIFactory factory;
        switch (appearance)
        {
            case Appearance.Win:
                factory = new WinFactory();
                break;
            case Appearance.OSX:
                factory = new OSXFactory();
                break;
            default:
                throw new System.NotImplementedException();
        }

        var button = factory.CreateButton();
        button.Paint();
    }
}
```

### ENUM (p. 275)  
* Use case: You have a list of constants, like MONDAY = 0, TUESDAY = 1, WEDNESDAY = 2 ... 
* Makes it (somewhat) difficult to change
* Instead: Use an enum class  
```  
public enum Weekdays {
    MONDAY = 0,
    TUESDAY = 1, 
    WEDNESDAY = 2,
    ...
 }
```

