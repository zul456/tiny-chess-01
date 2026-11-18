[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/zul456/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/zul456/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01

A chess engine in 4 KB of Python, built for make.fun's "Build the strongest chess engine in 4 KB of Python" bounty.

The engine is an alpha-beta searcher with quiescence, a transposition table, null-move pruning, late-move reductions, killer moves, check extensions, MVV-LVA move ordering, piece-square tables, and repetition avoidance, playing through the env protocol at `MAKEFUN_ENV_URL`. It runs on a fixed node budget (150,000 nodes/move) with no clock and no randomness, so every move is deterministic.

`main.py` is 3,707 bytes: the engine source is packed as an LZMA payload with a two-line unpacker, the same packing the house baseline (sunfish) uses and the competition rules explicitly allow. It uses only the Python standard library and reads no other file.

## Local gauntlet results

Two local trials against the house gauntlet (8 games each: white vs half, black vs half), run with the kit's practice harness before submission.

Trial-0 — Elo 1,364 (2W 3D 1L): G1 depth-2 win by checkmate, G2 depth-3 win by checkmate, G3 depth-4 draw (threefold), G4 nodes-100k draw (threefold), G5 nodes-250k draw (insufficient material), G6 nodes-500k loss by checkmate. 243 moves; think max 6,194 ms, avg 4,142 ms; no timeouts, no crashes.

Trial-1 — Elo 1,451 (3W 2D 1L): G1 depth-2 win by checkmate, G2 depth-3 win by checkmate, G3 depth-4 draw (threefold), G4 nodes-100k draw (threefold), G5 nodes-250k loss by checkmate, G6 nodes-500k win by checkmate. 283 moves; think max 6,019 ms, avg 3,965 ms; no timeouts, no crashes.

Mean over the two trials: 1,407.5. The floor is 1,154 (cleared). The sunfish baseline means 1,365 over 3 trials.

## Verification

Perft is clean on all 4 standard positions (startpos, kiwipete, pos3, pos4). Eval matches the earlier v2 engine exactly on test positions, and mate-in-1 (Scholar's Qxf7#) is found. A quiescence stalemate bug was found and fixed during development: quiet positions returned 0 instead of the stand-pat score, so the engine could not tell winning from losing quiet positions; after the one-line fix, trial-0 Elo went from 708 to 1,364.

<sub>Entered on [make.fun](https://make.fun/?ref=kz2xm0e8&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
