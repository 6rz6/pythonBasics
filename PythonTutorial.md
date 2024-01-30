Python Tutorial: Input, Output, and Essential Concepts
======================================================

Introduction
------------

This tutorial provides a detailed explanation of fundamental Python concepts. It covers a wide range of topics, from basic input/output operations to advanced concepts like working with modules and handling exceptions. Each section includes code examples with detailed explanations to help beginners understand and apply these concepts in their Python projects.

### Table of Contents

1.  [Input and Output Variables](#input-and-output-variables)
2.  [String Object Methods](#string-object-methods)
3.  [Numeric Calculations and Operations](#numeric-calculations-and-operations)
4.  [Logical Operations](#logical-operations)
5.  [Operators: and, or, not](#operators-and-or-not)
6.  [Conditional Statements: if, elif, else](#conditional-statements-if-elif-else)
7.  [Lists and Tuples](#lists-and-tuples)
8.  [Ranges](#ranges)
9.  [Loops and Iterating Over a List](#loops-and-iterating-over-a-list)
10.  [Math Functions](#math-functions)
11.  [Matrix Functions](#matrix-functions)
12.  [Dictionary Functions](#dictionary-functions)
13.  [Modules and Try-Except](#modules-and-try-except)

### 1\. Input and Output Variables

**Explanation:**
----------------

*   This section covers basic input/output operations and the use of variables.
*   Examples include obtaining user input, formatting output, and performing calculations.

python

Copy code

`# Input and Output Variables if bool(input('Enter to skip I/O')) == True:       pretext = 'the price is'      postext = "in total"     price = input(pretext[:] + ':')  # [:] all range of cells in pretext string     bul = True     ber = False          if bul:           print(f'{pretext}: {int(price) * 10} {postext}')  # formatted output vars in {}          conv = input('continue? (y/n)')          if bool(conv == 'y'):          print('ok')         val2 = input('enter a second value')         print(f'calculating {price} * {val2}... =')          print(int(int(price) * int(val2)))`

### 2\. String Object Methods

**Explanation:**
----------------

*   Demonstrates various string object methods for manipulating strings.
*   Examples include converting to uppercase, lowercase, finding substrings, and replacing text.

python

Copy code

`# String Object Methods if bool(input('Enter to skip Strings')) == True:     course = 'Python For Beginners'     print(course.upper())     print(course.lower())     print('location of thon: ' + str(course.find('thon')))     print(course.replace('Python', 'py'))     print('Python in str: ' + 'Python' in course)  # checks if 'Python' in var course and returns boolean`

### 3\. Numeric Calculations and Operations

**Explanation:**
----------------

*   Covers basic numeric calculations, including addition, division, modulus, and exponentiation.
*   Examples demonstrate arithmetic operations and updating variables.

python

Copy code

`# Numeric Calculations and Operations if bool(input('Enter to skip Numeric')) == True:       num = 3 + 3 - 2     print('3 + 3 - 2 = ' + str(num))     num3 = 10 / 3 * 2     print('10/3*2 = ' + str(num3))     num2 = 10 // 3     print('10 div 3 = ' + str(num2))     num4 = 10 % 3     print('10 mod 3 = ' + str(num4))     num5 = 10 ** 3     print('10^3 = ' + str(num5))     num += num  # num = num + number     print('+=num = ' + str(num))     num *= num  # num = num * number     print('*=num = ' + str(num))     num -= num  # num = num - number     print('-=num = ' + str(num))     num /= num + 1  # num = num / number     print('/=num = ' + str(num))`

### 4\. Logical Operations

**Explanation:**
----------------

*   Demonstrates logical operations such as greater than, less than, and not equal.
*   Examples use boolean variables and conditional statements.

python

Copy code

`# Logical Operations if bool(input('Enter to skip Operations')) == True:      num = 3 > 2  # = True     print('3 > 2 = ' + str(num))     num = 3 != 2  # = True     print('3 != 2 = ' + str(num))     num = 3 == 2  # = False     print('3 == 2 = ' + str(num))`

### 5\. Operators: and, or, not

**Explanation:**
----------------

*   Covers logical operators `and`, `or`, and `not`.
*   Examples demonstrate their usage in complex conditions.

python

Copy code

`# Operators: and, or, not if bool(input('Enter to skip Operators')) == True:        price = 25     print((price > 10) and (price < 30) or (price < 26) and not (price != 25))  # Returns bool`

### 6\. Conditional Statements: if, elif, else

**Explanation:**
----------------

*   Illustrates the use of conditional statements with `if`, `elif`, and `else`.
*   Examples show branching based on different conditions.

python

Copy code

`# Conditional Statements: if, elif, else if bool(input('Enter to skip IF')) == True:      temp = 5     if temp > 30:         print('hot')     elif temp > 20:         print('nice day')     elif temp > 10:         print('cool day')       else:          print('its cold')`  

### 7\. Lists and Tuples

**Explanation:**
----------------

*   Covers basic list operations, including `append()`, `insert()`, `remove()`, and `in`.
*   Introduces read-only tuples as an alternative to lists.

python

Copy code

`# Lists and Tuples if bool(input('Enter to skip lists')) == True:     nums = [1, 2, 3, 4, 5]     nums.append(6)     nums.insert(0, -1)     nums.remove(3)     print(nums)     if 1 in nums:          print('1 is IN total nums:')         print(len(nums))          # Tuples      nums = (5, 11, 2)  # start, end, step     print(str(nums.count(11)))     for num in nums:          print(num)`

### 8\. Ranges

**Explanation:**
----------------

*   Introduces the `range()` function for creating sequences of numbers.
*   Demonstrates the use of `range()` in a for loop.

python

Copy code

`# Ranges if bool(input('Enter to skip Ranges')) == True:     nums = range(5, 11, 2)  # start, end, step     print(range(13))      for num in nums:          print(num)`

### 9\. Loops and Iterating Over a List

**Explanation:**
----------------

*   Covers `while` and `for` loops, iterating over a list.
*   Includes examples of `break` and `else` in loops.

python

Copy code

`# Loops & Iterating over a list if bool(input('Enter to skip loops')) == True:     i = 1     fruits = ["apple", "banana", "cherry", "melon"]     while i < len(fruits):         print(i * "*")         print(fruits[i])         i += 1     print(fruits[-2])     fruits[-2] = "pineapple"     for fruit in fruits:         print(fruit)     print(fruits[1:3])     for item in range(1, 10):         print(item)     my_iterator = iter(fruits)  # define an iterator object from the list iterator     print('1:' + next(my_iterator))  # point to the iterator to the next cell     print('2:' + next(my_iterator))     print('3:' + next(my_iterator))     my_iterator = iter(fruits)  # define an iterator object from the list iterator     while True:         try:             element = next(my_iterator)             print(element)         except StopIteration:  # if StopIteration event is raised stop the loop             break`

### 10\. Math Functions

**Explanation:**
----------------

*   Introduces basic mathematical functions using the `math` module.
*   Examples include rounding and absolute value.

python

Copy code

`# Math functions if bool(input('Enter to skip Math')) == True:     import math     x = 2.9     print(round(x))     print(abs(x))     math.ceil(x)  # using the math library      math.floor(x)`

### 11\. Matrix Functions

**Explanation:**
----------------

*   Demonstrates operations on matrices, a form of nested lists.
*   Example includes modifying matrix elements.

csharp

Copy code

`# Matrix functions if bool(input('Enter to skip Matrix' )) == True:     Matrix = [         [1, 2, 3],         [4, 5, 6],         [7, 8, 9]     ]     Matrix[0][1] = 20     for row in Matrix:         for item in row:             print(item)`

### 12\. Dictionary Functions

**Explanation:**
----------------

*   Illustrates basic operations on dictionaries, including accessing values and setting default values.

python

Copy code

`# Dictionary functions if bool(input('Enter to skip Dictionary')) == True:     customer = {         "name": "John Smith",         "age": 30,         "is_verified": True     }     print(customer["name"])     print(customer.get("age"))     print(customer.get("Birthday", "1/1/1999"))  # value if birthday field`not exists print('\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_') for k in {"x": 1, "y": 2, "z": 3}: # set an iterator to run on a dictionary print(k)

### 13\. Modules and Try-Except

**Explanation:**
----------------

*   Introduces the concept of modules and demonstrates how to use them.
*   Shows how to handle exceptions using the `try-except` block.

python

Copy code

`# Modules & try except if bool(input('Enter to skip Modules')) == True:     import os  # use 'as' to address the module with an alias     print('The project workdir:' + str(os.getcwd()))     print('The project files in dir:' + str(os.listdir()))        print('______Langchain______')     try:         import langchain as LG         print('The module LangChain exposes these methods and properties:' + str(dir(LG)))     except ModuleNotFoundError:          print('Langchain not installed')            print('__________OS_________')     print('The module OS exposes these methods and properties:' + str(dir(os)))        # we can import a single function from the methods above using 'from'     from os import get_terminal_size     print('The module path:' + str(os.get_terminal_size()))     print('_____________________')     import sys     print('The sys module path:' + str(sys.path))`

### References

------------------------------------------



# Python Tutorial for Beginners

## Introduction

Welcome to the Python Tutorial for Beginners! Python is a versatile and beginner-friendly programming language that's widely used for web development, data analysis, artificial intelligence, and more. This tutorial will cover the basics of Python programming, along with some advanced topics.

## Table of Contents

1. Getting Started
   - Input and Output
   - String Manipulation
   - Numeric Calculations
   - Conditional Statements
   - Logical Operators
   - Loops and Iteration
   - Ranges

2. Advanced Topics
   - Working with Lists and Tuples
   - Databases
   - Curl and Web Crawling
   - API Access
   - Using Libraries

## 1. Getting Started

### Input and Output

```python
# Input output vars
if bool(input('Enter to skip I/O')) == True:
    pretext = 'the price is'
    postext = "in total"
    price = input(pretext[:] + ':')
    bul = True
    ber = False
    if bul:
        print(f'{pretext}: {int(price) * 10} {postext}')

    conv = input('continue? (y/n)')
    if bool(conv == 'y'):
        print('ok')
        val2 = input('enter a second value')
        print(f'calculating {price} * {val2}... =')
        print(int(int(price) * int(val2)))
```

**Explanation:**
- The code takes user input, manipulates strings, and performs basic arithmetic calculations.
- `input()` is used to get user input, and `print()` is used for output.
- Conditions (`if`, `elif`, `else`) are used for decision-making.

### String Manipulation

```python
# String object methods
if bool(input('Enter to skip Strings')) == True:
    course = 'Python For Beginners'
    print(course.upper())
    print(course.lower())
    print('location of thon: ' + str(course.find('thon')))
    print(course.replace('Python', 'py'))
    print('Python in str: ' + 'Python' in course)
```

**Explanation:**
- Demonstrates common string manipulation methods such as `upper()`, `lower()`, `find()`, `replace()`, and the use of the `in` keyword.

### Numeric Calculations

```python
# Numeric calc div mod
if bool(input('Enter to skip Numeric'))==True:  
  num = 3 + 3 - 2
  print('3+3-2 = ' + str(num))
  num3 = 10 / 3 * 2
  print('10/3*2 = ' + str(num3))
  num2 = 10 // 3
  print('10 div 3 = ' + str(num2))
  num4 = 10 % 3
  print('10 mod 3 = ' + str(num4))
  num5 = 10 ** 3
  print('10^3 =  ' + str(num5))
  num +=num # num = num+number
  print('+=num =  ' + str(num))
  num *=num # num = num*number
  print('*=num =  ' + str(num))
  num -=num # num = num-number
  print('-=num =  ' + str(num))
  num /=num+1 # num = num/number
  print('/=num =  ' + str(num))
```

**Explanation:**
- Basic numeric calculations using operators like `+`, `-`, `/`, `//`, `%`, `**`.
- Demonstrates the use of compound assignment operators (`+=`, `*=`, `-=`).

### Conditional Statements

```python
# operations > < !=
if bool(input('Enter to skip Operations'))==True: 
  num = 3 > 2 # = True
  print('3 > 2 =  ' + str(num))
  num = 3 != 2 # = True
  print('3 != 2 =  ' + str(num))
  num = 3 == 2 # = False
  print('3 == 2 =  ' + str(num))
```

**Explanation:**
- Examples of conditional statements using `if`, `elif`, and `else`.
- Demonstrates comparisons (`>`, `<`, `!=`, `==`) and their results.

### Logical Operators

```python
# Operators and/or/not
if bool(input('Enter to skip Operators')) == True:
    price = 25
    print((price > 10) and (price < 30) or (price < 26) and not (price != 25))
```

**Explanation:**
- Introduction to logical operators (`and`, `or`, `not`) and their use in compound conditions.

### Loops and Iteration
**Explanation:**
- Introduction to loops (`while` and `for`) and iterating over a list.
```python
# loops & Iterating over a list
if bool(input('Enter to skip loops'))==True:
  i=1
  
  fruits = ["apple", "banana", "cherry","melon"]
  
  while i < len(fruits):
    print(i*"*")
    print(fruits[i])
    i+=1
  
  print(fruits[-2])
  fruits[-2]="pineapple"
  
  for fruit in fruits:
    print(fruit)
  
  print(fruits[1:3]) 
```



### Ranges
**Explanation:**
- Demonstrates the use of `range()` to generate a sequence of numbers.
```python
# Ranges
if bool(input('Enter to skip Ranges')) == True:
    nums = range(5, 11, 2)
    for num in nums:
        print(num)
```



## 2. Advanced Topics

### Working with Lists and Tuples <a name="working-with-lists-and-tuples"></a>

**Explanation:**
- Lists are mutable sequences, meaning you can change their elements.
- Common operations include `append()`, `insert()`, `remove()`, `in`, `len()`.
- Tuples are similar to lists but are immutable, meaning their elements cannot be changed after creation.

```python
# Lists and Tuples
if bool(input('Enter to learn about Lists and Tuples')) == True:
    # Lists
    fruits = ['apple', 'banana', 'cherry']
    print(fruits)
    
    fruits.append('orange')  # Add an element to the end of the list
    print(fruits)

    fruits.insert(1, 'grape')  # Insert an element at a specific index
    print(fruits)

    fruits.remove('banana')  # Remove a specific element
    print(fruits)

    print('banana' in fruits)  # Check if an element is in the list (returns True or False)

    print(len(fruits))  # Get the length of the list

    # Tuples
    coordinates = (3, 5)
    print(coordinates)

    # Accessing elements in a tuple
    x, y = coordinates
    print(f'X: {x}, Y: {y}')
```

### Using Libraries <a name="using-libraries"></a>

**Explanation:**
- Libraries enhance Python's capabilities by providing additional functionality.
- Here are examples of five common libraries:
  1. **`requests`**: For making HTTP requests.
  2. **`BeautifulSoup`**: For web scraping.
  3. **`numpy`**: For numerical operations.
  4. **`pandas`**: For data manipulation and analysis.
  5. **`matplotlib`**: For creating visualizations.

```python
# Using Libraries
if bool(input('Enter to learn about Using Libraries')) == True:
    # Example using the 'requests' library for HTTP requests
    import requests

    response = requests.get('https://www.example.com')
    print(response.text)

    # Example using the 'BeautifulSoup' library for web scraping
    from bs4 import BeautifulSoup

    soup = BeautifulSoup(response.text, 'html.parser')
    title = soup.title.text
    print(f'Title: {title}')
    
    # Example using the 'numpy' library for numerical operations
    import numpy as np
    
    numbers = [1, 2, 3, 4, 5]
    mean = np.mean(numbers)
    print(f'Mean: {mean}')

    # Example using the 'pandas' library for data manipulation
    import pandas as pd
    
    data = {'Name': ['Alice', 'Bob', 'Charlie'], 'Age': [25, 30, 22]}
    df = pd.DataFrame(data)
    print(df)

    # Example using the 'matplotlib' library for creating visualizations
    import matplotlib.pyplot as plt
    
    x = [1, 2, 3, 4, 5]
    y = [10, 5, 20, 15, 25]
    plt.plot(x, y)
    plt.xlabel('X-axis')
    plt.ylabel('Y-axis')
    plt.show()
```
### 3. Additional Topics

#### API Access <a name="api-access"></a>

**Explanation:**
- APIs (Application Programming Interfaces) allow applications to communicate and share data.
- Python provides the `requests` library for interacting with APIs.
- Here are examples of accessing four different APIs: CoinGecko for crypto prices, OpenAI GPT-4 for chat, DuckDuckGo for search, and JokeAPI for jokes.
- Examples of accessing various APIs using the `requests` library.
- CoinGecko for crypto prices, OpenAI GPT-4 for chat, DuckDuckGo for search, and JokeAPI for jokes.
- Note: For the OpenAI GPT-4 API, you need to set 'YOUR_OPENAI_API_KEY'
```python

# Example 1: CoinGecko API for crypto prices
if bool(input('Enter to connect to coingecko')) == True:
    import requests    
    response_coingecko = requests.get('https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum&vs_currencies=usd')
    data_coingecko = response_coingecko.json()
    print('Crypto Prices:')
    print(f'Bitcoin: ${data_coingecko["bitcoin"]["usd"]}')
    print(f'Ethereum: ${data_coingecko["ethereum"]["usd"]}')
```
```python
# Example 2: OpenAI GPT-4 API for chat
if bool(input('Enter to connect to gpt4')) == True:
    import requests   
    response_openai = requests.post(
        'https://api.openai.com/v1/chat/completions',
        headers={'Authorization': 'Bearer YOUR_OPENAI_API_KEY'},
        json={'messages': [{'role': 'system', 'content': 'You are a helpful assistant.'}]}
    )
    data_openai = response_openai.json()
    print('\nOpenAI Chat Response:')
    print(data_openai['choices'][0]['message']['content'])
```
```python
# Example 3: DuckDuckGo API for search
if bool(input('Enter to connect to DuckDuckGo')) == True:
    import requests    
    query = input('\nEnter a search query for DuckDuckGo: ')
    response_duckduckgo = requests.get(f'https://api.duckduckgo.com/?q={query}&format=json')
    data_duckduckgo = response_duckduckgo.json()
    print('\nDuckDuckGo Search Results:')
    for result in data_duckduckgo['Results']:
        print(result['Text'])
```
```python
# Example 4: JokeAPI for jokes
if bool(input('Enter to connect to jokes')) == True:
    import requests
    response_jokeapi = requests.get('https://v2.jokeapi.dev/joke/Any')
    data_jokeapi = response_jokeapi.json()
    print('\nJokeAPI Joke:')
    if data_jokeapi['type'] == 'twopart':
        print(f'Q: {data_jokeapi["setup"]}')
        print(f'A: {data_jokeapi["delivery"]}')
    else:
        print(data_jokeapi['joke'])
```


  
### Databases <a name="databases"></a>

**Explanation:**
- Databases are used to store and retrieve data.
- In this example, we'll use MySQL, but Python supports various databases.
- We'll cover basic operations: connect, create a table, insert data, select data, and delete data.
- The `mysql.connector` module is used to interact with MySQL databases.
- `connect()` establishes a connection to the database, and `cursor()` creates a cursor object for executing SQL queries.
- Basic SQL operations like `CREATE TABLE`, `INSERT INTO`, `SELECT * FROM`, `DELETE FROM` are demonstrated.
- This example shows operations using MySQL; similar principles apply to other databases.

```python
# Databases
if bool(input('Enter to learn about Databases')) == True:
    import mysql.connector
    
    # Connect to a MySQL database (or create one if it doesn't exist)
    connection = mysql.connector.connect(
        host='localhost',
        user='your_username',
        password='your_password',
        database='your_database'
    )

    # Create a cursor object to interact with the database
    cursor = connection.cursor()

    # Create a table
    cursor.execute('''
        CREATE TABLE IF NOT EXISTS users (
            id INT AUTO_INCREMENT PRIMARY KEY,
            username VARCHAR(255),
            email VARCHAR(255)
        )
    ''')

    # Insert data into the table
    cursor.execute('INSERT INTO users (username, email) VALUES (%s, %s)', ('john_doe', 'john@example.com'))

    # Commit changes and close the connection
    connection.commit()
    connection.close()

    # Query the database
    connection = mysql.connector.connect(
        host='localhost',
        user='your_username',
        password='your_password',
        database='your_database'
    )
    cursor = connection.cursor()

    # Select data
    cursor.execute('SELECT * FROM users')
    users = cursor.fetchall()
    for user in users:
        print(user)

    # Delete data
    cursor.execute('DELETE FROM users WHERE username=%s', ('john_doe',))
    connection.commit()

    connection.close()
```

