# Python

[Python Playground](https://www.programiz.com/python-programming/online-compiler/)

Python is a **high-level, interpreted, dynamically-typed** programming language created by Guido van Rossum in 1991.

**Key Characteristics:**

1. **Interpreted**: Code runs line-by-line (like reading a recipe step-by-step)
2. **Dynamically Typed**: Variables don't need explicit type declaration and variable types determined at runtime (flexible but requires care)
3. **Object-Oriented**: Everything is an object (even integers and functions)
4. **Cross-Platform**: Write once, run anywhere (Windows, macOS, Linux)
5. **Multi-paradigm**: Supports procedural, functional, and OOP styles

## Quick Start

### Hello World

<details>
<summary><strong>View contents</strong></summary>

```python
def greeting(name: str) -> None:
    """
    Prints a personalized greeting message.
    
    Args:
        name: The name to greet.
    """
    print(f"Hello, {name}!")

if __name__ == '__main__':
    # The if __name__ == '__main__' pattern ensures code only runs
    # when the script is executed directly, not when imported
    greeting('Bangladesh')  # Output: Hello, Bangladesh!
```

**Key Concepts**:
- `if __name__ == '__main__':` ensures code runs only when script is executed directly, not when imported
- Type hints (`str`, `-> None`) are optional but recommended for clarity
- Docstrings use triple quotes for documentation
    
</details>

### Execution Model

```python
# Script execution
python script.py

# Interactive mode
python
>>> print("Hello")

# Module execution
python -m http.server 8000
```

---

## Python Keywords

Python has 35 reserved keywords that cannot be used as variable names.

<details>
<summary><strong>View contents</strong></summary>

### 1. Boolean Keywords (`True`, `False`, `is`, `None`)

#### Explanation

* `True` and `False` represent boolean values.
* `None` represents the absence of a value.
* `is` checks object identity (not equality).
* Commonly used in conditions, return values, and default states.

<details>
<summary><strong>View contents</strong></summary>

```python
# User authentication system
def authenticate_user(username: str, password: str) -> bool:
    """
    Authenticates a user login attempt.
    
    Returns:
        True if authentication succeeds, False otherwise.
    """
    stored_password = get_password_from_db(username)  # Simulated
    
    if stored_password is None:
        return False  # User doesn't exist
    
    return password == stored_password

# Usage in a login system
login_successful = authenticate_user('john_doe', 'secret123')
if login_successful:
    print("Access granted")
else:
    print("Access denied")
```

</details>

### 2. Logical Operators (`and`, `or`, `not`)

#### Explanation

* `and` → True if **both** conditions are true
* `or` → True if **at least one** condition is true
* `not` → Inverts a boolean value

<details>
<summary><strong>View contents</strong></summary>

```python
# E-commerce discount eligibility
def can_apply_discount(user_age: int, is_member: bool, cart_total: float) -> bool:
    """
    Determines if a user qualifies for a discount.
    
    Discount rules:
    - Senior citizens (65+) OR premium members
    - AND cart total must be over $50
    """
    is_senior = user_age >= 65
    qualifies_for_discount = (is_senior or is_member) and cart_total > 50
    
    return qualifies_for_discount

eligible_for_discount = can_apply_discount(70, False, 60) # True

if not eligible_for_discount:
    print("Pay full payment")
else:
    print("Pay 5% less")
```

</details>

### 3. Import Keywords (`import`, `from`, `as`)

#### Explanation

* `import` loads a module
* `from` imports specific items
* `as` creates an alias (shorter or clearer name)

<details>
<summary><strong>View contents</strong></summary>

```python
# Data analysis module
from datetime import datetime as dt
from typing import List, Dict
import json

def analyze_sales_data(filepath: str) -> Dict[str, float]:
    """
    Analyzes sales data from a JSON file.
    
    Real-world use: Business intelligence dashboards use this pattern
    to import necessary libraries and process data.
    """
    with open(filepath, 'r') as file:
        sales_data = json.load(file)
    
    total_revenue = sum(item['price'] for item in sales_data)
    average_sale = total_revenue / len(sales_data)
    
    return {
        'total_revenue': total_revenue,
        'average_sale': average_sale,
        'analysis_date': dt.now().strftime('%Y-%m-%d')
    }
```

</details>

### 4. Assertion (`assert`)

#### Explanation

* Used for **debugging**
* Stops the program if a condition is false
* Should not replace proper error handling in production

<details>
<summary><strong>View contents</strong></summary>

```python
assert len(api_key) > 0, "API key cannot be empty"
```

---

```python
# API rate limiting
def make_api_request(api_key: str, requests_made: int, rate_limit: int = 100) -> None:
    """
    Makes an API request with rate limit validation.
    
    Real-world use: Services like Twitter API, Google Maps API use
    assertions for debugging and validation.
    """
    assert len(api_key) > 0, "API key cannot be empty"
    assert requests_made < rate_limit, f"Rate limit exceeded: {requests_made}/{rate_limit}"
    
    print(f"Request successful! {requests_made + 1}/{rate_limit} requests used")

# Usage
try:
    make_api_request('abc123xyz', 50)     # Works fine
    make_api_request('abc123xyz', 100)    # Raises AssertionError
except AssertionError as e:
    print(f"Error: {e}")
```

</details>

### 5. Async Programming (`async`, `await`)

#### Explanation

* Used for **non-blocking**, concurrent tasks
* Common in networking, APIs, and I/O-heavy programs

<details>
<summary><strong>View contents</strong></summary>

```python
async def fetch_product_price(session, url):
    async with session.get(url) as response:
        data = await response.json()
        return data['price']
```

---

```python
# Concurrent web scraping
import asyncio
import aiohttp
from typing import List

async def fetch_product_price(session: aiohttp.ClientSession, url: str) -> float:
    """
    Fetches product price from an e-commerce website.
    
    Real-world use: Price comparison websites like PriceGrabber
    use async operations to fetch prices from multiple stores simultaneously.
    """
    async with session.get(url) as response:
        data = await response.json()
        return data['price']

async def compare_prices(product_urls: List[str]) -> Dict[str, float]:
    """Fetches prices from multiple websites concurrently."""
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_product_price(session, url) for url in product_urls]
        prices = await asyncio.gather(*tasks)
        
        return {url: price for url, price in zip(product_urls, prices)}

# Usage (in async context)
# prices = asyncio.run(compare_prices([
#     'https://store1.com/api/product/123',
#     'https://store2.com/api/product/123',
#     'https://store3.com/api/product/123'
# ]))
```

</details>

### 6. Control Flow (`if`, `elif`, `else`, `for`, `while`, `break`, `continue`)

#### Explanation

* Control the order in which code runs
* Decide **what**, **when**, and **how many times** code executes

<details>
<summary><strong>View contents</strong></summary>

```python
# Payment processing system
def process_payment(amount: float, payment_method: str, balance: float) -> str:
    """
    Processes a payment transaction.
    
    Real-world use: Payment gateways like Stripe, PayPal use
    similar logic for transaction processing.
    """
    if amount <= 0:
        return "Invalid amount"
    elif payment_method == "credit_card":
        return process_credit_card(amount)
    elif payment_method == "debit_card":
        if balance < amount:
            return "Insufficient funds"
        return process_debit_card(amount, balance)
    elif payment_method == "paypal":
        return process_paypal(amount)
    else:
        return "Payment method not supported"

def process_orders(orders: List[Dict]) -> None:
    """
    Processes multiple orders with priority handling.
    
    Real-world use: Fulfillment centers like Amazon warehouses
    use similar logic for order processing.
    """
    for order in orders:
        if order['priority'] == 'urgent':
            print(f"Processing urgent order: {order['id']}")
            continue  # Skip to next iteration
        
        if order['status'] == 'cancelled':
            break  # Stop processing
        
        print(f"Processing standard order: {order['id']}")
```

</details>

### 7. Function Definition (`def`, `return`, `lambda`)

#### Explanation

* `def` defines a function
* `return` sends a value back
* `lambda` creates short, anonymous functions

<details>
<summary><strong>View contents</strong></summary>

```python
tax_rates = {
    'USA': lambda x: x * 0.22 if x <= 89075 else x * 0.24
}
```

---

```python
# Tax calculation system
def calculate_tax(income: float, country: str) -> float:
    """
    Calculates income tax based on country's tax brackets.
    
    Real-world use: Payroll systems like ADP use similar functions.
    """
    tax_rates = {
        'USA': lambda x: x * 0.22 if x <= 89075 else x * 0.24,
        'UK': lambda x: x * 0.20 if x <= 50000 else x * 0.40,
        'Germany': lambda x: x * 0.14 if x <= 57918 else x * 0.42
    }
    
    calculate = tax_rates.get(country, lambda x: x * 0.20)  # Default 20%
    return calculate(income)

# Usage
print(calculate_tax(60000, 'USA'))     # Output: 14400.0
print(calculate_tax(60000, 'UK'))      # Output: 24000.0

# Lambda in data transformation
transactions = [
    {'amount': 100, 'currency': 'USD'},
    {'amount': 200, 'currency': 'EUR'},
    {'amount': 150, 'currency': 'USD'}
]

# Convert EUR to USD (1 EUR = 1.1 USD)
convert_to_usd = lambda t: t['amount'] * 1.1 if t['currency'] == 'EUR' else t['amount']
total_usd = sum(map(convert_to_usd, transactions))  # 495.0
```

</details>

### 8. Exception Handling (`try`, `except`, `finally`, `raise`)

#### Explanation

* Prevents program crashes
* Allows graceful error handling
* `finally` always runs
* `raise` throws an error manually

<details>
<summary><strong>View contents</strong></summary>

```python
try:
    file = open(filepath)
except FileNotFoundError:
    print("File not found")
finally:
    print("Cleanup complete")
```

---

```python
# File upload system
import os
from typing import Optional

class FileUploadError(Exception):
    """Custom exception for file upload failures."""
    pass

def upload_file(filepath: str, max_size_mb: int = 10) -> Optional[str]:
    """
    Uploads a file with size validation and error handling.
    
    Real-world use: Cloud storage services like Dropbox, Google Drive
    use similar patterns for file uploads.
    """
    file_handle = None
    
    try:
        # Check if file exists
        if not os.path.exists(filepath):
            raise FileNotFoundError(f"File not found: {filepath}")
        
        # Check file size
        file_size_mb = os.path.getsize(filepath) / (1024 * 1024)
        if file_size_mb > max_size_mb:
            raise FileUploadError(
                f"File too large: {file_size_mb:.2f}MB (max: {max_size_mb}MB)"
            )
        
        # Simulate upload
        file_handle = open(filepath, 'rb')
        # upload_to_cloud(file_handle)  # Simulated
        
        return f"Upload successful: {filepath}"
        
    except FileNotFoundError as e:
        print(f"Error: {e}")
        return None
    except FileUploadError as e:
        print(f"Upload failed: {e}")
        return None
    except Exception as e:
        print(f"Unexpected error: {e}")
        raise  # Re-raise unexpected errors
    finally:
        # Always close the file handle
        if file_handle:
            file_handle.close()
            print("File handle closed")

# Usage
result = upload_file('large_video.mp4', max_size_mb=5)
```

</details>

### 9. Scope Keywords (`global`, `nonlocal`)

#### Explanation

* `global` modifies variables outside functions
* `nonlocal` modifies variables in enclosing functions

<details>
<summary><strong>View contents</strong></summary>

```python
# Application configuration manager
app_config = {
    'debug_mode': False,
    'api_timeout': 30
}

def enable_debug_mode() -> None:
    """
    Enables debug mode globally.
    
    Real-world use: Web frameworks like Django, Flask use global
    configuration for debugging during development.
    """
    global app_config
    app_config['debug_mode'] = True
    print("Debug mode enabled globally")

def create_logger(log_level: str = 'INFO'):
    """
    Creates a logger with nested configuration.
    
    Real-world use: Logging systems use nonlocal to manage
    nested configuration scopes.
    """
    current_level = log_level
    
    def change_log_level(new_level: str) -> None:
        nonlocal current_level
        current_level = new_level
        print(f"Log level changed to: {current_level}")
    
    def log_message(message: str) -> None:
        print(f"[{current_level}] {message}")
    
    return change_log_level, log_message

# Usage
change_level, log = create_logger('INFO')
log("Application started")              # [INFO] Application started
change_level('DEBUG')                    # Log level changed to: DEBUG
log("Debugging connection issues")      # [DEBUG] Debugging connection issues
```

</details>

### 10. Context Manager (`with`)

#### Explanation

* Automatically handles setup and cleanup
* Commonly used for files, databases, and locks

<details>
<summary><strong>View contents</strong></summary>

```python
with open('data.txt') as file:
    content = file.read()
```

---

```python
# Database transaction manager
from contextlib import contextmanager
from typing import Generator

@contextmanager
def database_transaction(db_connection) -> Generator:
    """
    Manages database transactions with automatic rollback on error.
    
    Real-world use: ORMs like SQLAlchemy use this pattern for
    transaction management.
    """
    try:
        print("Transaction started")
        yield db_connection
        db_connection.commit()
        print("Transaction committed")
    except Exception as e:
        db_connection.rollback()
        print(f"Transaction rolled back due to: {e}")
        raise
    finally:
        print("Transaction cleanup completed")

# Usage
class MockDB:
    def commit(self): pass
    def rollback(self): pass

# with database_transaction(MockDB()) as db:
#     db.execute("INSERT INTO users VALUES (...)")
#     db.execute("UPDATE accounts SET balance = ...")
```

</details>

### 11. Generator (`yield`)

#### Explanation

* Produces values one at a time
* Saves memory for large datasets

<details>
<summary><strong>View contents</strong></summary>

```python
def read_large_log_file(filepath):
    for line in open(filepath):
        yield line
```

---

```python
# Log file processor
from typing import Generator

def read_large_log_file(filepath: str, chunk_size: int = 1000) -> Generator[str, None, None]:
    """
    Reads a large log file in chunks using a generator.
    
    Real-world use: Log analysis tools like Splunk, ELK Stack use
    generators to process massive log files without loading
    everything into memory.
    
    Memory benefit: Instead of loading a 10GB log file into memory,
    this processes 1000 lines at a time.
    """
    with open(filepath, 'r') as file:
        lines_buffer = []
        
        for line in file:
            lines_buffer.append(line.strip())
            
            if len(lines_buffer) >= chunk_size:
                yield '\n'.join(lines_buffer)
                lines_buffer = []
        
        # Yield remaining lines
        if lines_buffer:
            yield '\n'.join(lines_buffer)

def find_errors_in_logs(log_file: str) -> None:
    """Processes logs and finds errors efficiently."""
    error_count = 0
    
    for chunk in read_large_log_file(log_file):
        error_count += chunk.count('ERROR')
    
    print(f"Total errors found: {error_count}")
```

</details>

### 12. `class`

* Defines a class.

```python
class User:
    pass
```

---

### 13. `pass`

* Placeholder where a statement is required.

```python
if condition:
    pass
```

---

### 14. `del`

* Deletes a variable or object.

```python
del user_data
```

---

### 15. `in`

* Checks membership.

```python
if 'admin' in roles:
    print("Access granted")
```

---

### 16. `match` / `case` (Python 3.10+)

```python
match status_code:
    case 200:
        print("Success")
    case 404:
        print("Not Found")
```

---

### 17. `yield from`

* Delegates to another generator.

```python
yield from other_generator()
```

</details>

</details>

---

## Built-in functions

<details>
<summary>View contents</summary>

1. **abs()**: Returns the absolute value of a number.

```python
num = -5
print(abs(num))  # Output: 5
```

2. **min()**: Returns the smallest item in an iterable.

```python
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
print(min(numbers))  # Output: 1
```

3. **max()**: Returns the largest item in an iterable or the largest of two or more arguments.

```python
numbers = [3, 1, 4, 1, 5, 9, 2, 6]
print(max(numbers))  # Output: 9
```

4. **sum()**: Returns the sum of all elements in the iterable.

```python
numbers = [1, 2, 3, 4, 5]
print(sum(numbers))  # Output: 15
```

5. **pow(x, y, z=None)**: Returns x to the power of y (optionally modulo z)

```python
print(pow(2, 3))  # Output: 8
```

6. **divmod()**: Returns the quotient and the remainder when dividing two numbers.

```python
result = divmod(10, 3)
print(result)  # Output: (3, 1)
```

7. **round(number, ndigits=None)**: Rounds a number to a specified number of decimal places (ndigits).

```py
pi = 3.14159
rounded_pi = round(pi, 2)  # rounded_pi will be 3.14
```

8. **all()**: Returns `True` if all elements of an iterable are true.

```python
iterable = [True, True, False]
print(all(iterable))  # Output: False

my_dict = {'a': 5, 'b': 15, 'c': 8}
all(value > 4 for value in my_dict.values())  # True
```

9. **any()**: Returns `True` if any element of an iterable is true.

```python
iterable = [False, False, True]
any(iterable)  # Output: True

my_set = {-1, 2, 3, 4}
any(num < 0 for num in my_set)  # Output: True
```

10. **len(object)**: Gets the length (number of items) of an object that supports it (e.g., lists, strings, tuples, dictionary):

```python
my_dict = {"name": "Abul"}
len(my_dict) # 1
```

11. **reversed(iterable)**: Returns an iterator that yields elements of the iterable in reverse order.

```python
letters = "hello"
reversed_letters = reversed(letters)
for letter in reversed_letters:
    print(letter)  # Output: olleh
```

12. **next()**: Retrieves the next item from the iterator.

```python
iterator = iter([1, 2, 3])
print(next(iterator))  # Output: 1
```

13. **ascii()**: Returns a string containing a printable representation of an object, but escape non-ASCII characters.

```python
print(ascii('π is a greek letter'))  # Output: "'\\u03c0 is a greek letter'"
```

14. **enumerate()**: Returns an enumerate object, which yields pairs containing a count (from start, which defaults to 0) and a value yielded by the iterable.

```python
my_list = ['apple', 'banana', 'cherry']
for index, fruit in enumerate(my_list):
      print(index, fruit)
# Output:
# 0 apple
# 1 banana
# 2 cherry
```

15. **range(start, stop=None, step=1)**: Generates a sequence of numbers from start (inclusive) to stop (exclusive) at a step of step.

```python
my_range = range(5)
print(list(my_range))  # Output: [0, 1, 2, 3, 4]
```

16. **map()**: Applies a given function to all the items of an iterable and returns a new iterator.

```python
numbers = [1, 2, 3, 4, 5]
squared = map(lambda x: x**2, numbers)
print(list(squared))  # Output: [1, 4, 9, 16, 25]
```

17. **filter(function, iterable)**: Constructs an iterator from elements of an iterable for which the function returns True.

```python
numbers = [1, 2, 3, 4, 5]
def is_even(num):
    return num % 2 == 0

even_numbers = filter(is_even, numbers) # [2, 4]
```

18. **slice(start, stop=None, step=None)**: Returns a slice object representing the set of indices specified by range(start, stop, step).

```python
my_list = [1, 2, 3, 4, 5]
my_slice = slice(1, 4, 2)
print(my_list[my_slice])  # Output: [2, 4]
```

19. **sorted(iterable, key=None, reverse=False)**: Returns a new sorted list from the items in iterable. Optionally provides a key function for custom sorting or reverse=True for descending order.

```py
numbers = [3, 1, 4, 2]
sorted_numbers = sorted(numbers)  # [1, 2, 3, 4]

# Sort by length of strings
words = ["apple", "banana", "cherry"]
sorted_by_length = sorted(words, key=len)  # ["cherry", "apple", "banana"]
```

20. **zip()**: Returns an iterator of tuples, where the i-th tuple contains the i-th element from each of the argument sequences or iterables.

```python
list1 = [1, 2, 3]
list2 = ['a', 'b', 'c']
zipped = zip(list1, list2)
print(list(zipped))  # Output: [(1, 'a'), (2, 'b'), (3, 'c')]
```

21. **input()**: Reads a line from input, converts it to a string (stripping a trailing newline), and returns that.

```python
name = input("Enter your name: ")
print("Hello, " + name)
```

22. **type()**: Returns the type of an object.

```python
print(type(5))  # Output: <class 'int'>
```

23. **print(object, sep=" ", end="\n", file=None, flush=False)**: Prints the object to the console (or a specified file).

```python
message = "Hello, world!"
print(message)
```

24. **eval()**: Evaluates a Python expression given as a string and returns the result.

```python
result = eval('2 + 2')
print(result)  # Output: 4
```

25. **open(file, mode="r", buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)**: Opens a file and returns a corresponding file object.

```python
with open("myfile.txt", "r") as file:
   data = file.read()
   print(data)
```

26. **exec()**: Executes dynamically created Python code.

```python
exec('print("Hello, World!")')
```

27. **format(value, format_spec="")**: Formats a specified value into a specified format.

```python
formatted_string = format(123.456, '.2f')
print(formatted_string)  # Output: '123.46'
```

28. **oct()**: Converts an integer to an octal string prefixed with "0o".

```python
num = 8
print(oct(num))  # Output: 0o10
```

29. **bin()**: Converts an integer to a binary string prefixed with "0b".

```python
num = 5
print(bin(num))  # Output: 0b101
```

30. **hex()**: Converts an integer to a lowercase hexadecimal string prefixed with "0x".

```python
num = 255
print(hex(num))  # Output: 0xff
```

31. **bool()**: Converts a value to a Boolean.

```python
print(bool(0))  # Output: False
print(bool(1))  # Output: True
```

32. **int()**: Returns an integer object constructed from a number or string.

```python
num = int('10')
print(num)  # Output: 10
```

33. **float()**: Returns a floating-point number constructed from a number or string.

```python
my_float = float('3.14')
print(my_float)  # Output: 3.14
```

34. **str()**: Returns a string version of the specified object.

```python
my_string = str(123)
print(my_string)  # Output: '123'
```
   
35. **chr()**: Returns the string representing a character whose Unicode code point is the integer.

```python
print(chr(65))  # Output: A
```

36. **ord()**: Given a string representing one Unicode character, returns an integer representing the Unicode code point of that character.

```python
print(ord('A'))  # Output: 65
```

37. **complex(real=0, imag=0)**: Returns a complex number with the value real + imag*1j or converts a string or number to a complex number.

```python
my_complex = complex(2, 3)
print(my_complex)  # Output: (2+3j)
```

38. **bytes()**: Returns a new bytes object, which is an immutable sequence of integers in the range 0 <= x < 256.

```python
my_bytes = bytes([65, 66, 67])
print(my_bytes)  # Output: b'ABC'
```

39. **list()**: Returns a list.

```python
my_list = list((1, 2, 3))
print(my_list)  # Output: [1, 2, 3]
```

40. **dict()**: Creates a new dictionary.

```python
new_dict = dict(a=1, b=2, c=3)
print(new_dict)  # Output: {'a': 1, 'b': 2, 'c': 3}
```

41. **tuple()**: Returns a tuple.

```python
my_tuple = tuple([1, 2, 3])
print(my_tuple)  # Output: (1, 2, 3)
```

42. **set(iterable)**: Creates a set object from an iterable, removing duplicates and maintaining insertion order for Python 3.

```py
set([1, 2, 2, 3])  # {1, 2, 3}
```

43. **bytearray()**: Returns a new array of bytes.

```python
my_bytearray = bytearray(b'hello')
print(my_bytearray)  # Output: bytearray(b'hello')
```

44. **format_map()**: Similar to the str.format() method but accepts a mapping object.

```python
my_dict = {'name': 'John', 'age': 30}
formatted_string = '{name} is {age} years old'.format_map(my_dict)
print(formatted_string)  # Output: John is 30 years old
```

45. **callable()**: Checks if the object appears callable.

```python
def my_function():
      print("Hello, World!")

print(callable(my_function))  # Output: True
```

46. **frozenset()**: Returns a new frozenset object, optionally with elements taken from the iterable.

```python
my_set = frozenset([1, 2, 3])
print(my_set)  # Output: frozenset({1, 2, 3})
```

47. **hash()**: Returns the hash value of the object if it has one.

```python
my_set = {1, 2, 3}
print(hash(my_set))  # Output: TypeError: unhashable type: 'set'
```

48. **compile()**: Compiles the source into a code or AST object.

```python
code = compile('print("Hello, World!")', '', 'exec')
exec(code)  # Output: Hello, World!
```

49. **repr()**: Returns a string containing a printable representation of an object.

```python
my_string = repr('Hello, World!')
print(my_string)  # Output: 'Hello, World!'
```

50. **setattr()**: Sets the value of the attribute of an object.

```python
class MyClass:
      pass

obj = MyClass()
setattr(obj, 'name', 'John')
print(obj.name)  # Output: John
```

51. **staticmethod()**: Returns a static method for a function.

```python
class MyClass:
      @staticmethod
      def my_method():
         print("Static method")

MyClass.my_method()  # Output: Static method
```

52. **getattr()**: Returns the value of the named attribute of an object.

```python
class MyClass:
      name = 'John'

obj = MyClass()
print(getattr(obj, 'name'))  # Output: John
```

53. **hasattr()**: Checks if an object has the specified attribute.

```python
class MyClass:
      name = 'John'

obj = MyClass()
print(hasattr(obj, 'name'))  # Output: True
```

54. **classmethod()**: Returns a class method for a function.

```python
class MyClass:
      @classmethod
      def my_method(cls):
         print("Class method")

MyClass.my_method()  # Output: Class method
```

55. **object()**: Returns a new featureless object.

```python
my_object = object()
print(my_object)  # Output: <object object at 0x7f3d14484700>
```

56. **super()**: Returns a proxy object that delegates method calls to a parent or sibling class of type.

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

57. **vars()**: Returns the __dict__ attribute of the given object.

```python
class MyClass:
      def __init__(self):
         self.a = 1
         self.b = 2

obj = MyClass()
print(vars(obj))  # Output: {'a': 1, 'b': 2}
```

58. **isinstance()**: Returns True if the specified object is of the specified type, otherwise False.

```python
print(isinstance(5, int))  # Output: True
```

59. **issubclass(class, classinfo)**: Checks if a class is a subclass of another class.

```python
class Animal:
    pass

class Dog(Animal):
    pass

class Cat(Animal):
    pass

is_dog_subclass = issubclass(Dog, Animal)     # True
is_cat_subclass = issubclass(Cat, Dog)        # False (Cat is a subclass of Animal, not Dog)
```

60. **id()**: Returns the identity of an object.

```python
my_list = [1, 2, 3]
print(id(my_list))  # Output: <some memory address>
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
# same as x//2
x >> 1 # = 0000 0101 = 5
    
y = 5  # = 0000 0101 (Binary)
# same as x*2
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
new_list = [0] + num_list # [0, 1, 2, 3, 4]
  
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

people = [{'age: 5, 'name': 'Abul'}, {'age': 10, 'name': 'Abul'}]
sorted(people, key=lambda person: person['age']) # sorted by age

# sort by multiple criteria - return tuple
people = [
    {"name": "John", "age": 30},
    {"name": "Jane", "age": 25},
    {"name": "Dave", "age": 30},
    {"name": "Alice", "age": 25},
]
# Sort by age and then by name
sorted_people = sorted(people, key=lambda person: (person["age"], person["name"]))
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
# character to ASCII or ASCII to character
str = "Apple1 "
ord('a') # 97
chr(97) # 'a'
chr(ord('a') + 3) # 'd'

# Concatenation (+)
str1 = "Hello"
str2 = "World"
result = str1 + " " + str2
print(result)  # Output: Hello World

# Multiplication (*)
str1 = "abc"
result = str1 * 3
print(result)  # Output: abcabcabc

# Substring
my_str = "Hello, World!"
my_str[7:] # World!
my_str[-6:] # World!
my_str[0:5] # Hello
my_str[::-1] # !dlroW ,olleH

# Length
my_str = "Hello, World!"
len(my_str) # 13

# count(): Returns the number of occurrences of a substring in the string.
my_string = "apple banana apple orange apple"
count = my_string.count("apple")
print(count)  # Output: 3

# Case Conversion
my_str = "Hello, World!"
my_str.lower()  # hello, world!
my_str.upper()  # HELLO, WORLD!

# Strip: Removes leading and trailing whitespace from a string
my_string = "  Hello, World!  "
my_string.strip()  # Hello, World!

# lstrip(): Removes leading whitespace (or specified characters) from the beginning of the string.
my_string = "   hello"
print(my_string.lstrip())  # Output: 'hello'

# rstrip(): Removes trailing whitespace (or specified characters) from the end of the string.
my_string = "hello   "
print(my_string.rstrip())  # Output: 'hello'

# Split: Splits a string into a list of substrings based on a delimiter.
my_string = "apple,banana,orange"
fruits = my_string.split(",")
print(fruits)  # Output: ['apple', 'banana', 'orange']

# Join: Joins the elements of an iterable into a string using a separator.
fruits = ['apple', 'banana', 'orange']
my_string = ",".join(fruits) # apple,banana,orange

# Replace: Replaces occurrences of a substring within a string.
my_string = "Hello, World!"
new_string = my_string.replace("World", "Universe")
print(new_string)  # Output: Hello, Universe!

# Find: Returns the lowest index of the substring if found in the string. Returns -1 if not found.
my_string = "Hello, World!"
index = my_string.find("World")
print(index)  # Output: 7

# Count: Returns the number of occurrences of a substring in the string.
my_string = "apple banana apple orange apple"
count = my_string.count("apple")
print(count)  # Output: 3

# StartsWith and EndsWith: Checks if the string starts or ends with a specified substring.
my_string = "Hello, World!"
print(my_string.startswith("Hello"))  # Output: True
print(my_string.endswith("!"))       # Output: True

# Title: Returns a string with the first character of each word capitalized.
my_string = "hello world"
title_case = my_string.title()
print(title_case)  # Output: Hello World

# Capitalize: Returns a string with the first character capitalized.
my_string = "hello world"
capitalized = my_string.capitalize()
print(capitalized)  # Output: Hello world

# Encode and Decode: Encodes and decodes the string using a specified encoding.
my_string = "Hello, World!"
encoded = my_string.encode('utf-8')
print(encoded)  # Output: b'Hello, World!'
decoded = encoded.decode('utf-8')
print(decoded)  # Output: Hello, World!

# Format: Formats the string with placeholders.
name = "Alice"
age = 30
formatted_string = "My name is {} and I am {} years old.".format(name, age)
print(formatted_string)  # Output: My name is Alice and I am 30 years old.

# format_map(): Similar to format(), but accepts a mapping (dictionary-like object) as an argument.
person = {'name': 'Bob', 'age': 25}
formatted_string = "My name is {name} and I am {age} years old.".format_map(person)
print(formatted_string)  # Output: My name is Bob and I am 25 years old.

# isdigit(): Checks if all characters in the string are digits.
my_string = "123"
print(my_string.isdigit())  # Output: True

# isalpha(): Checks if all characters in the string are alphabetic.
my_string = "abc"
print(my_string.isalpha())  # Output: True

# islower(): Checks if all characters in the string are lowercase.
my_string = "hello"
print(my_string.islower())  # Output: True

# isupper(): Checks if all characters in the string are uppercase.
my_string = "HELLO"
print(my_string.isupper())  # Output: True

# istitle(): Checks if the string is in titlecase.
my_string = "Hello World"
print(my_string.istitle())  # Output: True

# isnumeric(): Checks if all characters in the string are numeric.
my_string = "123"
print(my_string.isnumeric())  # Output: True

# isalnum(): Checks if all characters in the string are alphanumeric.
my_string = "abc123"
print(my_string.isalnum())  # Output: True

# isascii(): Returns True if all characters in the string are ASCII, False otherwise.
my_string = "Hello, World!"
print(my_string.isascii())  # Output: True

# isdecimal(): Returns True if all characters in the string are decimals, False otherwise.
my_string = "123"
print(my_string.isdecimal())  # Output: True

# zfill(): Pads a numeric string with zeros on the left to fill a field of the specified width.
my_string = "42"
print(my_string.zfill(5))  # Output: '00042'

# index(): Returns the lowest index of the substring in the string, or raises a ValueError if the substring is not found.
my_string = "apple banana orange"
index = my_string.index("banana")
print(index)  # Output: 6

# rindex(): Returns the highest index of the substring in the string, or raises a ValueError if the substring is not found.
my_string = "apple banana apple orange apple"
index = my_string.rindex("apple")
print(index)  # Output: 28

# rfind(): Returns the highest index of the substring in the string, or -1 if the substring is not found.
my_string = "apple banana apple orange apple"
index = my_string.rfind("apple")
print(index)  # Output: 28
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

# Removing an element. Raises a KeyError if the element is not in the set.
my_set.remove(3)

# Removing an element if it exists
my_set.discard(6) # # no error if 4 is missing

# pop() - Removes and returns an arbitrary element (since sets are unordered).
s = {1, 2, 3}
x = s.pop()
print(x)  # could be 1, 2, or 3

# Clear or delete entire set
s = {1, 2, 3}
s.clear()
print(s)  # set()

s = {1, 2, 3}
del s
# Now `s` no longer exists

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
