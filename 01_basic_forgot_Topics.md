# Python Interview Notes – Q3 to Q20

## Q3. Concatenating Lists (+ vs. extend)

**Q. What is the difference between `+` and `extend()` in Python?**

Both are used to combine lists, but their behavior is different.

### 1. Using `+` Operator

- Creates a new list.
- Original lists remain unchanged.

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

result = list1 + list2

print(result)  # [1, 2, 3, 4, 5, 6]
print(list1)   # [1, 2, 3]
```

### 2. Using extend()

- Adds elements to the existing list.
- Modifies the original list.
- Returns `None`.

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

result = list1.extend(list2)

print(list1)   # [1, 2, 3, 4, 5, 6]
print(result)  # None
```

### Interview Questions

**Q1. Does `extend()` return a new list?**

Ans: No. It modifies the original list and returns `None`.

**Q2. What is the output?**

```python
a = [1, 2]
b = a
a.extend([3, 4])

print(b)
```

Ans: `[1, 2, 3, 4]`

Reason: Both variables reference the same list.

---

## Q5. How to Floor a Number?

**Q. What is floor in Python?**

Floor means rounding a number down to the nearest integer, towards negative infinity.

Python provides the `math.floor()` function.

```python
import math

print(math.floor(4.8))   # 4
print(math.floor(4.2))   # 4
print(math.floor(-4.2))  # -5
```

Important: Floor does not always mean removing decimal digits. It means rounding towards negative infinity.

### Difference: floor() vs int()

```python
import math

print(math.floor(-4.8))  # -5
print(int(-4.8))         # -4
```

- `math.floor()` rounds towards negative infinity.
- `int()` truncates the decimal part towards zero.

### Interview Questions

**Q1. What is the output?**

```python
import math
print(math.floor(-7.1))
```

Ans: `-8`

**Q2. Difference between `floor()` and `ceil()`?**

Ans:
- `floor()` rounds down.
- `ceil()` rounds up.

```python
import math

print(math.floor(4.8))  # 4
print(math.ceil(4.2))   # 5
```

---

## Q6. Division (/) vs. Floor Division (//)

**Q. What is the difference between `/` and `//` in Python?**

### 1. Normal Division (/)

Returns the division result as a floating-point number.

```python
print(10 / 3)  # 3.3333333333333335
print(10 / 2)  # 5.0
```

### 2. Floor Division (//)

Returns the floor of the division result.

```python
print(10 // 3)   # 3
print(10 // 2)   # 5
print(-10 // 3)  # -4
```

Important: `//` rounds towards negative infinity, not towards zero.

### Interview Questions

**Q1. What is the output?**

```python
print(7 / 2)
print(7 // 2)
```

Ans:
```text
3.5
3
```

**Q2. What is the output?**

```python
print(-7 // 2)
```

Ans: `-4`

**Q3. Does floor division always return an integer?**

Ans: No. If one or both operands are floats, the result can also be a float.

```python
print(7.0 // 2)  # 3.0
```

---

## Q7. Passing Functions as Arguments

**Q. Can we pass a function as an argument to another function in Python?**

Yes. Python treats functions as first-class objects.

This means functions can be:
- Assigned to variables.
- Passed as arguments.
- Returned from other functions.

### Example

```python
def greet():
    return "Hello Python"

def display(func):
    print(func())

display(greet)
```

Output:

```text
Hello Python
```

Explanation:

- `greet` is passed as an argument.
- `func` receives the function reference.
- `func()` executes that function.

Important difference:

```python
display(greet)    # Passes function reference
display(greet())  # Passes function's return value
```

### Interview Questions

**Q1. What is a first-class function?**

Ans: A function that can be assigned to variables, passed as an argument, and returned from another function.

**Q2. What is a higher-order function?**

Ans: A function that accepts another function as an argument or returns a function.

---

## Q8. Lambda Functions Explained

**Q. What is a lambda function in Python?**

A lambda function is a small anonymous function defined using the `lambda` keyword.

