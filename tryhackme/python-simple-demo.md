# TryHackMe: Python: Simple Demo

Pre Security path, Software Basics module. Completed September 2026.

**Situation:** Build a "Guess the Number" game in Python (`guess_v1.py`, `guess_v2.py`, `guess_v3.py`) on a VS Code lab VM.

**Task:** Run each version, understand how it works, and answer the task questions.

**Action:**

- **Task 2, variables:** `random.randint` picks the secret number; `tries` counts attempts; `guess` starts as a placeholder of 0; `print()` displays output; `input()` returns a string, so `int()` converts it to a number.
- **Task 3, conditionals:** `if` / `elif` / `else` (`elif` means "else if"). A guess outside the allowed range prints an error message and prompts again.
- **Task 4, while loop:** `while guess != secret` keeps asking until the guess is correct. Indentation defines the loop body. A correct guess prints how many tries it took.

**Result:** Completed the room, including all three versions of the game.

## Key terms

variable, string vs integer, `input()`, `int()`, `print()`, `random.randint(a, b)`, `if` / `elif` / `else`, `!=` operator, while loop, iteration, indentation
