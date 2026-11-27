# Stage Manager

A single-file stage manager's book for backstage work — prop tracking, a half-round virtual
stage with draggable blocking, recorded movement paths that play during the run, typed movement
directions the page animates itself, and a **run board** built to be held in one hand while you
call a show.

Open `StageManager.html` in any modern browser. No build step, no server, no dependencies.

## Run board — what to watch during the show

**Run show** is the backstage screen. Everything you need to answer "who should be out there
right now?" sits in one view:

- **Now on stage** — the live floor for the scene you are in: actors as coloured discs at their
  blocking marks, props as small tags. Under it, a row of name chips — tap one to check that
  actor off as they arrive; the disc gets a green ring. `Clear checks` resets the scene.
- **Paths** — when the scene has recorded movement paths, the floor header shows the count and a
  **Replay movement** button; the actors with paths follow them when the scene begins.
- **Wings** — everyone who is off stage right now, so you know who is waiting.
- **Standby** — the next cue with its type (SQ / LX / PQ), trigger and duration, plus a **THEN**
  list of the two or three cues after it.
- **Now cueing** — the cue you called, with its note.
- **Next scene** — the oncoming scene's floor plan plus explicit **ENTERS / EXITS** lists,
  so you can catch the changeover before it happens.
- **Called** — the last five cues, as a record.
- **GO** — sticky at the bottom of the screen, and each GO walks the floor to the next scene's
  blocking before your eyes (see **Moving people**). `Space` = GO, `Esc` = leave the run.
  The `↓ ↑ ⇄` buttons next to the clock turn the floor round, same as in the plan.
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
one and the position saves to that scene. **+ act** sits outside the scene tabs, at the right edge of
the tab strip, and adds another act. Click an act label in the tabs (or the act heading on
Overview) to rename it.

The **HOUSE** buttons turn the whole floor round without touching a single blocking mark:
`↓` puts the audience at the bottom of the screen, `↑` at the top, `⇄` mirrors stage left and
right. Use them when you are standing on the opposite side of the room, working from the
audience's point of view, or reading a plan drawn the other way up. The setting is remembered,
and it applies to the run board too.

**Cast & doubling** — enter/exit counts per character, doubling notes per track.

**Props** — quantity, status (Ready / In use / Needs work / Missing / Struck), location, and the
scenes that call them.

**Sound & light** — all SFX and LFX cues, with triggers and durations.

**Cue sheet** — a printable running order; cue numbers are generated per type (SQ / LX / PQ).

**Settings** — switch the interface between English (the default) and Simplified Chinese. The
choice is saved in this browser; the show, the demo and imported files keep their original text.

## Moving people

The cast moves itself. **Auto-move** is on by default: change scene in the plan, or press **GO**
in the run, and every actor already marked on the floor walks from where they stood to their new
mark — staggered, so you can see the changeover resolve. Anyone who was not in the previous
scene slides in from the wing nearest their mark. Speed is `slow / normal / quick` (2.6 s → 0.85 s).

Turn it off if you only want the marks to snap. `▸ Line up` runs the same animation from the
wings on demand — everyone goes out, then walks on — which is the quickest way to show a
designer what a scene looks like as it assembles.

You can also move people by hand. Drag a token, or click one and nudge it with the arrow keys
(hold Shift for 5% steps). ⌘/Ctrl Z undoes the last move or steps back through the last deletes
(up to 20; cleared when you edit again). Delete sends the selected actor to the wings.

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

Chinese directions use the same parser: `Gerda 走到左前`, `Kay 退场`, `所有人回位`. Position
words are `前 / 中 / 后` × `左 / 右`, plus `上场`, `退场` and `回位`.

## Movement paths

Select an actor on the Scenes & stage floor, then use **Movement paths**:

1. **Record path** (or **Edit path** if one exists)
2. click points on the floor in the order you want the actor to walk
3. **Save path**

The path starts from the actor's current mark. It is stored per scene and actor (up to 30 points),
travels with Export / Import, and **Clear path** removes it. **Preview path** plays it in the stage
editor. In **Run show**, when a scene begins, actors with a path are placed at their mark and follow
it; auto-move handles the rest. GO within the same scene does not restart it, and **Replay movement**
plays the current scene again. **Copy blocking from…** copies paths too.

## The demo show

The Snow Queen — 5 acts, 11 scenes, 14 tracks (3 doubling roles), 13 props, 28 cues.
Every block above can be edited in the app; the demo is just seeded on first load.
**Reset** rebuilds it, and **Export / Import** move a production as JSON. Import asks before
replacing the current show.

## Data

Everything lives in your browser's localStorage under `stagecraft.v2` — nothing leaves the
machine. **Export / Import** move a production as JSON, paths included; **Reset** rebuilds the demo.
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
