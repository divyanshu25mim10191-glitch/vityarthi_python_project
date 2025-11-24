# Text-Based Adventure Game

A **Python text-based adventure game** where players explore a mansion, collect items, solve puzzles, and try to escape. This is a choose-your-own-adventure style game designed to demonstrate Python programming concepts in a fun and interactive way.

---

## Table of Contents
- [Demo](#demo)
- [Features](#features)
- [How to Play](#how-to-play)
- [Game Structure](#game-structure)
- [Requirements](#requirements)
- [Installation](#installation)
- [Future Enhancements](#future-enhancements)

---

## Demo

After running the game, you will see a description of your current room, available items, exits, and your inventory. Example interaction:

\`\`\`
You are in the HALL.
Items in the room: torch
Available Exits: north, east, west, south
Inventory: empty

What do you do? (e.g., go north, get key, use key): get torch
You picked up the torch.
\`\`\`

---

## Features
- Multiple rooms with unique descriptions.
- Collectable items: \`torch\`, \`knife\`, \`key\`.
- Simple puzzles and locked objects (e.g., chest, main door).
- Inventory management.
- Clear win condition: escape the mansion using required items.
- User-friendly text-based input (\'go\', \'get\', \'use\', \'inventory\', \'quit\').

---

## How to Play
Commands available to the player:

- \'go <direction>\' – Move to another room (north, south, east, west).  
- \'get <item>\' – Pick up an item in the room.  
- \'use <item>\' – Use an item to solve puzzles or unlock doors.  
- \'inventory\' – Check your current inventory.  
- \'quit\' – Exit the game.

## 🎮 How to Play

Type commands into the terminal to interact with the game.

Basic Commands
Command	Example	Purpose
go <direction>	go north	Move between rooms
get <item>	get key	Pick up an item
use <item>	use key	Use an item
inventory	inventory	Show items you're carrying
quit	quit	Exit the game

Example:

\`\`\`
> go north
> get key
> use key
\`\`\`

---

## Game Structure
The game is structured using Python dictionaries and lists:

- **Rooms (\`r\`)**: Contains room name, description, items, exits, and puzzles.  
- **Inventory**: Tracks collected items.  

Example of a room structure:

\`\`\`python
'bedroom': {
    'description': "You are now in bedroom.",
    'items': [],
    'exits': {'south': 'hall'},
    'puzzle': {'locked_chest': 'key'}
}
\`\`\`

### Functions:
- \`s()\`: Displays room info, items, exits, and inventory.  
- \`moving(direction)\`: Moves the player.  
- \`get(item_name)\`: Picks up an item.  
- \`use(item_name)\`: Solves puzzles or unlocks doors.  
- \`starting()\`: Main game loop handling user commands.

---

## Requirements
- Python 3.7 or higher  
- No external libraries required  

---

## Installation
1. Clone the repository:

\`\`\`bash
git clone https://github.com/divyanshu25mim10191-glitch/vityarthi_python_project
\`\`\`

2. Navigate into the project directory:

\`\`\`bash
cd text-adventure-game
\`\`\`

3. Run the game:

\`\`\`bash
python vitproject.py
\`\`\`

---

## Future Enhancements
- Add more rooms, puzzles, and items.  
- Introduce NPCs (non-player characters) with dialogue.  
- Save/load game feature.  
- Scoring system based on items collected and puzzles solved.  
- Improved UI with colored text and ASCII art.  

---

