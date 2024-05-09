# Python

[Python Playground](https://www.programiz.com/python-programming/online-compiler/)

## Hello World

<details>
<summary>View codes</summary>

```py
def greeting(name: str) -> None:
    '''Takes in a string name, prints greeting message'''
    print(f"Hello, {name}") # print greeting

if __name__ == '__main__':
    greeting('Bangladesh')
```
    
</details>

## Reserved Words (Keywords)

<details>
<summary>View details</summary>

1. False
2. None
3. True

```py
is_valid = True
is_old = False
val = None
```

4. and
5. or
6. not

```py
a = True
b = False

print(a and b) # False
print(a or b) # True
print(not a) # False
```

7. import
8. from
9. as

```py
from math import sqrt as square_root

print(square_root(16)) # 4.0
```

10. assert

```py
# assert is used to check if a condition is True.
# If it's not, it raises an AssertionError with an optional error message.

x = 5
assert x > 0, "x must be positive"
```

11. async
12. await
13. def

```py
# async is used to define a coroutine function, which can be paused and resumed.
# await is used to suspend execution of an async function until the result is available.

import asyncio

async def example():
  await asyncio.sleep(1)
  print("Hello")

asyncio.run(example())
```

14. break
15. continue
16. for
17. if
18. elif
19. else

```py
for i in range(10):
  if i % 2 == 0:
    print("even:", i)
  elif i == 3:
    continue
  elif i == 9:
    break
  else:
    print("odd:", i)

# Outputs:
# even: 0
# odd: 1
# even: 2
# even: 4
# odd: 5
# even: 6
# odd: 7
# even: 8
```

20. class

```py
class MyClass:
  def __init__(self, x):
    self.x = x

mc = MyClass(10)
```

21. del

```py
# del is used to delete items from lists, slices of lists, variables, or even attributes from objects.

my_list = [1, 2, 3]
my_dict = {"name": "Ali", "age": 20}

del my_list[0]
del my_dict["name"]

print(my_list) # [2, 3]
print(my_dict) # {age: 20}
```

22. except
23. finally

```py
# except is used in exception handling to catch and handle exceptions.
# It specifies one or more exception types that the except block will handle.

try:
  f = open("my_file.txt")
except FileNotFoundError:
  print("File not found")
finally:
  # Ensure the file is always closed, even if an exception occurs
  f.close()
```

24. global

```py
# global is used inside functions to declare that a variable is global, meaning it belongs to the global scope.

x = 10

def my_func():
  global x
  x = 20

my_func()
print(x) # 20
```

25. in

```py
# in is used to check if a value exists in a sequence such as a list, tuple, string or dictionary.

my_list = [1, 2, 3]
my_tuple = (1, 2, 3)
my_str = "Hello"
my_dict = {"a": 1}

print(3 in my_list) # True
print(2 in my_tuple) # True
print("h" in my_str) # False
print("a" in my_dict) # True
```

26. is

```py
# is is used to test if two variables refer to the same object in memory.
x = [1, 2]
y = [1, 2]
z = True

print(x is y) # False
print(z is True) # True
```

27. lambda

```py
# lambda is used to create small anonymous functions.

square = lambda x: x * x
print(square(5)) # 25
```

28. nonlocal

```py
# nonlocal is used inside nested functions to declare that a variable belongs to an outer (but not global) scope.

def outer_func():
  x = 10
  def inner_func():
    nonlocal x
    x = 20
  inner_func()
  print(x) # 20
outer_func()
```

29. pass

```py
# pass is a null operation. It is used when a statement is required syntactically
# but you do not want any command or code to execute.

if 10 > 5:
  pass
```

30. raise
31. return

```py
# raise is used to raise an exception manually.

def check_positive(x):
  if x < 0:
    raise ValueError("x should be a positive number")
  return x

check_positive(10)
check_positive(-1)
```

32. while

```py
i = 0
while i < 5:
    print(i)
    i += 1
```

33. with

```py
# with is used to simplify exception handling by ensuring that clean-up code is executed, even if an error occurs.

with open("myfile.txt", "r") as file:
  data = file.read()
  print(data)
```

34. yield

```py
# yield is used inside a function like a return statement but it returns a generator.
#  a generator is a special type of iterator that allows you to iterate over a sequence of values lazily,
# generating values on-the-fly rather than storing them in memory all at once.

def generator():
  for i in range(5):
    yield i

gen = generator()
for value in gen:
  print(value)
```

</details>

## Built-in functions

<details>
<summary>View contents</summary>

1. **abs()**: Returns the absolute value of a number.
   ```python
   num = -5
   print(abs(num))  # Output: 5
   ```

2. **dict()**: Creates a new dictionary.
   ```python
   new_dict = dict(a=1, b=2, c=3)
   print(new_dict)  # Output: {'a': 1, 'b': 2, 'c': 3}
   ```

3. **help()**: Invokes the built-in help system.
   ```python
   help(str)
   ```

4. **min()**: Returns the smallest item in an iterable.
   ```python
   numbers = [3, 1, 4, 1, 5, 9, 2, 6]
   print(min(numbers))  # Output: 1
   ```

5. **all()**: Returns `True` if all elements of an iterable are true.
   ```python
   iterable = [True, True, False]
   print(all(iterable))  # Output: False
   ```

6. **dir()**: Returns a list of the names in the current local scope or a list of object attributes.
   ```python
   print(dir())  # Output: ['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', 'numbers']
   ```

7. **hex()**: Converts an integer to a lowercase hexadecimal string prefixed with "0x".
   ```python
   num = 255
   print(hex(num))  # Output: 0xff
   ```

8. **next()**: Retrieves the next item from the iterator.
   ```python
   iterator = iter([1, 2, 3])
   print(next(iterator))  # Output: 1
   ```

9. **any()**: Returns `True` if any element of an iterable is true.
   ```python
   iterable = [False, False, True]
   print(any(iterable))  # Output: True
   ```

10. **divmod()**: Returns the quotient and the remainder when dividing two numbers.
    ```python
    result = divmod(10, 3)
    print(result)  # Output: (3, 1)
    ```

11. **ascii()**: Returns a string containing a printable representation of an object, but escape non-ASCII characters.
   ```python
   print(ascii('π is a greek letter'))  # Output: "'\\u03c0 is a greek letter'"
   ```

12. **enumerate()**: Returns an enumerate object, which yields pairs containing a count (from start, which defaults to 0) and a value yielded by the iterable.
   ```python
   my_list = ['apple', 'banana', 'cherry']
   for index, fruit in enumerate(my_list):
       print(index, fruit)
   # Output:
   # 0 apple
   # 1 banana
   # 2 cherry
   ```

13. **input()**: Reads a line from input, converts it to a string (stripping a trailing newline), and returns that.
   ```python
   name = input("Enter your name: ")
   print("Hello, " + name)
   ```

14. **oct()**: Converts an integer to an octal string prefixed with "0o".
   ```python
   num = 8
   print(oct(num))  # Output: 0o10
   ```

15. **bin()**: Converts an integer to a binary string prefixed with "0b".
   ```python
   num = 5
   print(bin(num))  # Output: 0b101
   ```

16. **eval()**: Evaluates a Python expression given as a string and returns the result.
   ```python
   result = eval('2 + 2')
   print(result)  # Output: 4
   ```

17. **int()**: Returns an integer object constructed from a number or string.
   ```python
   num = int('10')
   print(num)  # Output: 10
   ```

18. **open()**: Opens a file and returns a corresponding file object.
   ```python
   file = open('example.txt', 'r')
   content = file.read()
   print(content)
   file.close()
   ```

19. **bool()**: Converts a value to a Boolean.
   ```python
   print(bool(0))  # Output: False
   print(bool(1))  # Output: True
   ```

20. **exec()**: Executes dynamically created Python code.
   ```python
   exec('print("Hello, World!")')
   ```

21. **format()**: Formats a specified value into a specified format.
   ```python
   formatted_string = format(123.456, '.2f')
   print(formatted_string)  # Output: '123.46'
   ```

22. **bool()**: Converts a value to a Boolean.
   ```python
   print(bool(0))  # Output: False
   print(bool(1))  # Output: True
   ```

23. **callable()**: Checks if the object appears callable.
   ```python
   def my_function():
       print("Hello, World!")

   print(callable(my_function))  # Output: True
   ```

24. **frozenset()**: Returns a new frozenset object, optionally with elements taken from the iterable.
   ```python
   my_set = frozenset([1, 2, 3])
   print(my_set)  # Output: frozenset({1, 2, 3})
   ```

25. **list()**: Returns a list.
   ```python
   my_list = list((1, 2, 3))
   print(my_list)  # Output: [1, 2, 3]
   ```

26. **range()**: Returns an immutable sequence of numbers between the given start and stop integers.
   ```python
   my_range = range(5)
   print(list(my_range))  # Output: [0, 1, 2, 3, 4]
   ```

27. **bytearray()**: Returns a new array of bytes.
   ```python
   my_bytearray = bytearray(b'hello')
   print(my_bytearray)  # Output: bytearray(b'hello')
   ```

28. **float()**: Returns a floating-point number constructed from a number or string.
   ```python
   my_float = float('3.14')
   print(my_float)  # Output: 3.14
   ```

29. **map()**: Applies a given function to all the items of an iterable and returns a new iterator.
   ```python
   numbers = [1, 2, 3, 4, 5]
   squared = map(lambda x: x**2, numbers)
   print(list(squared))  # Output: [1, 4, 9, 16, 25]
   ```

30. **repr()**: Returns a string containing a printable representation of an object.
   ```python
   my_string = repr('Hello, World!')
   print(my_string)  # Output: 'Hello, World!'
   ```

31. **setattr()**: Sets the value of the attribute of an object.
   ```python
   class MyClass:
       pass

   obj = MyClass()
   setattr(obj, 'name', 'John')
   print(obj.name)  # Output: John
   ```

32. **bytes()**: Returns a new bytes object, which is an immutable sequence of integers in the range 0 <= x < 256.
   ```python
   my_bytes = bytes([65, 66, 67])
   print(my_bytes)  # Output: b'ABC'
   ```

33. **format_map()**: Similar to the str.format() method but accepts a mapping object.
   ```python
   my_dict = {'name': 'John', 'age': 30}
   formatted_string = '{name} is {age} years old'.format_map(my_dict)
   print(formatted_string)  # Output: John is 30 years old
   ```

34. **max()**: Returns the largest item in an iterable or the largest of two or more arguments.
   ```python
   numbers = [3, 1, 4, 1, 5, 9, 2, 6]
   print(max(numbers))  # Output: 9
   ```

35. **slice()**: Returns a slice object representing the set of indices specified by range(start, stop, step).
   ```python
   my_list = [1, 2, 3, 4, 5]
   my_slice = slice(1, 4, 2)
   print(my_list[my_slice])  # Output: [2, 4]
   ```

36. **callable()**: Checks if the object appears callable.
   ```python
   def my_function():
       print("Hello, World!")

   print(callable(my_function))  # Output: True
   ```

37. **getattr()**: Returns the value of the named attribute of an object.
   ```python
   class MyClass:
       name = 'John'

   obj = MyClass()
   print(getattr(obj, 'name'))  # Output: John
   ```

38. **memoryview()**: Returns a memory view object.
   ```python
   my_bytes = bytes([65, 66, 67])
   my_memoryview = memoryview(my_bytes)
   print(my_memoryview[0])  # Output: 65
   ```

39. **staticmethod()**: Returns a static method for a function.
   ```python
   class MyClass:
       @staticmethod
       def my_method():
           print("Static method")

   MyClass.my_method()  # Output: Static method
   ```

40. **chr()**: Returns the string representing a character whose Unicode code point is the integer.
   ```python
   print(chr(65))  # Output: A
   ```

41. **hasattr()**: Checks if an object has the specified attribute.
   ```python
   class MyClass:
       name = 'John'

   obj = MyClass()
   print(hasattr(obj, 'name'))  # Output: True
   ```

42. **min()**: Returns the smallest item in an iterable or the smallest of two or more arguments.
   ```python
   numbers = [3, 1, 4, 1, 5, 9, 2, 6]
   print(min(numbers))  # Output: 1
   ```

43. **str()**: Returns a string version of the specified object.
   ```python
   my_string = str(123)
   print(my_string)  # Output: '123'
   ```

44. **classmethod()**: Returns a class method for a function.
   ```python
   class MyClass:
       @classmethod
       def my_method(cls):
           print("Class method")

   MyClass.my_method()  # Output: Class method
   ```

45. **hash()**: Returns the hash value of the object if it has one.
   ```python
   my_set = {1, 2, 3}
   print(hash(my_set))  # Output: TypeError: unhashable type: 'set'
   ```

46. **next()**: Retrieves the next item from the iterator.
   ```python
   iterator = iter([1, 2, 3])
   print(next(iterator))  # Output: 1
   ```

47. **sum()**: Returns the sum of all elements in the iterable.
   ```python
   numbers = [1, 2, 3, 4, 5]
   print(sum(numbers))  # Output: 15
   ```

48. **compile()**: Compiles the source into a code or AST object.
   ```python
   code = compile('print("Hello, World!")', '', 'exec')
   exec(code)  # Output: Hello, World!
   ```

49. **hex()**: Converts an integer to a lowercase hexadecimal string prefixed with "0x".
   ```python
   num = 255
   print(hex(num))  # Output: 0xff
   ```

50. **object()**: Returns a new featureless object.
   ```python
   my_object = object()
   print(my_object)  # Output: <object object at 0x7f3d14484700>
   ```

51. **super()**: Returns a proxy object that delegates method calls to a parent or sibling class of type.
   ```python
   class Parent:
       def show(self):
           print("Parent method")

   class Child(Parent):
       def show(self):
           super().show()

   obj = Child()
   obj.show()  # Output: Parent method
   ```

52. **complex()**: Returns a complex number with the value real + imag*1j or converts a string or number to a complex number.
   ```python
   my_complex = complex(2, 3)
   print(my_complex)  # Output: (2+3j)
   ```

53. **help()**: Invokes the built-in help system.
   ```python
   help(str)
   ```

54. **oct()**: Converts an integer to an octal string prefixed with "0o".
   ```python
   num = 8
   print(oct(num))  # Output: 0o10
   ```

55. **tuple()**: Returns a tuple.
   ```python
   my_tuple = tuple([1, 2, 3])
   print(my_tuple)  # Output: (1, 2, 3)
   ```

56. **delattr()**: Deletes the named attribute from the object.
   ```python
   class MyClass:
       name = 'John'

   obj = MyClass()
   delattr(obj, 'name')
   print(hasattr(obj, 'name'))  # Output: False
   ```

57. **id()**: Returns the identity of an object.
   ```python
   my_list = [1, 2, 3]
   print(id(my_list))  # Output: <some memory address>
   ```

58. **open()**: Opens a file and returns a corresponding file object.
   ```python
   file = open('example.txt', 'r')
   content = file.read()
   print(content)
   file.close()
   ```

59. **type()**: Returns the type of an object.
   ```python
   print(type(5))  # Output: <class 'int'>
   ```

60. **dict()**: Returns a new dictionary.
   ```python
   new_dict = dict(a=1, b=2, c=3)
   print(new_dict)  # Output: {'a': 1, 'b': 2, 'c': 3}
   ```

61. **input()**: Reads a line from input, converts it to a string (stripping a trailing newline), and returns that.
   ```python
   name = input("Enter your name: ")
   print("Hello, " + name)
   ```

62. **ord()**: Given a string representing one Unicode character, returns an integer representing the Unicode code point of that character.
   ```python
   print(ord('A'))  # Output: 65
   ```

63. **vars()**: Returns the __dict__ attribute of the given object.
   ```python
   class MyClass:
       def __init__(self):
           self.a = 1
           self.b = 2

   obj = MyClass()
   print(vars(obj))  # Output: {'a': 1, 'b': 2}
   ```

64. **dir()**: Returns a list of the names in the current local scope or a list of object attributes.
   ```python
   print(dir())  # Output: ['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', 'numbers']
   ```

65. **isinstance()**: Returns True if the specified object is of the specified type, otherwise False.
   ```python
   print(isinstance(5, int))  # Output: True
   ```

66. **pow()**: Returns x to the power of y.
   ```python
   print(pow(2, 3))  # Output: 8
   ```

67. **zip()**: Returns an iterator of tuples, where the i-th tuple contains the i-th element from each of the argument sequences or iterables.
   ```python
   list1 = [1, 2, 3]
   list2 = ['a', 'b', 'c']
   zipped = zip(list1, list2)
   print(list(zipped))  # Output: [(1, 'a'), (2, 'b'), (3, 'c')]
   ```

68. **divmod()**: Returns the quotient and the remainder when dividing two numbers.
   ```python
   print(divmod(10, 3))  # Output: (3, 1)
   ```

</details>

## Primitive Types

> In Python everything is an object-this includes `Booleans`, `integers`, `characters`, etc.

Python has a number of built-in types: numerics (e.g., integer), sequences (e.g., list), mappings (e.g., dict), as well as classes, instances and exceptions. All instances of these types are objects.

<details>
<summary>View contents</summary>

#### Bitwise operators
    
| Operator | Description         | Description |
| -------- | ------------------- | ----------- |
| &        | Bitwise AND         | x & y       |
| \|       | Bitwise OR          | x \| y      |
| ~        | Bitwise NOT         | ~x          |
| ^        | Bitwise XOR         | x ^ y       |
| >>       | Bitwise right shift | x >>        |
| <<       | Bitwise left shift  | x <<        |
    
```py
a = 10 # = 1010 (Binary)
b = 4  # =  0100 (Binary)

a & b # = 1010 & 0100 = 0000 = 0 (Decimal)
a | b # = 1010 & 0100 = 1110 = 14 (Decimal)
~a    # = ~1010 = -(1010 + 1) = -1011 = -11 (Decimal)
a ^ b # = 1010 ^ 0100 = 1110 = 14 (Deciaml)
    
# Shift Operators
    
x = 10 # = 0000 1010 (Binary)
x >> 1 # = 0000 0101 = 5
    
y = 5  # = 0000 0101 (Binary)
y << 1 # = 0000 1010 = 10
y << 2 # = 0001 0100 = 20 
```
    
</details>

## List

<details>
<summary>View details</summary>

1. Iterating a list

<details>
<summary>View codes</summary>

```py
# Using for loop

num_list = [1, 2, 3, 4, 5]

for num in num_list:
  print(num, end=' ') # 1 2 3 4 5
  
for i in range(len(num_list)):
  print(num_list[i], end=' ') # 1 2 3 4 5
  
for i, num in enumerate(num_list):
  print(num, end=' ') # 1 2 3 4 5
  print(i, end=' ') # 0 1 2 3 4
  
for i in range(2, len(num_list)):
  print(num_list[i], end=' ') # 3 4 5
```
  
```py
# Using while loop

num_list = [1, 2, 3, 4, 5]

i = 0

while len(num_list) != i:
    print(num_list[i], end=' ') # 1 2 3 4 5
    i += 1
```

```py
# Using recursion

num_list = [1, 2, 3, 4, 5]

def iterate_list(arr):
    print(arr[0], end=' ') # 1 2 3 4 5
    
    if len(arr) < 2: return
    # list[start_index(including) : end_index(not including) : step]
    iterate_list(arr[1:])

print(num_list[1::2]) # [2, 4]
iterate_list(num_list)
```
  
</details>
    
2. Backward/Reverse iteration of a list
    
<details>
<summary>View codes</summary>
    
```py
num_list = [1, 2, 3, 4, 5]

for num in range(len(num_list) - 1, -1, -1):
  print(num_list[i], end=' ') # 5 4 3 2 1
```
    
</details>

3. Filtering a list

<details>
<summary>View codes</summary>

```py
# Using for loop

num_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]

event_list = []
for num in num_list:
  if num % 2 == 0:
    even_list.append(num)
    
print(even_list) # [2, 4, 6, 8]
```

```py
# Using list comprehension

num_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]

even_list = [num for num in num_list if num % 2 == 0]

print(even_list) # [2, 4, 6, 8]
```

```py
# Using filter and lambda function

num_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]

even_list = list(filter(lambda num: num % 2 == 0, num_list))

print(even_list) # [2, 4, 6, 8]
```

</details>

4. Finding element in list

<details>
<summary>View codes</summary>

```py
# Using index() method

num_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]

try:
    index = num_list.index(3) # returns the index of the given element, or raise a ValueError exception
    print('The index of 3 is:', index)
except:
    print('not found')
```
  
```py
# Using the “in” operator
  
num_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]
  
if 3 in num_list:
  print('element 3 is found.')
else:
  print('not found')
```

</details>

5. Mapping list elements

<details>
<summary>View codes</summary>
  
```py
# Using for loop

num_list = [1, 2, 3, 4]

even_squared = []
for num in num_list:
  if num % 2 == 0:
    even_squared.append(num ** 2)
  else:
    even_squared.append(num)
    
print(even_squared) # [1, 4, 3, 16]
```
  
```py
# Using list comprehension

num_list = [1, 2, 3, 4]

even_squared = [num ** 2 if num % 2 == 0 else num for num in num_list]

print(even_squared) # [1, 4, 3, 16]
```

```py
# Using map and lambda function
  
num_list = [1, 2, 3, 4]

even_squared = list(map(lambda num: num ** 2 if num % 2 == 0 else num, num_list))

print(even_squared) # [1, 4, 3, 16]
```

</details>
  
6. list operations
  
<details>
<summary>View codes</summary>
    
```py
num_list = [1, 2]
  
# access to last element
num_list[-1] # 2
  
# multifly a list
num_list * 3 # [1,2,1,2,1,2]
  
# add 3 at the end
num_list.append(3) # [1, 2, 3]
  
# concate or merge two list
num_list += [4] # [1, 2, 3, 4]
  
# add 5 and 6 at the end
num_list.extend([4, 5]) # [1, 2, 3, 4, 4, 5]
  
# add 100 at 2nd index
num_list.insert(2, 100) # [1, 2, 100, 3, 4, 4, 5]
  
# remove 4 from first occurrence
num_list.remove(4) # [1, 2, 100, 3, 4, 5]
  
# remove 3rd and last element using pop. parameter is index number which is optional.
num_list.pop(2) # [1, 2, 3, 4, 5]
num_list.pop() # [1, 2, 3, 4]
  
# slice a list: [start_index:end_index], end_index is exclusive
num_list[1:] # [2, 3, 4]
num_list[:2] # [1, 2]
num_list[1:3] # [2, 3]
  
# reverse a list
num_list[::-1]     # does not modify the original list
num_list.reverse() # modifies the original list
  
# length, minimum, maximum and count
num_list = [1, 2, 5, 5, 8]
len(num_list) # 4
min(num_list) # 1
max(num_list) # 8
num_list.count(5) # 2
  
# find index of the first occurence. if element is not found, raise a ValueError exception
num_list = [1,2,10,4,5]
num_list.index(10)       # searches in the whole list
num_list.index(10, 0, 2) # searches from 0th to 2nd position
  
# sort a list using sort() and sorted(). sort() modify the list where sorted() doesn't modify the list
# sort in increasing order
sorted(num_list)
num_list.sort()
  
# sort in decreasing order
sorted(num_list, reverse=True) 
num_list.sort(reverse=True)
  
# sorted using function
cars = ['Ford', 'Mitsubishi', 'BMW', 'VW']
cars.sort(key=lambda car: len(car)) # sorted by car length
sorted(cars, key=lambda car: len(car))
# ['VW', 'BMW', 'Ford', 'Mitsubishi']
```
  
</details>

</details>

## Dictionary

<details>
<summary>View details</summary>

1. Iterating dictionary

<details>
<summary>View codes</summary>
  
```py
# Using for loop

dict = { 'name': 'zayan', 'age': 5, 'religion': 'Islam' }

for key in dict:
    print(key, '->', dict[key]) # name -> zayan, age -> 5, religion -> Islam
```

```py
# Using items() method

dict = { 'name': 'zayan', 'age': 5, 'religion': 'Islam' }

for key, value in dict.items():
    print(key, '->', value) # name -> zayan, age -> 5, religion -> Islam
```

```py
# Using keys() method

dict = { 'name': 'zayan', 'age': 5, 'religion': 'Islam' }

for key in dict.keys():
    print(key, '->', dict[key]) # name -> zayan, age -> 5, religion -> Islam
```

```py
# Using values() method

dict = { 'name': 'zayan', 'age': 5, 'religion': 'Islam' }

for value in dict.values():
    print(value) # zayan, 5, Islam
```
  
```py
# Using comprehension
  
dict = { 'name': 'zayan', 'age': 5, 'religion': 'Islam' }

new_dict = {key: value for key, value in dict.items() if key != 'age'}

print(new_dict) # {'name': 'zayan', 'religion': 'Islam'}
```

```py
# membership tests (in)

dict = { 'name': 'zayan', 'age': 5, 'religion': 'Islam' }

print('name' in dict.keys()) # True
print('zayan' in dict.values()) # True
print('village' in dict.keys()) # False
```

```py
# Modifying Values and Keys

dict = { 'name': 'zayan', 'age': 5, 'religion': 'Islam' }

dict['name'] = 'Zayan' # modify value
# del dict['age']

for key in list(dict.keys()):  # Use a list instead of a view to delete a key
    if key == 'age':
        del dict[key]

print(dict) # {'name': 'Zayan', 'religion': 'Islam'}
```

</details>

2. Dictionary operations

<details>
<summary>View codes</summary>

```py
# Using curly braces
my_dict = {'name': 'John', 'age': 30, 'city': 'New York'}

# Using dict() constructor
another_dict = dict(name='Jane', age=25, city='Los Angeles')

# Access
my_dict['name']  # Output: John

# Update value
my_dict['age'] = 31

# Add new key-value pair
my_dict['country'] = 'USA'

print(my_dict)  # Output: {'name': 'John', 'age': 31, 'city': 'New York', 'country': 'USA'}

# Deleting a key-value pair
del my_dict['age']

# Deleting and returning the value of a key
city = my_dict.pop('city')

print(my_dict)  # Output: {'name': 'John'}
print(city)     # Output: New York
```

</details>

</details>

## String

<details>
<summary>View details</summary>
  
1. Iterating a string

<details>
<summary>View codes</summary>

```py
# Using for loop

str = 'hello'

for ch in str:
  print(ch, end=' ') # h e l l o
  
for i in range(len(str)):
  print(str[i], end=' ') # h e l l o
  
for i, ch in enumerate(str):
  print(ch, end=' ') # h e l l o
  print(i, end=' ') # 0 1 2 3 4
```
  
</details>

2. Finding substring in a string

<details>
<summary>View codes</summary>

```py
# Using find() method

txt = "Hello, World."

index = txt.find("ell")

if index != -1:
  print('found substring. index is ', index)
else:
  print('not found')
```

```py
# Using index() method

txt = "Hello, World."

try:
    index = txt.index("ell") # returns the index of the given element, or raise a ValueError exception
    print('found substring. index is ', index)
except:
    print('not found')
```
  
</details>
  
3. Split a string into a list

<details>
<summary>View codes</summary>

```py
# string.split(separator, maxsplit)
# Default separator is any whitespace
# Default value is -1, which is "all occurrences
  
str = "apple#banana#cherry"
list = str.split("#", 1)
print(list) # ['apple', 'banana#cherry']
```
  
```py
# split string to characters
str = "apple"
ch = list(str)
print(ch) # ['a', 'p', 'p', 'l', 'e']
```
  
</details>
    
4. Built-in functions
    
<details>
<summary>View codes</summary>

```py
str = "Apple1 "
    
srt.lower() # "apple1 "
str[2].isalnum() # True
str[::-1] # " 1elppa"

# character to ASCII or ASCII to character
ord('a') # 97
chr(97) # 'a'
chr(ord('a') + 3) # 'd'
```
    
</details>

</details>

## Sets

<details>
<summary>View details</summary>

1. Iterating a set

```py
# Normal iteration

my_set = {1, 2, 3}

for num in my_set:
    print(num) # 1, 2, 3

```

```py
# Using set comprehension

number_set = {1, 2, 3}
squared_numbers = {num ** 2 for num in number_set}

for squared_num in squared_numbers:
    print(squared_num) # 1, 4, 9
```

```py
# Using enumerate

string_set = {"apple", "banana", "orange", "grape"}

for index, fruit in enumerate(string_set):
    print(f"Index {index}: {fruit}")
```

2. Set operations

```py
# Intersection (&): Returns a new set containing only the elements that are common to both sets.

set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

intersection = set1 & set2
print(intersection)  # Output: {3, 4}
```

```py
# Union (|): Returns a new set containing all unique elements from both sets.

set1 = {1, 2, 3}
set2 = {3, 4, 5}

union = set1 | set2
print(union)  # Output: {1, 2, 3, 4, 5}
```

```py
# Difference (-): Returns a new set containing elements that are in the first set but not in the second set.

set1 = {1, 2, 3, 4}
set2 = {3, 4, 5}

difference = set1 - set2
print(difference)  # Output: {1, 2}
```

```py
# Subset (<=) and Superset (>=): Checks if one set is a subset or superset of another.

set1 = {1, 2, 3}
set2 = {1, 2, 3, 4, 5}

is_subset = set1 <= set2
is_superset = set2 >= set1

print(is_subset)  # Output: True
print(is_superset)  # Output: True
```

```py
# Disjoint (isdisjoint()): Checks if two sets have no elements in common.

set1 = {1, 2, 3}
set2 = {4, 5, 6}

disjoint = set1.isdisjoint(set2)
print(disjoint)  # Output: True
```

```py
my_set = {1, 2, 3}

# Adding a single element
my_set.add(4)

# Adding multiple elements
my_set.update([5, 6])

print(my_set)  # Output: {1, 2, 3, 4, 5, 6}

# Removing an element
my_set.remove(3)

# Removing an element if it exists
my_set.discard(6)

print(my_set)  # Output: {1, 2, 4, 5}

# Set to list
my_set = {1, 2, 3, 4, 5}
my_list = list(my_set)
print(my_list)  # Output: [1, 2, 3, 4, 5]

# List to set
my_list = [1, 2, 3, 4, 5]
my_set = set(my_list)
print(my_set)  # Output: {1, 2, 3, 4, 5}
```

</details>
