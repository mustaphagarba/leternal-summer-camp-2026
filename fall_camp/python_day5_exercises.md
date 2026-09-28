# 🐍 Python Camp — Day 5 Worksheet (The Planet Class)

**Name: _______________**  |  You'll work in TWO files: `planet.py` and `main.py`, saved in the same folder.

---

## Exercise 1: Build the Planet Class 🧱
In a new file called `planet.py`, write a `Planet` class. Start the file with `from vpython import *`. Your `__init__` should take `name`, `distance`, `radius`, and `planet_color`, save each one on `self`, and also create the planet's 3D sphere:

```python
self.body = sphere(pos=vector(distance, 0, 0), radius=radius, color=planet_color)
```

## Exercise 2: Use It From main.py 📄
In `main.py`, bring back your Day 4 Sun, then:
1. Add `from planet import Planet` near the top
2. Create Earth: `Planet("Earth", 10, 0.5, color.blue)`
3. Create Mars: `Planet("Mars", 13, 0.4, color.red)`
4. Keep a `while True:` loop with `rate(60)` at the bottom so the scene stays alive

Run `main.py` (not `planet.py`!). You should see the Sun with two planets out to its right. Rotate and zoom to look around.

## Exercise 3: Add a describe() Method ⚙️
Inside your `Planet` class, add a method `describe(self)` that prints `NAME orbits DISTANCE units from the Sun`. Then, in `main.py`, call `earth.describe()` and `mars.describe()` and check your terminal.

## Exercise 4: Add Venus 🟠
Add a third planet, Venus, closer to the Sun than Earth: distance 7, radius 0.45, and `color.orange`. Make sure it doesn't overlap the Sun.

---

## ⭐ Bonus Challenges (fast finishers)

**B1. Year Length 📅** — Add a fifth fact to the class: `year_length` (days for one trip around the Sun). Earth is 365 and Mars is about 687. Update `describe()` to print it too.

**B2. Who's Closer? 📏** — Add a method `closer_than(self, other)` that returns `True` if this planet's distance is smaller than the other planet's. Test it with `print(earth.closer_than(mars))`.

**B3. Meet Jupiter 🪐** — Add Jupiter at distance 20 with radius 1.2 and a color of your choice. Zoom out with the scroll wheel to see the whole lineup.

---

## 🔑 Instructor Answer Key

```python
# planet.py
from vpython import *

class Planet:
    def __init__(self, name, distance, radius, planet_color):
        self.name = name
        self.distance = distance
        self.radius = radius
        self.body = sphere(pos=vector(distance, 0, 0),
                           radius=radius,
                           color=planet_color)

    def describe(self):
        print(f"{self.name} orbits {self.distance} units from the Sun")
```

```python
# main.py
from vpython import *
from planet import Planet

scene.title = "Solar Voyager"
scene.background = color.black

sun = sphere(pos=vector(0, 0, 0), radius=2,
             color=color.yellow, emissive=True)

earth = Planet("Earth", 10, 0.5, color.blue)
mars = Planet("Mars", 13, 0.4, color.red)
venus = Planet("Venus", 7, 0.45, color.orange)

earth.describe()
mars.describe()
venus.describe()

while True:
    rate(60)
```

```python
# B1: year_length (planet.py changes)
    def __init__(self, name, distance, radius, planet_color, year_length):
        ...
        self.year_length = year_length

    def describe(self):
        print(f"{self.name} orbits {self.distance} units from the Sun "
              f"and takes {self.year_length} days per year")

# main.py
earth = Planet("Earth", 10, 0.5, color.blue, 365)
mars = Planet("Mars", 13, 0.4, color.red, 687)

# B2: closer_than (add inside the class)
    def closer_than(self, other):
        return self.distance < other.distance

# main.py
print(earth.closer_than(mars))   # True

# B3
jupiter = Planet("Jupiter", 20, 1.2, color.orange)
```

## 🧑‍🏫 Instructor Notes

- **Testing status:** I ran `planet.py` and `main.py` above against a stand-in for VPython, and they import correctly, create the planets, and print the `describe()` lines. I could not run them against real VPython, because my testing environment has no browser. Please run the answer key once on a camp laptop before Day 5.
- **This is most students' first exposure to classes and `self`.** Expect confusion. The blueprint/house analogy on slide 5 and the Planet Factory activity on slide 8 are there to help. Reassure them that `self` simply means "this particular planet," and that it clicks with repetition. Point out that a method is the same idea as the Day 3 functions.
- **Keep the parameter list consistent.** The class signature is `Planet(name, distance, radius, planet_color)`. Day 6 builds all 8 planets from parallel lists (names, distances, radii, colors) using exactly this signature, so avoid letting students reorder the parameters. The bonus B1 adds a fifth parameter, which is fine as a side experiment, but B1 code shouldn't be carried into Day 6.
- **Why `planet_color` and not `color`:** the deck explains this on slide 14. A parameter named `color` would clash with VPython's `color` names, which is a real source of confusing bugs.
- **Common errors:** forgetting `self.` inside the class; typing `_init_` with one underscore per side; passing too few arguments (`missing required positional argument`); running `planet.py` instead of `main.py`; the two files being in different folders; capitalization mismatches between `planet` (file) and `Planet` (class).
- **If a group is behind:** it's fine to stop at Earth and Mars and skip Venus and the bonuses. Day 6's list-and-loop build only needs a working `Planet` class.
- **Scale honesty:** the distances (Earth = 10, Mars = 13) are squashed to fit the screen. Slide 17 tells students so. Please keep that framing, and the same squashed values, when you teach Day 6.
