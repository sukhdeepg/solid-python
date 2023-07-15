### 1. Single Responsibility Principle
Easy to understand. Every module, class, or function should only have a single responsibility or only one reason to change. But it’s difficult to practically implement because lines can get blurry during implementation.

To simplify this, Uncle Bob says that *"This principle is about people"* in this [blog](https://blog.cleancoder.com/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html).

Let’s understand with an example
```python
class Payment:
    
    # process the payment
    def process(self):
        pass
    
    # save the payment
    def save(self):
        pass
    
    # retrieve the payment information
    def retrieve(self):
        pass
    
    # return analytics data related to payment. E.g. processing time of payment
    def analytics(self):
        pass
    
    # check if the information for payment is correct or not. E.g. card number, CVV, etc
    def check(self):
        pass
```

As we can see, this class is performing a lot of functions for a given payment and has more than one reason to change. What if we have different people using these functionalities? If one person thinks to change the `check` function logic and return `dict` e.g `{“is_cvv_valid”: True}` instead of `list` e.g. `[("is_cvv_valid", True)]`, this will affect the processing logic and eventually, analytics will create panic!

It will be better if each functionality is isolated and handled by a single team or individual in order to avoid any dependency and compatibility issues. Each functionality will have a standard output format. So, even if the internal logic changes for a functionality, it won’t affect the other dependent functionalities and will also have a single responsibility and reason to change. This will make the code more cohesive and easier to maintain.

```python
class ProcessPayment:
    
    def process(self):
        pass
    
class SavePayment:
    
    def save(self):
        pass

class RetrievePayment:
    
    def retrieve(self):
        pass
    
class AnalyticsPayment:
    
    def analytics(self):
        pass
    
class SecCheckPayment:
    
    def security_check(self):
        pass
```
