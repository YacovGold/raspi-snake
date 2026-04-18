# Technical Guide

This document contains the setup, configuration, and project structure details for the project.

## Hardware Requirements

- Raspberry Pi
- 1602A LCD Display
- 4 Buttons

## Setup Instructions

1. Clone the repository.
2. Install dependencies with `pip install -r requirements.txt`. Use `--break-system-packages` if needed.
3. Connect the LCD display to the Raspberry Pi and note the I2C address.
4. Connect the buttons to the GPIO pins used by the project.

## Configuration

Configure the project in [`config.py`](config.py):

- `BUTTON_PINS`: GPIO pins connected to the buttons
- `DEFAULT_BOUNCE_TIME`: debounce time for button presses
- `DB_PATH`: database path for storing settings and high scores
- `LCD_TYPE`: type of the connected LCD display
- `LCD_ADDRESS`: I2C address of the LCD display

## Usage

Start the project with:

```bash
python starter.py
```

## Menu Interactions

The LCD menu allows the player to:

- start a game
- select a level
- enable or disable overflow at the screen edges

## Game Mechanics

The snake grows by eating food, the game tracks score, and the run ends when the snake hits itself or a wall unless overflow is enabled. The LCD shows the current score and the best score.

## Project Structure

- [`starter.py`](starter.py): main entry point for launching the game
- [`config.py`](config.py): stores configuration settings
- [`games/base.py`](games/base.py): abstract base class for games
- [`games/snake.py`](games/snake.py): Snake game implementation
- [`helpers/buttons.py`](helpers/buttons.py): button input handling
- [`helpers/common.py`](helpers/common.py): shared helpers and enums
- [`helpers/dal.py`](helpers/dal.py): data access layer for settings and scores
- [`helpers/menu.py`](helpers/menu.py): menu management and navigation
- [`helpers/screen.py`](helpers/screen.py): LCD screen handling and extra-row simulation
