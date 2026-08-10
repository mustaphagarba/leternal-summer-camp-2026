# 🐍 Python Camp — Day 3 Worksheet (Lists & Functions)

**Name: _______________**  |  Save your work in `python_camp/day3_exercises.py`

---

## Exercise 1: Playlist Manager 🎵
1. Create an empty list called `playlist`
2. Use a `for` loop to ask the user for 5 songs, `append()`-ing each one
3. Loop through `playlist` and print each song with a 🎶 in front

## Exercise 2: High Score Tracker 🏆
Write a function `check_high_score(score, high_score)` that:
- Returns `score` if it's bigger than `high_score`
- Otherwise returns `high_score` unchanged

Test it by calling it 3 times with different scores and printing the result each time.

## Exercise 3: Class Register 📋
Write a function `print_roster(names)` that loops through a list and prints `✅ NAME is present` for each one. Then:
1. Build a list called `roster` by asking for 4 student names in a loop
2. Call `print_roster(roster)`
3. Print the total number of students using `len()`

## Exercise 4: Shopping List 🛒
1. Start with `groceries = ["rice", "beans", "garri"]`
2. Ask the user for one more item and `append()` it
3. Ask the user which item to remove, and `remove()` it
4. Print the final list

---

## ⭐ Bonus Challenges (fast finishers)

**B1. remove_item() Function 🗑️** — Write a function `remove_item(items, item_to_remove)` that removes an item from a list and returns the updated list. Use it on your shopping list.

**B2. Total Calculator 🧮** — Write a function `total_price(prices)` that takes a LIST of numbers and returns their sum using a loop. Test it with `[500, 300, 150]`.

**B3. Longest Name 📏** — Loop through a list of names and print out whichever one has the most letters (hint: use `len()` inside your loop and keep track of the longest so far).

---

## 🔑 Instructor Answer Key

```python
# Ex 1
playlist = []
for i in range(5):
    song = input("Add a song: ")
    playlist.append(song)
for song in playlist:
    print(f"🎶 {song}")

# Ex 2
def check_high_score(score, high_score):
    if score > high_score:
        return score
    return high_score

high_score = 0
high_score = check_high_score(45, high_score)
high_score = check_high_score(80, high_score)
high_score = check_high_score(60, high_score)
print(high_score)

# Ex 3
def print_roster(names):
    for name in names:
        print(f"✅ {name} is present")

roster = []
for i in range(4):
    name = input("Student name: ")
    roster.append(name)
print_roster(roster)
print(f"Total students: {len(roster)}")

# Ex 4
groceries = ["rice", "beans", "garri"]
new_item = input("Add an item: ")
groceries.append(new_item)
remove_item = input("Remove which item? ")
groceries.remove(remove_item)
print(groceries)

# B1
def remove_item(items, item_to_remove):
    items.remove(item_to_remove)
    return items

# B2
def total_price(prices):
    total = 0
    for price in prices:
        total = total + price
    return total
print(total_price([500, 300, 150]))

# B3
names = ["Ada", "Chidinma", "Bo", "Olumide"]
longest = names[0]
for name in names:
    if len(name) > len(longest):
        longest = name
print(longest)
```

**Common student errors to watch for:** forgetting the list starts empty `[]` before appending in a loop, calling `.remove()` with an item that isn't in the list (crashes!), forgetting a function needs `return` to hand a value back, mixing up `print()` inside a function with `return`.
