There are two types of Factory Patterns...
- Factory Method
- Abstract Factory

#### Usecase
Factory pattern is used to encapsulate the instantiating of an object uniformly through the solution.
This can be used to encapsulate the creation of a complex object (with particular set of properties). This can then be used at runtime for creation of a particular type of object.

#### Definition
> Factory Method Pattern defines a contract for creating an object, but lets sub classes decide which object to create

![Factory Method Pattern](https://upload.wikimedia.org/wikipedia/commons/4/43/W3sDesign_Factory_Method_Design_Pattern_UML.jpg "Factory Method Pattern")

#### Example
- Product => Car
- Creator => CarFactory
- ConcreteProduct => Honda, Ford
- ConcreteCreator => RandomCarFactory, HondaFactory, FordFactory

  - Creator creates the Product
  - Can eliminate the need of having more types to define a size of car or model of car. A size or breed will be properties that can be passed to the factory to create an Animal
  
#### Code
~~~csharp
public class Program
{
  public static void Main()
  {
    var rndCar = new RandomCarFactory().Manufacture("EV");
    Console.WriteLine($"Make: {rndCar.Make} - Model: {rndCar.Model}");

    var car = new HondaFactory().Manufacture("Amaze");
    
    Console.WriteLine($"Make: {car.Make} - Model: {car.Model}");

    var car2 = new FordFactory().Manufacture("Amaze");
    
    Console.WriteLine($"Make: {car2.Make} - Model: {car2.Model}");

  }
    
}

#region Product
public interface ICar
{
  string Make { get; set;}
  string Model { get; set;}
}

public class Honda : ICar
{
  public string Make { get; set;}
  public string Model { get; set;}
}

public class Ford : ICar
{
  public string Make { get; set;}
  public string Model { get; set;}
}
#endregion

#region Factories
public interface ICarFactory
{
  ICar Manufacture(string model);
}

public class HondaFactory : ICarFactory
{
  public ICar Manufacture(string model)
  {
    return new Honda { Make = nameof(Honda), Model = model };
  }
}

public class FordFactory : ICarFactory
{
  public ICar Manufacture(string model)
  {
    return new Ford { Make = nameof(Ford), Model = model };
  }
}

public class RandomCarFactory : ICarFactory
{
  public ICar Manufacture(string model)
  {
    var rnd = new Random().Next(0,10);
    if(rnd % 2 == 0)
      return new Ford { Make = nameof(Ford), Model = model };
    else
      return new Honda { Make = nameof(Honda), Model = model };
  }
}
#endregion
~~~
