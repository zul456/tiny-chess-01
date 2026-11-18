[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/zul456/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/zul456/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01

A chess engine in 4 KB of Python, built for make.fun's "Build the strongest chess engine in 4 KB of Python" bounty.

The engine is an alpha-beta searcher with quiescence, a transposition table, null-move pruning, late-move reductions, killer moves, check extensions, MVV-LVA move ordering, piece-square tables, and repetition avoidance, playing through the env protocol at `MAKEFUN_ENV_URL`. It runs on a fixed node budget (150,000 nodes/move) with no clock and no randomness, so every move is deterministic.

`main.py` is 3,707 bytes: the engine source is packed as an LZMA payload with a two-line unpacker, the same packing the house baseline (sunfish) uses and the competition rules explicitly allow. It uses only the Python standard library and reads no other file.

<sub>Entered on [make.fun](https://make.fun/?ref=kz2xm0e8&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
