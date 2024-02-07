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
import asyncio, ollama, tkinter as tk
from ollama import AsyncClient
from tkinter import messagebox, simpledialog

# List available models
models = ollama.list()
model_string = "\n".join(f"{i+1}. {model['name']}" for i, model in enumerate(models['models']))

# Select a model
root = tk.Tk()
root.withdraw()
model_number = simpledialog.askinteger("Model Selection", "Choose a model by entering its number: \n"+ model_string) - 1
model = models['models'][model_number]['name']

print(f"Selected {model}")

# Function to handle chat responses
async def chat(input_data):
    message = {'role': 'user', 'content': input_data}        
    async for part in await AsyncClient().chat(model='mistral', messages=[message], stream=True):
        print(part['message']['content'], end='', flush=True)

# Interactive chat loop
input_data = '1'
while bool(input_data):
    input_data = input(">>> ")
    asyncio.run(chat(input_data))
```

## File Management in Python

```python
import os
import filecmp

# Function to read file content
def read_file(file_path):
    with open(file_path, 'r') as file:
        content = file.read()
    return content

# Write content to a new file
def write_file(file_path, content):
    with open(file_path, 'w') as file:
        file.write(content)

# Example usage: Reading a file
content = read_file("example.txt")
print("Content of the file:")
print(content)

# Further examples and functions follow similar patterns:
# append_to_file, edit_file, delete_file, compare_files, etc.
```

## Play a Snake Game with Pygame

```python
import pygame
import sys
import random

# Initial setup
pygame.init()
screen_width = 600
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))

# Game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    # Game logic and drawing code goes here

pygame.quit()
```
## Real-Time Tickers from Binance

```python
import tkinter as tk
import requests
from bs4 import BeautifulSoup
import csv
from datetime import datetime

# Setting up the GUI for displaying tickers
root = tk.Tk()

# URLs for various cryptocurrencies
urls = {
    'BTC': 'https://www.binance.com/en/trade/BTC_USDT?type=cross',
    'BTC FT': 'https://www.binance.com/en/futures/BTCUSDT',
    'SOL': 'https://www.binance.com/en/trade/SOL_USDT?type=cross',
    'SOL FT': 'https://www.binance.com/en/futures/SOLUSDT'
}

# Setup labels for cryptocurrencies
labels = {}
for name, url in urls.items():
    label = tk.Label(root, text=name + ":")
    label.grid(row=len(labels), column=0)
    var = tk.StringVar()
    title_label = tk.Label(root, textvariable=var)
    title_label.grid(row=len(labels), column=1)
    labels[name] = var

# Function to update the tickers
def update():
    for name, url in urls.items():
        r = requests.get(url)
        soup = BeautifulSoup(r.text, 'html.parser')
        title = soup.title.text
        labels[name].set(title)

    # Append data to CSV
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
import folium

root = tk.Tk()

geolocator = Nominatim(user_agent="myapp")

# GUI elements for entering city name and button to trigger map display
city_var = tk.StringVar()
city_entry = ttk.Entry(root, textvariable=city_var)
city_entry.grid(row=0, column=0)

def show_map():
    city = city_var.get()
    location = geolocator.geocode(city)
    
    if location:
        lat, lon = location.latitude, location.longitude
        m = folium.Map(location=[lat, lon], zoom_start=13)
        m.save("map.html")
        print(f"Map for {city} saved as map.html")
    else:
        print("Invalid city name")

ttk.Button(root, text="Search", command=show_map).grid(row=0, column=1)

root.mainloop()
```

## Connecting to MySQL Database

```python
import mysql.connector

# Database connection
mydb = mysql.connector.connect(
    host="localhost",
    user="yourusername",
    password="yourpassword",
    database="yourdatabase"
)

mycursor = mydb.cursor()

# Print all databases
mycursor.execute("SHOW DATABASES")
for db in mycursor:
    print(db)

# Execute other SQL queries as required
# For example, retrieving data from a specific table
mycursor.execute("SELECT * FROM your_table_name")
for row in mycursor:
    print(row)
```

## Creating a Web GUI Window Form

```python
import tkinter as tk
from tkhtmlview import HTMLLabel

root = tk.Tk()
root.title("Web Browser")

input1 = tk.Entry(root)
input1.insert(0, "https://example.com")
input1.pack()

def show_page():
    url = input1.get()
    response = requests.get(url)
    html_view = HTMLLabel(root, html=response.text)
    html_view.pack()

btn = tk.Button(root, text="Load Page", command=show_page)
btn.pack()

root.mainloop()
```

## Basic Python IO

```python
# Prompting user input and basic manipulation
pretext = 'the price is'
postext = "in total"
price = input(pretext + ': ')  # User inputs the price

# Basic boolean flag manipulation
bul = True
if bul:
    # Displaying formatted output
    print(f'{pretext}: {int(price)*10} {postext}')

# Continue based on user's choice
conv = input('continue? (y/n) ')
if conv == 'y':
    print('ok')
    val2 = input('enter a second value: ')
    # Demonstrating basic calculation with inputs
    print(f'calculating {price}*{val2}...= {int(price)*int(val2)}')
