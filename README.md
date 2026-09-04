# Super30 - Python Functions (Task 1)

This repository contains examples and explanations of basic Python functions: how to define them, call them, and why `return` is useful compared to `print()`.

## 1. print() vs return

- `print()` writes output to the console and returns `None`.
- `return` sends a value back to the caller so it can be used later in expressions, assigned to variables, or passed to other functions.

Example showing why `return` is useful:

```python
def greet_print(name):
    print(f"Hello, {name}!")

def greet_return(name):
    return f"Hello, {name}!"

# Using print(): the function prints but we cannot easily reuse the value
res = greet_print("Alice")
print("res from greet_print:", res)  # prints: res from greet_print: None

# Using return(): the caller receives the value and can reuse it
msg = greet_return("Bob")
print("res from greet_return:", msg)
# We can also transform or combine returned values:
upper_msg = msg.upper()
print(upper_msg)
```

Returning values is essential when you need to chain computations, test results, or retain function outputs.

## 2. Function call process sequence and positional parameters

Function call sequence (simple overview):
1. Python evaluates each argument expression in the call (left-to-right).
2. The interpreter binds arguments to parameters (positional first, then keyword).
3. The function body executes using those parameter values.
4. If a `return` statement is hit, the function execution stops and the value is returned; otherwise the function returns `None`.

Positional parameters: arguments matched by position.

Example:

```python
def concat(a, b, sep=' '):
    return f"{a}{sep}{b}"

# positional call
print(concat('hello', 'world'))  # 'hello world'

# mix positional and keyword
print(concat('hello', 'world', sep='-'))  # 'hello-world'
```

## 3. Task: Implementations

Below are implementations for the requested functions with example usage.

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

## Notes & style
- Functions use `return` when their result is needed for further computation or testing. Use `print()` only for direct console output/demo.
- Input validation (where appropriate) raises exceptions for clarity (e.g., division by zero, negative factorial input).

---

If you want, I can also add a `functions.py` file with the implementations above and a separate `examples.py` to run demonstrations and tests. Let me know if you want me to create those files in the repository.