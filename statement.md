# 🏰 Text Adventure Game — **State Documentation**

This document describes the full state of the game world including rooms, items, exits, puzzles, and player state.

---

## 📌 **Global State**

### **Player**
- **Current Room:** `hall`
- **Inventory:** `[]`

---

## 🏠 **Rooms & World Structure**

### **1. HALL**
**Key:** `hall`  
**Description:** “You are in hall.”

**Items:**  
- torch

**Exits:**  
- north → bedroom  
- east → kitchen  
- west → study  
- south → exit

**Puzzle:** None

---

### **2. BEDROOM**
**Key:** `bedroom`  
**Description:** “You are now in bedroom.”

**Items:**  
- *(none)*

**Exits:**  
- south → hall

**Puzzle:**  
- locked_chest → requires **key**

---

### **3. KITCHEN**
**Key:** `kitchen`  
**Description:** “You are now in kitchen.”

**Items:**  
- knife

**Exits:**  
- west → hall

**Puzzle:** None

---

### **4. STUDY**
**Key:** `study`  
**Description:** “You are now in study”

**Items:**  
- key

**Exits:**  
- east → hall

**Puzzle:** None

---

### **5. EXIT (MAIN DOOR)**
**Key:** `exit`  
**Description:** “To open the door you require torch and knife.”

**Items:** None  
**Exits:** None

**Puzzle:**  
- main_door → requires **torch** and **knife** to win

---

## 🧩 **Puzzles Summary**

| Room    | Puzzle        | Required Item(s) | Result |
|---------|----------------|------------------|--------|
| Bedroom | locked_chest   | key              | Puzzle solved (no reward) |
| Exit    | main_door      | torch + knife    | Player escapes mansion |

---

🔁 Game Loop Overview

The main loop (starting()) performs:

Show current room info (s())

Prompt for input

Interpret commands:

go <direction>

get <item>

use <item>

inventory

quit

If puzzle in exit room is solved → WIN + game ends
