---
id: khxu5xqcxi2rcuanehl87vu
title: Design Pattern
desc: ''
updated: 1651322797831
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

## Creation patterns

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
```

```python
class Cat:
  """A simple Cat class"""
  def __init__(self, name):
    slef._name = name

  def speak(self):
    return "Meow"
```

```python
# The below function not part of the Cat class
def get_pet(pet="dog"):
  """Factory method"""
  pets = dict(dog=Dog("Hope"), cat=Cat("Peace"))
  return pets[pet]
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

```python
class Borg:
  """Borg class making class attributes global"""
  _shared_state = {} # Attribute dictionary

  def __init__(self):
    self.__dict__ = self._shared_state # Make it an attribute dictionary
  def __str__(self):
    return str(self._shared_state)
class Singleton(Borg): # Inherits from the Borg class
  """This class now shares all its attributes among its various instances"""
  def __init__(self, **kwargs):
    Borg.__init__(self)
    self._shared_state.update(kwargs) # Update the attribute dictionary by inserting a new key-value pair
  def __str__(self):
    return str(self._shared_state)

x = Singleton(HTTP="Hyper Text Transfer Protocol")
print(x)

y = Singleton(SNMP="Simple Network Management Protocol")
print(y)
```

## Builder

Builder is a solution to an antipattern called telescoping constructor. An antipattern is the opposite of the best programming practice and what we want to avoid.

### Builder problem situation

The telescoping constructor antipattern occurs when a software developer attempts to build a complex object using an excessive number of constructors. The builder pattern is trying to solve this problem.

### Builder problem scenario

Think of a scenario in which you're trying to build a car. This test requires various car parts to be first constructed individually and then assembled. The builder pattern brings order to this chaotic process to remove unnecessary complexity as much as possible.

### Builder implementation

 It partitions the process of building a complex object into four different roles:

- The first role is a director in charge of actually building a product.
- The second role provides all the necessary interfaces required in building an object. We call this one an abstract builder because there'll be a concrete builder inheriting from it.
- The concrete builder class inherits from the abstract builder class and actually implements the details of the interfaces of the abstract builder class for the specific type of product.
- The product role represents an object being built.

```python
class Director:
  """Director"""
  def __init__(self, builder):
    self._builder = builder

  def construct_car(self):
    self._builder.create_new_car()
    self._builder.add_model()
    self._builder.add_tires()
    self._builder.add_engine()

  def get_car(self):
    return self._builder.car

class Builder():
  """Abstract Builder"""
  def __init__(self):
    self.car = None

  def create_new_car(self):
    self.car = Car()

class SkyLarkBuilder(Builder):
  """Concrete Builder --> provides parts and tools to work on the parts"""
  def add_model(self):
    self.car.model = "Skylark"

  def add_tires(self):
    self.car.tires = "Regular tires"

  def add_engine(self):
    self.car.engine = "Turbo engine"

class Car():
  """Product"""
  def __init__(self):
    self.model = None
    self.tires = None
    self.engine = None

  def __str__(self):
    return '{} | {} | {}'.format(self.model, self.tires, self.engine)

builder = SkyLarkBuilder()
director = Director(builder)
director.construct_car()
car = director.get_car()
print(car)
```

## Prototype

Prototype clones objects according to a prototypical instance. Here the keyword is cloning. Note that we're talking about making a copy instead of building.

### Prototype problem situation

Prototype is useful when instantiating many identical objects individually, which could be expensive in terms of computing power. Cloning could be a good alternative because it makes a carbon copy in the memory space instead of building individual objects, respectively, from scratch the usual way.

### Prototype problem scenario

Let's assume that we are building a car. We can mass produce cars more easily and quickly If the cars have the same color and options. Similarly, in our Python programming scenario, you can clone the objects by making a copy of a prototype object instead of building them through constructors, as long as they're supposed to be identical without variations.

### Prototype implementation

Our solution consists of creating a prototypical instance first and then cloning it whenever you need the replica. **The pattern related to the prototype pattern is the abstract factory**.

```python
import copy

class Prototype:
  """Prototype"""
  def __init__(self):
    self._objects = {}

  def register_object(self, name, obj):
    """Register an object"""
    self._objects[name] = obj

  def unregister_object(self, name):
    """Unregister an object"""
    del self._objects[name]

  def clone(self, name, **attr):
    """Clone a registered object and update its attributes"""
    obj = copy.deepcopy(self._objects.get(name))
    obj.__dict__.update(attr)
    return obj

class Car:
  """Product"""
  def __init__(self):
    self.name = "Skylark"
    self.color = "Red"
    self.options = "Ex"

  def __str__(self):
    return '{} | {} | {}'.format(self.name, self.color, self.options)

c = Car()
prototype = Prototype()
prototype.register_object('skylark', c)
c1 = prototype.clone('skylark')
```

