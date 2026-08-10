# 🐍 Python Camp — Day 1 Worksheet

**Name: _______________**  |  Save all your work in `python_camp/day1_exercises.py`

---

## Exercise 1: Greeting Machine 🤖
Write a program that:
1. Asks for the user's name with `input()`
2. Asks for their favorite color
3. Prints: `Hello NAME! COLOR is a great color!` using an **f-string**

**Example run:**
```
What is your name? Bola
Favorite color? blue
Hello Bola! blue is a great color!
```

## Exercise 2: Super Calculator 🧮
Create two variables, `a = 12` and `b = 5`. Print, each on its own line:
- their sum
- their difference
- their product
- `a` to the power of `b`

Then change `a` and `b` to any numbers you like and run it again. Did all four lines update by themselves? That's the power of variables!

## Exercise 3: About Me Card 🪪
Using **one variable of each type** — `str`, `int`, `float`, `bool` — print a card like this:

```
====================
Name: Chidi
Age: 12
Height: 1.52
Loves coding: True
====================
```

Hint: `print("=" * 20)` prints the border in one line!

## Exercise 4: Suya Stand 🍢
A stick of suya costs ₦500.
1. Ask the user how many sticks they want (remember `int()`!)
2. Print the total cost with an f-string: `That will be ₦3500, thank you!`

---

## ⭐ Bonus Challenges (fast finishers)

**B1. Age in Dog Years 🐕** — Ask for the user's age, multiply by 7, print `You are 84 in dog years!`

**B2. Mad Libs Deluxe 🎪** — Extend the class Mad Libs story with 5 inputs (a name, an animal, a food, a place, and a number). The sillier, the better.

**B3. Two-Line Swap 🔀** — Set `x = "amala"` and `y = "ewedu"`. Make the values swap places. (Hint: you may need a third variable... or research Python's one-line trick!)

---

## 🔑 Instructor Answer Key

```python
# Ex 1
name = input("What is your name? ")
color = input("Favorite color? ")
print(f"Hello {name}! {color} is a great color!")

# Ex 2
a = 12
b = 5
print(a + b)
print(a - b)
print(a * b)
print(a ** b)

# Ex 3
name = "Chidi"
age = 12
height = 1.52
loves_coding = True
print("=" * 20)
print(f"Name: {name}")
print(f"Age: {age}")
print(f"Height: {height}")
print(f"Loves coding: {loves_coding}")
print("=" * 20)

# Ex 4
sticks = int(input("How many sticks of suya? "))
print(f"That will be ₦{sticks * 500}, thank you!")

# B1
age = int(input("How old are you? "))
print(f"You are {age * 7} in dog years!")

# B3 (classic)          # B3 (Python trick)
x = "amala"             # x, y = y, x
y = "ewedu"
temp = x
x = y
y = temp
```

**Common student errors to watch for:** missing quotes around strings, forgetting `int()` before doing math on input, mismatched quote types, capital-letter `Print`.
