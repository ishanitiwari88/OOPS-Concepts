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

## Inheritance, Packages, and Interfaces


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
### Polymorphism
1. Compile-time Polymorphism (Static Binding or Method Overloading) -
   - In Python, method overloading is achieved in a different way, as the language does not support multiple methods with the same name but different parameter lists.
   ```
   class MyClass:
    def add(self, a, b):
        return a + b
    def add(self, a, b, c):
        return a + b + c
   # This will result in an ERROR in Python

   #CORRECT WAY:
   def add(a, b, c=None):
    if(c):
        return a+b+c 
    else:
        return a+b
   ```
2. Run-time Polymorphism (Dynamic Binding or Method Overriding):
   - a subclass can provide a specific implementation for a method that is already defined in its superclass.
   - Polymorphism enhances the flexibility and reusability of code
   ```
   class Animal:
     def make_sound(self):
       return "some sound"
   class Dog(Animal):
     def make_sound(self):
       return "Woof"
   dog = Dog()
   print(dog.make_sound())   #output: Woof
   ```

### Function Overloading
**Using Variable-Length Argument Lists:**  
```
class MyClass:
    def add(self, *args):
        return sum(args)

# Creating an instance of MyClass
my_object = MyClass()

# Calling the add method with different numbers of arguments
result1 = my_object.add(1)
result2 = my_object.add(1, 2)
result3 = my_object.add(1, 2, 3)

print(result1)  # Output: 1
print(result2)  # Output: 3
print(result3)  # Output: 6
```
the add method accepts a variable-length argument list (*args). It can take any number of arguments, and the sum function is used to calculate the sum of all arguments.

### Abstract Class  (@abstractmethod)

Abstract classes may contain abstract methods, which are methods that are declared in the abstract class but don't have an implementation.
```
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius ** 2
```
1. Abstract classes cannot be instantiated directly.
2. Abstract methods are declared using the @abstractmethod decorator in the abstract class.
3. Subclasses must provide concrete implementations for all abstract methods to be considered valid.
4. Abstract classes can contain both abstract and non-abstract methods.

### Nested Class
### Static method
.  
.  
.  




## Exception handling
- Try: The try block is used to enclose the code that might raise an exception
- Except: The except block is used to catch and handle specific exceptions that might occur within the try block. You can have multiple except blocks to handle different types of exceptions.
- Finally: The finally block contains code that will be executed regardless of whether an exception occurred or not. It is useful for cleanup operations.
- Else: The else block is optional and is executed only if no exceptions are raised in the try block. It is useful for code that should run only when there are no exceptions.
  ```
  try:
    result = 10 / 2
  except ZeroDivisionError:
    print("Error: Division by zero")
  else:
    print("No exceptions occurred")
    ```
- Raise: The raise statement is used to manually raise an exception. This can be useful when you want to indicate that a certain condition is an error.
  ```
  x = -1
  if x < 0:
      raise ValueError("Value must be non-negative")
  ```
Type of Exceptions in Python: Here are some common types of exceptions in Python:

- SyntaxError: Raised for syntax errors during parsing.
- IndentationError: Raised when there's an incorrect indentation.
- NameError: Raised when an identifier is not found in the local or global namespace.
- TypeError: Raised when an operation or function is applied to an object of an inappropriate type.
- ValueError: Raised when a function receives an argument of the correct type but an inappropriate value.
- ZeroDivisionError: Raised when division or modulo by zero is encountered.
- FileNotFoundError: Raised when a file or directory is requested but cannot be found.
- IndexError: Raised when a sequence subscript is out of range.
- Custom Exception  
   , etc


## Multithreading
1. Creating a Thread:
```
import threading

class MyThread(threading.Thread):
    def run(self):
        # Code to be executed in the thread
        print("Thread is running!")

# Create an instance of the custom thread class
my_thread = MyThread()
```
2. Starting a Thread:
Once you've created a thread instance, you can start it using the start() method. This method internally calls the run() method you defined.
my_thread.start()

3. Synchronization:
When multiple threads access shared resources, it's essential to synchronize them to avoid data corruption or unexpected behavior. You can use locks from the threading module for synchronization:

4. Thread State:
You can check the state of a thread using the is_alive() method. It returns True if the thread is currently executing.

5. Thread Join:
This method waits for the thread to complete its execution.
my_thread.join()
print("Thread has finished.")

> Additionally, you can use the Thread class's terminate() method to forcefully terminate a thread. However, it's generally not recommended to forcefully terminate threads due to potential resource leaks and data corruption.

### Sleep method
 used to pause the execution of the currently running thread for a specified amount of time.
```
import time

# Pause the current thread for 2 seconds
time.sleep(2)
```











