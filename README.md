<p align="center">
  <img src="https://github.com/user-attachments/assets/af5ab460-b294-47a6-a149-98c567770b8d" alt="Chase Take a Chance Logo" width="800" />
</p>

**Chase: Take A Chance** is a 3D horror-style maze game developed in **Python** using **Pygame**, **PyOpenGL**, **OpenCV**, and **MoviePy**.

The player explores a 3D maze while being chased by an enemy spider. The objective is to collect the required items before the enemy reaches the player. If the player is caught, a screamer video is shown and the game ends. If all required items are collected, the game plays a winning ending video.

> [!NOTE]
> This project was created as an academic programming project using Python, OpenGL rendering, 3D OBJ models, textures, sound, video playback, and basic game-state logic.

---

## Overview

**Chase: Take A Chance** is a first-person 3D maze game where the player must move through a textured maze, avoid an enemy, and collect objects.

The game includes:

- 3D maze rendering.
- First-person camera movement.
- Enemy chase behavior.
- Collectable items.
- Collision detection.
- Textured walls.
- OBJ model loading.
- Background music.
- Video-based endings.
- Game Over screen.
- Win screen.
- Screamer video after losing.
- Winning video after collecting all required objects.

> [!IMPORTANT]
> The game uses several multimedia libraries. Some features may require extra setup on Linux, especially OpenCV video windows, Pygame audio, and PyGetWindow compatibility.

---

## Project Structure

```text
Chase-Take-a-Chance/
│
├── map.py
├── map.csv
├── objloader.py
├── Enemy.py
├── Collectable.py
│
├── HSpider.obj
├── Coin.obj
│
├── spider_texture.jpg
├── wall_texture.jpg
│
├── background_music.mp3
├── SCREAMER.mp4
├── SCREAMER2.mp4
├── BOOGIE.mp4
│
└── README.md
```

---

## Main Files

| File | Description |
|---|---|
| `map.py` | Main game file. Handles initialization, rendering, movement, collisions, videos, music, and game states. |
| `map.csv` | Maze layout used to generate walls. |
| `objloader.py` | OBJ model loader used to render 3D models. |
| `Enemy.py` | Enemy logic and movement behavior. |
| `Collectable.py` | Collectable object logic. |
| `HSpider.obj` | 3D spider enemy model. |
| `Coin.obj` | 3D collectable model. |
| `spider_texture.jpg` | Texture used for the spider model. |
| `wall_texture.jpg` | Texture used for maze walls. |
| `background_music.mp3` | Background music played during gameplay. |
| `SCREAMER.mp4` | Losing ending video. |
| `SCREAMER2.mp4` | Alternative losing ending video. |
| `BOOGIE.mp4` | Winning ending video. |

---

## Technologies Used

| Technology | Purpose |
|---|---|
| `Python` | Main programming language. |
| `Pygame` | Window creation, events, keyboard input, audio, and text rendering. |
| `PyOpenGL` | 3D rendering with OpenGL. |
| `OpenCV` | Video playback for endings and screamers. |
| `MoviePy` | Extracts audio from videos for synchronized playback. |
| `CSV` | Loads the map layout from `map.csv`. |
| `Math` | Handles movement, angles, distance, and collision calculations. |
| `Random` | Selects random screamer video and delay timing. |
| `PyGetWindow` | Used to minimize windows on supported platforms. |

> [!WARNING]
> `PyGetWindow` does not support Linux. If you run this project on Linux, the import must be protected with a `try/except` block or disabled.

---

## Requirements

You need:

- Python 3.12 recommended
- Pygame
- PyOpenGL
- OpenCV
- MoviePy
- NumPy
- Pandas
- Pathfinding
- FFmpeg
- SDL2-related system libraries

> [!IMPORTANT]
> Python 3.14 may cause compatibility issues with some multimedia packages. Python **3.12** is recommended for this project.

---

## Installation on Arch Linux

### 1. Install system dependencies

```bash
sudo pacman -Syu
sudo pacman -S python python-pip uv git mesa freeglut glu ffmpeg base-devel
sudo pacman -S sdl2 sdl2_mixer sdl2_image sdl2_ttf
sudo pacman -S pipewire pipewire-alsa pipewire-pulse
sudo pacman -S libxcb xcb-util xcb-util-image xcb-util-keysyms xcb-util-renderutil xcb-util-wm
sudo pacman -S ttf-dejavu fontconfig
```

