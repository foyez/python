# Python

## Python Tips/Tricks

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

even_list = [num for num_list if num % 2 == 0]

print(even_list) # [2, 4, 6, 8]
```

```py
# Using filter and lambda function

num_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]

even_list = list(filter(lambda num: num % 2 == 0, num_list))

print(even_list) # [2, 4, 6, 8]
```

</details>
