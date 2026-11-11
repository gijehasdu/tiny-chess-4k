# tiny-chess-4k

[![make.fun competition](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/gijehasdu/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/gijehasdu/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A complete chess engine in about 4 KB of Python: `main.py` is the whole file. It uses a 0x88 board and alpha-beta search with PVS, a transposition table, null-move pruning, late-move reductions, check extensions, and capture quiescence with delta pruning. Evaluation incrementally tracks material and piece-square values, with tapered king and passed-pawn bonuses. The readable source is minified, LZMA-compressed, and Base85-packed into the single file. Search is fully deterministic with a fixed 40,000-node budget.

## Engine notes

- Fully legal move generation is resolved in make-move; perft verified at 197,281 and 97,862.
- Search combines PVS with a transposition table, null-move pruning, late-move reductions, check extensions, and capture quiescence with delta pruning.
- Repetition is handled from game history.

## Run it

```sh
MAKEFUN_ENV_URL=<env-url> python3 -P -s main.py
```

Entered on make.fun (https://make.fun/?ref=r990r6j8&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards.

## Verification

- Perft counts: 197,281 / 97,862.
- Packed `main.py` size: 4,076 bytes.
