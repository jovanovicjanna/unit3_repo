# Quiz 037
## Test
```.py
class CompoundInterest:
    def __init__(self, principal:int,rate:int,years:int):
        self.principal = principal
        self.rate = rate
        self.years = years

    def Calculate(self):
        return self.principal *(1 + self.rate) ** self.years


class AccountingProgram:
    def __init__(self):
        self.data = CompoundInterest(principal=0, rate=0,years=0)

    def set_rate(self,rate):
        self.data.rate = rate

    def set_years(self,years):
        self.data.years = years

    def set_principal(self,principal):
        self.data.principal = principal

    def calculate_interest(self):
        return self.data.Calculate()

Save = CompoundInterest(principal=100,rate=0.1,years=10)
print(Save.Calculate())
```