> [!NOTE]
> `ffmpeg` is required because MoviePy needs it to extract audio from video files.

---

### 2. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/Chase-Take-a-Chance.git
cd Chase-Take-a-Chance
```

If you already have the project folder locally:

```bash
cd Chase-Take-a-Chance
```

---

### 3. Create a virtual environment with Python 3.12

Using `uv`:

```bash
uv venv --python 3.12
```

If you use **fish shell**, activate it with:

```fish
source .venv/bin/activate.fish
```

If you use **bash** or **zsh**, activate it with:

```bash
source .venv/bin/activate
```

> [!TIP]
> If you use fish, do not run `source .venv/bin/activate`. That file is for bash/zsh. Use `activate.fish`.

---

### 4. Install Python dependencies

```bash
uv pip install pygame PyOpenGL PyOpenGL_accelerate numpy pandas pathfinding opencv-python moviepy==1.0.3
```

If you prefer regular `pip`:

```bash
pip install pygame PyOpenGL PyOpenGL_accelerate numpy pandas pathfinding opencv-python moviepy==1.0.3
```

> [!IMPORTANT]
> `moviepy==1.0.3` is recommended because the project imports:
>
> ```python
> from moviepy.editor import VideoFileClip
> ```

---

### 5. Run the game

```bash
python map.py
```

If you are on Wayland and OpenCV crashes because of Qt, run:

```bash
env QT_QPA_PLATFORM=xcb python map.py
```

For fish shell:

```fish
env QT_QPA_PLATFORM=xcb python map.py
```

---

## Installation on Windows

### 1. Install Python

Install Python 3.12 from the official Python website.

During installation, enable:

```text
Add Python to PATH
```

---

### 2. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/Chase-Take-a-Chance.git
cd Chase-Take-a-Chance
```

---

### 3. Create a virtual environment

```bash
python -m venv .venv
```

Activate it:

```bash
.venv\Scripts\activate
```

---

### 4. Install dependencies

```bash
pip install pygame PyOpenGL PyOpenGL_accelerate numpy pandas pathfinding opencv-python moviepy==1.0.3 pygetwindow
```

---

### 5. Run the game

```bash
python map.py
```

---

## Controls

| Action | Key |
|---|---|
| Move forward | `Up Arrow` |
| Move backward | `Down Arrow` |
| Turn right | `Right Arrow` |
| Turn left | `Left Arrow` |
| Exit game | `Escape` |

---

## Gameplay

The player starts inside a maze.

The main objective is to collect the required items while avoiding the spider enemy.

The game has three main states:

| State | Meaning |
|---|---|
| `edo_game = 0` | Normal gameplay. |
| `edo_game = 1` | Game Over state. |
| `edo_game = 2` | Win state. |

During gameplay:

- The enemy moves toward the player.
- The player navigates the maze.
- Collecting items reduces the remaining item counter.
- Colliding with the enemy triggers the Game Over sequence.
- Collecting all required items triggers the winning sequence.

---

## Game Flow

### Normal Gameplay

The game starts with:

```python
edo_game = 0
```

In this state, the program:

- Draws the floor.
- Draws the maze walls.
- Updates the enemy.
- Renders the enemy model.
- Renders collectable models.
- Checks enemy collision.
- Checks collectable collision.
- Updates the camera based on player movement.

---

### Game Over

When the player collides with the enemy:

```python
edo_game = 1
```

Then the game:

1. Stops the background music.
2. Freezes the scene briefly.
3. Waits for a random time.
4. Plays one of the screamer videos:
   - `SCREAMER.mp4`
   - `SCREAMER2.mp4`
5. Reinitializes the Pygame/OpenGL window.
6. Displays the `Game Over` message.
7. Closes the game after the configured end-screen duration.

> [!NOTE]
> The `Game Over` message must be drawn every frame while `edo_game == 1`. Drawing it only once will make it disappear immediately.

---

### Win State

When all required collectables are collected:

```python
edo_game = 2
```

Then the game:

1. Plays the winning video:
   - `BOOGIE.mp4`
2. Reinitializes the Pygame/OpenGL window.
3. Displays the `You win?` message.
4. Closes the game after the configured end-screen duration.

---

## Important Code Notes

### Game Over Display

The Game Over message is rendered with:

```python
show_game_over_message()
```

