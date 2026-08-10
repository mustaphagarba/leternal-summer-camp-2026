# 🐍 Python Camp — Day 2 Worksheet

**Name: _______________**  |  Save your work in `python_camp/day2_exercises.py`

---

## Exercise 1: Secret Password Gate 🔐
1. Create a variable `password = "sesame"`
2. Ask the user to enter the password
3. If it matches, print `🏰 Welcome inside!` — otherwise print `🚫 Access denied!`

**Level up:** use a `while` loop + `break` so it keeps asking until they get it right.

## Exercise 2: Grade Calculator 🎓
Ask the user for a test score (0–100) and print:
- 70 or above → `Distinction! 🌟`
- 50 to 69 → `Pass! 👍`
- below 50 → `Keep practising! 💪`

Use `if` / `elif` / `else` — and don't forget `int()`!

## Exercise 3: Times Table Machine ✖️
Ask the user for a number, then print its full times table (1 to 12) using a `for` loop:

```
Which table? 7
7 x 1 = 7
7 x 2 = 14
...
7 x 12 = 84
```

Hint: `range(1, 13)` gives you 1 through 12.

## Exercise 4: Rocket Countdown 🚀
Using a `while` loop, count down from 10 to 1, then print `Blast off! 🎆`.
**Twist:** ask the user what number to start from!

---

## ⭐ Bonus Challenges (fast finishers)

**B1. Star Triangle 🔺** — Use a loop to print:
```
⭐
⭐⭐
⭐⭐⭐
⭐⭐⭐⭐
```
Hint: `print("⭐" * i)` inside a loop.

**B2. FizzBuzz Jr. 🥤** — Loop from 1 to 20. For multiples of 3 print `Fizz` instead of the number; for multiples of 5 print `Buzz`. (Multiples of both? Try `Fizzbuzz`!) Hint: `i % 3 == 0` checks if `i` divides evenly by 3.

**B3. Guess My Number 2.0 🎯** — Take the class Guess My Number game and add a counter that tracks how many guesses the player used, then print it when they win.

---

## 🔑 Instructor Answer Key

```python
# Ex 1 (level-up version)
password = "sesame"
while True:
    attempt = input("Enter the password: ")
    if attempt == password:
        print("🏰 Welcome inside!")
        break
    print("🚫 Access denied!")

# Ex 2
score = int(input("Your score (0-100): "))
if score >= 70:
    print("Distinction! 🌟")
elif score >= 50:
    print("Pass! 👍")
else:
    print("Keep practising! 💪")

# Ex 3
n = int(input("Which table? "))
for i in range(1, 13):
    print(f"{n} x {i} = {n * i}")

# Ex 4
start = int(input("Count down from? "))
while start > 0:
    print(start)
    start = start - 1
print("Blast off! 🎆")

# B1
for i in range(1, 5):
    print("⭐" * i)

# B2
for i in range(1, 21):
    if i % 3 == 0 and i % 5 == 0:
        print("Fizzbuzz")
    elif i % 3 == 0:
        print("Fizz")
    elif i % 5 == 0:
        print("Buzz")
    else:
        print(i)

# B3
secret = 7
guess = 0
tries = 0
while guess != secret:
    guess = int(input("Guess (1-10): "))
    tries = tries + 1
    if guess < secret:
        print("Too low! ⬇️")
    elif guess > secret:
        print("Too high! ⬆️")
print(f"🎉 Got it in {tries} tries!")
```

**Common student errors to watch for:** using `=` instead of `==` in conditions, missing colons, wrong indentation, infinite loops (remind them: Ctrl+C stops a runaway program).
