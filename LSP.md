### 3. Liskov Substitution Principle
This principle was introduced by [Barbara Liskov](https://en.wikipedia.org/wiki/Barbara_Liskov). If we have an object of superclass (A) and an object of child class (B), then we should be able to replace A with B without affecting the existing behaviour of the program.

This Principle is about substitutability. Think about a vehicle rental service where they rent out cars. If they decide to offer motorbikes, those motorbikes should be able to be used wherever cars are used (like for transportation), without causing any issues. This is what LSP mandates in a programming context: if a program is using a base class (like "Vehicle"), and you decide to introduce a derived class (like "MotorBike"), the derived class should be able to be used wherever the base class is used, without causing any problems or changes in behavior.

Another example, consider a team of software developers using different IDEs (Integrated Development Environments) like Visual Studio, Eclipse, or PyCharm. Each IDE has its specific features and operations, but all of them allow for writing, editing, compiling, and debugging code.

In the context of a developer's daily routine, any IDE could be substituted for another, and their tasks - writing, editing, compiling, and debugging code - can still be achieved. This mirrors the Liskov Substitution Principle: any subclass (specific IDE) can replace their superclass (general concept of an IDE) without affecting the correctness of the program (the developer's tasks).

Continuing the example from the Open-closed principle, if we want to create a function that takes the `Hardware` and prints its functionality, we don’t want to create `if` `elif` `else` condition blocks to decide what to print. Instead, it will be much cleaner to create a generic function that just takes an object and prints the functionality.

```python
from abc import ABC, abstractmethod

class Hardware(ABC):
    
    @abstractmethod
    def functionality():
        pass

class Monitor(Hardware):
    
    def functionality(self):
        print('To display information on the screen.')

class Mouse(Hardware):
    
    def functionality(self):
        print('To move cursor on the screen and click on elements.')

class Keyboard(Hardware):
    
    def functionality(self):
        print('To help type the required information.')
        
class Printer(Hardware):
    
    def functionality(self):
        print('To print information on the paper.')

def print_functionality(h: Hardware):
    h.functionality()

mon = Monitor()
mou = Mouse()
key = Keyboard()
pri = Printer()

print_functionality(mon)
print_functionality(mou)
print_functionality(key)
print_functionality(pri)
```

In the `print_functionality` function, we can easily replace the object of the `Hardware` class with objects of the `Monitor`, `Mouse`, `Keyboard`, `Printer` classes.
