# Stage Manager

A single-file rehearsal and cue book for stage managers — prop tracking, a half-round virtual
stage with draggable blocking, recorded movement paths that play during the run, and typed movement
directions that the page animates itself.

Open `StageManager.html` in any modern browser. No build step, no server, no dependencies.

## What's inside

**Overview** — the run order act by act, with cast calls, per-scene timings and flags for
missing props or unassigned cues.

**Scenes & stage** — a plan view of a half-round floor: flat back wall upstage, arc into the
audience. Actors are coloured discs, props are tags preset along the back wall. Drag either
one and the position saves to that scene. **+ act** sits outside the scene tabs, at the right edge of
the tab strip, and adds another act. Click an act label in the tabs (or the act heading on
Overview) to rename it.

**Cast & doubling** — enter/exit counts per character, doubling notes per track.

**Props** — quantity, status (Ready / In use / Needs work / Missing / Struck), location, and the
scenes that call them.

**Sound & light** — all SFX and LFX cues, with triggers and durations.

**Cue sheet** — a printable running order; cue numbers are generated per type (SQ / LX / PQ).

**Run show** — the big GO button, running clock, and the executed cue list. A stage plan above the
cues shows the cast; when a scene with recorded paths starts, the actors glide along those paths.
**Replay movement** runs the current scene again. The cue position and called list survive a refresh.

**Settings** — switch the interface between English (the default) and Simplified Chinese. The
choice is saved in this browser; the show, the demo and imported files keep their original text.

## Moving people

Drag a token, or click one and nudge it with the arrow keys (hold Shift for 5% steps).
⌘/Ctrl Z undoes the last move or steps back through the last deletes (up to 20; cleared when you
edit again). Delete sends the selected actor to the wings.

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

Chinese directions use the same parser: `Gerda 走到左前`, `Kay 退场`, `所有人回位`. Position
words are `前 / 中 / 后` × `左 / 右`, plus `上场`, `退场` and `回位`.

## Movement paths

Select an actor on the Scenes & stage floor, then use **Movement paths**:

1. **Record path** (or **Edit path** if one exists)
2. click points on the floor in the order you want the actor to walk
3. **Save path**

The path starts from the actor's current mark. It is stored per scene and actor (up to 30 points),
travels with Export / Import, and **Clear path** removes it. **Preview path** plays it in the stage
editor. In **Run show**, a path plays when its scene begins; GO within the same scene does not restart
it, and **Replay movement** plays the current scene again. **Copy blocking from…** copies paths too.

## The demo show

The Snow Queen — 5 acts, 11 scenes, 14 tracks (3 doubling roles), 13 props, 28 cues.
Snow Queen and Midsummer Night's Dream versions both store separately; **Reset** rebuilds the
demo, **Export / Import** move a production as JSON. Import asks before replacing the current show.

## Data

Everything lives in your browser's localStorage under `stagecraft.v2` — nothing leaves the
machine. Export before clearing site data.

## Files

```
StageManager.html   the whole app — inline CSS, inline JS, no external requests
README.md
```
