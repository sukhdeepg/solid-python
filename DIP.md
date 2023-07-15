### 5. Dependency Inversion Principle
High-level modules or classes should not depend on low-level modules (concrete implementations) or classes. High-modules should depend on abstractions or interfaces.

Let's say we have a phone that charges via a specific brand's proprietary charger. This would be like a high-level module (the phone) depending on a low-level module (the specific charger). If we lose that charger, or if it breaks, we would have a tough time finding a replacement unless it's from the same brand.

The Dependency Inversion Principle would be like saying: instead of our phone only being able to charge from one specific charger, it should be able to charge from any power source that provides a standard USB connection (like a universal concept or rule). This way, we could use any charger as long as it has a USB connection.

So, a simpler real-world explanation could be: "Instead of relying on one specific item to work, things should be designed to work with any item that follows a common standard or rule, so it's easier to replace or change them."

Let’s see example for high-level and low-level class

```python
from abc import ABC, abstractmethod

class MusicPlayer:
    
    def play(self):
        music_service_a = MusicServiceA()
        music_service_a.play()
        
class MusicServiceA:
    
    def play(self):
        print('Playing music from MusicServiceA.')
        
mp = MusicPlayer()
mp.play()
```

`MusicPlayer` is the high-level class and `MusicServiceA` is the low-level class. Here, `MusicPlayer` is directly dependent on the `MusicServiceA` class. If tomorrow, we need another service to play music from, we would need to modify the `MusicPlayer` class which violates the OCP. To avoid this dependency, we can create a `MusicService` abstract class and pass it to the `MusicPlayer`.

```python
from abc import ABC, abstractmethod

class MusicPlayer:
    
    def __init__(self, music_service):
        self.music_service = music_service
    
    def play(self):
        self.music_service.play()
        
class MusicService(ABC):
    
    @abstractmethod
    def play(self):
        pass
        
class MusicServiceA(MusicService):
    
    def play(self):
        print('Playing music from MusicServiceA.')
        
class MusicServiceB(MusicService):
    
    def play(self):
        print('Playing music from MusicServiceB.')

msa = MusicServiceA()
msb = MusicServiceB()
mp1 = MusicPlayer(msa)
mp2 = MusicPlayer(msb)
mp1.play()
mp2.play()
```
