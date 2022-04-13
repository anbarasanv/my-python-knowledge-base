---
id: khxu5xqcxi2rcuanehl87vu
title: Design Pattern
desc: ''
updated: 1649819745343
created: 1648522082649
---

Design patterns are the well-known solutions to **recurring** problems.

```mermaid
flowchart LR
    id1(Systematic reuse of best design ideas) --> id2(lower cost and higher quality)
```

### Characteristics

- Language neutral
- Dynamic
- Incomplete by design to promote customization.

### Design pattern types

- Creation
  - Use
    - Create objects systematically
  - Benefits
    - Flexibility
- Structural
  - Use
    - Establish relationship between software components
    - Accomplish both functional and non-functional goals
  - Benefits
    - Based on the goals structures can be defined
- Behavioral
  - Use
    - How well the objects can interact with each other
    - Accomplish both function and non-function goals
  - Benefits
    - Defining protocols while these objects interacting each other to achieve the common goal

### OOP use case for design patterns

```mermaid
flowchart LR
    id1(Creational) --> id2(Polymorphism)
    id3(Structural) --> id4(Inheritance)
    id5(Behavioral) --> id6(Methods)
```

```mermaid
flowchart LR
    id8(Creational) --> id7(Interface)
    id9(Structural) --> id7(Interface)
    id10(Behavioral) --> id7(Interface)
```

### Inheritance

In object-oriented programming, inheritance is the mechanism of basing an object or class upon another object or class, retaining similar implementation. Also defined as deriving new classes from existing ones such as super class or base class and then forming them into a hierarchy of classes.

```mermaid
classDiagram
Pet <|-- Cat
Pet <|-- Dog
Pet: +String name
Pet: +int age
Pet: +speak()
class Cat{
  +speak()
}
class Dog{
  +speak()
}
```

In the above **Cat** and **Dog** can inherit the attributes of **Pet**, but it will override the attribute _speak()_ based on their requirement.

### Polymorphism

- Relies on inheritance
- Allows child classes to be instantiated and treated as the same type as their parent
- Enables a parent class to be manifested any of its child classes.

### How to describe design pattern context

- Participants
  - Class involved to form a design pattern
  - Roles of these classes
- Quality attributes
  - Nonfunctional requirement's such as
    - usability
    - modifiability
    - reliability
    - performance
  - Effect on the entire software, such as
    - architectural solutions
- Forces
  - Various factors or trade-offs to consider
    - manifested in quality attributes
    - unintended consequences
- Consequences
  - worse performance
  - Decision makers should consider consequences.

### Pattern Language

- Name
  - capture the gist
  - vocabulary
  - Meaningful and memorable
- Context
  - Scenario
  - Insights on when and where
- Problem
  - Design challenges the pattern trying to address
- Solution
  - Specifies the pattern
  - Structure → relationships (between the elements)
  - Behavior → interactions (between the elements)
- Related patterns
  - Lists other patterns used to describe
  - Used together to solve a problem
  - Similar but different

## Factory

**Factory encapsulate object creation** that is factory is an object that is specialized in creating other object.

### Factory problem situation

- Uncertain in type of objects
- Decision to be made in runtime regarding what classes to use.

### Factory Scenario

A pet shop originally selling dogs only, now they want to sell cats too, and they want to describe their attributes too.

### Factory method implementation

```python
class Dog:
  """A simple Dog class"""
  def __init__(self, name):
    slef._name = name

  def speak(self):
    return "Woof"

  def get_pet(pet="dog"):
    """Factory method"""
    pets = dict(dog=Dog("Hope"))
    return pets[pet]
```

```python
class Cat:
  """A simple Cat class"""
  def __init__(self, name):
    slef._name = name

  def speak(self):
    return "Meow"

# The below function not part of the Cat class
def get_pet(pet="dog"):
  """Factory method"""
  pets = dict(dog=Dog("Hope"), cat=Cat("Peace"))
  return pets[pet]
```

```python
# now will try initiate and test above classes
d = get_pet("dog")
print(d.speak())
# Output: Woof
c = get_pet("cat")
print(c.speak())
# Output: Meow
```

## Abstract Factory

Abstract factory builds on factory pattern and it' useful when we are expecting the family of related objects at a given time but doesn't have to know which family it is until runtime.

### Abstract Factory problem situation

- The user expectations yields

### Abstract Factory scenario

A pet factory whose concrete factories include dog factory and cat factory. Both dog and cat factories produce dogs and cats, as well as related products, such as dog food and cat food.

### Abstract Factory Implementation

```mermaid
classDiagram
PetFactory <|-- CatFactory
PetFactory <|-- DogFactory
CatFactory <|-- Cat
CatFactory <|-- CatFood
DogFactory <|-- Dog
DogFactory <|-- DogFood

```

We implement our abstract factory without using inheritance because Python is a dynamically typed language, and therefore does not require abstract classes.

```python
class Dog:
  """One of the obhects to be returned"""
  def speak(slef):
    return "Woof!"

  def __str__(self):
    return "Dog"

class DogFactory:
  """Concrete factory"""
  def get_pet(self):
    """Returns a Dog object"""
    return Dog()
  def get_food(self):
    """Returns a Dog Food object"""
    return "Dog Food!"

class PetStore:
  """PetStore houses our Abstract Factory"""
  def __init__(self, pet_factory=None):
    """pet_factory is our Abstract Factory"""
    self._pet_factory = pet_factory # concrete factory

  def show_pet(self):
    """Utility method to display the details of the objects returned by the DogFactory"""
    pet = self._pet_factory.get_pet()
    pet_food = self._pet_factory.get_food()
    print("Our pet is '{}'!".format(pet))
    print("Our pet says hello by '{}'".format(pet.speak()))
    print("Its food is '{}'!".format(pet_food))

# Create a Concrete Factory
factory = DogFactory()

# Create a pet store housing our Abstract Factory
shop = PetStore(factory)

# Invoke the utility method to show the details of our pet
shop.show_pet()
```

## Singleton

When we have a class that is supposed to have only one instance, we can use the singleton pattern to ensure that.

### Singleton problem situation

- Global variant in an object-oriented way
- Borg
  - The Borg class implements the Borg design pattern which provides a singleton like pattern for Python. A Borg object can be accessed by calling the getInstance() function. This function returns an instance of the Borg class which stores its state between successive calls to get the Borg object.

### Singleton scenario

- An information cache shared by multiple objects

By keeping this information in a single object like Singleton or sharing it constantly in Borg objects, There is no need to retrieve the information from its original sources each time. All modules in Python act as Singletons. In our scenario, Borg acts as an information cache for networking acronyms, and their spelled out versions.

### Singleton implementation