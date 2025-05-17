# OOPS Concepts in Python

  Imagine you have a box of toys (cars, dolls, robots, etc ). OOP is like orgsnizing them neatly by what they are and what they do.

### 1. Class — the blueprint
  > If you want to make many toy cars, you first need a "ToyCar Plan" that says:
  > A ToyCar has 4 wheels and can vrooom!
  ```
  class ToyCar:
      wheels = 4

      def drive(self):
          print("Vroom vroom!")
  ```
### 2. Object — the real toy
  When you actually make a toy car from the plan, it’s called an object. You can make as many as you want from the same plan
  ```
  car1 = ToyCar()
  car2 = ToyCar()

  car1.drive()  # Vroom vroom!
  car2.drive()  # Vroom vroom!
  ```
### 3. Attributes — special details
  Each toy might have special details, like color or speed.
  ```
  class ToyCar:
    def __init__(self, color):
      self.color = color
  car1=ToyCar("red")
  car2=ToyCar("blue")
  print(car1.color)  # red
  print(car2.color)  # blue
  ```
  *(The __init__ thing is like saying "When you build it, ask for the color!")*
  
### 4. Methods — toy actions
  toys can do actions like making sound or moving. These actions are called methods.
  ```
  class Robot:
    def dance(self):
      print("robot is dancing")
  robot1=Robot()
  robot1.dance
  ```
### 5. Inheritance — passing cool tricks
  Inherits existing features from parent class. Like -  a "FlyingCar" is just a ToyCar plus flying powers!
  ```
  class FlyingCar(ToyCar):
    def fly(self):
        print("I'm flying!")  #Now it can drive and fly
  ```
### 6. Encapsulation — keeping secrets 
  Some parts inside a toy should be hidden — you don’t need to know everything to play!
  - python lets you hide by adding an underscore:
  ```
  class SecretToy:
    def __init__(self):
      self._secret = "This toy has a secret"
  toy = SecretToy()
  print(toy._secret)
  # You can see it, but it's a hint you shouldn't mess with it!
  ```
### 7. Polymorphism — same button, different magic
  Imagine you press the Start button on a toy car and a toy robot- same button diff actions
```
class ToyCar:
  def start(self):
    print("Car is driving!")

class Robot:
    def start(self):
        print("Robot is dancing!")

def start_toy(toy):
    toy.start()

car = ToyCar()
robot = Robot()

start_toy(car)
start_toy(robot)
```
> [!NOTE]
> In super simple words:  
> - Attributes are like adjectives (red, fast, small).  
> - Methods are like verbs (run, jump, fly).  
> - Polymorphism is like — you say one thing, but each object shows its own special trick!  

### How Real World uses OOP
**Example: _Uber App_ - Cars and Drivers**
In a company like Uber, they have:
- Different types of cars
- Different drivers
- And they perform actions like accepting rides, driving, completing trips.
```
class Driver :
  def __init__(self, name, car_type):
    self.name = name
    self.car_type = car_type
  def acceptRide(self):
    return f"{self.name} has accepted the ride!"
  def completeRide(self):
    return f"{self.name} has completed the trip in {self.car_type}."

#creating drivers(objects)
driver1 = Driver("Alice", "Sedan")
driver2 = Driver("Sourav" "SUV")

#actions(methods)
print(driver1.acceptRide())     # Alice has accepted the ride!
print(driver1.completeRide())   # Alice has completed the trip in a Sedan.

print(driver2.accept_ride())   # Sourav has accepted the ride!
print(driver2.complete_ride()) # Sourav has completed the trip in a SUV.
```

![image](https://github.com/user-attachments/assets/8cf9e360-e932-4445-ac46-1dd96acdf70a)


# FEATURES OF OOP
## Accessing and Modifying Private Data Members
Using **_Getter and Setter_**: You can use the getter and setter methods to access and modify the _private field_.
```
class MyClass:
  __myField = None
  # Getter method
  def getMyField(self):
    return MyClass.__myField
  # Setter method
  def setMyField(self, value):
    MyClass.__myField=value

obj = MyClass()
obj.setMyField(42)
value = obj.getMyField()
print(value)
```
> [!NOTE]
>  "getter" and "setter" refer to a convention in object-oriented programming rather than fixed methods that are built into Python or other languages.  
> a common practice but not a language requirement.

For a more Pythonic approach, you could rewrite your code using the @property decorator:
## @property Decorator
This allows you to access the method as if it were an attribute:
```
class Person:
    def __init__(self):
        self._age = 0
    
    @property
    def age(self):
        return self._age
person = Person()
print(person.age)  # Calls the age() method, but written like an attribute
```
### @attribute.setter Decorator
The setter decorator works together with the property to handle assignment:
```
class Person:
    def __init__(self):
        self._age = 0
    
    @property
    def age(self):
        return self._age
    
    @age.setter
    def age(self, value):
        if value < 0:
            raise ValueError("Age cannot be negative")
        self._age = value
person = Person()
person.age = 25  # Calls the setter method
```
These properties give best of both worlds- clean syntax of attributes with the control and flexibility of methods.

## Inheritance


| Member Visibility| Public (default) | Protected (_single)              | Private (__double)  |
|------------------|------------------|----------------------------------|---------------------|
| In Base Class    | Accessible       | Accessible                       | Accessible          |
| In Derived Class | Accessible       | Accessible within subclass/module| Not Accessible      |



Python supports five types of inheritance:  
- Single inheritance
- Hierarchical inheritance
- Multilevel inheritance
- Multiple inheritance(inherit attributes and methods from more than one base class)
- Hybrid inheritance (combination of multiple and hierarchical inheritance)

>  super().__init__ : used to explicitly call a superclass constructor from a subclass constructor

### Aggregation
Aggregation represents a "has-a" relationship between classes. It implies that one class (the whole or container) has objects of another class (the part or component).  
```
class Address:
    def __init__(self, street, city, postal_code):
        self.street = street
        self.city = city
        self.postal_code = postal_code
    def display_address(self):
        print("Street:", self.street, ", City:", self.city, ", Postal Code:", self.postal_code)

class Person:
    def __init__(self, name, age, address):
        self.name = name
        self.age = age
        self.address = address
    def display_info(self):
        print("Name:", self.name, ", Age:", self.age)
        print("Address:", end=" ")
        self.address.display_address()

person_address = Address("123 Main St", "Cityville", "12345")
person = Person("John Doe", 30, person_address)
person.display_info()
```










