# Tic-Tac-Toe skill

Play a 3×3 Tic-Tac-Toe game against Codex. The board is reprinted after every move: unused cells retain their position numbers, while played cells show `X` or `O`. The skill also evaluates the game when asked.

## Use in Codex

Start Codex in a project directory, then ask:

```text
Use $tic-tac-toe. I will play X.
```

Reply with a board position from `1` to `9` on each turn. For example:

```text
5
```

At the end, ask for `Evaluate the game` to receive the move history and tactical feedback. A user win prints a congratulatory ASCII celebration; a model win prints a sad face.

## Run with `codex exec`

For a one-off non-interactive run, invoke the skill in the task prompt:

```bash
codex exec "Use the \$tic-tac-toe skill. Start a 3×3 Tic-Tac-Toe game; I play X. Show the numbered grid after every move and evaluate the game when it ends."
```

`codex exec` runs a single task prompt, so a live multi-turn game is best played in interactive Codex. Use `codex exec` for a scripted request, a move-analysis request, or a single-run evaluation.