This function switches temporarily to a 2D orthographic projection so text can be drawn on top of the OpenGL scene.

```python
gluOrtho2D(0, screen_width, 0, screen_height)
```

> [!IMPORTANT]
> The message must be called repeatedly inside the render loop, not only once.

Correct logic:

```python
elif edo_game == 1:
    if not screamer_played:
        play_ending_video()
        screamer_played = True
        game_over_time = pygame.time.get_ticks()

    show_game_over_message()
```

---

### Window Size and Aspect Ratio

The project uses:

```python
screen_width = 1800
screen_height = 800
```

These values affect both the window size and the OpenGL camera perspective:

```python
gluPerspective(FOVY, screen_width / screen_height, ZNEAR, ZFAR)
```

For standard 16:9 proportions, use:

```python
screen_width = 1280
screen_height = 720
```

or:

```python
screen_width = 1600
screen_height = 900
```

or:

```python
screen_width = 1920
screen_height = 1080
```

> [!WARNING]
> Extremely large values such as `9999x800` may not actually create a larger window. The operating system may limit the window size, while OpenGL still uses the incorrect aspect ratio, causing the scene to look distorted.

---

### Fullscreen Mode

To use fullscreen properly, create the window using the real display size:

```python
def create_window(fullscreen=False):
    global screen, screen_width, screen_height

    flags = DOUBLEBUF | OPENGL

    if fullscreen:
        flags |= FULLSCREEN
        screen = pygame.display.set_mode((0, 0), flags)
    else:
        screen = pygame.display.set_mode((screen_width, screen_height), flags)

    screen_width, screen_height = screen.get_size()

    glViewport(0, 0, screen_width, screen_height)
```

Then create the window with:

```python
create_window(fullscreen=True)
```

> [!IMPORTANT]
> When fullscreen is enabled, always update `screen_width` and `screen_height` using `screen.get_size()` and call `glViewport()` with the real size.

---

### PyGetWindow on Linux

The original code imports:

```python
import pygetwindow as gw
```

However, `pygetwindow` does not support Linux.

Use this instead:

```python
try:
    import pygetwindow as gw
except NotImplementedError:
    gw = None
```

Then protect any PyGetWindow usage:

```python
if gw is not None:
    windows = gw.getAllTitles()
```

> [!NOTE]
> On Linux, the window-minimizing feature is skipped. The game can still run without it.

---

### OpenCV and Wayland

On Arch Linux or other Wayland systems, OpenCV may fail with:

```text
Could not find the Qt platform plugin "wayland"
Available platform plugins are: xcb.
```

Run the game with:

```bash
env QT_QPA_PLATFORM=xcb python map.py
```

Or add this before importing `cv2`:

```python
import os
os.environ["QT_QPA_PLATFORM"] = "xcb"
```

---

## Assets

The game uses several asset types:

| Asset Type | Files |
|---|---|
| 3D models | `HSpider.obj`, `Coin.obj` |
| Textures | `wall_texture.jpg`, `spider_texture.jpg` |
| Audio | `background_music.mp3` |
| Videos | `SCREAMER.mp4`, `SCREAMER2.mp4`, `BOOGIE.mp4` |
| Map data | `map.csv` |

> [!IMPORTANT]
> The asset files must remain in the same folder as `map.py`, unless the paths are updated in the code.

---

## Troubleshooting

### `pygetwindow` does not support Linux

Error:

```text
NotImplementedError: PyGetWindow currently does not support Linux
```

Fix:

```python
try:
    import pygetwindow as gw
except NotImplementedError:
    gw = None
```

And wrap usages with:

```python
if gw is not None:
    ...
```

---

### `pygame.mixer` is not available

Error:

```text
NotImplementedError: mixer module not available
```

Recommended fix:

- Use Python 3.12.
- Recreate the virtual environment.
- Reinstall Pygame.
- Install SDL2 mixer libraries.

Arch Linux:

```bash
sudo pacman -S sdl2 sdl2_mixer pipewire pipewire-alsa pipewire-pulse
```

Then:

```bash
pip uninstall pygame
pip install --no-cache-dir pygame
```

---

### OpenCV crashes on Wayland

Run:

```bash
env QT_QPA_PLATFORM=xcb python map.py
```

If needed, install XCB dependencies:

```bash
sudo pacman -S libxcb xcb-util xcb-util-image xcb-util-keysyms xcb-util-renderutil xcb-util-wm
```

