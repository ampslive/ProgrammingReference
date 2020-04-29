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
- Product => Animal
- Creator => AnimalFactory
- ConcreteProduct => Cats, Dogs, Ducks
- ConcreteCreator => RandomAnimalFactory, BalancedAnimalFactory

  - Creator creates the Product
  - Can eliminate the need of having more types to define a size of cat or breed of dog. A size or breed will be properties that can be passed to the factory to create an Animal
