# 🐍 Python Camp — Day 5 Worksheet (Classes, Sprites & Shooting)

**Name: _______________**  |  You'll build TWO files: `player.py` and `main.py`, in the same folder.

---

## Exercise 1: Build the Player Class 🧱
In a new file `player.py`, write a `Player` class with:
- `__init__(self, x, y)` that stores `x`, `y`, and `speed = 5`
- A `move_left(self)` method that subtracts speed from x
- A `move_right(self)` method that adds speed to x
- A `draw(self, screen)` method that draws a 40×40 gold rectangle at (x, y)

## Exercise 2: Use It From main.py 📄
In `main.py`:
1. `from player import Player`
2. Create `curator = Player(380, 550)`
3. In the game loop, call `curator.move_left()` / `curator.move_right()` based on arrow keys, and `curator.draw(screen)` every frame

*(This replaces yesterday's loose x/y variables — everything now lives inside the Player object!)*

## Exercise 3: Add Shooting 🔫
1. Create an empty list `bullets = []` before the game loop
2. When SPACE is pressed, append `[curator.x + 18, curator.y]` to `bullets`
3. Every frame: loop through `bullets` and subtract 8 from each bullet's y (bullet[1])
4. Every frame: loop through `bullets` and draw each one as a small yellow rectangle

## Exercise 4: Clean Up Bullets 🧹
Remove bullets that have gone off the top of the screen:
```python
bullets = [b for b in bullets if b[1] > 0]
```
Add this line once per frame and test that your bullet count doesn't grow forever.

---

## ⭐ Bonus Challenges (fast finishers)

**B1. One Bullet at a Time 🎯** — Only allow firing if `len(bullets) == 0`. Notice how this changes the feel of the game — more like classic Space Invaders!

**B2. Bullet Speed Variable 🏎️** — Add a `bullet_speed = 8` variable and use it instead of a hardcoded 8. Try changing just that number.

**B3. Curator Color by Health 🎨** — (Preview thinking, not required to work fully) Imagine adding `self.health = 3` to Player. What would you check in `draw()` to make the curator flash red when health is low?

---

## 🔑 Instructor Answer Key

```python
# player.py
import pygame

class Player:
    def __init__(self, x, y):
        self.x = x
        self.y = y
        self.speed = 5

    def move_left(self):
        self.x -= self.speed

    def move_right(self):
        self.x += self.speed

    def draw(self, screen):
        pygame.draw.rect(screen, (255, 215, 0), (self.x, self.y, 40, 40))
```

```python
# main.py
import pygame
from player import Player

pygame.init()
screen = pygame.display.set_mode((800, 600))
curator = Player(380, 550)
bullets = []

running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and curator.x > 0:
        curator.move_left()
    if keys[pygame.K_RIGHT] and curator.x < 760:
        curator.move_right()
    if keys[pygame.K_SPACE]:
        bullets.append([curator.x + 18, curator.y])

    for bullet in bullets:
        bullet[1] -= 8
    bullets = [b for b in bullets if b[1] > 0]

    screen.fill((10, 10, 30))
    curator.draw(screen)
    for bullet in bullets:
        pygame.draw.rect(screen, (255, 255, 0), (bullet[0], bullet[1], 4, 12))
    pygame.display.flip()

pygame.quit()
```

**Teaching notes:**
- This is most students' FIRST time with `self` and classes. Expect confusion — reassure them that `self` just means "this particular object," and it clicks with repetition.
- Common bug: forgetting `self.` in front of `x`/`y`/`speed` inside the class — Python then complains the variable doesn't exist outside `__init__`.
- Import errors: remind students `player.py` and `main.py` must be in the SAME folder, and the import line must exactly match the filename and class name (case-sensitive).
- If bullets "spam" every frame while holding SPACE, that's expected default behavior — B1 (limit to one at a time) is the fix, offered as a bonus rather than required.
