# 🐍 Python Camp — Day 4 Worksheet (Meet 3D Python: Light Up the Sun)

**Name: _______________**  |  Save your work in `python_camp/main.py`

---

## Exercise 1: Your First 3D Scene 🌐
1. Type `pip install vpython` in the VS Code terminal (if you haven't already)
2. Write a program with just two lines: `from vpython import *` and `sun = sphere()`
3. Run it. A browser tab should open with a white ball in 3D. Try to rotate and zoom around it with your mouse.

## Exercise 2: Design Your Sun ☀️
Change your sphere so that it:
- sits at the center: `pos=vector(0, 0, 0)`
- has a `radius` of 2
- is `color.yellow` (try `color.orange` or `color.red` too!)
- glows on its own with `emissive=True`

Then add `scene.background = color.black` above it so the scene looks like outer space.

## Exercise 3: Explore x, y, z 📐
Add a second, smaller sphere called `test_planet` with `radius=0.5` and `color=color.blue`. Place it at each position below (one at a time), run the program, and write a comment saying which way it moved from the Sun:
1. `vector(6, 0, 0)`
2. `vector(0, 6, 0)`
3. `vector(0, 0, 6)`

*(Delete or comment out the test planet when you're done. Tomorrow we build real ones!)*

## Exercise 4: Make the Sun Pulse 🌟
Add a `while True:` loop that makes the Sun's radius grow slowly to 2.5, then shrink back to 2, over and over. You'll need:
- A variable `growing = True` before the loop
- `rate(60)` as the FIRST line inside the loop
- An `if growing:` / `else:` that adds or subtracts 0.01 from `sun.radius`
- Two `if` checks that flip `growing` when the radius passes 2.5 or drops below 2

---

## ⭐ Bonus Challenges (fast finishers)

**B1. Speed Control 🏎️** — Add a variable `pulse_speed = 0.01` and use it instead of the number 0.01. Try 0.005 and 0.03. What changes?

**B2. Custom Space 🌌** — Change `scene.title` to your own name for the simulation, and try a very dark blue background: `scene.background = vector(0.02, 0.02, 0.1)`.

**B3. Color-Changing Sun 🎨** — Make the Sun turn `color.orange` while it's growing and `color.yellow` while it's shrinking. (Hint: set `sun.color` inside your existing `if growing:` / `else:` blocks.)

---

## 🔑 Instructor Answer Key

```python
# Ex 1
from vpython import *
sun = sphere()

# Ex 2
from vpython import *

scene.background = color.black
sun = sphere(pos=vector(0, 0, 0), radius=2,
             color=color.yellow, emissive=True)

# Ex 3 (one position at a time)
test_planet = sphere(pos=vector(6, 0, 0), radius=0.5, color=color.blue)  # moves right
# test_planet = sphere(pos=vector(0, 6, 0), ...)                         # moves up
# test_planet = sphere(pos=vector(0, 0, 6), ...)                         # moves toward you

# Ex 4 (also the Day 4 deliverable)
from vpython import *

scene.title = "Solar Voyager"
scene.background = color.black

sun = sphere(pos=vector(0, 0, 0), radius=2,
             color=color.yellow, emissive=True)

growing = True
while True:
    rate(60)
    if growing:
        sun.radius = sun.radius + 0.01
    else:
        sun.radius = sun.radius - 0.01
    if sun.radius > 2.5:
        growing = False
    if sun.radius < 2:
        growing = True
```

```python
# B1: replace 0.01 with a variable
pulse_speed = 0.01
...
        sun.radius = sun.radius + pulse_speed

# B2
scene.title = "Amina's Solar System"
scene.background = vector(0.02, 0.02, 0.1)

# B3
    if growing:
        sun.radius = sun.radius + 0.01
        sun.color = color.orange
    else:
        sun.radius = sun.radius - 0.01
        sun.color = color.yellow
```

## 🧑‍🏫 Instructor Notes

- **Pre-camp rehearsal (important):** the scene renders in a browser tab, and I could not verify the full render loop myself, because my testing environment has no browser. I confirmed `pip install vpython` works (version 7.6.5) and that `from vpython import *` and the `scene.title` / `scene.background` / `scene.width` / `scene.height` settings run. I did NOT confirm that `sphere(...)`, `emissive`, `rate()`, or the rotate/zoom controls behave as described. Please run the Ex 4 code on a camp laptop, ideally with the internet off, before Day 4.
- **Offline install:** on a machine with internet, run `pip download vpython -d wheels`, copy the `wheels` folder to a USB stick, then install on each camp laptop with `pip install --no-index --find-links wheels vpython`. Test this on a clean machine.
- **Camera controls:** the deck says right-click drag rotates, scroll zooms, and shift + drag pans. Laptop trackpads may differ, so have a few USB mice on hand, and confirm the controls on your actual machines.
- **Ctrl+C gotcha:** closing the browser tab does NOT stop the Python program. Students should click in the terminal and press Ctrl + C, or they'll pile up hidden running programs.
- **Most common bugs:** `rate()` missing or outside the loop (frozen tab); `color.Yellow` with a capital letter; forgetting commas inside `vector(...)`; a browser tab that opened behind VS Code.
- **Pacing:** Day 4 ends Week 1 with a showcase, so leave 15 minutes at the end for students to demo their Sun.
