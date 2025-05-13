# 🌠🌠🌠 space-shooter 🌠🌠🌠

Space shooter game by [@clear-code-projects](https://github.com/clear-code-projects)

## 🛠️ Getting Started

To set up and run the game:

1. Run `install.sh` to create a Python virtual environment and install dependencies:

   ```bash
   ./install.sh
   ```

2. Then launch the game using:

   ```bash
   ./game.sh
   ```

These scripts ensure the game runs in an isolated Python environment with all the required packages.

## 🚀 Try out the iterations of the game!

You can run the game as it evolved through 10 code iterations shown in [this video](https://www.youtube.com/watch?v=8OMghdHP-zs) by @clear-code-projects:

```bash
b=$(git branch --show-current); for c in $(git log --pretty=format:%h%n code/main.py | tac); do git checkout $c; python code/main.py; done; git checkout $b
```

This script checks out each commit that modified `code/main.py`, runs the game in that version, then returns to your current branch. It's a great way to watch the game take shape step by step, as explained in the video.

---

## 🎯 Challenge: Rotate the game 90° clockwise

Here’s a challenge for you: rotate the entire gameplay by 90 degrees clockwise.

1. **Rotate player sprite**:

   ```python
   self.image = pygame.transform.rotate(self.image, -90)
   ```

   The player ship originally faced upward. Rotating by -90° turns it to the right, aligning with horizontal gameplay.

2. **Change laser firing direction**:

   ```python
   -    Laser(laser_surf, self.rect.midtop, ...)
   +    Laser(laser_surf, self.rect.midright, ...)
   ```

   Previously, lasers fired from the top of the ship. Now, they fire from the right side.

3. **Rotate laser sprite and move it rightward**:

   ```python
   self.image = pygame.transform.rotate(self.image, -90)
   ...
   self.rect.centerx += 400 * dt
   ```

   The laser graphic is rotated to point right, and movement is now horizontal instead of vertical.

4. **Change meteor spawn direction**:

   ```python
   self.direction = pygame.Vector2(-1, uniform(-0.5, 0.5))
   ```

   Meteors now come from the right side of the screen and move leftward.

5. **Change meteor spawn location**:

   ```python
   x, y = randint(WINDOW_WIDTH+100, WINDOW_WIDTH+200), randint(0, WINDOW_HEIGHT)
   ```

   Meteors spawn off-screen to the right and appear to fly in from that side.
