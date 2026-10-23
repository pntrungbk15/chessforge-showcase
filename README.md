# ChessForge

**A 3D chess game and chess workstation for Windows and Linux.**
- Play on five sculpted piece sets with their own shapes, six boards and five arenas, with sound and music, or follow a twelve-mission campaign.
- Play a friend on one computer: the camera glides around the table to whoever is to move.
- Collect piece sets, boards and arenas with coins earned in play.
- Analyse with Stockfish, train with puzzles and drills, keep a game library, and train your own neural network: AI training sets itself up from one button.

Built with [FluentQt](https://github.com/pntrungbk15/fluentqt-showcase) on PyQt5.

![Portfolio](https://img.shields.io/badge/portfolio-showcase_only-1F3A5F)
![Source](https://img.shields.io/badge/source-private-6B6B6B)
![Qt](https://img.shields.io/badge/Qt-PyQt5_5.15-41CD52)
![PyTorch](https://img.shields.io/badge/AI_Lab-PyTorch-EE4C2C)

> **About this repository.** It presents ChessForge through screenshots and a written overview. It contains no source
> code: the application's source is private at this stage.

![A campaign mission on the 3D board against the built-in sparring partner, dark theme, with navigation across the top](assets/chess-mission-3d.png)

| At a glance | |
|---|---|
| **What** | An independent desktop application: a 3D chess game with a campaign and a cosmetic collection, plus analysis, training, a game database and a neural-network lab, all running locally. |
| **3D** | A custom OpenGL 2.1 renderer. Five original piece families sculpted as signed distance functions and baked by a build script; six board styles and five arenas built as geometry at run time; physically based, fully procedural materials with no textures; planar and contact shadows; a camera you can orbit and zoom while picking stays exact. |
| **Sound** | Original effects and music, synthesised by a script (no samples): one sound per event, volumes, quick mute, music that pauses while minimized; the game runs silent without a sound device. |
| **Progression** | Twelve missions judged move by move; a coin ledger whose rows are keyed by the event they pay for, so nothing is paid twice; purchases in one transaction. Coins buy looks only, and there is no way to buy coins in this version. |
| **AI setup** | The app explains in plain words what the computer can do and installs a private PyTorch runtime (processor or NVIDIA CUDA) on request, as a cancellable job that never touches the system and never replaces a working runtime. Intel and AMD graphics are named but not promised as accelerators. |
| **Engine integration** | Stockfish over UCI in its own processes; live multi-line analysis; background game review with an evaluation graph, critical moments and accuracy. |
| **Packaging** | A standalone Windows build compiled with Nuitka and verified by launching it (3D board, window, sound, engine, datasets), packed into a per-user Inno Setup installer; Stockfish and PyTorch are downloaded on request, never bundled. |

## Features

| Area | What it does |
|---|---|
| **3D board** | On by default with hardware OpenGL. Piece sets that differ in shape (Staunton, royal, gothic, ancient, modern), boards that differ in frame and material (bevelled marble, a stepped rim, raised stone tiles, sandstone with dentils and pyramids, a slim metal frame on volcanic glass, rounded walnut) and arenas that differ in architecture, sky and floor (a royal hall, a sunrise terrace, a moonlit grove, a lava-lit forge, a domed observatory). Drag outside the squares to turn the camera, wheel to zoom, C to reset; the camera never moves by itself. Detail and smooth-edges settings for older graphics. |
| **Two players** | After each move the camera travels 180° around the table to the other player (smooth, quick or instant; at once with Reduce motion); the board never moves and input waits for the camera. An optional screen asks the next player to press Continue. |
| **Sound** | Wooden moves, heavier captures, castling, bells for check, promotion and checkmate, phrases for wins, losses and draws, a fanfare for a completed mission, glints for rewards, two calm music pieces. Master, effects and music volumes, mute with Ctrl+M. |
| **Campaign** | Three chapters against named opponents, from a built-in sparring engine to Stockfish level 11; goals are win, do not lose, or hold out for a number of moves; rewards are paid once. |
| **Collection** | Five piece sets, six boards and five arenas in sections, each tile a picture rendered by the 3D board, the selected look previewed live; listed in a FluentQt Pro `CatalogView`. |
| **Play** | Against Stockfish (levels 0–20), the built-in sparring partner (no download), a friend, a model trained in the AI Lab, or engine against engine; clocks with increment, any FEN start, draws, takebacks, rematch. |
| **Analysis** | Live multi-line analysis with the best move drawn as an arrow; **Review game** grades every move in the background and marks the critical moments. |
| **Training** | 2,475 puzzles by theme and rating band, SM-2 spaced repetition of missed puzzles, 3,815 named opening lines to drill, endgame drills against Stockfish. |
| **AI Lab** | "What this computer can do" and **Set up AI training** (processor or NVIDIA GPU, recommended for this computer). Stockfish datasets generated by several engine processes in parallel and committed in chunks; training, self-play and evaluation in a separate process; every job in a persistent queue with progress, pause, resume, cancel and retry. |
| **Desktop** | Opens maximized, then as you left it; navigation across the top (FluentQt Pro `TopNavigationWindow`) with search, mute and Settings at its right end; a splash screen with the real loading steps; a system tray icon. |
| **Accessibility** | Full keyboard play, reduced motion, a high-contrast board, text scaling, light/dark/system theme. |

## The 3D board

![The Staunton set on a marble board with a brass inlay, on a dais in a torchlit hall](assets/chess-3d-arena.jpg)

**Five piece sets with their own shapes:** Staunton, royal, gothic, ancient and modern.

![The five piece sets in line-ups](assets/chess-3d-sets.jpg)

![The knight and the king of each set, close up](assets/chess-3d-family-closeups.jpg)

**Six boards with their own frames and materials:**

![Royal Marble, Midnight Marble, Verdant Stone, Desert Sandstone, Obsidian and Gold, Walnut and Maple](assets/chess-3d-boards.jpg)

**Five arenas with their own architecture, sky and floor:**

![Twilight Keep, Dawn Terrace, Moonlit Grove, Ember Forge and Celestial Observatory](assets/chess-3d-arenas.jpg)

**Two players on one computer:** five frames of the camera turning from White's side to Black's.

![Five frames of the camera's arc around the table](assets/chess-3d-turn.jpg)

| | |
|---|---|
| ![The board at the default camera, mid-opening](assets/chess-3d-board.jpg) | ![White's pieces in front, Black's behind](assets/chess-3d-pieces-white.jpg) |
| The default view in play. | All six Staunton pieces from White's side. |
| ![A selected knight with its legal moves and the last move highlighted](assets/chess-3d-highlights.jpg) | ![The board after the player turned the camera](assets/chess-3d-rotated.jpg) |
| Legal moves, the last move and the selection on light and dark squares. | The camera stays wherever the player puts it. |

![Close-ups of the Staunton knight, king, queen, bishop and rook](assets/chess-3d-closeups.jpg)

Rendered by the application's own renderer at the shader quality it uses on a GPU.

## Screens

![The installed app on Windows 11, maximized: navigation across the top and the 3D board on Intel Iris Xe](assets/chess-installed-windows.jpg)

| | |
|---|---|
| ![AI setup](assets/chess-lab-setup.png) | ![Pass the device](assets/chess-handover.png) |
| **AI setup:** what this computer can do, and the runtimes it can use (here Intel Iris Xe graphics, so the processor runtime is recommended and the NVIDIA one explains why it is not offered). | **Two players:** the board is covered until the next player presses Continue, then the camera turns to their side. |
| ![Collection: boards](assets/chess-collection-boards.png) | ![Sound settings](assets/chess-settings-sound.png) |
| **Collection:** tiles rendered by the 3D board, the selected board previewed live; buying coins is not offered. | **Sound:** mute, master, effects and music volumes. |
| ![Home](assets/chess-home.png) | ![Campaign](assets/chess-campaign.png) |
| **Home:** the next campaign mission first, then quick actions, recent games and training progress. | **Campaign:** chapters, the mission briefing and achievements. |
| ![Analysis](assets/chess-analysis.png) | ![Training](assets/chess-training.png) |
| **Analysis:** live Stockfish lines and a reviewed game. | **Training:** puzzles by theme and rating with hints and progress. |
| ![Library](assets/chess-library.png) | ![AI Lab](assets/chess-lab.png) |
| **Library:** filters, search, tags, collections and a preview (demo players are fictional). | **AI Lab:** a training run with live losses, accuracy and throughput. |
| ![Play](assets/chess-play.png) | ![Command palette](assets/chess-commands.png) |
| **Play:** clocks, move list, captured material and an evaluation bar (2D board). | **Ctrl+K:** the command palette. |

Game-page screenshots use demo progress. The installed app, AI setup, pass-the-device and Sound screens were captured
on Windows 11 with real graphics and sound; the others are drawn offscreen.

## Architecture

```
app           main window: top navigation, lazily built pages, window state
audio         sound effects and music (loaded after the window shows)
game/         game model (PGN tree + cursor), clocks, play controller
engine/       UCI protocol, one process per engine, detection and probing, a built-in sparring engine
progression/  campaign missions and their judge, coin ledger, collection, achievements
analysis/     background game review
rendering/    board view and camera (including the turn between players), 2D renderer, OpenGL 3D renderer,
              piece families, board styles, arenas, finishes
storage/      SQLite schema and repositories (games, collections, runs, training)
training/     puzzle, opening and endgame catalogues, drills, rating, SM-2
ai/           training process and controller, network, MCTS, datasets, AI runtimes, hardware detection
ui/           pages and widgets (FluentQt)
```

The GUI never waits on an engine or on training: Stockfish runs in its own processes and training in a separate
Python process, both reporting progress through throttled updates.

## Performance

Measured with the project's benchmark scripts (medians):

| Measurement | Result |
|---|---|
| Import 10,000 PGN games | 295 ms, worst GUI stall 20 ms |
| Library page at 100,000 games | 1.1 ms (text search 23 ms) |
| Stockfish dataset, depth 8, 4 engine processes through the job queue | 1,119 positions/s, worst GUI stall 17 ms |
| 3D camera turning on Intel Iris Xe, 1320 × 880 window, every look | 16.7 ms per frame (vsync, the display rate) |
| The same, maximized (1500 × 796 board) | 19–21 ms with smooth edges, 16.7 ms with smooth edges off |
| AI runtime setup on Windows 11 (processor), then training a small network | 3–4 minutes once; 100 training steps in under 40 s |

## Availability

There is no public download at this stage. The Windows build (a standalone Nuitka folder packed into a per-user Inno
Setup installer, `ChessForge-<version>-Setup.exe`, 56 MB for version 0.3) is produced and tested privately: installed,
run, set up for AI training and uninstalled. It needs Windows 10 or 11 (64-bit) and, for the 3D board, hardware OpenGL
2.1 such as Intel Iris Xe or any recent GPU.

## Not in this version

Online multiplayer (local two-player only), buying coins (disabled and labelled as a future feature), playtested
difficulty for the campaign, and a test of GPU training on NVIDIA hardware (the processor runtime is tested end to end).

## Author

Phạm Ngọc Trung · [github.com/pntrungbk15](https://github.com/pntrungbk15)

All screenshots © Phạm Ngọc Trung. Shown here for portfolio purposes; no licence to the software is granted by this
repository.
