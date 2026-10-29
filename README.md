# Trick-or-Treat TriPeaks — Halloween Card Game with Moon Bridges

**Three towers. One moonlit trail.** Trick-or-Treat TriPeaks is a Halloween solitaire game built around familiar higher-or-lower card chains. Clear the three peaks, keep a candy combo alive, and save a Moon Bridge for the moment your path runs out.

[**Play online**](https://halloween-tripeaks.crazy3d.org/) · [Watch the visual introduction](docs/media/intro.mp4) · [Rules](#how-to-play-tripeaks) · [Embed the game](#embed-halloween-tripeaks)

**Live deployment:** Play on Cloudflare using the link above. The site is deployed from this GitHub repository. Hosting scripts and request logging may be added by Cloudflare independently of the game code.

[Video player and transcript](https://halloween-tripeaks.crazy3d.org/intro.html) · [Captioned MP4 file](docs/media/intro.mp4). The 24-second silent introduction uses actual game screenshots; it is not a live gameplay recording.

[![Halloween TriPeaks gameplay showing three card peaks, a stock pile, the current waste card, and a Moon Bridge meter](docs/images/gameplay.jpg)](docs/media/intro.mp4)

If you enjoy the card game or want to follow its development, **[star this repository](https://github.com/AshinTop/halloween-tripeaks)**. Reproducible reports with a journey number or shuffled-deal seed are particularly useful.

## What's in the deck?

- **A complete 52-card game:** 28 cards form the peaks, 23 form the stock, and one starts the waste pile.
- **Traditional higher-or-lower matching:** remove uncovered cards one rank above or below the waste. Suits do not matter, and Ace connects to King.
- **Moon Bridges:** earn a limited wildcard-like move through consecutive removals, then spend it on any uncovered card.
- **Eight Journey deals:** each fixed rescue challenge has a verified 28-removal route with no stock draws.
- **Classic shuffled deals and a daily challenge:** reproducible seeds and dates make it easy to share a starting position.
- **Undo, restart, legal-move hints, scoring, and stars.**
- **Local persistence**, English and Simplified Chinese, optional synthesized sound, and mouse/touch/keyboard controls.
- **Original Halloween card faces:** black-cat Jacks, witch Queens, and pumpkin Kings on a muted green card table.

Made for [FreeCell Game](https://freecell-game.top) and the Midnight Candy Club collection, TriPeaks offers a different rhythm from FreeCell: short card chains, changing visible choices, and carefully timed stock draws.

## How to play TriPeaks

### Clear the three towers

A card is available only when no remaining card covers it. Remove an available card if its rank is one higher or one lower than the top waste card. That removed card becomes the new waste card.

For example, a 7 can connect to a 6 or an 8. Aces wrap around to Kings, so **K–A–2** is legal. Card color and suit do not affect matching. Clear all 28 tableau cards to win.

### Draw a new path

You may draw the next stock card whenever you choose. The stock has 23 cards and is used once; there is no redeal. Drawing resets the candy chain.

A deal ends when the stock is empty, no uncovered card fits, and no Moon Bridge remains. A full stock or an available bridge means there is still an action you can try. The result screen allows Undo or another attempt.

### Earn and spend Moon Bridges

Five consecutive normal removals without drawing can earn a bridge. You can hold **one at a time** and earn **at most two per deal**. Select Moon Bridge, then select any uncovered card to remove it regardless of rank.

A bridge does not invent an extra card or reveal a covered card. It moves an existing exposed card to the waste, spends the bridge, and resets your chain. Select the bridge again to cancel before choosing a card. Undo restores the complete previous state, including its stock and magic resources.

## Scores and stars

| Event | Result |
| --- | --- |
| Normal card removal | 10 points + current chain × 5 |
| Remove a peak's top card | An additional 50 points |
| Use a Moon Bridge | Chain resets; the removal scores the 10-point base, plus a peak bonus if applicable |
| Win without drawing | Three stars |
| Win with at most five stock draws | Two stars |
| Any other completed deal | One star |

There is no timer pushing you to choose quickly. Plan a longer chain, use a bridge to rescue a route, or replay a fixed deal to improve your result.

## Three ways to play

**Journey** contains eight named, fixed deals. Each one uses a complete nonduplicated deck and has a tested solution requiring no stock draws. You can choose any journey from the selector.

**Classic** shuffles a full deck from a numeric seed. Selecting Classic again starts a fresh shuffle; Restart restores the same deal. Random classic deals are **not guaranteed to be solvable**.

**Daily** uses the UTC calendar date as its seed. Everyone opening the same date receives the same shuffled deal. Daily deals follow the same rules and are also not guaranteed to be solvable.

## Controls

| Action | Input |
| --- | --- |
| Remove an available card | Click/tap it, or use Tab and Enter |
| Draw from the stock | Click/tap the stock; Space when focus is outside a button/input |
| Use magic | Select Moon Bridge, then an uncovered card |
| Undo | **Z** or Undo |
| Highlight a legal card | Spot a Move |
| Replay the current layout | Restart |
| Help, language, sound | Header buttons |

**Spot a Move is a legal-step helper, not a full solver.** A highlighted card can be played now, but the hint does not guarantee that this choice leads to a win.

## Share a reproducible deal

- [Journey 1](https://halloween-tripeaks.crazy3d.org/?level=1)
- [Journey 8](https://halloween-tripeaks.crazy3d.org/?level=8)
- [Classic seed 12345](https://halloween-tripeaks.crazy3d.org/?mode=classic&seed=12345)
- [Today's challenge](https://halloween-tripeaks.crazy3d.org/?mode=daily)
- [October 31, 2026 daily deal](https://halloween-tripeaks.crazy3d.org/?mode=daily&date=2026-10-31)

The Share button copies the chosen journey, seed, or exact daily date. If clipboard access is blocked, a selectable link appears. Explicit daily dates are validated as real calendar dates.

## Frequently asked questions

### Are all eight Journey deals really solvable?

Yes. Each has an executable full solution exposed to the test suite by `journeyDeal(index).solution`. The tests play all 28 removals and verify that the full deck remains valid throughout. This guarantee applies to the authored Journey deals, not every shuffled Classic or Daily deal.

### Why can't I select a covered card?

It still has at least one card resting on it. Remove both covering cards to expose it. Moon Bridge ignores rank, not the covering rule.

### Can I recycle the stock?

No. The 23 stock cards are drawn once. This makes draw timing and available bridges meaningful choices.

### What is saved between visits?

Current play, best results, language, and sound preference are stored locally when browser storage is available. Explicit URL parameters start the requested deal instead of restoring a different saved one. Undo history lasts for the page session. There is no account or cross-device synchronization.

### Can I play on a phone or embed this on my own page?

The game supports tapping and computes card size from the available player area. Desktop and short landscape layouts use a side panel; narrow portrait layouts move the tools above the peaks. See [EMBEDDING.md](EMBEDDING.md) for integration notes. Responsive viewport review does not certify every physical phone or browser.

### Does the game use downloaded card images or audio?

No. Card art is SVG created for the project. Sound is synthesized locally and starts only after it is enabled. There are no runtime CDN assets or external game-player dependencies.

## Run locally and verify

Serve this repository over HTTP:

```sh
python3 -m http.server 4173
```

Open [http://localhost:4173](http://localhost:4173). No build or dependency installation is needed. JavaScript modules may be restricted if you open `index.html` through `file://`.

Run the tests with Node.js:

```sh
npm test
```

For the full list of individual checks:

```sh
node tests/engine.test.js
```

The **12 checks** cover all eight Journey solutions, deck uniqueness, cover relationships, Ace/King wrapping, stock behavior, bridge earning and limits, exact loss conditions, deterministic shuffles, corrupt saved data, bounded URL parameters, and calendar-date sharing.

## Compact-player walkthrough

![Halloween TriPeaks in a compact host iframe, with the three peaks, waste card and Moon Bridge controls](docs/images/mobile.jpg)

Read the exposed card ranks, compare them with the waste card, and tap a rank one higher or lower. The narrow layout prioritizes a readable upper card corner. Use the stock when you need a new rank, or save a Moon Bridge for a difficult choice.

*Actual interface captured in a browser iframe sized for the host player. This is a compact-window illustration, not a physical-phone test.*

## Embed Halloween TriPeaks

```html
<iframe
  src="https://halloween-tripeaks.crazy3d.org/"
  title="Trick-or-Treat TriPeaks — Halloween card game"
  width="100%"
  height="654"
  scrolling="no"
  allow="fullscreen"
  style="display:block;border:0"
></iframe>
```

Allocate a real player area after accounting for any parent toolbar. The game automatically resizes its cards and does not access the parent document. It needs scripts, but not a camera, microphone, pointer lock, or automatic audio playback. See [EMBEDDING.md](EMBEDDING.md) for complete guidance.

## Source guide

- `engine.js` — full-deck rules, cover graph, deterministic deals, score, bridge resources, validation.
- `app.js` — card rendering, input, localization, storage, sound, and sharing.
- `index.html`, `style.css`, `icon.svg` — original interface and Halloween artwork.
- `tests/engine.test.js` — executable game and data-validation checks.
- [DESIGN.md](DESIGN.md) — the intended experience, scoring, and fairness decisions.

## More Halloween games

- **[Haunted FreeCell](https://halloween-freecell.crazy3d.org/)** · [Source](https://github.com/AshinTop/halloween-freecell) — full-deck FreeCell and three verified Lantern Rescue endgames.
- **[Pumpkin Shift](https://halloween-pumpkin-shift.crazy3d.org/)** · [Source](https://github.com/AshinTop/halloween-pumpkin-shift) — 12 sliding-number rooms with limited Moon Glides.
- **[Witch’s Candy Blocks](https://halloween-block-blast.crazy3d.org/)** · [Source](https://github.com/AshinTop/halloween-block-blast) — place candy shapes, clear rows, and complete potion orders.
- **[Pumpkin 2048](https://halloween-2048.crazy3d.org/)** · [Source](https://github.com/AshinTop/halloween-2048) — classic number merging with a moonlit garden and positional trials.

## Credits

Created for **AshinTop** and **Midnight Candy Club**, with AI-assisted design, implementation, and review. The card faces, table illustration, interface, and synthesized sounds were produced for this project. This is an independent TriPeaks implementation, with no implied endorsement by another solitaire publisher. No analytics, advertisements, payments, or remote leaderboard is included in the game source.
