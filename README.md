# Go Boom Card Game

A Java implementation of the trick-taking card game "Go Boom" with both console and JavaFX GUI modes. Features save/load functionality, multi-round gameplay, and score tracking. Developed as part of the TCP1201 (Object-Oriented Programming and Data Structures) assignment.

---

## 🎮 Overview

Go Boom is a strategic trick-taking card game for 4 players. Each player is dealt 7 cards and must follow the suit or rank of the lead card. The highest-rank card matching the lead suit wins the trick. Players must draw from the deck if they cannot play, and the game continues across multiple rounds until a player reaches 100 points.

This implementation includes:
- Console-based gameplay (Part 1 & Part 2)
- JavaFX GUI interface (Part 2)
- Save/load game state functionality
- Score tracking across rounds
- Input validation and game rule enforcement

---

## 👥 Contributors

- Wong Ju Wei (1211104210)
- Ter Zheng Bin (1211103705)
- Lim Ye Xin (1211104730)
- Yap Rui Ern (1211105182)

---

## 📁 Repository Structure

```
Go-Boom/
├── Part 1/                          # Initial console implementation
│   ├── Boom.java                    # Main game logic (console mode)
│   ├── Card.java                    # Card class (rank, suit)
│   ├── Deck.java                    # Deck management
│   ├── Game.java                    # Game state initialization
│   ├── Player.java                  # Player class with hand management
│   ├── PART1.md                     # Part 1 feature completion checklist
│   └── TCP1201 Assignment Part 1.pdf
│
├── Part 2/                          # Extended version with GUI and persistence
│   ├── Boom.java                    # Enhanced game logic
│   ├── Card.java                    # Card class
│   ├── Deck.java                    # Deck management
│   ├── Game.java                    # Game initialization
│   ├── Player.java                  # Player class
│   ├── Gui.java                     # JavaFX GUI implementation
│   ├── SaveBox.java                 # Save game dialog
│   ├── ExitBox.java                 # Exit confirmation dialog
│   ├── MessageBox.java              # Alert/message dialog
│   ├── WinGameBox.java              # Game over screen
│   ├── PART2.md                     # Part 2 feature completion checklist
│   ├── bin/                         # Compiled .class files
│   └── TCP1201 Assignment Part 1.pdf
│
└── README.md                        # This file
```

---

## ✨ Features

### Part 1 (Console Mode)
- ✅ Randomized 52-card deck shuffle
- ✅ Deal 7 cards to each of 4 players
- ✅ First card determines the lead card and starting player
- ✅ Follow suit or rank enforcement
- ✅ Highest-rank card with matching suit wins the trick
- ✅ Trick winner leads next card
- ✅ All cards displayed face-up for validation

### Part 2 (Enhanced Console + GUI)
- ✅ Draw from deck if unable to play (until valid card or deck exhausted)
- ✅ Skip turn if deck exhausted and no playable card
- ✅ Multi-round gameplay with score tracking
- ✅ Save/load game state (file-based persistence)
- ✅ Reset game (clear scores, restart from round 1)
- ✅ JavaFX GUI mode with interactive card play
- ✅ Console output maintained alongside GUI (for validation)
- ✅ Exit confirmation and win condition screens

---

## 🧠 Key Concepts Demonstrated

- **Object-Oriented Design:** Separation of concerns (Card, Deck, Player, Game)
- **Collections Framework:** ArrayList, HashMap, HashSet for deck/hand/center management
- **File I/O:** Save/load game state using serialization or file streams
- **JavaFX GUI:** Scene graph, event handling, layout management (HBox, VBox, BorderPane)
- **Game Logic:** Turn-based flow, rule validation, winner determination
- **Randomization:** Deck shuffling and card distribution

---

## 🚀 Getting Started

### Prerequisites
- **JDK 21** (or compatible version)

### Setup

1. **Clone the repository:**
   ```powershell
   git clone https://github.com/juwei-w/Go-Boom.git
   cd Go-Boom
   ```

2. **Open in VS Code:**
   - JavaFX JARs are already included in the `lib/` folder
   - VS Code will auto-detect them via `.vscode/settings.json`
   - If red squiggles appear, reload: Command Palette (Ctrl+Shift+P) → `Developer: Reload Window`

That's it! No manual downloads needed.

---

## ▶️ Running the Game

### Console Mode (Part 2)

```powershell
# Navigate to Part 2 folder
cd "Go-Boom\Part 2"

# Compile (no JavaFX needed for console)
javac -d bin *.java

# Run console mode
java -Xms128m -Xmx512m -cp bin Boom
```