Syntax:

```python
lambda arguments: expression
```

### Example 1: Normal Function

```python
def add(a, b):
    return a + b

print(add(10, 20))
```

### Example 2: Lambda Function

```python
add = lambda a, b: a + b

print(add(10, 20))
```

Output:

```text
30
```

### Lambda with map()

```python
numbers = [1, 2, 3, 4]

result = list(map(lambda x: x * 2, numbers))

print(result)
```

Output:

```text
[2, 4, 6, 8]
```

### Lambda with filter()

```python
numbers = [1, 2, 3, 4, 5, 6]

result = list(filter(lambda x: x % 2 == 0, numbers))

print(result)
```

Output:

```text
[2, 4, 6]
```

### Interview Questions

**Q1. Can a lambda function contain multiple expressions?**

Ans: No. A lambda function contains a single expression.

**Q2. Can lambda functions have multiple arguments?**

Ans: Yes.

```python
multiply = lambda a, b: a * b
print(multiply(5, 4))
```

**Q3. Difference between lambda and def?**

Ans:
- `def` defines a regular named function.
- `lambda` creates an anonymous function using a single expression.

---

## Q9. List Comprehension

**Q. What is list comprehension in Python?**

List comprehension provides a shorter way to create a new list from an iterable.

Syntax:

```python
[expression for item in iterable if condition]
```

### Example 1: Normal Approach

```python
numbers = [1, 2, 3, 4, 5]

result = []

for num in numbers:
    result.append(num * 2)

print(result)
```

### Example 2: List Comprehension

```python
numbers = [1, 2, 3, 4, 5]

result = [num * 2 for num in numbers]

print(result)
```

Output:

```text
[2, 4, 6, 8, 10]
```

### List Comprehension with Condition

Get only even numbers:

```python
numbers = [1, 2, 3, 4, 5, 6]

result = [num for num in numbers if num % 2 == 0]

print(result)
```

Output:

```text
[2, 4, 6]
```

### Interview Questions

**Q1. What is the advantage of list comprehension?**

Ans: It provides concise and readable code for creating lists.

**Q2. Can we use if-else in list comprehension?**

Ans: Yes.

```python
numbers = [1, 2, 3, 4]

result = ["Even" if x % 2 == 0 else "Odd" for x in numbers]

print(result)
```

Output:

```text
['Odd', 'Even', 'Odd', 'Even']
```

**Q3. Difference between list comprehension and generator expression?**

Ans:

```python
a = [x * 2 for x in range(5)]  # List
b = (x * 2 for x in range(5))  # Generator
```

- List comprehension creates the complete list in memory.
- Generator expression produces values lazily, one at a time.

---

## Q10. *args vs. **kwargs

**Q. What are *args and **kwargs in Python?**

They allow a function to accept a variable number of arguments.

### 1. *args

Used to pass a variable number of positional arguments.

Inside the function, `args` is a tuple.

```python
def add(*args):
    print(args)
    print(type(args))

add(10, 20, 30, 40)
```

Output:

```text
(10, 20, 30, 40)
<class 'tuple'>
```

Example:

```python
def add(*args):
    return sum(args)

print(add(10, 20, 30))
```

Output: `60`

### 2. **kwargs

Used to pass a variable number of keyword arguments.

Inside the function, `kwargs` is a dictionary.

```python
def display(**kwargs):
    print(kwargs)
    print(type(kwargs))

display(name="Govind", age=30, city="Indore")
```

Output:

```text
{'name': 'Govind', 'age': 30, 'city': 'Indore'}
<class 'dict'>
```

### Difference

| Feature | *args | **kwargs |
|---|---|---|
| Purpose | Positional arguments | Keyword arguments |
| Data type | Tuple | Dictionary |
| Symbol | Single * | Double ** |

### Interview Questions

**Q1. Can we use both *args and **kwargs together?**

Ans: Yes.

```python
def test(*args, **kwargs):
    print(args)
    print(kwargs)

test(10, 20, name="Python")
```

Output:

