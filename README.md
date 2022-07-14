# Python

[Python Playground](https://www.programiz.com/python-programming/online-compiler/)

## Python Tips/Tricks

### List

1. Filtering a list

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

2. Finding element in list

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

3. Mapping list elements

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

1. Finding substring in a string

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