## Structural Patterns

## Decorator

The decorator design pattern is a structural pattern that allows users to add new features to existing objects without changing their structures.

Pattern makes implementing the decorator pattern very straightforward due to its built-in language feature.

### Decorator problem situation

 Our challenge here is to add additional features to an existing object dynamically without using subclasses.

### Decorator problem scenario

We start with a function displaying a hello world message. You want to make the message look fancier by decorating it with additional tasks, such as blink.

### Decorator implementation

Functions are objects in Python, and we can add additional features to these functions using the built-in decorator in Python.

Patterns such as adapter, composite and strategy are related to the decorator pattern.

```python
from functools import wraps

def make_blink(function):
  """Defines the decorator"""
  # This makes the decorator transparent in terms of its name and docstring
  @wraps(function)
  # Define the inner function
  def decorator():
    # Grab the return value of the function being decorated
    ret = function()
    # Add new functionality to the function being decorated
    return "<blink>{}</blink>".format(ret)
  return decorator

# Apply the decorator here!
@make_blink
def hello_world():
  """Original function"""
  return "Hello World!"

# Check the result of decorating
print(hello_world())
# Check if the function name is still the same
print(hello_world.__name__)
# Check if the docstring is still the same
print(hello_world.__doc__)
```

## Proxy

Proxy becomes handy when creating a highly resource-intensive object.

### Proxy problem situation

The problem we need to solve here is postponing our object creation as long as possible, due to the high-resource requirement of the object we're creating. Therefore, there's a need for a placeholder that will, in turn, create the object when its creation is absolutely necessary.

### Proxy problem scenario

We create an instance of a producer class only when it's available because only a fixed number of producer objects can exist at a given time. Our proxy is an artist who is checking to see if the producer becomes available for a guest. In the proxy design pattern, clients interact with a proxy object most of the time until the resource-intensive object becomes available.

### Proxy implementation

The proxy object is in charge of creating the resource-intensive objects. **Adapter and Decorator are related to the proxy design pattern**.

```python
import time
class Producer:
  """Define the 'resource-intensive' object to instantiate!"""
  def produce(self):
    print("Producer is hard-working!")

  def meet(self):
    print("Producer has time to meet you now!")

class Proxy:
  """Define the 'relatively less resource-intensive' proxy to instantiate as a middleman!"""
  def __init__(self):
    self.occupied = 'No'
    self.producer = None

  def produce(self):
    """Check if producer is available"""
    print("Artist checking if producer is available...")

    if self.occupied == 'No':
      # If the producer is available, create a producer object!
      self.producer = Producer()
      time.sleep(2)

      # Make the producer meet the guest!
      self.producer.meet()
    else:
      # Otherwise, don't instantiate a producer
      time.sleep(2)
      print("Producer is busy!")

# Instantiate a Proxy
p = Proxy()
# Make the proxy: Artist produce until Producer is available
p.produce()
# change the state to 'occupied'
p.occupied = 'Yes'
# Make the Producer produce
p.produce()
```

## Adapter

The adapter pattern converts the interface of a class into another one a client is expecting.

### Adapter problem situation

This time, our problem is that the interfaces are incompatible between a client and a server.

### Adapter problem scenario

We have Korean and British objects that have different method names for speaking. The client would like to use a uniform interface that is the speak method.

### Adapter implementation

The adapter pattern that translates the method names between the client and the server code. British and decorators are related to the adapter pattern.

```python
class Korean:
  """Korean speaker"""
  def __init__(self):
    self.name = "Korean"

  def speak_korean(self):
    return "An-neyong?"

class British:
  """English speaker"""
  def __init__(self):
    self.name = "British"

  def speak_english(self):
    return "Hello!"

class Adapter:
  """This changes the generic method name to the desired one"""
  def __init__(self, object, **adapted_method):
    """Change the name of the method"""
    self._object = object

    # Add a new dictionary item that establishes the mapping between the generic method name: speak() and the concrete method
    # For example, speak_korean will be translated to speak() by the adapter
    self.__dict__.update(adapted_method)

  def __getattr__(self, attr):
    """Simply return the rest of attributes!"""
    return getattr(self._object, attr)

# List to store speaker objects
objects = []

# Create a Korean object
korean = Korean()

# Create a British object
british = British()

# Append the objects to the objects list
objects.append(Adapter(korean, speak=korean.speak_korean))
objects.append(Adapter(british, speak=british.speak_english))

for obj in objects:
  print("{} says '{}'\n".format(obj.name, obj.speak()))
```

