# Quiz 033
## Code
```.py
def mystery(list1:list,list2:list)->list:
    output = []
    for element1 in list1:
        for element2 in list2:
            if element1==element2:
                output.append(element1)
    return output
```
## Test

```.py

import pytest
from quiz033 import mystery

def test_empty_lists():
  assert mystery([], []) == []

def test_one_common_element():
  assert mystery([1, 2, 3], [3, 4, 5]) == [3]

def test_multiple_common_elements():
  assert mystery([1, 2, 3, 4], [3, 4, 5, 6]) == [3, 4]
  ```
## Evidence
  
