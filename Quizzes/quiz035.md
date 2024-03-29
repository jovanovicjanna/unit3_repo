# Quiz 35
## Code
```.py
import random
class Account:
     def __init__(self):
          self.balance = 0
          self.holder_name = ""
          self.holder_email = ""
          self.number = [random.randint(100,999), random.randint(10000,99999), random.randint(0,9)]

     def get_account_no(self)->str:
          return f"{self.number[0]}-{self.number[1]}-{self.number[2]}"

     def set_holder_name(self,name:str)->str:
          self.holder_name=name
          if not isinstance(self.holder_name, str):
               raise ValueError("Input must be string")
          return f"Holder's name set to {name}"

     def set_holder_email(self,email:str)->str:
          self.holder_email=email
          count = 0
          for l in self.holder_email:
               if l is "@":
                    count+=1
               if count >1:
                    raise ValueError()

          return f"Holder's email set to {email}"

     def get_balance(self)->int:
          return self.balance

     def deposit(self,amount:int)->str:
          self.balance=amount
          return f"New balance: {amount} USD"
```

## Test
```.py
import pytest
from quiz035 import Account

def test_empty_account():
    bk = Account()
    assert bk.balance == 0
    assert bk.holder_name == ""
    assert bk.holder_email == ""
    assert isinstance(bk.number, list)
    number = bk.get_account_no().split("-")
    assert  len(number)==3 and len(number[0])==3 and len(number[1])==5 and len(number[2])==1

def test_create_account():
    bk = Account()
    assert bk.get_balance() == 0
    assert bk.set_holder_name(name="Bob") == "Holder's name set to Bob"
    assert bk.set_holder_email(email="bob@company.xyz") == "Holder's email set to bob@company.xyz"
    assert bk.deposit(amount=100) == "New balance: 100 USD"
    assert bk.get_balance() == 100


def test_value_errors():
    bk = Account()
    with pytest.raises(ValueError):
        bk.set_holder_email(email="bob@bob@bob")
        bk.set_holder_name(name=["Bob"])
        bk.set_holder_name(name=100)
```

## Evidence
![](Screen%20Shot%202023-01-26%20at%2023.33.32.png)
