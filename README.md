# Python Tutorial: From Basics to Advanced

Welcome to this comprehensive Python tutorial where we'll explore various Python functionalities, from basic commands and scripting to interacting with external APIs and libraries. Let's dive into the world of Python, step by step. 

## Table of Contents

- [Scraping URL](#scraping-url)
- [Using Ollama for AI Conversations](#using-ollama-for-ai-conversations)
- [File Management in Python](#file-management-in-python)
- [Play a Snake Game with Pygame](#play-a-snake-game-with-pygame)
- [Real-Time Tickers from Binance](#real-time-tickers-from-binance)
- [City View from Google Maps](#city-view-from-google-maps)
- [Connecting to MySQL Database](#connecting-to-mysql-database)
- [Creating a Web GUI Window Form](#creating-a-web-gui-window-form)
- [Basic Python IO](#basic-python-io)
- [String Methods in Python](#string-methods-in-python)
- [Performing Numerical Calculations](#performing-numerical-calculations)
- [Understanding Python Operations](#understanding-python-operations)
- [Exploring Python Operators](#exploring-python-operators)
- [Control Flow with if-else in Python](#control-flow-with-if-else-in-python)
- [Working with Lists and Tuples](#working-with-lists-and-tuples)
- [Navigating Ranges in Python](#navigating-ranges-in-python)
- [Looping Through Collections](#looping-through-collections)
- [Math Functions in Python](#math-functions-in-python)
- [Working with Matrices](#working-with-matrices)
- [Dictionaries and Their Functions](#dictionaries-and-their-functions)
- [Modules and Exception Handling](#modules-and-exception-handling)
- [Interacting with MongoDB](#interacting-with-mongodb)
- [Database Operations with MongoDB](#database-operations-with-mongodb)
- [Real-Time Data with CoinPaprika API](#real-time-data-with-coinpaprika-api)
- [Crypto Data with CoinGecko API](#crypto-data-with-coingecko-api)
- [Playing PacMan with Pygame](#playing-pacman-with-pygame)
- [Analyzing Crypto Data with CoinGecko and Pandas](#analyzing-crypto-data-with-coingecko-and-pandas)
- [Creating an AI Chat Interface with Gradio](#creating-an-ai-chat-interface-with-gradio)

## Scraping URL

```python
# Import necessary libraries
import requests
from bs4 import BeautifulSoup

# Enter the URL you want to scrape
url = 'https://www.example.com'
response = requests.get(url)

# Parse the HTML content of the page
soup = BeautifulSoup(response.text, 'html.parser')

# Extract the title of the page
title = soup.title.text

# Print the URL and its title
print(url)
print(title)
```

## Using Ollama for AI Conversations

```python
#Ollama https://github.com/ollama/ollama-python

import asyncio, ollama, tkinter as tk
    from ollama import AsyncClient
    from tkinter import messagebox, simpledialog

    root = tk.Tk()
    root.withdraw()

    models = ollama.list()

    # create a string with all model names
    model_string = "\n".join(f"{i+1}. {model['name']}" for i, model in enumerate(models['models']))

    #messagebox.showinfo("Available Models", model_string)

    model_number = simpledialog.askinteger("Model Selection", "Choose a model by entering its number: \n"+ model_string) - 1

    # store chosen model name in 'model' variable
    model = models['models'][model_number]['name']

    print(f"Selected {model}")

    async def chat(input_data):
        message = {'role': 'user', 'content': input_data}        
        async for part in await AsyncClient().chat(model='mistral', messages=[message], stream=True):
            print(part['message']['content'], end='', flush=True)
    input_data = '1'
    while bool(input_data):
        input_data = input(">>> ")
        asyncio.run(chat(input_data))
        

    #Ollama Client
    from ollama import Client
    client = Client(host='http://localhost:11434')
    response = client.chat(model='mistral', messages=[
    {
        'role': 'user',
        'content': 'Why is the sky blue?',
    },
    ])
    
    import ollama
    response = ollama.chat(model='mistral', messages=[
    {
        'role': 'user',
        'content': 'how big is the USA?',
    },
    ])
    print('how big is the USA?')
    input_data = print(response['message']['content'])

 
    
    #Ollama Stream
    input_data = input("Enter your input: ")
    stream = ollama.chat(
        model='mistral',
        messages=[{'role': 'user', 'content': input_data}],
        stream=True,
    )

    for chunk in stream:
        print(chunk['message']['content'], end='', flush=True)
```

## File Management in Python

```python
#File managment
if bool(input('Enter File managment'))==False:
    import os
    import filecmp

    # Open and read a file
    def read_file(file_path):

        with open(file_path, 'r') as file:
            content = file.read()
        return content

    # Write (save) to a file
    def write_file(file_path, content):
        with open(file_path, 'w') as file:
            file.write(content)

    # Append (update) a file
    def append_to_file(file_path, additional_content):
        with open(file_path, 'a') as file:
            file.write(additional_content)

    # Edit a file (replace a specific string)
    def edit_file(file_path, old_string, new_string):
        with open(file_path, 'r') as file:
            content = file.read()
        content = content.replace(old_string, new_string)
        with open(file_path, 'w') as file:
            file.write(content)

    # Delete a file
    def delete_file(file_path):
        if os.path.exists(file_path):
            os.remove(file_path)
        else:
            print(f"The file {file_path} does not exist.")

    # Compare two files
    def compare_files(file_path1, file_path2):
        return filecmp.cmp(file_path1, file_path2, shallow=False)

    # Search for a string in a file
    def search_in_file(file_path, search_string):
        with open(file_path, 'r') as file:
            for line_number, line in enumerate(file, start=1):
                if search_string in line:
                    return line_number, line
        return None

    # Best Practice 1: Use context managers (with statement) to handle files
    # Example: Reading from a file using a context manager
    def read_file_with_context_manager(file_path):
        try:
            with open(file_path, 'r') as file:
                content = file.read()
            return content
        except FileNotFoundError:
            print(f"File not found: {file_path}")
            return None

    # Best Practice 2: Check if a file exists before trying to use it
    # Example: Deleting a file only if it exists
    def safe_delete_file(file_path):
        if os.path.exists(file_path):
            os.remove(file_path)
            print(f"File {file_path} has been deleted.")
        else:
            print(f"The file {file_path} does not exist, so it cannot be deleted.")

    # Best Practice 3: Use exception handling to deal with potential runtime errors
    # Example: Handling errors while writing to a file
    def write_file_with_exception_handling(file_path, content):
        try:
            with open(file_path, 'w') as file:
                file.write(content)
        except IOError as e:
            print(f"An error occurred while writing to the file: {e}")

    # Best Practice 4: Avoid using absolute file paths
    # Example: Using a relative path to specify a file location
    relative_file_path = "py/example.txt"  # Relative to the current working directory

    # Best Practice 5: Use os.path.join to construct file paths
    # Example: Constructing a file path that is OS-independent
    base_directory = "py"
    file_name = "example.txt"
    file_path = os.path.join(base_directory, file_name)

    # Example usage of the functions with best practices:

    # Using context manager to read a file
    content = read_file_with_context_manager(file_path)
    if content:
        print("Content of the file:")
        print(content)

        # Safely deleting a file
        if input('delete?' + file_path +'(y/n)')=='y':
           safe_delete_file(file_path)

    # Writing to a file with exception handling
    write_file_with_exception_handling(file_path, "Hello, World!")

    # Note: The 'data' directory should exist in the current working directory for these examples to work.
    # Example usage of the functions:

    # Define file paths
    file1 = 'example1.txt'
    file2 = 'example2.txt'

    # Write to files
    write_file(file1, "Hello, World!\nThis is the first example file.")
    write_file(file2, "Hello, World!\nThis is the second example file.")

    # Read files
    print("Content of file1:")
    print(read_file(file1))

    # Append to file1
    append_to_file(file1, "\nThis is additional content for file1.")

    # Edit file1 (replace 'first' with 'updated first')
    edit_file(file1, 'first', 'updated first')

    # Compare files
    are_files_equal = compare_files(file1, file2)
    print(f"Are the two files equal? {are_files_equal}")

    # Search for a string in file1
    line_number, line_content = search_in_file(file1, 'additional')
    print(f"String found in file1 at line {line_number}: {line_content.strip()}")

    # Delete file2
    #delete_file(file2)
```

## Play a Snake Game with Pygame

```python
if bool(input('Enter Play Snake'))==False:
    import pygame
    import random
    import sys

    # Initialize pygame 
    pygame.init()

    # Set screen size
    screen_width = 600
    screen_height = 600
    screen = pygame.display.set_mode((screen_width, screen_height))

    # Set title 
    pygame.display.set_caption('Snake Game')

    # Colors
    green = (0,255,0)
    red = (255,0,0)
    black = (0,0,0)
    white = (255,255,255)

    # FPS controller
    fps_controller = pygame.time.Clock()

    # Game variables
    snake_pos = [100, 50]
    snake_body = [[100, 50], [90, 50], [80, 50]]
    food_pos = [random.randrange(1, screen_width/10)*10, random.randrange(1, screen_height/10)*10]
    food_spawn = True
    direction = 'RIGHT'
    change_to = direction
    score = 0

    # Game Over
    def game_over():
        pygame.quit()
        sys.exit()

    # Display Score
    def show_score(choice, color, font, size):
        score_font = pygame.font.SysFont(font, size)
        score_surface = score_font.render('Score : ' + str(score), True, color)
        score_rect = score_surface.get_rect()
        if choice == 1:
            score_rect.midtop = (screen_width/10, 15)
        else:
            score_rect.midtop = (screen_width/2, screen_height/1.25)
        screen.blit(score_surface, score_rect)
        pygame.display.flip()

    # Main logic
    while True:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                game_over()
            # Keyboard handling
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_UP or event.key == ord('w'):
                    change_to = 'UP'
                if event.key == pygame.K_DOWN or event.key == ord('s'):
                    change_to = 'DOWN'
                if event.key == pygame.K_LEFT or event.key == ord('a'):
                    change_to = 'LEFT'
                if event.key == pygame.K_RIGHT or event.key == ord('d'):
                    change_to = 'RIGHT'

        # Validate direction
        if change_to == 'UP' and direction != 'DOWN':
            direction = 'UP'
        if change_to == 'DOWN' and direction != 'UP':
            direction = 'DOWN'
        if change_to == 'LEFT' and direction != 'RIGHT':
            direction = 'LEFT'
        if change_to == 'RIGHT' and direction != 'LEFT':
            direction = 'RIGHT'

        # Update snake position 
        if direction == 'UP':
            snake_pos[1] -= 10
        if direction == 'DOWN':
            snake_pos[1] += 10
        if direction == 'LEFT':
            snake_pos[0] -= 10
        if direction == 'RIGHT':
            snake_pos[0] += 10

        # Snake body mechanism
        snake_body.insert(0, list(snake_pos))
        if snake_pos[0] == food_pos[0] and snake_pos[1] == food_pos[1]:
            score += 1
            food_spawn = False
        else:
            snake_body.pop()

        # Spawn food
        if not food_spawn:
            food_pos = [random.randrange(1, screen_width/10)*10, random.randrange(1, screen_height/10)*10]
        food_spawn = True

        # Draw background
        screen.fill(black)

        # Draw snake
        for pos in snake_body:
            pygame.draw.rect(screen, green, pygame.Rect(pos[0], pos[1], 10, 10))

        # Draw food
        pygame.draw.rect(screen, white, pygame.Rect(food_pos[0], food_pos[1], 10, 10))

        # Game Over conditions
        if snake_pos[0] < 0 or snake_pos[0] > screen_width-10:
            game_over()
        if snake_pos[1] < 0 or snake_pos[1] > screen_height-10:
            game_over()

    # Touching tail
        for block in snake_body[1:]:
            if snake_pos[0] == block[0] and snake_pos[1] == block[1]:
                game_over()
                
        show_score(1, white, 'consolas', 20)

        # Refresh screen
        pygame.display.update()

        # Refresh rate
        fps_controller.tick(25)
```
## Real-Time Tickers from Binance

```python
import tkinter as tk
    import requests 
    from bs4 import BeautifulSoup
    import csv
    from datetime import datetime

    root = tk.Tk()

    urls = {
    'BTC': 'https://www.binance.com/en/trade/BTC_USDT?type=cross',
    'BTC FT': 'https://www.binance.com/en/futures/BTCUSDT',
    'SOL': 'https://www.binance.com/en/trade/SOL_USDT?type=cross',
    'SOL FT': 'https://www.binance.com/en/futures/SOLUSDT'  
    }

    labels = {}
    for name, url in urls.items():
        label = tk.Label(root, text=name + ":")
        label.grid(row=len(labels), column=0)
        var = tk.StringVar()
        title_label = tk.Label(root, textvariable=var)
        title_label.grid(row=len(labels), column=1)
        labels[name] = var

    def update():
        for name, url in urls.items():
            r = requests.get(url)
            soup = BeautifulSoup(r.text, 'html.parser')
            title = soup.title.text
            labels[name].set(title)
        
        with open('data.csv', 'a') as f:
            writer = csv.writer(f)
            for name in labels:
                writer.writerow([name, datetime.now(), labels[name].get()])

        root.after(1000, update)

    update()
    root.mainloop()
```

## City View from Google Maps

```python
import tkinter as tk
    from tkinter import ttk
    from geopy.geocoders import Nominatim
    from geopy.distance import geodesic
    import folium

    root = tk.Tk()

    geolocator = Nominatim(user_agent="myapp")

    city_var = tk.StringVar()
    city_entry = ttk.Entry(root, textvariable=city_var)
    city_entry.grid(row=0, column=0)

    def show_map():
        city = city_var.get()

        location = geolocator.geocode(city)
        
        if location is None:
            print("Invalid city name")
            return
        
        lat, lon = location.point
        
        # Create map using folium
        m = folium.Map(location=[lat, lon], zoom_start=13)

        # Get city bounds
        north, south, east, west = bounds = location.raw['boundingbox']

        # Add bounds to map
        folium.Rectangle(
            bounds=[north, south, east, west],
            color='blue', 
            fill=True,
            fill_color='blue',
            fill_opacity=0.1
        ).add_to(m)

        # Save map as image
        m.save("map.html")

        # Open image and display in Tkinter
        img = tk.ImageTk.PhotoImage(file="map.html")
        label = ttk.Label(root, image=img)
        label.image = img
        label.grid(row=1, column=0)

    ttk.Button(root, text="Search", command=show_map).grid(row=0, column=1)

    root.mainloop()
```

## Connecting to MySQL Database

```python
import mysql.connector

    mydb = mysql.connector.connect(
    host="172.17.32.1",
    user="root",
    password="",
    database="btcpy"
    )

    # Print databases (just the current one for MySQL)
    print("\nDatabases:" + mydb.database)

    # Get cursor
    mycursor = mydb.cursor()
    
    mycursor.execute("SHOW DATABASES") 

    for db in mycursor:
        print(db)
        
    # Loop through "tables" (MySQL tables)
    for table_name in mycursor.execute("SHOW TABLES"):
    
        print("\nTable:", table_name)
        
        # Get column names
        mycursor.execute(f"SELECT COLUMN_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = '{table_name}'")
        columns = [column[0] for column in mycursor.fetchall()]
        print("Columns:", columns)

        # Print table data
        mycursor.execute(f"SELECT * FROM {table_name}")
        print("Data:")
        for row in mycursor:
            print(row)

        print("\n" + "="*40 + "\n")
```

## Creating a Web GUI Window Form

```python
import tkinter as tk #import tkinter module
    from tkhtmlview import HTMLLabel  # for rendering HTML 
    from tkinter import messagebox 
    from datetime import datetime
    import webbrowser,requests

    root = tk.Tk()
    root.title("Web Browser")

    input1 = tk.Entry(root)
    input1.insert(0, "https://example.com")
    input1.pack()

    browser = tk.Frame(root)
    browser.pack()

    # Use HTMLLabel to display content
    html_view = HTMLLabel(browser) 
    html_view.pack()
    html_view.use_ttk = True
    
    def show_page():
        url = input1.get()
        response = requests.get(url)
        html = response.text
        
        # Set HTML content 
        html_view.set_html(html) 

    btn = tk.Button(root, text="Load Page", command=show_page)
    btn.pack()

    root.mainloop()

#GUI window form   
if bool(input('Enter to skip GUI'))==True:
    root = tk.Tk() #create root window set title and size
    root.title("Concat Input") 
    root.geometry("400x400")

    input1 = tk.Entry(root) #create input box 1
    input1.pack()  

    input2 = tk.Entry(root) #create input box 2
    input2.pack()

    def concat_inputs():
        #get text from input boxes
        concat_text = input1.get() + input2.get()  
        
        #update label with concatenated text
        result_label.config(text=concat_text)

        #get current date and time
        now = datetime.now()  
        
        #format date as DD/MM/YYYY
        date_text = now.strftime("%d/%m/%Y")
        
        #update date label
        date_label.config(text=date_text)

    #button to trigger concat function on click  
    button = tk.Button(root, text="Click Me", command=concat_inputs)
    button.pack()

    #label to display concatenated text
    result_label = tk.Label(root, text="")
    result_label.pack()

    #label to display date
    date_label = tk.Label(root, text="")
    date_label.pack()

    root.mainloop() #start GUI event loop
```

## Basic Python IO

```python
pretext = 'the price is' 
  postext = "in total"
  price = input(pretext[:]+':') # [:] all range of cells in pretext string
  bul = True;
  ber = False;
  if bul : #if then
    print(f'{pretext}:{int(price)*10} {postext}') #formatted output vars in {}
  conv = input('continue? (y/n)')
  if bool(conv=='y') : 
    print('ok')
    val2 = input('enter a second value')
    print(f'calculating {price}*{val2}...=') 
    print(int(int(price)*int(val2)))
```

## String Methods in Python

```python
course = 'Python For Beginners'
    print(course.upper())
    print(course.lower())
    print('location of thon:' + str(course.find('thon')))
    print(course.replace('Python','py'))
    print('Python in str:'+'Python' in course) # checks if 'Python' in var course and returns boolean

```

## Performing Numerical Calculations

```python
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

## Understanding Python Operations

```python
# Basic comparison and logical operations
num = 3 > 2 # = True
  print('3 > 2 =  ' + str(num))
  num = 3 != 2 # = True
  print('3 != 2 =  ' + str(num))
  num = 3 == 2 # = False
  print('3 == 2 =  ' + str(num))
```

## Exploring Python Operators

```python
# Demonstrating the use of logical operators
price = 25
  print((price > 10) and (price < 30) or (price < 26) and not (price !=25)) # Returns bool

```

## Control Flow with if-else in Python

```python
temp = 5
  if temp > 30:
    print('hot')
  elif temp > 20:
    print('nice day')
  elif temp > 10:
    print('cool day')  
  else: print('its cold')  
```

## Working with Lists and Tuples

```python
# Demonstrating list operations
nums = [1,2,3,4,5]
  nums.append(6)
  nums.insert(0,-1)
  nums.remove(3)
  print(nums)
  if (1 in nums): 
    print('1 is IN total nums:')
    print(len(nums))

#Tuples 
  nums = (5,11,2) # start,end,step
  print(str(nums.count(11)))
  for num in nums: print(num)

```

## Navigating Ranges in Python

```python
# Using range for iterations
nums = range(5, 11, 2)  # start, end, step
print(list(range(13)))  # Generating a range up to 12

for num in nums:
    print(num)

```

  
## Looping Through Collections

```python
# Demonstrating while and for loops
nums = range(5,11,2) # start,end,step
  print(range(13)) 

  for num in nums: print(num)

#Loops & Iterating over a list
if bool(input('Enter to skip loops'))==True:
  i=1
  
  fruits = ["apple", "banana", "cherry","melon"]  
  
  while i < len(fruits):
    print(i*"*")
    print(fruits[i])
    i+=1
    #break and else: can be added to act as finally (incase of NO break) 
  print(fruits[-2])
  fruits[-2]="pineapple"

  for fruit in fruits:
    print(fruit)

  print(fruits[1:3]) 

  for item in range(1,10):
    print(item)

  my_iterator = iter(fruits) #define an iterator object from the list iterator
  print('1:'+next(my_iterator)) #point to the iterator to the next cell
  print('2:'+next(my_iterator))
  print('3:'+next(my_iterator))

  my_iterator = iter(fruits) #define an iterator object from the list iterator
  while True:
    try:
      element = next(my_iterator)
      print(element)
    except StopIteration: #if stopiteration event is raised stop the loop
      break
```

## Math Functions in Python

```python
import math #(search python3 math module in google)
  x=2.9
  print(round(x))
  print(abs(x))
  math.ceil(x) #using the math library 
  math.floor(x)



#Dictionary functions
if bool(input('Enter to skip Dictionary'))==True:
  customer = {
    "name": "John Smith",
    "age": 30,
    "is_verified": True
  }
  print(customer["name"])
  print(customer.get("age"))
  print(customer.get("Birthday","1/1/1999")) #value if birthday field not exists 
  print('_____________________')
  for k in {"x":1,"y":2,"z":3}: #set an iterator to run on a dictionary
    print(k)
```

## Working with Matrices

```python
# Demonstration of managing a Matrix in Python
#Matrix functions
if bool(input('Enter to skip Matrix'))==True:
  Matrix = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
  ]
  Matrix[0][1]=20
  for row in Matrix:
      for item in row:
        print(item)  
```

## Dictionaries and Their Functions

```python
# Utilizing dictionary and its functions
customer = {
    "name": "John Smith",
    "age": 30,
    "is_verified": True
  }
  print(customer["name"])
  print(customer.get("age"))
  print(customer.get("Birthday","1/1/1999")) #value if birthday field not exists 
  print('_____________________')
  for k in {"x":1,"y":2,"z":3}: #set an iterator to run on a dictionary
    print(k)
```

## Modules and Exception Handling

```python
import os #use as to address the module in an alias
  print('The project workdir:' + str(os.getcwd()))
  print('The project files in dir:' + str(os.listdir()))
  
  print('______Langchain______')
  try:
    import langchain as LG
    print('The module LangChain exposes these methods and properties:' + str(dir(LG)))
  except ModuleNotFoundError: print('Langchain not installed')
    
  print('__________OS_________')
  print('The module OS exposes these methods and properties:' + str(dir(os)))
  
  #we can import a single function from the methods above using 'from'
  from os import get_terminal_size
  print('The module path:' + str(os.get_terminal_size()))
  print('_____________________')
  import sys
  print('The sys module path:' + str(sys.path))
```

## Interacting with MongoDB

```python
import pymongo
    # Set your MongoDB credentials
    username = ""
    password = ""

    # Connect to MongoDB with without credentials
    client = pymongo.MongoClient(f"mongodb://localhost:27017/")
    # if username / password not null use --->> (f"mongodb://{username}:{password}@localhost:27017/")
       
    # Print all the databases and table names in the client variable
    print(f'\nDatabases:'+ str(client.list_database_names()))

    # For each database, print all the tables and their columns
    for db_name in client.list_database_names():
        db = client[db_name]
        print(f"\nDatabase: {db_name}")
        # For each collection (table) in the database, print its name and columns
        for collection_name in db.list_collection_names():
            collection = db[collection_name]
            print(f"Table: {collection_name}")

            # Print column names
            if bool(input('Enter to show Columns'))==False:   
                sample_document = collection.find_one()
                if sample_document:
                    print("Columns:", list(sample_document.keys()))

            # Print data in the table
            if bool(input('Enter to skip print data'))==True:     
                print("Data:")
                for document in collection.find():
                    print(document)

                print("\n" + "="*40 + "\n")
    
#DataBase operations (Mongo) 
if bool(input('Enter to skip DataBase operations (Mongo)'))==True:
    import pymongo
    # Create Database,Table,Columns (No explicit command in MongoDB)
    # Databases are implicitly created when data is inserted.
    # Collections are created when data is inserted.
    # Add Columns and Primary Key (No explicit command in MongoDB)
    # Indexes can be added later.

    # Insert Rows
    database_name = 'TESTDB'
    collection_name = 'TestTable'

    # Access the collection
    client = pymongo.MongoClient(f"mongodb://localhost:27017/")
    test_table = client[database_name][collection_name]

    def printdb():
      print(f"Table Name: {collection_name}")
    # Print columns
      sample_document = test_table.find_one()
      if sample_document:
        columns = list(sample_document.keys())
        print("Columns:", columns)

    # Print data
      print("\nData:")
      for document in test_table.find():
        print(document)

    #Insert Rows
    print('Insert Rows:')    
    test_table.insert_many([
        {'sequence': 1, 'userid': 101, 'username': 'Mark', 'createdate': '2023-03-21', 'description': 'Blue', 'status': 'Active'},
        {'sequence': 2, 'userid': 102, 'username': 'Dave', 'createdate': '2022-05-30', 'description': 'Green', 'status': 'Inactive'},
        {'sequence': 3, 'userid': 103, 'username': 'Gin', 'createdate': '2024-01-11', 'description': 'Red', 'status': 'Inactive'},
        {'sequence': 4, 'userid': 104, 'username': 'Calvin', 'createdate': '2023-01-31', 'description': 'Light Gray', 'status': 'Active'},
        {'sequence': 5, 'userid': 105, 'username': 'Randy', 'createdate': '2024-01-21', 'description': 'Yellow Rainbow', 'status': 'Active'},
        
    ])
    
    printdb()

    # Update Rows
    print('Update Rows:')
    test_table.update_many({}, {'$set': {'username': {'$toLower': '$username'}}})
    
    printdb()

    # Transaction - Start Transaction
    print('Start Transaction:')
    with client.start_session() as session:
        try:
            with session.start_transaction():
                # Perform multiple operations within the transaction
                test_table.update_many({}, {'$set': {'username': {'$toUpper': '$username'}}})
                printdb()
                raise Exception("Simulating an error, triggering rollback")
            # If no exception occurred, commit the transaction
            session.commit_transaction()
        except Exception as e:
            # Handle the exception and log the error
            print(f"Error: {e}")
            printdb()
            # The transaction will be automatically rolled back

    # Delete Row
    #test_table.delete_one({'sequence': 5}) 
```

## Database Operations with MongoDB

```python
import pymongo

client = pymongo.MongoClient("mongodb://localhost:27017/")
db = client['testdb']
collection = db['testcollection']

# Inserting multiple documents
collection.insert_many([
    {"name": "Alice", "age": 25},
    {"name": "Bob", "age": 30}
])

# Updating documents
collection.update_one({"name": "Alice"}, {"$set": {"age": 26}})

# Deleting a document
collection.delete_one({"name": "Bob"})

# Finding documents
for doc in collection.find():
    print(doc)
```

## Real-Time Data with CoinPaprika API

```python
import requests
    import tkinter as tk
    from tkinter import ttk
    root = tk.Tk()
    
    # update the URL to https://api.coinpaprika.com/v1/coins/btc-bitcoin' for coin
    # API docs https://api.coinpaprika.com/#tag/Coins/paths/~1coins/get

    url = 'https://api.coinpaprika.com/v1/coins'
    response = requests.get(url)
    coins = response.json()
    print(str(coins))
    top_10 = sorted(coins, key=lambda x: x['market_cap_usd'], reverse=True)[:10]

    table = ttk.Treeview(root)

    table['columns'] = ('name', 'symbol', 'price', 'marketcap')
    table.column('#0', width=0, stretch=tk.NO)  
    table.heading('name', text='Name')
    table.heading('symbol', text='Symbol')
    table.heading('price', text='Price')
    table.heading('marketcap', text='Market Cap')

    for coin in top_10:
        table.insert('', 'end', 
            values=(coin['name'], coin['symbol'], coin['quotes']['USD']['price'], coin['market_cap_usd']))

    table.pack()

    root.mainloop()
```

## Crypto Data with CoinGecko API

```python
import tkinter as tk
    import requests
    import json
    from tkinter import ttk

    root = tk.Tk()

    table = ttk.Treeview(root)

    table['columns'] = ('name', 'price', 'marketcap', 'volume')
    table.column('#0', width=0, stretch=tk.NO)
    table.heading('name', text='Name')
    table.heading('price', text='Price')
    table.heading('marketcap', text='Market Cap')
    table.heading('volume', text='Volume')

    table.pack()

    def update_data():
        url = 'https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=10'
        
        response = requests.get(url)
        print(str(response.text))
        coins = json.loads(response.text)
        
        for i in table.get_children():
            table.delete(i) 
            
        for coin in coins:
            table.insert('', 'end', values=(coin['name'], coin['current_price'], 
                                        coin['market_cap'], coin['total_volume']))

    tk.Button(root, text='Refresh', command=update_data).pack()

    update_data()
    root.mainloop()
```

## Playing PacMan with Pygame

```python
import pygame
    import random

    # Screen size 
    SCREEN_WIDTH = 600
    SCREEN_HEIGHT = 600

    # Pacman settings
    pacman_x = 300
    pacman_y = 500
    pacman_speed = 2
    pacman_rect = pygame.Rect(pacman_x, pacman_y, 20, 20)

    # Enemy settings
    enemy_x = 420
    enemy_y = 320
    enemy_speed = 1
    enemy_rect = pygame.Rect(enemy_x, enemy_y, 20, 20)

    # Maze borders
    BORDERS = [
        pygame.Rect(0, 0, SCREEN_WIDTH, 10),
        pygame.Rect(0, 0, 10, SCREEN_HEIGHT),
        pygame.Rect(SCREEN_WIDTH-10, 0, 10, SCREEN_HEIGHT),
        pygame.Rect(0, SCREEN_HEIGHT-10, SCREEN_WIDTH, 10)
    ] 

    # Inner walls
    INNER_WALLS = [
        pygame.Rect(100, 100, 10, 400),  
        pygame.Rect(200, 300, 500, 10),
        pygame.Rect(300, 200, 10, 100)
    ]

# Initialize Pygame  
pygame.init()
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption('Pacman')

# Game loop
running = True
while running:
# Event handling
  for event in pygame.event.get():
    if event.type == pygame.QUIT:
      running = False
      
  # User input
  keys = pygame.key.get_pressed()
  if keys[pygame.K_LEFT] and pacman_rect.x > pacman_speed:
    pacman_x -= pacman_speed
  if keys[pygame.K_RIGHT] and pacman_rect.x < SCREEN_WIDTH - pacman_speed - pacman_rect.width:  
    pacman_x += pacman_speed
  if keys[pygame.K_UP] and pacman_rect.y > pacman_speed:
    pacman_y -= pacman_speed
  if keys[pygame.K_DOWN] and pacman_rect.y < SCREEN_HEIGHT - pacman_speed - pacman_rect.height:
    pacman_y += pacman_speed
    
  # Update rects
  pacman_rect.x = pacman_x
  pacman_rect.y = pacman_y
  
  enemy_x += enemy_speed
  if enemy_rect.collidelist(BORDERS + INNER_WALLS) >= 0: 
    enemy_speed *= -1
  enemy_rect.x = enemy_x
  
  # Draw maze
  screen.fill((0,0,0))
  
  for border in BORDERS:
    pygame.draw.rect(screen, (255,0,0), border)
  for wall in INNER_WALLS:
    pygame.draw.rect(screen, (255,0,0), wall)
    
  # Draw characters
  pygame.draw.rect(screen, (255,200,0), pacman_rect) 
  pygame.draw.rect(screen, (255,0,0), enemy_rect)
   
  # Update display
  pygame.display.update()

pygame.quit()
```

## Analyzing Crypto Data with CoinGecko and Pandas

```python
if bool(input('Enter to Enter CoinGecko pandas'))==0:
    import requests
    import csv
    import pandas as pd

    # Get the data from a free API
    response = requests.get("https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=10&page=1&sparkline=false")
    data = response.json()

    # Create a csv file
    with open('cryptocoins.csv', 'w', newline='') as file:
        writer = csv.writer(file)
        writer.writerow(["name", "market_cap", "volume", "price_change_percentage_24h", "circulating_supply"])
        for coin in data:
            writer.writerow([coin['name'], coin['market_cap'], coin['total_volume'], coin['price_change_percentage_24h_in_currency'], coin['circulating_supply']])

    # Use pandas to display and analyze the data
    df = pd.read_csv('cryptocoins.csv')

    # Analyzing the data
    market_cap_mean = df['market_cap'].mean()
    high_volume_coins = df[df['volume'] > df['volume'].mean()]
    positive_price_change_coins = df[df['price_change_percentage_24h'] > 0]

    # Detailed report on the recommended coins
    recommended_coins = df[(df['market_cap'] > market_cap_mean) & (df['price_change_percentage_24h'] > 0)]
    recommended_coins.to_csv('recommended_coins.csv')
    
    # Read the recommended_coins.csv file and print it
    recommended_coins_df = pd.read_csv('recommended_coins.csv')
    print(recommended_coins_df)
```

## Creating an AI Chat Interface with Gradio

```python
import gradio as gr
    from transformers import pipeline

    # Load the Mistral LLM pipeline
    mistral_llm = pipeline("text-generation", model="mistralai/Mixtral-8x7B-Instruct-v0.1")

    # Define the chat interface function
    def chat_interface(input_text):
        response = mistral_llm(input_text, max_length=50)[0]['generated_text']
        return response

    # Create the Gradio interface
    iface = gr.Interface(
        fn=chat_interface,
        inputs="textbox",
        outputs="textbox",
        layout="vertical",
        title="Mistral LLM Chat",
        description="Enter your message and get a response from the Mistral LLM model."
    )

    # Run the interface
    iface.launch()
```
