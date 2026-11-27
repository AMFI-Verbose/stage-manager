# Stage Manager

A single-file stage manager's book for backstage work — prop tracking, a half-round virtual
stage with draggable blocking, typed movement directions the page animates itself, and a
**run board** built to be held in one hand while you call a show.

Open `StageManager.html` in any modern browser. No build step, no server, no dependencies.

## Run board — what to watch during the show

**Run show** is the backstage screen. Everything you need to answer "who should be out there
right now?" sits in one view:

- **Now on stage** — the live floor for the scene you are in: actors as coloured discs at their
  blocking marks, props as small tags. Under it, a row of name chips — tap one to check that
  actor off as they arrive; the disc gets a green ring. `Clear checks` resets the scene.
- **Wings** — everyone who is off stage right now, so you know who is waiting.
- **Standby** — the next cue with its type (SQ / LX / PQ), trigger and duration, plus a **THEN**
  list of the two or three cues after it.
- **Now cueing** — the cue you called, with its note.
- **Next scene** — the oncoming scene's floor plan plus explicit **ENTERS / EXITS** lists,
  so you can catch the changeover before it happens.
- **Called** — the last five cues, as a record.
- **GO** — sticky at the bottom of the screen. `Space` = GO, `Esc` = leave the run.
  `◀ Previous scene` / `Next scene ▶` jump to the neighbouring scene that has cues,
  `↩ Back one cue` steps back a single cue.

Running clock counts from when you entered the run. At the end of the cue list the board flips
to **END OF SHOW** with the total called time.

### Using it on a phone

Open the file in a mobile browser, add it to the home screen, and turn the phone sideways.
Below 720 px the sidebar becomes a scrollable strip along the top and the GO button grows — the
run board is the only view worth using on a small screen.

## What's inside

**Overview** — the run order act by act, with cast calls, per-scene timings and flags for
missing props or unassigned cues.

**Scenes & stage** — a plan view of a half-round floor: flat back wall upstage, arc into the
audience. Actors are coloured discs, props are tags preset along the back wall. Drag either
one and the position saves to that scene.

**Cast & doubling** — enter/exit counts per character, doubling notes per track.

**Props** — quantity, status (Ready / In use / Needs work / Missing / Struck), location, and the
scenes that call them.

**Sound & light** — all SFX and LFX cues, with triggers and durations.

**Cue sheet** — a printable running order; cue numbers are generated per type (SQ / LX / PQ).

## Moving people

Drag a token, or click one and nudge it with the arrow keys (hold Shift for 5% steps).
⌘/Ctrl Z undoes the last move, Delete sends the selected actor to the wings.

Better still, type the blocking into **Movement directions** and press **Run moves**
(⌘/Ctrl ↵ also works):

```
Snow Queen crosses to downstage left
Gerda and Kay to centre
Kay moves upstage
Gerda enters from stage left
The Snow Queen exits
Everybody to marks
```

Names resolve against roles and actors, doubling included — both `Reindeer` and `Snowflake`
reach the same track, and articles are ignored, so `Snow Queen` and `The Snow Queen` both work.
Places are `upstage / centre / downstage` × `left / right`, plus `enter`, `exit` and
`to marks`. Lines the app cannot read stay in the log with a hint instead of guessing.
**Undo run** reverts the whole batch at once.

## The demo show

The Snow Queen — 5 acts, 11 scenes, 14 tracks (3 doubling roles), 13 props, 28 cues.
Every block above can be edited in the app; the demo is just seeded on first load.

## Data

Everything lives in your browser's localStorage under `stagecraft.v2` — nothing leaves the
machine. **Export / Import** move a production as JSON; **Reset** rebuilds the demo.
Clearing site data wipes the show, so export before you do.

## Files

```
StageManager.html   the whole app — inline CSS, inline JS, no external requests
README.md
.gitattributes      keeps line endings LF so the file opens the same everywhere
```

## Working on it — GitHub Desktop

The repo is `https://github.com/AMFI-Verbose/stage-manager` and `main` tracks `origin/main`.

1. **File → Add local repository…** → choose the folder that holds `StageManager.html`
   (`~/Doubao/chats/2026-11-25/new-chat`). GitHub Desktop will find the existing `.git`
   and list it in the sidebar.
2. Edit `StageManager.html`, and the change appears in **Changes** on the left.
   Write a summary in the bottom-left box, press **Commit to main**.
3. Press **Push origin** (top bar) to publish. **Fetch origin** pulls anything new.
4. **Repository → Repository settings…** is where you would add a remote or change the default
   branch, if you ever need to.

Because the app is one file, a diff shows the whole `<style>` or `<script>` block changing at
once — commit a working version each time, and use **History** to roll back if a change breaks
the show.
