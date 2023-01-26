# Quiz 34
## Code
```.py
class quiz34:
    def __init__(self, num:int):
        self.num = num

    def to_roman(self)->str:
        roman_num = ""
        if not isinstance(self.num,int):
            raise TypeError("Input must be integer")
        if self.num > 100 or self.num <= 0:
            raise ValueError("The input needs to be more than 0 and less or equal to 100")
        while self.num >0:
            for dig,r in [(100,'C'),(90,'XC'),(50,'L'),(40,'XL'),(10,'X'),(9,'IX'),(5,'V'),(4,'IV'),(1,'I')]:
                if self.num >= dig:
                    roman_num += r
                    self.num = self.num - dig
                    break

        return roman_num
  ```
        
# Test

```.py

from QUIZ_034 import quiz34
import pytest


def test_to_roman():
    assert quiz34(num=1).to_roman() == 'I'
    assert quiz34(num=4).to_roman() == 'IV'
    assert quiz34(num=9).to_roman() == 'IX'
    assert quiz34(num=37).to_roman() == 'XXXVII'
    assert quiz34(num=44).to_roman() == 'XLIV'
    assert quiz34(num=50).to_roman() == 'L'
    assert quiz34(num=99).to_roman() == 'XCIX'
    assert quiz34(num=100).to_roman() == 'C'
    assert quiz34(num=77).to_roman() == 'LXXVII'
    assert quiz34(num=93).to_roman() == 'XCIII'


def test_to_roman_exceptions():
    # check that the program raises a ValueError
    with pytest.raises(ValueError):
        quiz34(num=101).to_roman()

```

## Evidence
