# 🐍 Python Camp — Day 3 Worksheet (The Planet Database)

**Name: _______________**  |  Save your work in `python_camp/day3_exercises.py`

---

## Exercise 1: Planet Log 🪐
1. Create an empty list called `discovered`
2. Use a `for` loop to ask the user for 5 planet or moon names, `append()`-ing each one
3. Loop through `discovered` and print each one with a 🪐 in front

## Exercise 2: Distance Function 📏
Write a function `closer_planet(distance1, distance2)` that:
- Returns `distance1` if it's smaller (closer to the Sun) than `distance2`
- Otherwise returns `distance2`

Test it by calling it 3 times with different distance pairs and printing the result each time.

## Exercise 3: Planet Database 📋
Write a function `report_planet(name, distance)` that prints `🪐 NAME: DISTANCE million km from the Sun`. Then:
1. Build two parallel lists: `names` (4 planet names) and `distances` (their distances in millions of km)
2. Use a `for i in range(len(names))` loop to call `report_planet(names[i], distances[i])` for each planet
3. Print the total number of planets using `len()`

## Exercise 4: Exoplanet Watchlist 🔭
1. Start with `exoplanets = ["Kepler-452b", "TRAPPIST-1e", "Proxima b"]`
2. Ask the user for one more exoplanet name and `append()` it
3. Ask the user which one turned out to be a false positive, and `remove()` it
4. Print the final watchlist

---

## ⭐ Bonus Challenges (fast finishers)

**B1. remove_dwarf_planet() Function 🪐** — Write a function `remove_dwarf_planet(planet_list, name)` that removes a planet from a list and returns the updated list. Use it on a solar system list that still includes `"Pluto"`.

**B2. Total Distance Calculator 🧮** — Write a function `total_distance(distances)` that takes a LIST of numbers and returns their sum using a loop. Test it with `[58, 108, 150, 228]`.

**B3. Farthest Planet 📏** — Loop through parallel `names` and `distances` lists and print out whichever planet has the greatest distance (hint: keep track of the largest distance seen so far, and the name that goes with it).

---

## 🔑 Instructor Answer Key

```python
# Ex 1
discovered = []
for i in range(5):
    name = input("A planet or moon you know: ")
    discovered.append(name)
for planet in discovered:
    print(f"🪐 {planet}")

# Ex 2
def closer_planet(distance1, distance2):
    if distance1 < distance2:
        return distance1
    return distance2

print(closer_planet(58, 150))
print(closer_planet(228, 108))
print(closer_planet(778, 1400))

# Ex 3
def report_planet(name, distance):
    print(f"🪐 {name}: {distance} million km from the Sun")

names = ["Mercury", "Venus", "Earth", "Mars"]
distances = [58, 108, 150, 228]
for i in range(len(names)):
    report_planet(names[i], distances[i])
print(f"Total planets: {len(names)}")

# Ex 4
exoplanets = ["Kepler-452b", "TRAPPIST-1e", "Proxima b"]
new_planet = input("Add an exoplanet: ")
exoplanets.append(new_planet)
false_positive = input("Which one was a false positive? ")
exoplanets.remove(false_positive)
print(exoplanets)

# B1
def remove_dwarf_planet(planet_list, name):
    planet_list.remove(name)
    return planet_list

solar_system = ["Mercury", "Venus", "Earth", "Mars", "Pluto"]
solar_system = remove_dwarf_planet(solar_system, "Pluto")
print(solar_system)

# B2
def total_distance(distances):
    total = 0
    for d in distances:
        total = total + d
    return total
print(total_distance([58, 108, 150, 228]))

# B3
names = ["Mercury", "Venus", "Earth", "Mars"]
distances = [58, 108, 150, 228]
farthest_name = names[0]
farthest_distance = distances[0]
for i in range(len(names)):
    if distances[i] > farthest_distance:
        farthest_distance = distances[i]
        farthest_name = names[i]
print(f"{farthest_name} is farthest at {farthest_distance} million km")
```

**Common student errors to watch for:** forgetting the list starts empty `[]` before appending in a loop, calling `.remove()` with an item that isn't in the list (crashes!), forgetting a function needs `return` to hand a value back, mixing up `print()` inside a function with `return`, and — new this session — using two parallel lists that get out of sync (make sure `names[i]` and `distances[i]` always refer to the SAME planet).
