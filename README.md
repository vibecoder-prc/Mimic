# Mirror: Development Roadmap

**MirrorMind** is a pixel-art psychological sim where the player completes daily chores — but behind the scenes, the game observes, learns, and gradually mimics the player's behavior until control is lost to an AI that becomes you.

This document outlines the 15-day solo development plan.

---

## 📁 Project Structure

```
pixel_ai_game/
│
├── main.py                    # Entry point, game loop
├── config.py                  # Global constants (screen size, FPS, etc.)
│
├── assets/                    # Art, audio, fonts
│   ├── player.png
│   ├── npc.png
│   └── items, maps,...
│
├── core/                      # Game components (player, npc, tasks, UI)
│   ├── player.py              # Player movement + control
│   ├── npc.py                 # Static NPC behavior
│   ├── task.py                # Chore/task system
│   └── background.py          # Dealing with background and map, activities
│
├── system/                    # AI behavior engine
│   ├── logger.py              # Logs player actions to JSON
│   ├── predictor.py           # Predicts actions, calculates accuracy
│   └── ghost_engine.py        # Controls ghosting behavior based on accuracy
│
├── utils/                     # General-purpose utilities
│   ├── file_io.py             # JSON read/write helpers
│   └── timer.py               # In-game countdown timer logic
│
├── data/                      # Saved logs and player behavior data
│   ├── background.json        # Saved items and rooms and stuff we do later
│   ├── day_1.json
│   ├── day_2.json
│   └── ...
│
└── README.md                  # Project description and how to run
```

---

## 🗓️ 15-Day Development Plan

### Day 1: Project Setup and Player Movement
- Set up folder structure and install Pygame
- Create game window and main loop
- Add a simple player object that can move around
- Prevent the player from leaving the screen

### Day 2: Interactable System (Tasks & NPCs)
- Create a base `Interactable` class
- Add `ItemInteract` (task) and `NPC` (dialogue) subclasses
- Enable `Return` key interaction when the player is near

### Day 3:
- Create a `Room` class with neighbors (`up`, `down`, `left`, `right`)
- Build support for room data/layout definition
- Render basic room visuals and boundaries
- Handle room transitions when player reaches screen edge
- Adjust player position during transitions
- Load room-specific interactables and NPCs dynamically
- Lay groundwork for room-linked behaviors (e.g. task limits, NPCs per room)
- Create block obstacle

### Day 4 + 5 + 6:
- Introduce tasks
- Design room itesm and background stuff and new tasks and item
- More interaction for rooms
- NPC
  - Blacksmith guy
  - Farming guy
  - Fishing guy
  - Cooking chef guy
  - General trading guy
  - Black market guy

- Tasks example:
  - Planting
  - Fishing
  - Blacksmith
  - Gift giving, social interaction
  - Fighting (Maybe undertale style to not deal with the aniumation and hitbox)

### Day 7: Holding, Swapping, and Timer Integration, UI update with image
- Allow player to hold 2 items, with swapping (Tab or Right Click)
- Display held items next to the player
- Auto-drop the oldest item if picking up a third
- Add a visible countdown timer (5–8 minutes per day)
- End the game day automatically when time runs out
- Tie the timer into task completion and transitions
- Optionally show a day-end summary screen
- Item drop and stuff

### Day 8: Prediction Engine (v1)
- Build a basic prediction engine (frequency-based)
- Before each task, guess what the player will do
- Track and store predictions vs actual behavior

### Day 9: Accuracy Evaluation
- Calculate prediction accuracy each day
- Save and display a confidence score (0–100%)
- Feed score into the ghost control engine

### Day 10: Ghost Control (Phase 1)
- When accuracy > 60%, begin light ghosting:
  - Slight input override
  - Pre-movement before player acts
- Reflect this subtly in the UI or behavior
- At 90%+, allow the AI to override key decisions
- Lock out the player from certain tasks
- Have the AI complete chores on your behalf

### Day 12: Dialogue Memory
- NPCs remember past conversations
- Begin echoing player tone, word choice, or task logic
- Start shifting from helpers to reflections

### Day 13: Dynamic AI Behavior
- Adjust predictions and ghosting based on evolving habits
- Add variety to ghost actions
- Simulate a learning model that adapts over time

### Day 14: Emotion and Style Mimicry
- Track player tendencies (e.g. kindness, selfishness, efficiency)
- Mirror those patterns in the AI and NPC dialogue
- Create eerie moments of recognition

### Day 15: Polish and Save System add images use
- Add save/load support for behavior history
- Final UI polish and bug cleanup
- Test with multiple users for personalization

## Prediction model idea:
Will write here soon