## Composite

### Composite problem situation

The composite design pattern maintains a tree data structure to represent part-whole relationships. Here, we want to build a recursive tree data structure so that an element of the tree can have its own sub-elements.

### Composite problem scenario

Creating menu and sub-menu items. The sub-menu items can also have their own sub-menu items. Our coding challenge is to display menu and sub-menu items using the composite design pattern.

### Composite implementation

Our solution consists of three major elements. The first one is Component. The second one is Child. And the third one is Composite. The Component element is an abstract class or concrete class called Child, inherit from the component class. And then, we have another concrete class called Composite, which also inherits from the Component class. Finally, our Composite class maintains Child objects by adding a removing them to and from a tree data structure.

```python
class Component(object):
  """Abstract class"""
  def __init__(self, *args, **kwargs):
    pass
  def component_function(self):
    pass

class Child(Component): # Inherit from the Component class
  """Concrete class"""
  def __init__(self, *args, **kwargs):
    Component.__init__(self, *args, **kwargs)
    # This is where we store the name of the child item
    self.name = args[0]

  def component_function(self):
    # Print the name of your child item
    print("{}".format(self.name))

class Composite(Component): # Inherit from the abstract class, Component
  """Concrete class and maintains a list of children"""
  def __init__(self, *args, **kwargs):
    Component.__init__(self, *args, **kwargs)
    # This is where we store the name of the composite object
    self.name = args[0]
    # This is where we keep our children
    self.children = []

  def append_child(self, child):
    """Method to add a new child"""
    self.children.append(child)

  def remove_child(self, child):
    """Method to remove a child"""
    self.children.remove(child)

  def component_function(self):
    # Print the name of the composite object
    print("{}".format(self.name))

    # Iterate through the children of this composite object
    for i in self.children:
      # Call the component_function() method on each child
      i.component_function()

# Build a composite submenu 1
sub1 = Composite("submenu1")

# Create a new child sub_submenu11
sub11 = Child("sub_submenu11")
# Create a new child sub_submenu12
sub12 = Child("sub_submenu12")

# Add the sub_submenu11 to submenu1
sub1.append_child(sub11)
# Add the sub_submenu12 to submenu1
sub1.append_child(sub12)

# Build a top-level composite menu
top = Composite("top_menu")

# Build a submenu 2 that is not a composite
sub2 = Child("submenu2")

# Add the composite sub1 to the top-level composite menu
top.append_child(sub1)

# Add the composite sub2 to the top-level composite menu
top.append_child(sub2)

# Let's test if our composite pattern works!
top.component_function()
```

## Bridge

### Bridge problem situation

The bridge pattern helps untangle an unnecessarily complicated class hierarchy. Especially when implementation-specific classes are mixed with implementation-independent classes. The problem here is that there are two parallel or orthogonal abstractions. One is implementation specific, and the other is implementation independent.

### Bridge problem scenario

 Implementation-independent circle abstraction and implementation-dependent circle abstraction. The implementation-dependent circle abstraction involves how to draw a circle. And the implementation-independent circle abstraction involves defining the properties of a circle and scaling it.

### Bridge implementation

Avoiding the abstracting in both implementation-specific and implementation-independent classes in a single class hierarchy. **The abstract factory and adapter patterns are the related patterns to the bridge design pattern**.

```python
class DrawingAPIOne(object):
  """Implementation-specific abstraction: concrete class one"""
  def draw_circle(self, x, y, radius):
    print("API 1 drawing a circle at ({}, {} with radius {}!)".format(x, y, radius))

class DrawingAPITwo(object):
  """Implementation-specific abstraction: concrete class two"""
  def draw_circle(self, x, y, radius):
    print("API 2 drawing a circle at ({}, {} with radius {}!)".format(x, y, radius))

class Circle(object):
  """Implementation-independent abstraction: for example, there could be a rectangle class!"""
  def __init__(self, x, y, radius, drawing_api):
    """Initialize the necessary attributes"""
    self._x = x
    self._y = y
    self._radius = radius
    self._drawing_api = drawing_api

  def draw(self):
    """Implementation-specific abstraction taken care of by another class: DrawingAPI"""
    self._drawing_api.draw_circle(self._x, self._y, self._radius)

  def scale(self, percent):
    """Implementation-independent"""
    self._radius *= percent

# Build the first circle object using API One
circle1 = Circle(1, 2, 3, DrawingAPIOne())
# Draw a circle
circle1.draw()

# Build the second circle object using API Two
circle2 = Circle(2, 3, 4, DrawingAPITwo())
# Draw a circle
circle2.draw()
```

