# 🐍 Python Camp — Day 4 Worksheet (Meet Pygame)

**Name: _______________**  |  Save your work in `python_camp/main.py`

---

## Exercise 1: Open a Window 🪟
1. `pip install pygame` in the terminal (if you haven't already)
2. Write a program that opens an 800×600 window titled "Museum Invaders"
3. Add the game loop so the window stays open and closes properly with the X button

## Exercise 2: Draw the Curator 🎨
Inside your loop, fill the background with a dark color and draw a gold rectangle (40×40) near the bottom of the screen to represent the Night Curator.

## Exercise 3: Move Left and Right ⌨️
Add keyboard reading so the LEFT and RIGHT arrow keys move the curator's rectangle. Remember: `screen.fill()` must run every loop, BEFORE you draw!

## Exercise 4: Stay On Screen 🚧
Add a check so the curator can't move past the left or right edge of the 800-pixel-wide window.

---

## ⭐ Bonus Challenges (fast finishers)

**B1. New Colors 🎨** — Change the curator's color, or make the background a different dark shade. Try (20, 5, 40) for a purple gallery-at-night feel.

**B2. Up and Down Too ↕️** — Add UP and DOWN arrow key movement as well (careful — don't let the curator wander into the museum ceiling! Cap the y range too).

**B3. Speed Boost 🏃** — Add a variable `speed = 5` and use it instead of the number 5 directly. Then try changing just that ONE number to make the curator faster or slower.

---

## 🔑 Instructor Answer Key

```python
import pygame

pygame.init()
screen = pygame.display.set_mode((800, 600))
pygame.display.set_caption("Museum Invaders")

x = 380
y = 550
speed = 5

running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and x > 0:
        x -= speed
    if keys[pygame.K_RIGHT] and x < 760:
        x += speed

    screen.fill((10, 10, 30))
    pygame.draw.rect(screen, (255, 215, 0), (x, y, 40, 40))
    pygame.display.flip()

pygame.quit()
```

```python
# B2 — up/down added
if keys[pygame.K_UP] and y > 300:
    y -= speed
if keys[pygame.K_DOWN] and y < 560:
    y += speed
```

**Teaching notes:**
- The single most common Day 4 bug: students put `pygame.display.flip()` INSIDE the `for event in pygame.event.get():` block instead of at the end of the `while` loop. Walk around checking indentation early.
- Second most common: forgetting `screen.fill()` each frame → smeary trails. This is actually a great visual bug to let students see once before fixing, so they understand WHY the fill line matters.
- If a student's window "flashes and closes instantly," they're missing the `while running:` loop entirely — the program just runs once top to bottom.
- Remind students Ctrl+C in the terminal (or just closing the window) stops a runaway/frozen game.
