### 3. Liskov Substitution Principle
If we have an object of superclass (A) and an object of child class (B), then we should be able to replace A with B without affecting the existing behaviour of the program.

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
