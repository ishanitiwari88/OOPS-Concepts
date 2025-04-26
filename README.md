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








