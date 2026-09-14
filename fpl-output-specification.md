# FPL output specification

How the weekly output must be built. A worked example is in the project files as
`gw5-test.html` — match that structure.

---

## Part A — the chat message

Two sections of bullets, nothing else. No table in the chat, no restating the file.

**Section 1 — Transfers.** One bullet per option, ranked best to worst, each naming the move,
the price, the projected gain, and one or two sentences on why. Refer to the move number in
the table rather than reproducing its numbers. Include rolling the transfer as an option
whenever it is competitive. Add a Google Images link for every player recommended in.

**Section 2 — Everything else.** One bullet each for:
- captain and vice, with the case for the alternative if it is close
- who comes into the eleven and who drops out
- bench order, with the reason if auto-substitution legality drove it
- whether to play a chip this week, and what is pencilled in next
- one line on the four-gameweek outlook where it changes this week's decision — a player whose
  run falls apart, or a transfer worth delaying

Close with one line naming the assumption most likely to be wrong.

---

## Part B — the HTML file

Five sections, in this order. No scenarios section.

### 1 · Transfer comparison
Three rows per move — out, in, difference — ranked best to worst. The move number cell spans
all three rows and carries the projected gain to the starting eleven beneath it. A verdict
cell also spans all three rows. Columns: player with club and position beneath, xPts, last-4
average, starts out of 4, price, xPts per £m, ownership.

### 2 · Lineup
Exactly three rows, plus a fourth only when the formation changes away from 3-5-2.
- **Captain & vice** — one row, showing both, with the previous pairing beneath
- **In and out** — one row, who enters the eleven and who leaves
- **Bench structure** — one row, the full order
Columns: decision, change, effect in points, reason.

### 3 · Squad and candidates
All 15 players plus every transfer candidate from section 1, candidates highlighted in green
with a left border. Sorted by xPts descending by default. Columns:
- Player — name, with club and position in smaller text beneath
- Role — XI, B1, B2, B3, B GK, or IN
- xPts — one decimal
- Spread ±1 SD — a horizontal band on a fixed 0–14 scale with faint gridlines at 25/50/75%,
  the low and high values labelled at each end in small text, and a dark vertical tick at the
  projection. No number repeated at the end of the bar.
- Last 4 average — one decimal
- Starts — out of 4
- Opponent — club and home or away, with league position, goal difference and
  win/draw/loss percentages in smaller text beneath
- Ownership — one decimal, percent
- Price — one decimal, millions
- xPts per £m — two decimals
- Note — **only where a decision is needed**. Leave blank otherwise. Never fill every row.

Totals row covers the **starting eleven only**, bench excluded, and states the split between
the eleven players and the doubled captain.

### 4 · Chip plan
One row per chip: target window, backstop week, condition. No summary row inside the table —
put the GW19 expiry note in the caption line beneath it.

### 5 · Four-gameweek projection
The next four gameweeks from the current one, as **per-gameweek averages** across that window.
Same 15 players plus the same transfer candidates from section 1, candidates highlighted.
Sortable, sorted by xPts descending by default.

Horizon is four **gameweeks**, not four calendar weeks — international breaks mean these are
not the same thing.

Columns, mirroring section 3 with two changes:
- Player — name, club and position beneath
- Role — XI, B1, B2, B3, B GK, or IN
- xPts — averaged per gameweek across the window, one decimal
- Spread ±1 SD — same fixed 0–14 band, built on the averaged projection
- Last 4 average — one decimal, same as section 3
- Starts — out of 4, same as section 3
- **Fixtures** — replaces the opponent column. All four opponents with home or away
  (`BHA(A) LEE(H) NFO(A) EVE(A)`), with average FDR and the number of home games in smaller
  text beneath. Name the single hardest or most decisive fixture there if one stands out.
- Ownership, Price, xPts per £m — as section 3
- Note — only where a decision is needed across the window, such as a sell point, a fixture
  swing, or a player who becomes startable later. Leave blank otherwise.

Totals row covers the starting eleven only, giving the per-gameweek XI projection, the squad
average FDR across the window, and the projected cumulative total over the four gameweeks.

This section is where the multi-week thinking lands: it should make visible when a player's
run deteriorates, when a transfer can wait, and which gameweek a chip is being aimed at.

---

## Part C — table behaviour

- **Frozen first column.** The player or row-label column stays fixed when scrolling sideways.
- **Horizontal scroll only, inside the table.** Set `overflow-x: auto` and `overflow-y: visible`
  on the wrapper. Do **not** set a max-height and do not allow a vertical scrollbar inside any
  table — every table renders at its full natural height so the page scrolls vertically, not
  the table.
- **Give the transfer comparison and lineup sections enough vertical room** that they never
  clip; they are short tables and should sit fully visible within the page flow.
- **Consequence to accept:** without a vertical scroll container a sticky header row cannot
  work, so the header scrolls away with the page. The frozen first column still works.
- **Sortable columns** on the squad table: clicking a header sorts ascending, clicking again
  descending, with an arrow indicator. Numeric cells carry a `data-v` attribute holding the
  raw value so sorting uses numbers rather than displayed text. The transfer comparison,
  lineup and chip tables are not sortable, since their rows are grouped.
- Colour: green for transfer candidates coming in, muted warm grey for players going out,
  green and red only for positive and negative deltas. Keep it quiet.
- One decimal everywhere except xPts per £m, which takes two.

---

## Part D — delivery

Write the file to the outputs folder and present it so I get a file card I can open. A file
that is written but not presented is unreachable on mobile. Name it `gw{n}.html`.
