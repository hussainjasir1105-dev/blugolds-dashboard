# Blugolds 2025–26: Anatomy of a Collapse

**Live dashboard:** https://hussainjasir1105-dev.github.io/blugolds-dashboard/

The UW–Eau Claire men's basketball team opened 2025–26 at 11–0, then went 3–11 in WIAC conference play to finish 14–11. This project asks what actually separated wins from losses, and what the team could do about it.

## Key findings

- **Season-wide, the gap was defensive.** Opponents shot 45.0% eFG in wins and 57.7% in losses, while UWEC's own shooting barely moved (54.6% vs 52.5%).
- **In conference play, it was about possessions.** A Four Factors driver model shows that the offensive-rebound and turnover battles explain most of the WIAC win/loss gap, while opponent shooting explains only about a fifth of it.
- **Games were decided early.** UWEC went 13–2 when leading at halftime and 1–9 when tied or trailing.
- **Player splits are about production per minute, not playing time.** Xavier Lewis played the same minutes in wins and losses but produced about a third less per minute in losses.

## What's in the dashboard

| Section | What it shows |
|---|---|
| Season strip | Final margin of all 25 games |
| How the stats connect | The four drivers and how each leads to the next |
| Driver model | Waterfall splitting the 45.8-point net-rating gap into Four Factors contributions (R² = 97.6%) |
| Drivers 1–4 | Defense, rebounding, halftime and shot selection, each with a gap-size meter, p-value and WIAC check |
| Every stat, ranked | ~20 stats ranked by gap size, with permutation-test p-values and Benjamini–Hochberg q-values |
| Game log | Sortable, filterable heatmap of 13 stats across all 25 games |
| In-depth report | A long-form write-up with methods, limitations and recommendations |

## Methods

- **Data:** official box scores and play-by-play for all 25 games, compiled into a game-level workbook. Player rows sum exactly to official team totals, and play-by-play scoring reconciles to every final score.
- **Gap size:** (average in wins − average in losses) ÷ standard deviation across games.
- **Significance:** permutation test (5,000 shuffles of the win/loss labels, fixed seed), then a Benjamini–Hochberg adjustment for testing many stats at once.
- **Robustness:** every stat is re-checked on WIAC games only, to separate real factors from schedule effects.
- **Driver model:** least-squares regression of net rating on the Four Factors; each factor's contribution = weight × (average in wins − average in losses).

## Limitations

- 25 games (only 3 WIAC wins), so conference-only findings are suggestive, not proven.
- Opponent strength isn't adjusted beyond the WIAC-only check.
- The analysis shows which factors move with winning, not proof that they cause it.

## Repository contents

```
index.html              The dashboard and report (self-contained; open it in any browser)
data/games.json         One row per game: results, margins, Four Factors, ratings and more
data/player_games.json  One row per UWEC player per game
```

All statistics are computed in the browser from the files in `data/`. View the page source to see every calculation.

## Tools

Data collection and workbook built in Excel. Dashboard built with HTML, CSS and D3.js, developed with the help of Claude (an AI assistant) for the visualization code and for stress-testing the analysis.

---
*Analysis by Jasir, UW–Eau Claire.*
