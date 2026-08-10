# 🐍 Python Camp — Day 6 Worksheet (Enemy Squads)

**Name: _______________**  |  You'll now have THREE files: `main.py`, `player.py`, `alien.py` — all in the same folder.

---

## Exercise 1: Build the Alien Class 👾
In a new file `alien.py`, write an `Alien` class with:
- `__init__(self, x, y)` that stores `x` and `y`
- A `draw(self, screen)` method that draws a 32×32 rectangle in a color of your choice

## Exercise 2: Create a Row of 8 Aliens 📋
In `main.py`:
1. `from alien import Alien`
2. Before the game loop, create an empty list `aliens = []`
3. Use a `for` loop (`range(8)`) to create 8 Alien objects, each 80 pixels further right than the last, and `append()` each to `aliens`

## Exercise 3: Draw the Whole Squad 🎨
Inside the game loop, add a `for` loop that calls `.draw(screen)` on every alien in the list. Run it — you should see all 8 aliens appear!

## Exercise 4: March, Bounce & Drop 🚶
1. Before the loop, set `direction = 1`
2. Every frame: loop through `aliens` and add `direction * 2` to each one's `x`
3. Check if any alien's `x` is `<= 0` or `>= 760` — if so, flip `direction` and add 20 to every alien's `y`

---

## ⭐ Bonus Challenges (fast finishers)

**B1. Two-Tone Squad 🎨** — Give aliens in even list positions one color and odd positions another. Hint: use the loop counter `i` and check `i % 2 == 0`.

**B2. Faster Squad 🏃** — Add a variable `alien_speed = 2` and use it instead of the number 2. What happens to the game's difficulty if you bump it up?

**B3. Bigger Squad 🧱** — Change the loop to create 10 aliens instead of 8, with tighter spacing (try 65 pixels apart instead of 80) so they still fit on screen.

---

## 🔑 Instructor Answer Key

```python
# alien.py
import pygame

class Alien:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def draw(self, screen):
        pygame.draw.rect(screen, (200, 60, 200), (self.x, self.y, 32, 32))
```

```python
# main.py (relevant parts)
import pygame
from player import Player
from alien import Alien

pygame.init()
screen = pygame.display.set_mode((800, 600))
curator = Player(380, 550)

aliens = []
for i in range(8):
    aliens.append(Alien(50 + i * 80, 50))

direction = 1

running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    hit_edge = False
    for alien in aliens:
        alien.x += direction * 2
        if alien.x <= 0 or alien.x >= 760:
            hit_edge = True

    if hit_edge:
        direction *= -1
        for alien in aliens:
            alien.y += 20

    screen.fill((10, 10, 30))
    curator.draw(screen)
    for alien in aliens:
        alien.draw(screen)
    pygame.display.flip()

pygame.quit()
```

**Teaching notes — this is a historically tricky day, flag pacing carefully:**
- The #1 confusion: students often try to give EACH alien its own direction variable, rather than sharing one `direction` for the whole squad. Reinforce: "the whole group turns around together."
- The `hit_edge` pattern (check everyone first, THEN react once) is a new idea — walk through it on the board/slides before students code it themselves.
- A very common bug: the `alien.x +=` line sits OUTSIDE the `for alien in aliens:` loop by accident (bad indentation), so only the last alien moves. This is the same class of bug as Day 3's list loops — worth pointing out the pattern explicitly.
- If a group is running behind, it's safe to let them stop at "aliens march and bounce" and skip the "drop down a row" piece — full row-dropping isn't required for tomorrow's collision detection to work.
- Per the syllabus pacing note: if today overruns, trim Day 8 stretch goals rather than rushing tomorrow's collision/win-lose day — that's the day that makes it feel like a finished game.
