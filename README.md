# Super30 - Python Functions (Task 1)

## 1. Introduction to Python Functions

### What is a Python Function?

A Python function is a reusable block of code that performs a specific task. Functions allow you to:
- **Break down complex problems** into smaller, manageable pieces
- **Avoid code repetition** by writing once and calling multiple times
- **Organize code logically** for better readability and maintenance
- **Test code more easily** by isolating functionality

### Basic Syntax Structure

```python
def function_name(parameters):
    """Optional docstring explaining what the function does."""
    # Function body - the code that executes
    return value  # Optional - returns a value to the caller
```

**Example:**
```python
def greet(name):
    """Greet a person by name."""
    return f"Hello, {name}!"

# Calling the function
message = greet("Alice")
print(message)  # Output: Hello, Alice!
```

### Key Concepts to Know

1. **Function Definition**: Created using the `def` keyword
2. **Parameters**: Named placeholders in the function definition
3. **Arguments**: Actual values passed when calling the function
4. **Return Statement**: Sends a value back to the caller
5. **Scope**: Variables defined inside a function are local to that function
6. **Default Parameters**: Provide default values if no argument is passed

### Parameters vs Arguments

| Concept | Definition | Example |
|---------|-----------|---------|
| **Parameters** | Variables listed in function definition | `def add(a, b):` — `a` and `b` are parameters |
| **Arguments** | Actual values passed when calling the function | `add(5, 3)` — `5` and `3` are arguments |
| **Positional Arguments** | Arguments matched by position | `add(5, 3)` matches `a=5, b=3` |
| **Keyword Arguments** | Arguments passed with explicit parameter names | `add(a=5, b=3)` or `add(b=3, a=5)` |
| **Default Parameters** | Parameters with predefined values | `def discount(price, percent=10):` |

**Example showing positional and keyword arguments:**
```python
def concat(a, b, sep=' '):
    return f"{a}{sep}{b}"

# Positional call
print(concat('hello', 'world'))  # 'hello world'

# Keyword call
print(concat(a='hello', b='world', sep='-'))  # 'hello-world'

# Mixed call
print(concat('hello', 'world', sep='_'))  # 'hello_world'
```

### Returning Data

- `print()` writes output to the console and returns `None`
- `return` sends a value back to the caller so it can be used, assigned to variables, or passed to other functions
- Functions can return a single value, multiple values (as a tuple), or nothing (`None`)

**Comparison: print() vs return**

```python
def greet_print(name):
    print(f"Hello, {name}!")

def greet_return(name):
    return f"Hello, {name}!"

# Using print(): the function prints but we cannot reuse the value
res = greet_print("Alice")
print("res from greet_print:", res)  # prints: res from greet_print: None

# Using return(): the caller receives the value and can reuse it
msg = greet_return("Bob")
print("Message:", msg)  # prints: Message: Hello, Bob!
upper_msg = msg.upper()  # We can transform the returned value
print(upper_msg)  # BOB!
```

### Quick Summary

| Aspect | Details |
|--------|---------|
| **Why Functions?** | Reusability, organization, testability |
| **Definition** | Use `def keyword(parameters):` |
| **Calling** | `function_name(arguments)` |
| **Parameters** | Placeholders in definition; can have defaults |
| **Arguments** | Actual values passed; can be positional or keyword |
| **Return** | Sends value back; enables reuse and chaining |
| **Scope** | Variables inside function are local by default |

---

## 2. Questions & Implementations Map

| # | Question | Notebook File | Function Signature | Key Concept |
|---|----------|----------------|-------------------|------------|
| 1 | Create a function that returns the addition of two numbers. | `01_arithmetic_add.ipynb` | `def add(a, b)` | Basic arithmetic operation |
| 2 | Create functions for subtraction, multiplication, and division. | `02_arithmetic_operations.ipynb` | `def subtract(a, b)`, `def multiply(a, b)`, `def divide(a, b)` | Multiple arithmetic operations with error handling |
| 3 | Create a function that determines whether a number is even or odd. | `03_even_odd_check.ipynb` | `def is_even(n)` | Conditional logic, modulo operator |
| 4 | Create a function that returns the largest of three numbers without using max(). | `04_largest_of_three.ipynb` | `def largest_of_three(a, b, c)` | Conditional comparisons |
| 5 | Create a function that calculates factorial. | `05_factorial.ipynb` | `def factorial(n)` | Iterative loops, input validation |
| 6 | Create a function that checks whether a number is prime. | `06_prime_check.ipynb` | `def is_prime(n)` | Optimized loop logic |
| 7 | Create `def calculate_discount(price, discount=10)` where the default discount is 10%. | `07_discount_calculator.ipynb` | `def calculate_discount(price, discount=10)` | Default parameters, keyword arguments |
| 8 | Create a function that accepts a list and returns its sum without using sum(). | `08_list_sum.ipynb` | `def sum_list(numbers)` | List iteration, accumulation |
| 9 | Create a function that accepts a string and returns the number of vowels. | `09_vowel_counter.ipynb` | `def count_vowels(s)` | String iteration, set membership |
| 10 | Create a function that accepts a string and determines whether it is a palindrome. | `10_palindrome_check.ipynb` | `def is_palindrome(s)` | String manipulation, comparison |
| 11 | Create a function that accepts name, age, course and returns a formatted student profile. Use both positional and keyword arguments while calling it. | `11_student_profile.ipynb` | `def student_profile(name, age, course)` | String formatting, positional & keyword arguments |

