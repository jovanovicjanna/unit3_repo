# Quiz 36

### HL and SL part
## Code
```.py
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    def get_name(self):
        if not isinstance(self.name, str):
            raise ValueError("Name must be a string")
        return self.name

    def get_age(self):
        if not isinstance(self.age, int):
            raise ValueError("Number must be an integer")
        return self.age

class Student(Person):
    def __init__(self,name,age,grade):
        super().__init__(name,age)
        self.name = name
        self.age = age
        self.grade = grade
    def get_grade(self):
        return self.grade

class Classroom():
    def __init__(self):
        self.students = []

    def add_student(self,student:Student):
        self.students.append(student)

    def remove_student(self,student:Student):
        if student not in self.students:
            raise ValueError("Invalid student")
        self.students.remove(student)

    def get_average_score(self):
        if len(self.students) == 0:
            raise ValueError("No one is in the classroom")
        total = 0
        for student in self.students:
            total += student.get_grade()
        average=total/len(self.students)
        return average
```

## Test file

```.py
import pytest
from quiz036 import Student
from quiz036 import Classroom

def test_add_student():
    classroom = Classroom()
    student = Student("John", 18, 90)
    classroom.add_student(student)
    assert student in classroom.students

def test_remove_student():
    classroom = Classroom()
    student = Student("John", 18, 90)
    classroom.add_student(student)
    classroom.remove_student(student)
    assert student not in classroom.students

def test_remove_non_existing_student():
    classroom = Classroom()
    student = Student("John", 18, 90)
    with pytest.raises(ValueError):
        classroom.remove_student(student)

def test_get_average_score():
    classroom = Classroom()
    student1 = Student("John", 18, 90)
    student2 = Student("Jane", 19, 80)
    classroom.add_student(student1)
    classroom.add_student(student2)
    assert classroom.get_average_score() == (90 + 80) / 2

def test_empty_classroom():
    classroom = Classroom()
    with pytest.raises(ValueError):
        classroom.get_average_score()
```

## Evidence
![](Screen%20Shot%202023-02-06%20at%2020.13.52.png)

## UML diagram
![](Screen%20Shot%202023-02-07%20at%200.02.36.png)
