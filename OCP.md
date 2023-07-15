### 2. Open-closed Principle
Open for extension but closed for modification. *Extension* means that we’re extending the functionality of our code. *Modification* means that we’re modifying our existing code.

Now, which sounds more risky? modification, right? Because when we write our code, test it, and deploy it, we should not go back and modify it, as this can lead to instability, create bugs, etc.

In Python (and in many other languages), we can make use of an abstract base class to help us extend the functionality of our code.

Let’s understand with an example

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

mon = Monitor()
mou = Mouse()
key = Keyboard()

mon.functionality()
mou.functionality()
key.functionality()
```

Here, if we need to add functionality for Printer, we don’t need to modify any existing class or function, we can simply extend the Hardware class and create the functionality.

```python
class Printer(Hardware):
    
    def functionality(self):
        print('To print information on the paper.')
```