## Behavioral patterns

## Observer

### Observer problem situation

The observer pattern establishes a one too many relationships between a subject and multiple observers. Our problem here is that a subject needs to be monitored, and other observer objects should be notified when there is a change in the subject.

### Observer problem scenario

In our scenario, we keep track of the core temperatures of reactors at a power plant. When there is a change in the core temperature, registered observers must be notified.

### Observer implementation

Our solution uses an abstract class called subject, which has the interface that allows operations such as attaching, detaching, and notifying observers. We also need concrete subject classes inheriting from the abstract subject class. Singleton is related to the observer design pattern.

```python
class Subject(object):
  # Represents what is being 'observed'
  def __init__(self):
    # This where references to all the observers are being kept
    # Note that this is a one-to-many relationship: there will be
    # one subject to be observed by multiple _observers
    self._observers = []

  def attach(self, observer):
    # If the observer is not in the observers list
    # append the observer to the list
    if observer not in self._observers:
      self._observers.append(observer)

  def detach(self, observer):
    # Simply remove the observer
    try:
      self._observers.remove(observer)
    except ValueError:
      pass

  def notify(self, modifier=None):
    # For all observers in the list
    # Don't notify the observer who changed the state
    # Alert the observers that the subject state
    # or state has changed
    for observer in self._observers:
      if modifier != observer:
        observer.update(self)

class Core(Subject):
  # Note that the core class inherits from the Subject class
  def __init__(self, name):
    Subject.__init__(self)
    # Name of the core
    self._name = name
    # Temperature of the core
    self._temp = 0

  @property # Getter that gets the core temperature
  def temp(self):
    return self._temp

  @temp.setter # Setter that sets the core temperature
  def temp(self, temp):
    self._temp = temp
    # Notify the observers whenever somebody changes the core tempe
    self.notify()

class TempViewer:
  def update(self, subject):
    # Alter method that is invoked when then subject notifies us
    print("Temperature Viewer: {} has Temperature {}".format(subject._name, subject._temp))

# Let's create our subjects
c1 = Core("Core 1")
c2 = Core("Core 2")

# Let's create our observers
v1 = TempViewer()
v2 = TempViewer()

# Let's attach our observers to the first core
c1.attach(v1)
c1.attach(v2)

# Let's change the temperature of the first core
c1.temp = 80
c1.temp = 90
```

## Visitor

### Visitor problem situation

The visitor design pattern allows adding new features to an existing class hierarchy without changing it. It's sometimes necessary to add new operations, dynamically to exist in classes with minimal changes.

### Visitor problem scenario

Visitors in this scenario include an HVAC specialist and an electrician. The HVAC specialist in our scenario is visitor type one, and the electrician is visitor type two.

### Visitor implementation

The visitor pattern represents new operations to be performed on the various elements of an existing class hierarchy. Visitors can also provide operations on a composite object.

```python
class House(object):
  # The class being visited
  def accept(self, visitor):
    """Interface to accept a visitor"""
    # Triggers the visiting operation!
    visitor.visit(self)

  def work_on_hvac(self, hvac_specialist):
    # Note that we now have a reference to a HVAC specialist object
    print(self, "worked on by", hvac_specialist)

  def work_on_electricity(self, electrician):
    # Note that we now have a reference to a electrician object
    print(self, "worked on by", electrician)

  def __str__(self):
    """Simply return the class name when the House object is printed"""
    return self.__class__.__name__

class Visitor(object):
  """Abstract visitor"""
  def __str__(self):
    """Simply return the class name when the Visitor object is printed"""
    return self.__class__.__name__

class HVACSpecialist(Visitor):
  # Inherits from the parent class, visitor
  """Concrete visitor: HVAC specialist"""
  def visit(self, house):
    # Note that the visitor now has a reference to the house object
    """The HVAC specialist visits a house to work on the HVAC"""
    house.work_on_hvac(self)

class Electrician(Visitor):
  # Inherits from the parent class, visitor
  """Concrete visitor: electrician"""
  def visit(self, house):
    # Note that the visitor now has a reference to the house object
    """The electrician visits a house to work on the electricity"""
    house.work_on_electricity(self)

# Create an HVAC specialist
hv = HVACSpecialist()

# Create an electrician
e = Electrician()

# Create a house
home = House()

# Let the house accept the HVAC specialist and work on the house by invoking the visit() method
home.accept(hv)

# Let the house accept the electrician and work on the house by invoking the visit() method
home.accept(e)
```

