# Chess AI ♟️

A neural network-powered chess engine featuring a graphical interface built with **Pygame** and **python-chess**. The bot predicts moves by calculating probability scores across source and destination squares.

## Setup Instructions

### Windows
```bash
# Clone the repository
git clone [https://github.com/bhavjsh/chess-ai.git]
cd chess-ai

# Create and activate virtual environment
py -3.10 -m venv .venv
.venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the GUI
cd gui
python main.py
```
### macOS / Linux
```bash
# Clone the repository
git clone [https://github.com/bhavjsh/chess-ai.git]
cd chess-ai

# Create and activate virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run the GUI
cd gui
python3 main.py
```

### Technical Stack
-Language: Python 3.10 (64-bit)
-Deep Learning: TensorFlow 2.10
-GUI: Pygame
-Chess Logic: python-chess

## How the AI Works
The engine utilizes two distinct neural networks to evaluate the board state:

1. **From-Model:** Predicts the probability of the starting square.
2. **To-Model:** Predicts the probability of the destination square.

**Move Selection Logic:**
The AI calculates a score for every legal move using the following formula:

$$score = P(from\_square) \times P(to\_square)$$

The legal move with the highest resulting score among all available legal moves is executed.


## Dataset & Training
Training data is sourced from the [Lichess Database](https://database.lichess.org).

* **Preprocessing:** Used `pgn-extract` to append FEN strings to each game move.
* **Extraction:** Custom Python scripts parse board states and map consecutive positions to determine specific move coordinates.
* **Storage:** Cleaned data stores the source and destination squares mapped directly to the corresponding board state.

## Project Structure
* `gui/` — Main game interface, rendering logic, and user interaction.
* `data_cleaning/` — Scripts for PGN parsing, data extraction, and dataset preparation.
* `models/` — Pre-trained TensorFlow models and architecture definition files.

## Notes
* **Compatibility:** TensorFlow versions are pinned to **2.10** to ensure stable GPU acceleration on Windows systems.
* **Optimization:** Dependencies are structured to avoid common installation conflicts between macOS (Metal) and Windows (CUDA) environments.
