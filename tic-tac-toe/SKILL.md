---
name: tic-tac-toe
description: Play and evaluate an interactive 3×3 Tic-Tac-Toe game between a user and the model. Use for conversational games, move analysis, and post-game evaluation; not for building a game application.
---

# Tic Tac Toe

Run a clear, stateful game of standard 3×3 Tic-Tac-Toe. The user and model alternate marks; three equal marks in a row, column, or diagonal wins.

## Start and display

- Ask the user to choose `X` or `O` only if they have not specified it. `X` moves first.
- Use positions `1`–`9`, left to right and top to bottom, so a user can reply with a single number. In every board display, show an unoccupied cell's position number and replace it with `X` or `O` after it is played.
- After every accepted move—whether it is the user's or the model's—render the current board in this monospaced 3×3 layout, identify whose turn it is, and retain the full move history:

  ```text
   X | 2 | O
  ---+---+---
   4 | X | 6
  ---+---+---
   7 | 8 | 9
  ```
- Reject an invalid, occupied, or out-of-turn move without changing the board, then ask for a legal position.

## Model play

Play optimally unless the user explicitly asks for a difficulty level, teaching mode, or a deliberately casual game. Never claim randomness or use a move that allows a forced loss when a drawing or winning move is available.

For each turn, select a legal move using this priority:

1. Take an immediate win.
2. Block the opponent's immediate win.
3. Choose a move that preserves a forced win; otherwise, one that guarantees a draw.
4. If several moves are equally good, prefer the center, then a corner, then an edge, and mention only a brief rationale if the user asked for explanation.

## End and evaluate

After each move, check all eight winning lines and then check whether the board is full. Once the game ends, state the result and do not accept further moves unless the user starts a new game.

When the user wins, print this celebration after the final board and result:

```text
  \o/  Congratulations — you win!
   |
  / \\
```

When the model wins, print this sad face after the final board and result:

```text
  .-.
 ( :-( )
  `-'
```

For a draw, state that the game is a draw without either outcome ASCII.

Offer or provide an evaluation when requested. Include the final result, move list, decisive tactical moment (or why perfect defense produced a draw), and concise feedback for both sides. Judge moves relative to optimal play at that position; label an inferior move as a mistake only when it loses a forced win or changes a forced draw into a loss. If the user asks for a detailed evaluation, identify better legal alternatives and their likely outcome.
