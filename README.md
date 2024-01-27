# pythonBasics
#Input output vars
if bool(input('Enter to skip I/O'))==True:  #any input = True
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

#String object methods
if bool(input('Enter to skip Strings'))==True:
    course = 'Python For Beginners'
    print(course.upper())
    print(course.lower())
    print('location of thon:' + str(course.find('thon')))
    print(course.replace('Python','py'))
    print('Python in str:'+'Python' in course) # checks if 'Python' in var course and returns boolean

#Numeric calc div mod
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

#operations > < !=
if bool(input('Enter to skip Operations'))==True: 
  num = 3 > 2 # = True
  print('3 > 2 =  ' + str(num))
  num = 3 != 2 # = True
  print('3 != 2 =  ' + str(num))
  num = 3 == 2 # = False
  print('3 == 2 =  ' + str(num))

#Operators and/or/not
if bool(input('Enter to skip Operators'))==True:   
  price = 25
  print((price > 10) and (price < 30) or (price < 26) and not (price !=25)) # Returns bool

#if else
if bool(input('Enter to skip IF'))==True: 
  temp = 5
  if temp > 30:
    print('hot')
  elif temp > 20:
    print('nice day')
  elif temp > 10:
    print('cool day')  
  else: print('its cold')  

#lists -> for read only Tuples use (1,2,3) instead of [1,2,3]
if bool(input('Enter to skip lists'))==True:
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
  
#loops & Iterating over a list
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

#Ranges
if bool(input('Enter to skip Ranges'))==True:
  nums = range(5,11,2) # start,end,step
  print(range(13)) 
  for num in nums: print(num)

# Input output vars
if bool(input('Enter to skip I/O')) == True:  # any input = True
    pretext = 'the price is' 
    postext = "in total"
    price = input(pretext[:] + ':')  # [:] all range of cells in pretext string
    bul = True
    ber = False
    if bul:  # if then
        print(f'{pretext}: {int(price) * 10} {postext}')  # formatted output vars in {}
    conv = input('continue? (y/n)')
    if bool(conv == 'y'): 
        print('ok')
        val2 = input('enter a second value')
        print(f'calculating {price} * {val2}... =') 
        print(int(int(price) * int(val2)))

# String object methods
if bool(input('Enter to skip Strings')) == True:
    course = 'Python For Beginners'
    print(course.upper())
    print(course.lower())
    print('location of thon: ' + str(course.find('thon')))
    print(course.replace('Python', 'py'))
    print('Python in str: ' + 'Python' in course)  # checks if 'Python' in var course and returns boolean

# Numeric calc div mod
if bool(input('Enter to skip Numeric')) == True:  
    num = 3 + 3 - 2
    print('3 + 3 - 2 = ' + str(num))
    num3 = 10 / 3 * 2
    print('10/3*2 = ' + str(num3))
    num2 = 10 // 3
    print('10 div 3 = ' + str(num2))
    num4 = 10 % 3
    print('10 mod 3 = ' + str(num4))
    num5 = 10 ** 3
    print('10^3 = ' + str(num5))
    num += num  # num = num + number
    print('+=num = ' + str(num))
    num *= num  # num = num * number
    print('*=num = ' + str(num))
    num -= num  # num = num - number
    print('-=num = ' + str(num))
    num /= num + 1  # num = num / number
    print('/=num = ' + str(num))

# operations > < !=
if bool(input('Enter to skip Operations')) == True: 
    num = 3 > 2  # = True
    print('3 > 2 = ' + str(num))
    num = 3 != 2  # = True
    print('3 != 2 = ' + str(num))
    num = 3 == 2  # = False
    print('3 == 2 = ' + str(num))

# Operators and/or/not
if bool(input('Enter to skip Operators')) == True:   
    price = 25
    print((price > 10) and (price < 30) or (price < 26) and not (price != 25))  # Returns bool

# if else
if bool(input('Enter to skip IF')) == True: 
    temp = 5
    if temp > 30:
        print('hot')
    elif temp > 20:
        print('nice day')
    elif temp > 10:
        print('cool day')  
    else: 
        print('its cold')  

# lists -> for read only Tuples use (1,2,3) instead of [1,2,3]
if bool(input('Enter to skip lists')) == True:
    nums = [1, 2, 3, 4, 5]
    nums.append(6)
    nums.insert(0, -1)
    nums.remove(3)
    print(nums)
    if 1 in nums: 
        print('1 is IN total nums:')
        print(len(nums))
    # Tuples 
    nums = (5, 11, 2)  # start, end, step
    print(str(nums.count(11)))
    for num in nums: 
        print(num)
  
# loops & Iterating over a list
if bool(input('Enter to skip loops')) == True:
    i = 1
  
    fruits = ["apple", "banana", "cherry", "melon"]
  
    while i < len(fruits):
        print(i * "*")
        print(fruits[i])
        i += 1
  
    print(fruits[-2])
    fruits[-2] = "pineapple"
  
    for fruit in fruits:
        print(fruit)
  
    print(fruits[1:3]) 

# Ranges
if bool(input('Enter to skip Ranges')) == True:
    nums = range(5, 11, 2)  # start, end, step
    print(range(13)) 
    for num in nums: 
        print(num)