---

### Qt cannot find fonts

Warning:

```text
QFontDatabase: Cannot find font directory
```

Install fonts:

```bash
sudo pacman -S ttf-dejavu fontconfig
```

If the warning continues:

```bash
mkdir -p .venv/lib/python3.12/site-packages/cv2/qt/fonts
cp /usr/share/fonts/TTF/DejaVuSans.ttf .venv/lib/python3.12/site-packages/cv2/qt/fonts/
```

---

### MoviePy cannot find a video file

Error:

```text
MoviePy error: the file could not be found
```

Make sure these files exist in the project folder:

```text
SCREAMER.mp4
SCREAMER2.mp4
BOOGIE.mp4
```

Also check that `videoEnding` is not empty before calling:

```python
VideoFileClip(videoEnding)
```

---

### Game Over appears for less than one second

This happens when the text is drawn only once and then cleared on the next frame.

Fix:

```python
elif edo_game == 1:
    if not screamer_played:
        ...
        game_over_time = pygame.time.get_ticks()

    show_game_over_message()
```

The call to `show_game_over_message()` must be outside:

```python
if not screamer_played:
```

---

### The scene only appears on part of the screen in fullscreen

This means OpenGL is not using the real window size.

Fix:

```python
screen_width, screen_height = screen.get_size()
glViewport(0, 0, screen_width, screen_height)
gluPerspective(FOVY, screen_width / screen_height, ZNEAR, ZFAR)
```

---

## Recommended Development Settings

For easier testing, use a normal 16:9 window:

```python
screen_width = 1280
screen_height = 720
```

For fullscreen, use:

```python
create_window(fullscreen=True)
```

Recommended end-screen duration:

```python
END_SCREEN_DURATION = 60000
```

This keeps Game Over or Win screens visible for one minute.

---

## Possible Improvements

Future versions could include:

- Add a start menu.
- Add pause menu.
- Add restart option after Game Over.
- Add mouse camera control.
- Add better lighting.
- Add improved wall textures.
- Add more enemies.
- Add enemy sound effects.
- Add health or lives system.
- Add collectable counter UI.
- Add fullscreen toggle.
- Add configurable resolution.
- Add better Linux compatibility.
- Replace OpenCV video playback with Pygame-compatible video handling.
- Separate code into multiple modules.
- Add a `requirements.txt` file.
- Add a `README` assets section with credits.
- Improve error handling for missing files.
- Add a proper game state manager.

> [!TIP]
> A strong next improvement would be separating rendering, player movement, enemy logic, collision logic, video playback, and UI text into separate files.

---

## Preview

### Good Ending Gameplay
https://github.com/user-attachments/assets/60a83d16-8485-4994-87bc-03865016b402

### Bad Ending Gameplay
https://github.com/user-attachments/assets/571cf7ee-323f-4c33-a90c-59210752918e

---

## Educational Purpose

This project is useful for practicing:

- Python game development.
- Pygame window management.
- Pygame audio.
- PyOpenGL rendering.
- 3D camera movement.
- OBJ model loading.
- Texture mapping.
- Collision detection.
- Maze generation from CSV data.
- Enemy following logic.
- Game states.
- Video playback with OpenCV.
- Audio extraction with MoviePy.
- Cross-platform debugging.
- Linux compatibility fixes.

---

## Team

Created by:

| Name |
|---|
| Abigail Pérez García |
| Alejandro Kong Montoya |
| Álvaro Alberto Cruz Jiménez |
| Rodrigo López Guerra |

---

## License

This project is publicly available for educational and portfolio review purposes only.

The source code, visual assets, audio, videos, logos, screenshots, documentation, and other project materials may not be used, copied, modified, redistributed, sublicensed, or used commercially without explicit permission from the project authors.

All rights reserved unless otherwise stated.

> [!IMPORTANT]
> Some third-party assets, music, libraries, or references may be subject to their own licenses. Those materials remain owned by their original creators and are not covered by this project license.

---

## Disclaimer

**Chase: Take A Chance** is an educational programming project.

It is not a commercial-ready game unless the assets, performance, compatibility, licenses, and gameplay systems are reviewed and improved.

> [!CAUTION]
> Horror content, flashing visuals, loud sounds, or screamer videos may be uncomfortable for some players. Use clear warnings before distributing the game.
