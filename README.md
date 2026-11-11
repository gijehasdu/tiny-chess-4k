# tiny-chess-4k

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/gijehasdu/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/gijehasdu/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A complete chess engine in 4,044 bytes of Python (`main.py`, the whole file).
0x88 board, alpha-beta search with PVS, a transposition table, null-move
pruning, late-move reductions and check extensions, plus capture quiescence
with delta pruning. Evaluation is incremental material + piece-square tables
with a tapered king, bishop pair and passed-pawn bonuses. The readable source
is minified, lzma-compressed and base85-encoded into the single file; the stub
at the top unpacks and runs it. Fully deterministic: a fixed node budget
(40,000 nodes per move), no clock, no randomness — same position and history,
same move, every time.

## Engine notes

- Move generation is fully legal (no pseudo-legal leakage into search):
  castling through check, en passant pins and king safety are all resolved
  inside the make-move step, and the generator is perft-verified against
  the standard test positions.
- Search extras beyond plain alpha-beta: principal-variation search,
  transposition table with mate scores stored relative to the root,
  null-move pruning guarded against zugzwang-heavy endgames, late-move
  reductions on quiet moves, and a one-ply extension when in check.
- Repetition is handled with a position-count table fed by the game
  history the environment sends, so the engine will take a draw it is
  owed and avoid offering one it is not.

## Run it

```sh
MAKEFUN_ENV_URL=<env-url> python3 -P -s main.py
```

---
<sub>Entered on [make.fun](https://make.fun/?ref=r990r6j8&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
