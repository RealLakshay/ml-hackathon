# Hangman with Probabilistic Letter Predictions (HMM Simulation)

## Overview
This project demonstrates a manual Hangman game powered by a simplified Hidden Markov Model (HMM)-like mechanism that predicts the probability of each letter being part of the hidden word.

The environment simulates how an RL (Reinforcement Learning) or probabilistic agent could play Hangman — balancing exploration (trying new letters) and exploitation (using high-probability letters).

---

## Features
- Custom Hangman environment with:
  - Word masking (_ for unknown letters)
  - Lives tracking and win/loss detection
  - Reward feedback for correct/incorrect guesses
- Mock HMM probability model:
  - Generates probabilities for each alphabet letter
  - Avoids already guessed letters
  - Normalizes probabilities to simulate letter likelihoods

---

## Code Structure

### 1. HangmanEnv Class
Implements the game logic:
- `reset()` initializes a new game
- `step(action)` processes a guessed letter and returns:
  - Updated mask
  - Updated guessed vector
  - Normalized remaining lives
  - Reward and game info (win/lose/repeated/wrong)

### 2. CharHMM Class
A mock Hidden Markov Model that:
- Estimates pseudo-probabilities for each letter
- Adds minor random noise to simulate model uncertainty
- Ignores already guessed letters

### 3. Manual Demo Loop
- Initializes an environment and mock HMM
- Iterates through a fixed sequence of guesses
- Prints:
  - Letter probability distribution (Top 10)
  - Mask updates after each guess
  - Lives and reward progress
- Displays final result and summary statistics

---

## Example Output

```
MANUAL DEMO GAME — Word: 'hangman'
Initial Mask: _______

Step 1: Current Mask: _______
Letter Probabilities (Top 10):
  e: 0.0431
  a: 0.0427
  t: 0.0418
  o: 0.0412
  ...
Guess 1: 'a' | Mask: _a___a_ | Lives: 6 | Reward: 1

Guess 2: 'n' | Mask: _an__an | Lives: 6 | Reward: 1

Guess 3: 'm' | Mask: _an_man | Lives: 5 | Reward: -1

You WON! The word was: 'hangman'
Total Reward: 5.00
Wrong Guesses: 1
Repeated Guesses: 0
```

---

## How to Run
1. Copy the full Python code into a file named `hangman_hmm_demo.py` or a Jupyter Notebook cell.
2. Run the file using Python 3.8+ or execute the cell in Jupyter.
3. The script will automatically:
   - Initialize a Hangman environment
   - Print letter probabilities and guesses
   - Display the game progression and results

---

## Future Enhancements
- Integrate with a real HMM model (trained on character sequences)
- Replace fixed guesses with a reinforcement learning agent
- Add dynamic word difficulty selection
- Enable user input mode for manual play
