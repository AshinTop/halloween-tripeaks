[English](README.md) | [简体中文](README.zh-CN.md) | [Español](README.es.md) | [Português (Brasil)](README.pt-BR.md) | [日本語](README.ja.md)

# 🎃 Trick-or-Treat TriPeaks — Halloween Solitaire with Moon Bridges

**Three towers, a trail of sweets, and one well-timed moonlit shortcut.** Trick-or-Treat TriPeaks is a Halloween solitaire game made for [FreeCell Game](https://freecell-game.top/). Link higher-or-lower cards, clear the peaks, and earn a Moon Bridge to rescue a difficult chain. Original black-cat Jacks, witch Queens, and pumpkin Kings make the table feel like a small autumn celebration.

**[Play online](https://halloween-tripeaks.crazy3d.org/)** · [All Halloween games](https://github.com/AshinTop/halloween-games) · [Embedding guide](EMBEDDING.md) · [Design notes](DESIGN.md)

**Document languages:** English, 简体中文, Español, Português (Brasil), 日本語. **Game interface:** English and Simplified Chinese only; the other README languages do not add in-game translations.

![Halloween TriPeaks solitaire showing three card peaks, stock, waste and a Moon Bridge meter](docs/images/gameplay.jpg)

## In the deck 👻

- A complete **52-card deck**: 28 cards in the peaks, 23 in the stock, and one starting waste card.
- **Eight Journey deals**, each with a verified winning route requiring no stock draws.
- Reproducible Classic shuffles and a daily challenge based on UTC.
- Limited Moon Bridges, undo, legal-move hints, stars, local saves, and optional synthesized sound.

## How to clear the peaks

Remove an uncovered card that is one rank higher or lower than the waste card. The removed card becomes the new waste. Suits and colors do not matter, and Aces connect to Kings: **K–A–2** is valid. A card remains covered until every card resting on it has been removed. Clear all 28 peak cards to win.

Draw from the stock whenever you choose. Drawing resets the chain. The 23 stock cards are used once, with no redeal. A loss requires all three conditions: the stock is empty, no uncovered card fits, and no Moon Bridge remains.

Five consecutive normal removals can earn a **Moon Bridge**. Hold one at a time and earn at most two per deal. Select the bridge, then any uncovered card: its rank no longer matters. Covered cards remain unavailable. Using a bridge resets the chain; selecting the bridge again cancels the selection. Undo restores cards, stock, score, and magic.

Normal removals score 10 points plus the current chain × 5. Removing a peak’s top card adds 50 points. A bridge removal scores the 10-point base plus any peak bonus. A win earns three stars with no stock draws, two with at most five, and one otherwise. There is no timer.

## Controls

| Action | Input |
|---|---|
| Remove a card | Click / tap, or Tab then Enter |
| Draw | Stock pile; Space outside a button or input |
| Use magic | Moon Bridge, then an uncovered card |
| Undo | Z or Undo |
| Highlight a legal step | Spot a Move |
| Replay or change mode | Restart and the mode selector |

**Spot a Move checks the next legal action; it is not a full solver.** A playable card does not guarantee a future win.

## Choose and share a deal

[Journey 1](https://halloween-tripeaks.crazy3d.org/?level=1) begins the authored campaign. [Classic seed 12345](https://halloween-tripeaks.crazy3d.org/?mode=classic&seed=12345) shares a shuffle; selecting Classic again creates another, while Restart replays the current one. [A dated daily deal](https://halloween-tripeaks.crazy3d.org/?mode=daily&date=2026-10-31) preserves its exact UTC date.

Current play, best results, and preferences are saved locally. Explicit URL parameters start the requested deal. Undo history lasts for the page session.

## FAQ

**Is every deal solvable?** The eight Journey deals have tested solutions. Shuffled Classic and Daily deals are not guaranteed to be solvable.

**Can a Moon Bridge remove a covered card?** No. It changes rank matching only; the covering rule still applies.

**Can I recycle the stock?** No. Draw timing, long chains, and bridge management are the main decisions.

## See the game

![Compact TriPeaks iframe with readable card corners, waste pile and Moon Bridge controls](docs/images/mobile.jpg)

Actual game interface in a compact browser iframe. This illustrates the layout; it is not a physical-phone performance test.

[Watch the 24-second introduction](https://halloween-tripeaks.crazy3d.org/intro.html) · [Download the captioned MP4](docs/media/intro.mp4). This silent visual tour is assembled from actual game screenshots, not a continuous gameplay recording. The screenshots and video show captured interface states and may predate later visual refinements.

## Embed it on your site

```html
<iframe src="https://halloween-tripeaks.crazy3d.org/"
  title="Trick-or-Treat TriPeaks"
  style="display:block;width:100%;height:654px;border:0"
  allow="fullscreen" allowfullscreen></iframe>
```

Cards adapt to the available player area, including desktop, narrow portrait and short landscape layouts. Use a real iframe height; the upper card corners need enough space to read. The game does not access the parent document or require a microphone, camera or pointer lock.

The live site uses Cloudflare and is deployed from this GitHub repository. Give the iframe a real height and leave space for the host toolbar. Fullscreen may be provided by the host. See [EMBEDDING.md](EMBEDDING.md) for the integration contract.

## Run locally and check the rules

```sh
python3 -m http.server 4173
```

Serve the repository root, then open [http://localhost:4173/](http://localhost:4173/). The game is static: no build or dependency installation is needed. Use HTTP(S), because direct `file://` access can block ES modules. Node.js is required for the tests.

```sh
npm test
```

The **12 tests** cover all eight Journey solutions, deck uniqueness, card coverage, Ace/King wrapping, stock use, bridge earning and limits, exact loss conditions, reproducible shuffles, date links, and saved-data validation.

The game source does not require an account, remote API, advertising SDK, or external asset CDN. Records stay in browser storage; there is no cloud sync. Cloudflare may add its own hosting scripts and request logs. Optional synthesized audio follows browser sound permissions.

## More moonlit adventures 🍬

- [Haunted FreeCell](https://halloween-freecell.crazy3d.org/) · [Source](https://github.com/AshinTop/halloween-freecell) — Classic FreeCell and Lantern Rescue endgames.
- [Pumpkin Shift](https://halloween-pumpkin-shift.crazy3d.org/) · [Source](https://github.com/AshinTop/halloween-pumpkin-shift) — Number-sliding rooms with Moon Glides.
- [Witch’s Candy Blocks](https://halloween-block-blast.crazy3d.org/) · [Source](https://github.com/AshinTop/halloween-block-blast) — 8×8 candy-block placement.
- [Pumpkin 2048](https://halloween-2048.crazy3d.org/) · [Source](https://github.com/AshinTop/halloween-2048) — Classic merging and Lantern Trials.

## Credits and a little support

Created for **AshinTop’s Midnight Candy Club** through human-directed AI collaboration in design, programming, writing, testing, and review. The original artwork and synthesized sounds were made for this project. [Design notes](DESIGN.md) explain its intent.

Enjoyed this little adventure? **[Star Trick-or-Treat TriPeaks on GitHub](https://github.com/AshinTop/halloween-tripeaks)** to save it for later and follow updates. Useful issue reports include the game mode or level, browser, window size, and steps that reproduce the problem. Explore the [complete Halloween collection](https://github.com/AshinTop/halloween-games).