---

## 3. Task: Implementations

Below are implementations for all requested functions with example usage.

```python
# 1) add(a, b)
def add(a, b):
    """Return the sum of a and b."""
    return a + b

# 2) basic arithmetic functions

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        raise ValueError("Division by zero is not allowed")
    return a / b

# 3) check even or odd

def is_even(n):
    return n % 2 == 0

# 4) largest of three numbers (without using max())

def largest_of_three(a, b, c):
    largest = a
    if b > largest:
        largest = b
    if c > largest:
        largest = c
    return largest

# 5) factorial (iterative)

def factorial(n):
    if n < 0:
        raise ValueError("Factorial is not defined for negative numbers")
    result = 1
    for i in range(2, n + 1):
        result *= i
    return result

# 6) check prime

def is_prime(n):
    if n <= 1:
        return False
    if n <= 3:
        return True
    if n % 2 == 0:
        return False
    i = 3
    while i * i <= n:
        if n % i == 0:
            return False
        i += 2
    return True

# 7) calculate_discount(price, discount=10)

def calculate_discount(price, discount=10):
    """Return final price after applying discount percentage (discount default 10)."""
    if price < 0:
        raise ValueError("Price cannot be negative")
    if discount < 0 or discount > 100:
        raise ValueError("Discount must be between 0 and 100")
    return price * (1 - discount / 100)

# 8) sum_list without using sum()

def sum_list(numbers):
    total = 0
    for n in numbers:
        total += n
    return total

# 9) count vowels in a string

def count_vowels(s):
    vowels = set('aeiouAEIOU')
    count = 0
    for ch in s:
        if ch in vowels:
            count += 1
    return count

# 10) check palindrome

def is_palindrome(s):
    cleaned = ''.join(ch.lower() for ch in s if ch.isalnum())
    return cleaned == cleaned[::-1]

# 11) student profile

def student_profile(name, age, course):
    return f"Name: {name}\nAge: {age}\nCourse: {course}"

# Usage examples (positional and keyword arguments):
if __name__ == '__main__':
    print('add(2,3)=', add(2,3))
    print('subtract(5,2)=', subtract(5,2))
    print('multiply(3,4)=', multiply(3,4))
    print('divide(10,2)=', divide(10,2))

    print('is_even(4)=', is_even(4))
    print('largest_of_three(5,9,2)=', largest_of_three(5,9,2))
    print('factorial(5)=', factorial(5))
    print('is_prime(13)=', is_prime(13))

    print('calculate_discount(100)=', calculate_discount(100))
    print('calculate_discount(100, discount=25)=', calculate_discount(100, discount=25))

    print('sum_list([1,2,3,4])=', sum_list([1,2,3,4]))
    print("count_vowels('Hello World')=", count_vowels('Hello World'))
    print("is_palindrome('A man, a plan, a canal: Panama')=", is_palindrome('A man, a plan, a canal: Panama'))

    # student_profile called with positional args
    print('\nStudent profile (positional):')
    print(student_profile('Alice', 22, 'Physics'))

    # student_profile called with keyword args
    print('\nStudent profile (keyword):')
    print(student_profile(name='Bob', course='Mathematics', age=24))
```

## Notes & Best Practices

- Functions use `return` when their result is needed for further computation or testing. Use `print()` only for direct console output/demo.
- Input validation (where appropriate) raises exceptions for clarity (e.g., division by zero, negative factorial input).
- Always use descriptive function names and include docstrings.
- Keep functions focused on a single task for better reusability and testing.

---

If you want, I can also create individual `functions.py` files for each notebook or a combined `functions.py` file with all implementations. Let me know!
