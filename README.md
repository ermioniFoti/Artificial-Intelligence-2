# HexThello AI Player

A strategy game agent developed to play **HexThello** (Othello on a hexagonal grid) using Artificial Intelligence techniques. This project was developed as part of the **Artificial Intelligence** course at the **Technical University of Crete** (Fall 2024).



## 📌 Project Overview

The primary objective of this application is to implement an intelligent agent capable of playing **HexThello**. Unlike standard Othello, this game is played on a hexagonal grid, requiring specialized logic for move validation and strategy.

The project implements and compares distinct search and optimization methods to determine the best possible move in a given timeframe.



## 🚀 Implemented AI Strategies

The application manages decision-making using the following architectures:

### 1. Minimax Algorithm (Depth-Limited)

* **Structure:** A recursive tree search that alternates between players.
* **Search Algorithm:** Minimax with specific depth constraints.
* **Process:** The system expands the game tree up to a **Maximum Depth of 3** ($MAX\_DEPTH = 3$) or until no moves are available.
* **Functionality:** It alternates between the **Maximizer** (AI) and the **Minimizer** (Opponent) to select the optimal move. When the depth limit is reached, the Evaluation Function is called.

### 2. Alpha-Beta Pruning ($\alpha-\beta$)

* **Structure:** An optimization layer applied to the Minimax tree.
* **Search Algorithm:** Pruning logic using `alpha` (lower bound) and `beta` (upper bound) values.
* **Process:** During the search, if a state is found where $\beta \le \alpha$, the algorithm cuts off (prunes) that branch.
* **Advantage:** Significantly reduces the number of nodes expanded by ignoring paths that cannot possibly lead to a better outcome than those already examined.

### 3. Heuristic Evaluation Function

* **Structure:** A weighted scoring system for board states.
* **Components:**
    * **Piece Count (`pieceValue`):** The total number of discs owned by the player.
    * **Mobility (`mobilityValue`):** The number of valid moves available (limiting opponent mobility is key).
    * **Stability (`stableValue`):** Uses the `is_stable` helper to identify discs that cannot be flipped by the opponent.
    * **Corner Control (`cornerValue`):** Uses the `is_corner` helper to reward occupying strategic corner cells.
* **Process:** Calculates a final score by combining these four factors with specific weights.

### 4. Forward Pruning (Experimental)

* **Structure:** A `get_top_moves` function designed to filter candidate moves.
* **Process:** Sorts all available moves by their evaluation score and retains only the top 5.
* **Outcome:** This method was implemented but **not used** in the final submission, as it did not provide a significant improvement in execution speed.

---

## 🛠️ Technical Specifications

* **Core Logic:** Minimax with $\alpha-\beta$ pruning.
* **Helper Functions:** `is_stable` (checks neighborhood uniformity) and `is_corner` (checks grid boundaries).
* **Execution:** The AI calculates moves dynamically based on the current board state provided by the game environment.



## 📊 Performance Analysis

The project includes an execution test demonstrating the AI's capability against a Random Player.

* **Result:** Black (AI "Ermil") Won.
* **Final Score:** White: **30** | Black: **139**.
* **Execution Time:** 205 units.





## 📂 Project Structure

* **Minimax:** Implements the recursive search and pruning logic.
* **Evaluation:** Contains the `evaluation_function` and weighting logic.
* **Helpers:**
    * `is_stable`: Returns 1 if all neighbors match the player's color.
    * `is_corner`: Identifies critical corner positions.
    * `get_top_moves`: (Experimental) Move sorting and filtering.

---

**Developed for the School of Electrical and Computer Engineering, Technical University of Crete.**
