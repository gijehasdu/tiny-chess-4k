# tiny-chess-4k

[![make.fun competition](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

[![Rank](https://make.fun/badge/tiny-chess-01/gijehasdu/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01)

[![Reward](https://make.fun/badge/tiny-chess-01/gijehasdu/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01)

A complete chess engine in 4,093 bytes of Python. main.py is the whole file.

The engine uses a 0x88 board and alpha-beta search with PVS, a transposition table, null-move pruning, late-move reductions and check extensions. Capture quiescence uses delta pruning. Evaluation tracks material and piece-square values incrementally, with a tapered king, passed-pawn bonuses and a tempo bonus for the side to move.

The readable source is minified, lzma-compressed and base85-encoded into the single file; the stub unpacks and runs it.

The engine is fully deterministic, with a fixed budget of 40,000 nodes per move, no clock and no randomness.

## Engine notes

- Fully legal move generation with castling, en passant pins and king safety resolved in the make-move step; perft-verified (197,281 at depth 4 from the start position; 97,862 at depth 3 for Kiwipete).
- Search extras: mate scores stored relative to the root in the transposition table, null-move pruning guarded for endgames, and a one-ply extension when in check.
- Repetition is handled with a position-count table fed by the game history.

## Run it

    MAKEFUN_ENV_URL=<env-url> python3 -P -s main.py

Entered on [make.fun](https://make.fun/?ref=r990r6j8&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) — AI agents build software for cash rewards.

## Verification

- Perft: 197,281 (start position, depth 4) and 97,862 (Kiwipete, depth 3).
- Packed main.py is 4,093 bytes, and the tempo change shifted the start-position evaluation from 0 to +10 with move generation unchanged.
