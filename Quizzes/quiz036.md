# Quiz 36
## Code
```.py
class Person:
    def __init__(self, name:str, age:int):
        self.name = name
        self.age = age
    def get_name(self) -> str:
        return self.name.title()
    def get_age(self) -> int:
        return self.age

class Student(Person):
    def __init__(self, name:str, age:int, grade:str):
        super().__init__(name=name, age=age)
        self.grade = grade
    def get_grade(self):
        return self.grade

bob = Student(name="bob", age=17, grade = "g11")
print(f"{bob.get_name()} is {bob.get_age()} and he is {bob.get_grade()}")
```