### GUI Mode (Part 2)

```powershell
# Navigate to Part 2 folder
cd "Part 2"

# Compile with JavaFX (using bundled lib folder)
javac --module-path ../lib --add-modules javafx.controls -d bin *.java

# Run GUI mode with reduced heap (to avoid memory errors)
java -Xms128m -Xmx512m --module-path ../lib --add-modules javafx.controls -cp bin Gui
```

### VS Code Launch Configuration (Optional)

Create `.vscode/launch.json`:

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "java",
      "name": "Run Gui (JavaFX)",
      "request": "launch",
      "mainClass": "Gui",
      "projectName": "Go-Boom",
      "cwd": "${workspaceFolder}/Part 2",
      "vmArgs": "-Xms128m -Xmx512m --module-path \"${workspaceFolder}/lib\" --add-modules javafx.controls"
    },
    {
      "type": "java",
      "name": "Run Boom (Console)",
      "request": "launch",
      "mainClass": "Boom",
      "projectName": "Go-Boom",
      "cwd": "${workspaceFolder}/Part 2",
      "vmArgs": "-Xms128m -Xmx512m"
    }
  ]
}
```

Then use VS Code's Run > Start Debugging (F5).

---

## 🎯 Game Rules (Go Boom)

1. **Setup:**
   - 52-card deck, shuffled randomly
   - 4 players, each dealt 7 cards
   - First card from remaining deck becomes the lead card and determines starting player

2. **Playing a Trick:**
   - Players must follow the **suit** or **rank** of the lead card
   - If unable to play, draw from deck until a valid card is obtained or deck is exhausted
   - If deck is empty and no valid card, player skips the turn
   - The **highest-rank card** of the **lead suit** wins the trick
   - Winner of the trick leads the next card

3. **Scoring:**
   - At end of round (when a player runs out of cards), remaining players count card values in hand
   - Card values: Ace=1, 2-10=face value, Jack=11, Queen=12, King=13
   - Scores accumulate across rounds
   - Game ends when a player reaches 100+ points (that player loses; others win)

4. **Save/Load:**
   - Save current game state (players, hands, scores, round/trick number) to file
   - Resume from saved state at any time

---

## 🛠 Technology Stack

- **Language:** Java (JDK 21)
- **GUI Framework:** JavaFX 21.x (Scene, Stage, Controls)
- **Data Structures:** ArrayList, HashMap, HashSet, Scanner
- **I/O:** File streams for save/load functionality
- **Build Tool:** Manual compilation (javac) or IDE (VS Code, Eclipse)

---

## 📊 Sample Gameplay Flow

1. **Start Game:** 7 cards dealt to each of 4 players; lead card placed in center
2. **Player Turn:** Current player selects a card from hand (matching suit/rank)
3. **Draw if Needed:** If no valid card, draw from deck until playable or deck empty
4. **Determine Winner:** After all players play (or skip), highest-rank card of lead suit wins
5. **Next Trick:** Winner leads next card; repeat until a player's hand is empty
6. **Score Round:** Calculate remaining card values for other players; add to totals
7. **Check Win Condition:** If any player ≥100 points, game ends; otherwise start new round
8. **Save/Exit:** At any time, save game state or exit with confirmation

---

## 🔗 Resources

- **Repository:** https://github.com/juwei-w/Go-Boom
- **Issues:** https://github.com/juwei-w/Go-Boom/issues

---

## 📸 Screenshots

*(Optional: Add screenshots of console output and GUI gameplay here)*

**Console Mode:**
```
========== START GAME ==========
Round #1
Trick #1

----- Center -----
5♦

Player 1 turn
Player 1 cards: [A♠, 3♦, 7♣, J♥, K♠, 2♦, 9♠]
Enter card to play: 3♦
...
```

**GUI Mode:**
- Main menu with Play/Load/Exit buttons
- Game board showing all 4 players' hands (face-up for validation)
- Center area with lead card and current trick cards
- Choice box for card selection + Play/Draw buttons
- Save/Reset/Exit controls
- Win screen with final scores

---

## 📝 Academic Context

**Course:** TCP1201 – Object-Oriented Programming and Data Structures  
**Institution:** MMU (Multimedia University)  
**Assignment:** Two-part card game implementation (console + GUI)  
**Date:** 2022 – 2023 Academic Year

This project demonstrates practical application of OOP principles (encapsulation, inheritance), data structure usage (lists, maps, sets), file I/O, and GUI development in a game development context.

---

*Object-Oriented Programming and Data Structures • Degree Year 1 Sem 2 • March 2023 - Aug 2023*
