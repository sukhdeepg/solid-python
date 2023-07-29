### 4. Interface Segregation Principle
> The interface segregation principle (ISP) states that no code should be forced to depend on methods it does not use. [Source](https://en.wikipedia.org/wiki/Interface_segregation_principle#cite_note-ASD-1).

Think of a coffee shop that offers various services, such as making coffee, selling baked goods, and providing free Wi-Fi. The Interface Segregation Principle (ISP) is like saying that instead of having a single line where a customer has to wait to order coffee, buy a croissant, and ask for the Wi-Fi password, it would be better to segregate these interfaces. So, you'd have one line for ordering coffee, another for buying baked goods, and a sign with the Wi-Fi details. This way, customers who just want a croissant aren't stuck behind someone trying to decide which coffee to order, and those who just want the Wi-Fi don't have to queue at all. Each service is an 'interface', and customers only use the ones they need.

If we add the `firmware_update` function to our `Hardware` class, it would mean that, all our child classes would need to have the `firmware_update` function.

```python
class Hardware(ABC):
    
    @abstractmethod
    def functionality():
        pass
    
    @abstractmethod
    def firmware_update():
        pass
```

Now, this `firmware_update` function will not be used by the `mouse` and `keyboard` usually. So, why do these classes even need to have this function? This violates the ISP.
To avoid this, we can have the following update

```python
from abc import ABC, abstractmethod

class Hardware(ABC):
    
    @abstractmethod
    def functionality():
        pass
    
class Firmware(ABC):
    
    @abstractmethod
    def update():
        pass

class Monitor(Hardware, Firmware):
    
    def functionality(self):
        print('To display information on the screen.')
        
    def update():
        print('Updating firmware.')

class Mouse(Hardware):
    
    def functionality(self):
        print('To move cursor on the screen and click on elements.')

class Keyboard(Hardware):
    
    def functionality(self):
        print('To help type the required information.')
        
class Printer(Hardware, Firmware):
    
    def functionality(self):
        print('To print information on the paper.')
        
    def update(self):
        print('Updating firmware.')
```