```

## String Methods in Python

```python
course = 'Python For Beginners'
# Using various string methods
print(course.upper())  # Converts to uppercase
print(course.lower())  # Converts to lowercase
print('location of "thon": ' + str(course.find('thon')))  # Finds substring
print(course.replace('Python', 'py'))  # Replaces substring
print('Python' in course)  # Checks if substring exists
```

## Performing Numerical Calculations

```python
# Basic arithmetic operations
num = 3 + 3 - 2
print('3+3-2 = ' + str(num))

# Division, multiplication, and modulus operations
num3 = 10 / 3 * 2
print('10/3*2 = ' + str(num3))

num2 = 10 // 3
print('10 div 3 = ' + str(num2))

num4 = 10 % 3
print('10 mod 3 = ' + str(num4))

# Power and augmented assignment operations
num5 = 10 ** 3
print('10^3 = ' + str(num5))

num += num
print('+=num = ' + str(num))
```

## Understanding Python Operations

```python
# Basic comparison and logical operations
num = 3 > 2
print('3 > 2 = ' + str(num))

num = 3 != 2
print('3 != 2 = ' + str(num))

num = 3 == 2
print('3 == 2 = ' + str(num))
```

## Exploring Python Operators

```python
# Demonstrating the use of logical operators
price = 25
print((price > 10) and (price < 30))
print((price < 26) and not (price !=25))
```

## Control Flow with if-else in Python

```python
temp = 5

# Exploring if-elif-else ladder
if temp > 30:
    print('hot')
elif temp > 20:
    print('nice day')
elif temp > 10:
    print('cool day')  
else:
    print('it's cold')
```

## Working with Lists and Tuples

```python
# Demonstrating list operations
nums = [1, 2, 3, 4, 5]
nums.append(6)  # Adding an element
nums.insert(0, -1)  # Inserting at specific position
nums.remove(3)  # Removing an element
print(nums)

# Exploring tuples
nums_tuple = (5, 11, 2)
print(nums_tuple.count(11))  # Counting an element

for num in nums_tuple:
    print(num)
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
i = 1
fruits = ["apple", "banana", "cherry", "melon"]

while i < len(fruits):
    print(i * "*")
    print(fruits[i])
    i += 1

# Iterating over lists
for fruit in fruits:
    print(fruit)
```

## Math Functions in Python

```python
import math

# Using math module for mathematical operations
x = 2.9
print(round(x))  # Rounds the number
print(abs(-2.9))  # Absolute value

print(math.ceil(x))  # Ceiling function
print(math.floor(x))  # Floor function
```

## Working with Matrices

```python
# Demonstration of managing a Matrix in Python
Matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Changing a specific element
Matrix[0][1] = 20
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

print(customer.get("name"))  # Retrieves a value
print(customer.get("Birthday", "1/1/1999"))  # Returns a default if key doesn't exist

# Looping through dictionary keys
for key in customer:
    print(key)
```

## Modules and Exception Handling

```python
import os
import sys

try:
    # Attempting to use a module that may not be installed
    import langchain as LG
except ModuleNotFoundError:
    print('Langchain not installed')

# Printing directories and files in the current directory
print('The project workdir: ' + str(os.getcwd()))
print('The project files in dir: ' + str(os.listdir()))

# Using sys module and os module for system related operations
try:
    print('The sys module path: ' + str(sys.path))
except Exception as e:
    print(f"An error occurred: {e}")
```

## Interacting with MongoDB

```python
import pymongo

# Creating MongoDB connection
client = pymongo.MongoClient("mongodb://localhost:27017/")

# Listing databases
print("Databases:" + str(client.list_database_names()))

db = client['sample_db']
collection = db['sample_collection']

# Inserting a document
collection.insert_one({"name": "John Doe", "age": 30})

# Querying documents
for doc in collection.find():
    print(doc)
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
import json

# Fetching data from CoinPaprika API
response = requests.get('https://api.coinpaprika.com/v1/tickers')
data = json.loads(response.text)

# Printing data of first 5 cryptocurrencies
for coin in data[:5]:
    print(coin['name'], coin['quotes']['USD']['price'])
```

## Crypto Data with CoinGecko API

```python
import requests

# Fetching data from CoinGecko API
url = 'https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd'
response = requests.get(url)
coins = response.json()

# Displaying names and current prices of the first 5 coins
for coin in coins[:5]:
    print(f"Name: {coin['name']}, Price: ${coin['current_price']}")
```

## Playing PacMan with Pygame

```python
import pygame
pygame.init()

screen = pygame.display.set_mode((640, 480))
pygame.display.set_caption('PacMan')

# Main game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
    # Game logic and rendering goes here
    pygame.display.flip()

pygame.quit()
```

## Analyzing Crypto Data with CoinGecko and Pandas

```python
import requests
import pandas as pd

# Fetching data
url = 'https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=10'
response = requests.get(url)
data = response.json()

# Creating DataFrame
df = pd.DataFrame(data)

# Basic data analysis
print(df[['name', 'current_price', 'market_cap']].head())

# Save to CSV
df.to_csv('crypto_data.csv', index=False)
```

## Creating an AI Chat Interface with Gradio

```python
import gradio as gr
from transformers import pipeline

# Load the pipeline
chatbot = pipeline('text-generation', model='gpt2')

def chat_with_ai(user_input):
    response = chatbot(user_input, max_length=100)[0]['generated_text']
    return response

# Create Gradio interface
gr.Interface(fn=chat_with_ai, inputs="text", outputs="text", title="AI ChatBot").launch()
```