## Iterator

### Iterator problem situation

The iterator pattern allows a client to have sequential access to the elements of an aggregate object without exposing its underlying structure. The problem is that some programmers overcrowd the traversal interfaces of an aggregate object for every possible way of iteration.

### Iterator problem scenario

We'll be building our own iterator that takes advantage of a built-in Python iterator called zip. The iterator goes through a list of German counting words. It will iterate only up to a certain point based on client input. The iterator isolates access and traversal features from the aggregate object. It also provides an interface for accessing the elements of an aggregate object. An iterator keeps track of the objects being traversed.

### Iterator implementation

Our solution is to make the aggregate object create an iterator for a client. The [[Composite|python.design-pattern#composite]] design pattern is related to the iterator pattern**.

```python
def count_to(count):
  """Our iterator implementation"""
  # Our list
  numbers_in_german = ["eins", "zwei", "drei", "vier", "funf"]

  # Our built-in iterator
  # Creates a tuple such as (1, "eins")
  iterator = zip(range(count), numbers_in_german)

  # Iterate through our iterable list
  # Extract the German numbers
  # Put them in a generator called number
  for position, number in iterator:
    # Returns a 'generator' containing numbers in German
    yield number

# Let's test the generator returned by our iterator
for num in count_to(3):
  print("{}".format(num))
```

## Strategy

### Strategy problem situation

The strategy pattern offers a family of interchangeable algorithms to a client. The problem we often see is that there is a need for dynamically changing the behavior of an object.

### Strategy problem scenario

We offer our strategy class with its default behavior. When there is a need, we provide another variation of the strategy class by dynamically replacing its default method with a new one.

### Strategy implementation

Python allows adding methods dynamically by importing the **types** module.

```python
import types

class Strategy:
  """The Strategy Pattern class"""
  def __init__(self, function=None):
    self.name = "Default Strategy"
    # If a reference to a function is provided, replace the strategy method with the given function
    if function:
      self.execute = types.MethodType(function, self)

  def execute(self):
    # This gets replaced by another version if a new strategy is provided
    """The default method that prints the name of the strategy being used"""
    print("{} is used!".format(self.name))

# Replacement method 1
def strategy_one(self):
  print("{} is used to execute method 1".format(self.name))

# Replacement method 2
def strategy_two(self):
  print("{} is used to execute method 2".format(self.name))

# Let's create our default strategy
s0 = Strategy()
# Let's execute our default strategy
s0.execute()

# Let's create the first variation of our default strategy
s1 = Strategy(strategy_one)
# Let's set its name
s1.name = "Strategy One"
# Let's execute the first variation
s1.execute()

s2 = Strategy(strategy_two)
s2.name = "Strategy Two"
s2.execute()
```

## Chain of responsibility

### Chain of responsibility problem situation

The chain of responsibility pattern opens up various possibilities of processing for a given request. The chain of responsibility pattern decouples the request and its processing. Our problem is that many types of processing need to be done depending on the request.


### Chain of responsibility problem scenario

We receive an integer value. We use different handlers to find out its range.


### Chain of responsibility implementation

We use an abstract handler that stores a successor that will handle a request if the current handler doesn't handle it. Concrete handlers check if they can handle the request. If they can, they handle it and return a true value, indicating that the request was handled. Composite is related to the chain of responsibility, design pattern.

```python
class Handler:
  """The Handler"""
  def __init__(self, successor=None):
    self._successor = successor

  def handle(self, request):
    """Handle the request or pass it to the successor"""
    handled = self._handle(request)
    # If the request was not handled, then pass it to the successor
    if not handled:
      self._successor.handle(request)

  def _handle(self, request):
    """This is where the actual request handling happens"""
    raise NotImplementedError("Must provide implementation in subclass!")

class ConcreteHandler1(Handler):
  """Concrete handler 1"""
  def _handle(self, request):
    """If the request is 1, then handle it"""
    if request == 1:
      print("{} handled request {}".format(self.__class__.__name__, request))
      # indiacate that the request has been handled
      return True
  def _handle(self, request):
    """If the request is 2, then handle it"""
    if request == 2:
      print("{} handled request {}".format(self.__class__.__name__, request))
      # indiacate that the request has been handled
      return True
class Client:
  """The client"""
  def __init__(self):
    self.handler = ConcreteHandler1(ConcreteHandler2(ConcreteHandler3()))

  def delegate(self, requests):
    """Send the requests to the handler"""
    for request in requests:
      self.handler.handle(request)
# create a client
c = Client()

requests = [2, 5, 1, 3, 2]
# send requests to the client
c.delegate(requests)
```
