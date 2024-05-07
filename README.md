# Python

[Python Playground](https://www.programiz.com/python-programming/online-compiler/)

### Hello World

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

### Reserved Words (Keywords)

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

### Primitive Types

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

### List

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

### Dictionary

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

### String
  
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
