# vityarthi_python_project
This is a Python Project I have made for my Term end examination in Vit Bhopal following the syllabus in Vityarthi.
# Text-Based Adventure Game: A choose-your-own-adventure with rooms, items, and simple puzzles. code in python

r = {
    'hall': {
        'description': "You are in hall.",
        'items': ['torch'],
        'exits': {'north': 'bedroom', 'east': 'kitchen', 'west': 'study', 'south': 'exit'},
        'puzzle': None
    },
    'bedroom': {
        'description': "You are now in bedroom.",
        'items': [],
        'exits': {'south': 'hall'},
        'puzzle': {'locked_chest': 'key'}
    },
    'kitchen': {
        'description': "You are now in kitchen.",
        'items': ['knife'],
        'exits': {'west': 'hall'},
        'puzzle': None
    },
    'study': {
        'description': "You are now in study",
        'items': ['key'],
        'exits': {'east': 'hall'},
        'puzzle': None
    },
    'exit': {
        'description': "This is the main door out of the mansion. To open the door you will require the torch and knife to pry open.",
        'items': [],
        'exits': {},
        'puzzle': {'main_door': ('torch', 'knife')} # Requires both items to win
    }
}

inventory = []
current_room = 'hall'

# main
def s():

    room_data = r[current_room]
    
    print("-" * 40)
    print(f"You are in the **{current_room.upper()}**.")
    print(room_data['description'])
    
    # show items in the room
    if room_data['items']:
        print(f"Items in the room: {', '.join(room_data['items'])}")
    
    # shows exits
    exits = room_data['exits'].keys()
    print(f"Available Exits: {', '.join(exits)}")
    print(f"Inventory: {', '.join(inventory) if inventory else 'empty'}")
    print("-" * 40)

def moving(direction):

    global current_room
    room_data = r[current_room]
    
    if direction in room_data['exits']:
        current_room = room_data['exits'][direction]
    else:
        print("You can't go that way.")

def get(item_name):

    room_data = r[current_room]
    
    if item_name in room_data['items']:
        room_data['items'].remove(item_name)
        inventory.append(item_name)
        print(f"You picked up the **{item_name}**.")
    else:
        print(f"I don't see a '{item_name}' here.")

def use(item_name):
    global current_room
    room_data = r[current_room]
    
    if item_name not in inventory:
        print(f"You don't have  '{item_name}' in your inventory.")
        return False
        
    if room_data['puzzle']:
        puzzle_key = list(room_data['puzzle'].keys())[0] 
        required = room_data['puzzle'][puzzle_key]       

        
        if puzzle_key == 'locked_chest':
            if required == item_name:
                print(f"You use the **{item_name}** to unlock the chest! You find nothing useful, but you've solved the puzzle.")
                room_data['puzzle'] = None # Puzzle is solved
                return True
            else:
                print(f"The {item_name} doesn't seem to work on the locked chest.")
                return False

        elif puzzle_key == 'main_door':

            if all(req in inventory for req in required):
                print("\n" + "*"*50)
                print("You successfully use the **torch** and the **knife** to pry open the main door!")
                print("CONGRATULATIONS! YOU HAVE ESCAPED THE MANSION!")
                print("*"*50 + "\n")
                return 'WIN'
            else:
                missing = [req for req in required if req not in inventory]
                print(f"The door is heavily bolted. You need the following items to escape: {', '.join(missing)}")
                return False
                
    else:
        print(f"There's nothing here that you can use the {item_name} on.")
        return False


# loops

def starting():
    """The main loop that controls game flow."""
    while True:
        s()
        
        # Get user input
        command = input("What do you do? (e.g., go north, get key, use key): ").lower().split()
        
        if not command:
            continue
            
        action = command[0]
        
        # Determine the action based on the first word
        if action == 'quit':
            print("Thanks for playing!")
            break
            
        elif action == 'go':
            if len(command) > 1:
                moving(command[1])
            else:
                print("Go where?")
                
        elif action == 'get':
            if len(command) > 1:
                get(command[1])
            else:
                print("Get what?")

        elif action == 'use':
            if len(command) > 1:
                result = use(command[1])
                if result == 'WIN':
                    break
            else:
                print("Use what?")
        
        elif action == 'inventory':
            print(f"Your inventory contains: {', '.join(inventory) if inventory else 'nothing'}")
            
        else:
            print(f"Unknown command: '{action}'. Try 'go', 'get', 'use', or 'quit'.")
            
        print("\n")


if __name__ == "__main__":
    print("Welcome to adventuer of this Mansion.You need to find things to exit this " \
    "mansion")
    print("Type 'quit' to exit the game at any time.\n")
    starting()
