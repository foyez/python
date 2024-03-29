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
