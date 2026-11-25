# Stage Manager

A single-file rehearsal and cue book for stage managers — prop tracking, a half-round virtual
stage with draggable blocking, and typed movement directions that the page animates itself.

Open `StageManager.html` in any modern browser. No build step, no server, no dependencies.

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

**Run show** — the big GO button, running clock, and the executed cue list.

## Moving people

Drag a token, or click one and nudge it with the arrow keys (hold Shift for 5% steps).
⌘/Ctrl Z undoes the last move, Delete sends the selected actor to the wings.

Better still, type the blocking into **Movement directions** and press **Run moves**
(⌘/Ctrl ↵ also works):

```
Puck crosses to downstage left
Titania and Bottom to centre
Snug moves upstage
Hermia enters from stage left
Theseus exits
Everybody to marks
```

Names resolve against roles and actors, doubling included — both `Flute` and `Thisbe` reach the
same track. Places are `upstage / centre / downstage` × `left / right`, plus `enter`, `exit` and
`to marks`. Lines the app cannot read stay in the log with a hint instead of guessing.
**Undo run** reverts the whole batch at once.

## The demo show

The Snow Queen — 5 acts, 11 scenes, 14 tracks (3 doubling roles), 13 props, 28 cues.
Snow Queen and Midsummer Night's Dream versions both store separately; **Reset** rebuilds the
demo, **Export / Import** move a production as JSON.

## Data

Everything lives in your browser's localStorage under `stagecraft.v2` — nothing leaves the
machine. Export before clearing site data.

## Files

```
StageManager.html   the whole app — inline CSS, inline JS, no external requests
README.md
```
