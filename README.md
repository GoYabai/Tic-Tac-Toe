## Description

Tic-Tac-Toe (Console Edition) is a highly customizable, terminal-based strategy game built entirely in C++20. Designed as a robust game engine, it scales from classic 3x3 Tic-Tac-Toe to expansive 12x12 Gomoku (Caro) matches. Players can challenge their friends or test their skills against built-in AI opponents with varying difficulty levels.

**Key features:**

1. **Dynamic Board & Rules:** Fully customizable grid sizes (up to 12x12) and adjustable win conditions (connect 3, 4, or 5 symbols).
2. **Versatile Game Modes:** Supports Player vs Player (PvP), Player vs Bot (PvE), and automated Bot vs Bot (EvE) simulations.
3. **Versatile Level:** Features multiple difficulty levels, including an Easy random-picker and a Medium heuristic-evaluator capable of blocking and attacking.
4. **Automated Testing Support:** Includes a `--judge` mode for headless execution, minimal output formatting, and input redirection for Grader systems.
5. **Comprehensive Logging:** Built-in `GameLogger` tracks game events, errors, and AI execution time to a local `log.txt` file.
6. **Robust Input Validation:** Safe console interaction system that prevents crashes from invalid data types or out-of-bound coordinates.

**Game mechanics:**

* Enter coordinates in a `row col` format to place your symbol ('X' or 'O').
* Outsmart your opponent to align the required number of symbols horizontally, vertically, or diagonally.
* AI (Medium) analyzes the board state to actively block your winning moves and prioritize its own.
* Game automatically detects terminal states (Win, Lose, or Full-board Draw).

## 🤖 Bot Difficulty Explained

### 🟢 EASY: Random Selection
* **Algorithm:** Pure Randomness.
* **Logic:** Collects all empty cells and picks one randomly using `std::mt19937`.
* **Behavior:** Unpredictable and has no strategy.

### 🟡 MEDIUM: One-Step Heuristic
* **Algorithm:** Greedy Approach.
* **Logic:** 1. **Win:** Checks if any move wins immediately.
  2. **Block:** If not, blocks the opponent's immediate winning move.
  3. **Random:** Otherwise, picks a random cell.
* **Behavior:** Reactive; punishes simple blunders but doesn't plan ahead.

### 🔴 HARD: Optimized Minimax
* **Algorithm:** Minimax with Alpha-Beta Pruning.
* **Key Components:**
  * **Minimax:** Recursively simulates game states (depth: 4) to find the optimal path.
  * **Alpha-Beta Pruning:** Skips redundant branches to boost computation speed.
  * **Candidate Filtering:** Only evaluates cells near existing pieces to optimize search space.
  * **Evaluation Function:** Scores the board based on chain lengths and "Open Ends" (crucial for `OPEN_TWO` rules).
* **Behavior:** Proactive; anticipates opponent moves and builds long-term threats.

---

## Installation

### Prerequisites

* C++ Compiler supporting C++20 (e.g., GCC/g++ via MSYS2/MinGW64 for Windows)
* Git

### Steps

1. Clone the repository:
   ```bash
   git clone [https://github.com/GoYabai/Tic-Tac-Toe.git](https://github.com/GoYabai/Tic-Tac-Toe.git)
   cd Tic-Tac-Toe
2. Compile the game:
   ```bash
   g++ -std=c++20 game.cpp -o game.exe
3. Run the game (Interactive Mode):
   ```bash
   ./game.exe
