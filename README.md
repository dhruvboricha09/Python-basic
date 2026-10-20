int(input("Enter your age: "))

year = 2026 + (100 - age)

print(name, "will turn 100 years old in", year)

num = int(input("Enter a number: "))

#whether no. is even or odd
if num % 2 == 0:
    print("Number is even")
else:
    print("Number is odd")

#fibonacci series
    n = int(input("Enter the number of terms: "))

a, b = 0, 1

for i in range(n):
    print(a, end=" ")
    a, b = b, a + b

#reverse a number
    num = input("Enter a number: ")

rev = num[::-1]

print("Reversed number:", rev)

#check if a character is a vowel
def is_vowel(ch):
    if ch.lower() in "aeiou":
        return True
    else:
        return False

ch = input("Enter a character: ")
print(is_vowel(ch))

#find the length of a string
def find_length(value):
    count = 0
    for item in value:
        count += 1
    return count

text = input("Enter a string: ")
print("Length:", find_length(text))

#check if a number is an Armstrong number
def armstrong(num):
    digits = str(num)
    total = sum(int(d) ** len(digits) for d in digits)
    return total == num

n = int(input("Enter a number: "))

if armstrong(n):
    print("Armstrong number")
else:
    print("Not an Armstrong number")


#check if a number is a palindrome
    def palindrome(value):
     return str(value) == str(value)[::-1]

n = input("Enter a value: ")

if palindrome(n):
    print("Palindrome")
else:
    print("Not a palindrome")

#calculate the factorial of a number
    def factorial(n):
     if n == 0 or n == 1:
        return 1
     else:
        return n * factorial(n - 1)

num = int(input("Enter a number: "))
print("Factorial:", factorial(num))


#check if a sentence is a pangram
def pangram(sentence):
    alphabet = "abcdefghijklmnopqrstuvwxyz"

    for ch in alphabet:
        if ch not in sentence.lower():
            return False

    return True

text = input("Enter a sentence: ")

if pangram(text):
    print("Pangram")
else:
    print("Not a pangram")


# print elements of a list that are less than 5

    a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]

for num in a:
    if num < 5:
        print(num)

#check if two lists have at least one common member
        list1 = [1, 2, 3, 4]
list2 = [3, 5, 6, 7]

common = False

for item in list1:
    if item in list2:
        common = True
        break

print(common)


#remove the 0th, 2nd, 4th, and 5th elements from a list
a = ['Red', 'Green', 'Blue', 'Yellow',
     'Black', 'White', 'Pink']

result = [x for i, x in enumerate(a)
          if i not in (0, 2, 4, 5)]

print(result)



#sort a dictionary by value in ascending and descending order
d = {'A': 40, 'B': 10, 'C': 30, 'D': 20}

asc = dict(sorted(d.items(), key=lambda x: x[1]))
desc = dict(sorted(d.items(), key=lambda x: x[1],
                   reverse=True))

print("Ascending:", asc)
print("Descending:", desc)



#merge two dictionaries into one
dic1 = {1: 10, 2: 20}
dic2 = {3: 30, 4: 40}
dic3 = {5: 50, 6: 60}

result = {}
result.update(dic1)
result.update(dic2)
result.update(dic3)

print(result)

#sum all the values in a dictionary
d = {'A': 10, 'B': 20, 'C': 30}

total = sum(d.values())

print("Sum:", total)

#read from a file
file = open("sample.txt", "r")

content = file.read()

print(content)

file.close()

#append to a file
file = open("sample.txt", "a")

text = input("Enter text to append: ")
file.write(text + "\n")

file.close()

file = open("sample.txt", "r")
print(file.read())
file.close()



#read the last n lines of a file
n = int(input("Enter number of lines: "))

file = open("sample.txt", "r")
lines = file.readlines()
file.close()

for line in lines[-n:]:
    print(line, end="")
