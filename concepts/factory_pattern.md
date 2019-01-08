## Factory pattern 
*for C#*  
[Source](https://www.dofactory.com/net/factory-method-design-pattern)  
[See also: Abstract Factory in *Clean Code*](https://github.com/seblexis/learning/blob/master/clean_code/chapter16.md#abstract-factory-pattern-p-273)

* Definition: Pattern that abstracts creation of class instances. 

* Use case: You have different classes (Resume, Report) which are implementations of a more abstract class (Documents). You want a generic way of creating instances of those classes, instead of having to individually creating each. 

* Implementation: You create a Factory method on the abstract class, e.g., FactoryMethod(). You then write implementations of this method for each implementations of that class. This allows, for example, to iterate over a list of implementations of the abstract class and create instances of each by calling FactoryMethod() on each. 

* Related concepts: 
  * **Liskov Substitution Principle**: Classes should be replaceable by its superclass. When following factory pattern, the implementations of the abstract class, i.e., its superclass, are replaceable by its superclass (Documents). That way, iteratively calling the same method on them is possible.  
  * **Polymorphism**: Two classes can share the same behaviour (FactoryMethod()) but implement them very differently. 

* Example  
```
                 
using System;
using System.Collections.Generic;
 
namespace DoFactory.GangOfFour.Factory.RealWorld
{
  /// <summary>

  /// MainApp startup class for Real-World 

  /// Factory Method Design Pattern.

  /// </summary>

  class MainApp

  {
    /// <summary>

    /// Entry point into console application.

    /// </summary>

    static void Main()
    {
      // Note: constructors call Factory Method

      Document[] documents = new Document[2];
 
      documents[0] = new Resume();
      documents[1] = new Report();
 
      // Display document pages

      foreach (Document document in documents)
      {
        Console.WriteLine("\n" + document.GetType().Name + "--");
        foreach (Page page in document.Pages)
        {
          Console.WriteLine(" " + page.GetType().Name);
        }
      }
 
      // Wait for user

      Console.ReadKey();
    }
  }
 
  /// <summary>

  /// The 'Product' abstract class

  /// </summary>

  abstract class Page

  {
  }
 
  /// <summary>

  /// A 'ConcreteProduct' class

  /// </summary>

  class SkillsPage : Page

  {
  }
 
  /// <summary>

  /// A 'ConcreteProduct' class

  /// </summary>

  class EducationPage : Page

  {
  }
 
  /// <summary>

  /// A 'ConcreteProduct' class

  /// </summary>

  class ExperiencePage : Page

  {
  }
 
  /// <summary>

  /// A 'ConcreteProduct' class

  /// </summary>

  class IntroductionPage : Page

  {
  }
 
  /// <summary>

  /// A 'ConcreteProduct' class

  /// </summary>

  class ResultsPage : Page

  {
  }
 
  /// <summary>

  /// A 'ConcreteProduct' class

  /// </summary>

  class ConclusionPage : Page

  {
  }
 
  /// <summary>

  /// A 'ConcreteProduct' class

  /// </summary>

  class SummaryPage : Page

  {
  }
 
  /// <summary>

  /// A 'ConcreteProduct' class

  /// </summary>

  class BibliographyPage : Page

  {
  }
 
  /// <summary>

  /// The 'Creator' abstract class

  /// </summary>

  abstract class Document

  {
    private List<Page> _pages = new List<Page>();
 
    // Constructor calls abstract Factory method

    public Document()
    {
      this.CreatePages();
    }
 
    public List<Page> Pages
    {
      get { return _pages; }
    }
 
    // Factory Method

    public abstract void CreatePages();
  }
 
  /// <summary>

  /// A 'ConcreteCreator' class

  /// </summary>

  class Resume : Document

  {
    // Factory Method implementation

    public override void CreatePages()
    {
      Pages.Add(new SkillsPage());
      Pages.Add(new EducationPage());
      Pages.Add(new ExperiencePage());
    }
  }
 
  /// <summary>

  /// A 'ConcreteCreator' class

  /// </summary>

  class Report : Document

  {
    // Factory Method implementation

    public override void CreatePages()
    {
      Pages.Add(new IntroductionPage());
      Pages.Add(new ResultsPage());
      Pages.Add(new ConclusionPage());
      Pages.Add(new SummaryPage());
      Pages.Add(new BibliographyPage());
    }
  }
}
```