```text
(10, 20)
{'name': 'Python'}
```

**Q2. Are args and kwargs reserved keywords?**

Ans: No. They are conventional names. The `*` and `**` symbols provide the special behavior.

---

## Q11. Set vs. Dictionary

**Q. What is the difference between a Set and a Dictionary in Python?**

### 1. Set

A set is an unordered collection of unique elements.

```python
numbers = {1, 2, 3, 4, 4}

print(numbers)
```

Output:

```text
{1, 2, 3, 4}
```

Important:
- Duplicate elements are automatically removed.
- Sets are mutable.
- Elements must be hashable.
- Set does not support indexing.

### 2. Dictionary

A dictionary stores data in key-value pairs.

```python
student = {
    "name": "Govind",
    "age": 30,
    "city": "Indore"
}

print(student["name"])
```

Output:

```text
Govind
```

Important:
- Keys must be unique.
- Values can be duplicated.
- Dictionaries preserve insertion order (Python 3.7+).
- Keys must be hashable.

### Empty Set vs Empty Dictionary

```python
a = set()
b = {}

print(type(a))  # <class 'set'>
print(type(b))  # <class 'dict'>
```

### Difference

| Feature | Set | Dictionary |
|---|---|---|
| Data | Unique values | Key-value pairs |
| Duplicate | Not allowed | Duplicate keys not allowed |
| Indexing | No | Access using keys |
| Mutable | Yes | Yes |
| Syntax | `{1, 2, 3}` | `{"a": 1}` |

### Interview Questions

**Q1. How do you create an empty set?**

Ans: `set()`

**Q2. Can a set contain duplicate values?**

Ans: No.

**Q3. Can a dictionary have duplicate keys?**

Ans: No. Assigning a value to an existing key updates its value.

---

## Q12. Docstrings in Python

**Q. What is a docstring in Python?**

A docstring is a string literal used to document a module, class, or function.

It is generally written using triple quotes immediately after the definition.

### Example

```python
def add(a, b):
    """
    This function adds two numbers.

    Parameters:
        a: First number
        b: Second number

    Returns:
        Sum of two numbers
    """
    return a + b

print(add(10, 20))
```

### Accessing Docstring

```python
print(add.__doc__)
```

Or:

```python
help(add)
```

### Interview Questions

**Q1. What is the difference between a comment and a docstring?**

Ans:
- Comments explain code to developers and start with `#`.
- Docstrings document modules, classes, and functions.
- Docstrings are accessible at runtime using `__doc__`.

**Q2. Where should a docstring be placed?**

Ans: Immediately after the function, class, or module definition.

---

## Q13. Exception Handling (Try/Except)

**Q. What is exception handling in Python?**

Exception handling allows us to handle runtime errors without abruptly terminating the program.

Python provides:
- `try`
- `except`
- `else`
- `finally`
- `raise`

### Basic Example

```python
try:
    a = 10
    b = 0

    result = a / b

except ZeroDivisionError:
    print("Cannot divide by zero")
```

Output:

```text
Cannot divide by zero
```

### try-except-else-finally

```python
try:
    a = 10
    b = 2

    result = a / b

except ZeroDivisionError:
    print("Division error")

else:
    print("Result:", result)

finally:
    print("Execution completed")
```

Explanation:

- `try`: Code that may generate an exception.
- `except`: Handles the exception.
- `else`: Executes if no exception occurs in the try block.
- `finally`: Executes whether an exception occurs or not.

### Multiple Exceptions

```python
try:
    num = int(input("Enter number: "))
    result = 10 / num

except ValueError:
    print("Please enter a valid integer")

except ZeroDivisionError:
    print("Cannot divide by zero")
```

### Raising an Exception

```python
age = 15

if age < 18:
    raise ValueError("Age must be 18 or above")
```

### Interview Questions

**Q1. Is finally always executed?**

Ans: In normal program execution, yes. However, situations like forced process termination or certain system-level failures can prevent it.

**Q2. What is the difference between errors and exceptions?**

