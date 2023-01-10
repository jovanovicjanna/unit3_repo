# Quiz 033
# Code
```.py
def mystery(list1:list,list2:list)->list:
    output = []
    for element1 in list1:
        for element2 in list2:
            if element1==element2:
                output.append(element1)
    return output
```
