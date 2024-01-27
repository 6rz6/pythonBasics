
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
if bool(input('Enter to skip Numeric')) == True:
    num = 3 + 3 - 2
    print('3 + 3 - 2 = ' + str(num))
    # ... (more numeric operations)
```

**Explanation:**
- Basic numeric calculations using operators like `+`, `-`, `/`, `//`, `%`, `**`.
- Demonstrates the use of compound assignment operators (`+=`, `*=`, `-=`).

### Conditional Statements

```python
# operations > < !=
if bool(input('Enter to skip Operations')) == True:
    num = 3 > 2
    print('3 > 2 = ' + str(num))
    # ... (more conditional operations)
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

```python
# loops & Iterating over a list
if bool(input('Enter to skip loops')) == True:
    i = 1
    fruits = ["apple", "banana", "cherry", "melon"]
    while i < len(fruits):
        print(i * "*")
        print(fruits[i])
        i += 1
    # ... (more loop examples)
```

**Explanation:**
- Introduction to loops (`while` and `for`) and iterating over a list.

### Ranges

```python
# Ranges
if bool(input('Enter to skip Ranges')) == True:
    nums = range(5, 11, 2)
    for num in nums:
        print(num)
```

**Explanation:**
- Demonstrates the use of `range()` to generate a sequence of numbers.

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