Ans: Exceptions are runtime events that can often be handled. Errors is a broader term for problems in a program.

**Q3. Can we have multiple except blocks?**

Ans: Yes.

**Q4. What is the purpose of raise?**

Ans: It explicitly raises an exception.

---

## Q14. Shallow Copy vs. Deep Copy

**Q. What is the difference between shallow copy and deep copy in Python?**

Python provides the `copy` module for copying objects.

### 1. Shallow Copy

A shallow copy creates a new outer object but keeps references to the nested objects.

```python
import copy

original = [[1, 2], [3, 4]]

shallow = copy.copy(original)

shallow[0][0] = 100

print(original)
print(shallow)
```

Output:

```text
[[100, 2], [3, 4]]
[[100, 2], [3, 4]]
```

Reason: Both outer lists reference the same nested lists.

### 2. Deep Copy

A deep copy creates a new outer object and recursively copies nested objects.

```python
import copy

original = [[1, 2], [3, 4]]

deep = copy.deepcopy(original)

deep[0][0] = 100

print(original)
print(deep)
```

Output:

```text
[[1, 2], [3, 4]]
[[100, 2], [3, 4]]
```

Reason: Nested objects are copied independently.

### Difference

| Feature | Shallow Copy | Deep Copy |
|---|---|---|
| Outer object | New | New |
| Nested objects | Shared references | Recursively copied |
| Module function | copy.copy() | copy.deepcopy() |
| Performance | Generally faster | Generally slower |
| Memory | Generally less | Generally more |

### Interview Questions

**Q1. Does shallow copy create a new object?**

Ans: Yes, it creates a new outer object.

**Q2. Why does changing a nested list in shallow copy affect the original?**

Ans: Because both lists reference the same nested object.

**Q3. Which copy is independent of nested objects?**

Ans: Deep copy.

---

## Q15. Python Decorators are Higher-Order Functions

**Q. What is a decorator in Python?**

A decorator is a function that takes another function as an argument, adds or modifies its behavior, and returns a function.

Decorators are commonly used for:
- Logging
- Authentication
- Authorization
- Performance measurement
- Caching

### Basic Example

```python
def my_decorator(func):

    def wrapper():
        print("Before function execution")

        func()

        print("After function execution")

    return wrapper


@my_decorator
def greet():
    print("Hello Python")


greet()
```

Output:

```text
Before function execution
Hello Python
After function execution
```

### How does @my_decorator work?

This:

```python
@my_decorator
def greet():
    print("Hello")
```

Is equivalent to:

```python
def greet():
    print("Hello")

greet = my_decorator(greet)
```

### Decorator with Arguments

Use `*args` and `**kwargs` to support different function arguments.

```python
def my_decorator(func):

    def wrapper(*args, **kwargs):
        print("Before execution")

        result = func(*args, **kwargs)

        print("After execution")

        return result

    return wrapper


@my_decorator
def add(a, b):
    return a + b


print(add(10, 20))
```

Output:

```text
Before execution
After execution
30
```

### Interview Questions

**Q1. Why are decorators called higher-order functions?**

Ans: Because they accept another function as an argument and return a function.

**Q2. What is the purpose of wrapper()?**

Ans: It wraps the original function and adds additional behavior.

**Q3. What is @ syntax called?**

Ans: Decorator syntax.

**Q4. What is functools.wraps?**

Ans: It preserves metadata such as the original function's name and docstring.

Example:

```python
from functools import wraps

def my_decorator(func):

    @wraps(func)
    def wrapper(*args, **kwargs):
        return func(*args, **kwargs)

    return wrapper
```

---

## Q16. Range vs. Xrange

**Q. What is the difference between range() and xrange()?**

This is an important Python 2 vs Python 3 interview question.

### Python 2

- `range()` returns a list.
- `xrange()` returns a lazy sequence-like object.
- `xrange()` is generally more memory efficient for large ranges.

### Python 3

- `range()` returns an immutable range object.
- `xrange()` does not exist.
- Python 3 `range()` is memory efficient because it does not create a complete list of numbers.

Example:

```python
numbers = range(1, 6)

print(numbers)
print(list(numbers))
```

Output:

```text
range(1, 6)
[1, 2, 3, 4, 5]
```

### Interview Questions

**Q1. Does xrange() exist in Python 3?**

Ans: No.

**Q2. What does range() return in Python 3?**

Ans: An immutable range object.

**Q3. How do you convert range into a list?**

Ans:

```python
numbers = list(range(1, 6))
```

---

## Q17. Inheritance in Python

**Q. What is inheritance in Python?**

Inheritance is an OOP concept in which one class acquires the properties and methods of another class.

It promotes:
- Code reusability
- Extensibility
- Better code organization

### Example

```python
class Parent:

    def show(self):
        print("This is Parent class")


class Child(Parent):

    def display(self):
        print("This is Child class")


obj = Child()

obj.show()
obj.display()
```

Output:

```text
This is Parent class
This is Child class
```

Explanation:

- `Parent` is the base or parent class.
- `Child` is the derived or child class.
- Child inherits the `show()` method from Parent.

### Interview Questions

**Q1. What is inheritance?**

Ans: It allows one class to reuse properties and methods of another class.

**Q2. What is a parent class?**

Ans: The class whose properties and methods are inherited.

**Q3. What is a child class?**

Ans: The class that inherits from another class.

**Q4. Does Python support multiple inheritance?**

Ans: Yes.

---

## Q18. Types of Inheritance

Python supports the following major types of inheritance.

### 1. Single Inheritance

One child class inherits from one parent class.

```python
class A:
    def show(self):
        print("Class A")


class B(A):
    pass


obj = B()
obj.show()
```

### 2. Multiple Inheritance

One child class inherits from multiple parent classes.

```python
class A:
    def show_a(self):
        print("Class A")


class B:
    def show_b(self):
        print("Class B")


class C(A, B):
    pass


obj = C()

obj.show_a()
obj.show_b()
```

### 3. Multilevel Inheritance

A class inherits from a child class, forming multiple levels.

```python
class A:
    def show(self):
        print("Class A")


class B(A):
    pass


class C(B):
    pass


obj = C()
obj.show()
```

### 4. Hierarchical Inheritance

Multiple child classes inherit from the same parent class.

```python
class Parent:
    def show(self):
        print("Parent class")


class Child1(Parent):
    pass


class Child2(Parent):
    pass


obj1 = Child1()
obj2 = Child2()

obj1.show()
obj2.show()
```

### 5. Hybrid Inheritance

Combination of two or more types of inheritance.

```python
class A:
    def show(self):
        print("Class A")


class B(A):
    pass


class C(A):
    pass


class D(B, C):
    pass


obj = D()
obj.show()
```

### Interview Questions

**Q1. How many major types of inheritance are commonly discussed in Python?**

Ans: Five: Single, Multiple, Multilevel, Hierarchical and Hybrid.

**Q2. Does Python support multiple inheritance?**

Ans: Yes.

**Q3. What is hybrid inheritance?**

Ans: It is a combination of multiple inheritance structures.

**Q4. What is MRO?**

Ans: Method Resolution Order defines the order in which Python searches for methods in an inheritance hierarchy.

---

## Q19. Method Overriding

**Q. What is method overriding in Python?**

Method overriding occurs when a child class provides its own implementation of a method already defined in its parent class.

### Example

```python
class Parent:

    def show(self):
        print("Parent method")


class Child(Parent):

    def show(self):
        print("Child method")


obj = Child()

obj.show()
```

Output:

```text
Child method
```

Explanation:

The child class overrides the parent's `show()` method.

### Using Parent Method with super()

```python
class Parent:

    def show(self):
        print("Parent method")


class Child(Parent):

    def show(self):
        super().show()
        print("Child method")


obj = Child()
obj.show()
```

Output:

```text
Parent method
Child method
```

### Interview Questions

**Q1. What is method overriding?**

Ans: Providing a new implementation of a parent class method in the child class.

**Q2. Is method overriding related to inheritance?**

Ans: Yes. It occurs when a child class redefines an inherited method.

**Q3. Does Python support method overloading?**

Ans: Python does not support traditional compile-time method overloading based only on different parameter signatures. Similar behavior can be implemented using default arguments, `*args`, or other techniques.

---

## Q20. The super() Function

**Q. What is the super() function in Python?**

The `super()` function provides access to methods from the next class in the Method Resolution Order (MRO).

It is commonly used to call parent class methods and constructors.

### Example 1: Calling Parent Method

```python
class Parent:

    def show(self):
        print("Parent show method")


class Child(Parent):

    def show(self):
        super().show()
        print("Child show method")


obj = Child()
obj.show()
```

Output:

```text
Parent show method
Child show method
```

### Example 2: Calling Parent Constructor

```python
class Parent:

    def __init__(self, name):
        self.name = name


class Child(Parent):

    def __init__(self, name, age):
        super().__init__(name)
        self.age = age


obj = Child("Govind", 30)

print(obj.name)
print(obj.age)
```

Output:

```text
Govind
30
```

### Interview Questions

**Q1. Why do we use super()?**

Ans: To access the next implementation of a method in the MRO.

**Q2. Can super() call the parent constructor?**

Ans: Yes.

**Q3. Is super() limited to the immediate parent class?**

Ans: No. It follows the Method Resolution Order, which is especially important in multiple inheritance.

**Q4. What is MRO?**

Ans: MRO is the order in which Python searches classes for a method or attribute.

Check MRO:

```python
print(Child.mro())
```

---

# Quick Interview Revision – Important Questions

| Topic | Must Remember |
|---|---|
| List + vs extend() | New list vs modify existing list |
| floor() | Rounds towards negative infinity |
| / vs // | Normal vs floor division |
| First-class functions | Functions are objects |
| Lambda | Anonymous single-expression function |
| List comprehension | Short way to create lists |
| *args | Tuple |
| **kwargs | Dictionary |
| Set | Unique elements |
| Dictionary | Key-value pairs |
| Docstring | Function/class documentation |
| Exception handling | try, except, else, finally |
| Shallow copy | Nested objects are shared |
| Deep copy | Nested objects are recursively copied |
| Decorator | Function that wraps another function |
| range() | Immutable range object in Python 3 |
| Inheritance | Code reusability |
| MRO | Method lookup order |
| Overriding | Child redefines inherited method |
| super() | Calls next implementation in MRO |

# Practice: Output-Based Interview Questions

**Q1. What is the output?**

```python
a = [1, 2]
b = a
a = a + [3]

print(b)
```

<details>
<summary>Answer</summary>

`[1, 2]`

Reason: `+` creates a new list and `a` references the new list. `b` still references the original list.

</details>

**Q2. What is the output?**

```python
print(-10 // 3)
print(int(-10 / 3))
```

<details>
<summary>Answer</summary>

```text
-4
-3
```

Reason: Floor division rounds down, while int() truncates towards zero.

</details>

**Q3. What is the output?**

```python
x = lambda a: a * 2

print(x(5))
```

<details>
<summary>Answer</summary>

`10`

</details>

**Q4. What is the output?**

```python
def test(*args):
    return type(args)

print(test(1, 2, 3))
```

<details>
<summary>Answer</summary>

`<class 'tuple'>`

</details>

**Q5. What is the output?**

```python
a = {1, 2, 2, 3}

print(len(a))
```

<details>
<summary>Answer</summary>

`3`

Reason: Sets do not store duplicate elements.

</details>

**Q6. What is the output?**

```python
class A:
    def show(self):
        print("A")


class B(A):
    def show(self):
        print("B")


obj = B()
obj.show()
```

<details>
<summary>Answer</summary>

`B`

Reason: Child class overrides the parent method.

</details>

---

**End of Python Interview Notes – Q3 to Q20**