# claude context — TT1nKer github profile repo

this repo is `TT1nKer/TT1nKer` on github — the special "profile readme"
repo that renders on the user's github profile page. there is no app
here, just three files:

- `README.md` — markdown that embeds the two svgs
- `banner.svg` — the title banner with the cyberpunk dossier vibe + bit-counter egg
- `shell.svg` — fake terminal session that reveals line by line

deploy = just `git push origin main`. github fetches the files and
renders the readme on the profile page. **github camo proxies all
images aggressively** — page refresh often shows the cached version
even after a push. always test against the raw url to verify changes:

```
https://raw.githubusercontent.com/TT1nKer/TT1nKer/main/banner.svg
https://raw.githubusercontent.com/TT1nKer/TT1nKer/main/shell.svg
```

camo eviction is unpredictable; ctrl-shift-r in the browser does not
bust it. if you need the profile page itself to update visibly, wait
~5-15 minutes after pushing.

---

## about the user

they explicitly do **not** want their profile to lock them into a
fixed aesthetic identity. earlier drafts of `shell.svg` had manifesto
lines like "i'd rather understand a thing than just use it" and "if i
can't read it end-to-end, i don't trust it yet" — those got pulled
because the user is open to many aesthetics and approaches (including
vibe-coding) and didn't want the profile to commit to a single stance.

current `shell.svg` thoughts are softer: only attitude lines
("control my computer", "works in progress, that's fine") survive.
the thesis line is also softened from "controllable systems" to "i
build and study things" — same reason.

`banner.svg` stays cyberpunk because it's a visual flourish, not a
textual identity claim. but **don't push that aesthetic onto new
projects** without asking — see `~/.claude/projects/.../memory/` if
loaded for the canonical aesthetic-fluidity note.

---

## banner.svg — the bit-counter egg

the row of small squares in the top-right of the banner is a
**6-bit binary counter**. periods double per bit:

```
b0=2s, b1=4s, b2=8s, b3=16s, b4=32s, b5=64s
```

every 64s the counter naturally hits all-1s (0x3f) for ~1s. at that
moment the egg fires:

- a phantom 7th bit (red, `#d96666`) appears to the left
- bits flash from `#ededed` to `#ffffff`
- the `[ ALIVE ]` label flips to `[ 0x3F ]`
- the `TT1NKER` title hides
- a big red message appears in its place
- a small comment line appears below

the egg lingers for **5 seconds** total, crossing the cycle boundary
into the start of the next 64s cycle. four different messages cycle
through a 256s outer period:

```
cycle 1 (t=63):   OVERFLOW       // observed.
cycle 2 (t=127):  RESET          // you again?
cycle 3 (t=191):  PANIC          // stop.
cycle 4 (t=255):  STILL HERE     // please push something.
```

after t=256 the sequence loops.

### critical implementation details (don't break these)

**1. `animation-delay: -6s` on every egg-related rule.**

without this, page refresh shows `STILL HERE` + hidden title for 4s
because the cross-cycle-boundary `STILL HERE` window (which uses a
wraparound keyframe pattern `0%, 1.5625% { opacity: 1 }`) is active
at animation t=0. the -6s delay shifts every animation past that
wraparound zone on first paint. **all bit and egg animations get the
same -6s** — keeps bits and egg perfectly synced. first egg fires at
clock t=58 instead of t=63 (acceptable trade for a clean refresh).

if you add or modify any of these animations, they need the same
`animation-delay: -6s`.

**2. multiple `animation:` declarations from different classes do
NOT compose — the later one wins via cascade.**

a previous bug: bits had `class="b5 bit-flash"` with `.b5` defining
one animation and `.bit-flash` defining another — only `.bit-flash`
applied. fix is to combine into a single animation declaration:

```css
.b0 { animation: bit  2s step-end infinite, bitFlash 64s step-end infinite; }
```

if you ever want to layer more animations on the bits, do it in this
single declaration.

**3. svg transforms apply right-to-left to points.**

`transform="translate(50 0) rotate(90)"` rotates first, then
translates. used in case any future feature needs to rotate svg
content while keeping coordinates positive.

---

## shell.svg — the fake terminal session

content is a sequence of `$ command` + output blocks. each text line
has a sibling `<rect>` that covers it; the rect slides right (via
`<animate>` or `<set>`) at a specific time, "revealing" the line as
if it were being typed. timings cascade across the file.

if you add a new line:

1. add a `<text>` element at the right `y` coordinate
2. add a sibling masking `<rect>` at `y = text_y - 14`, with width
   ~= text_width + 4
3. give the rect either an `<animate>` (typing-style reveal) or
   `<set>` (instant) and pick a `begin` time fitting the cascade

if you *reorder* or *remove* lines, the y coordinates of everything
below shift, **and** the masking rect ys must follow.

content rule: keep lines tight, no manifesto. attitude lines OK,
identity claims not OK (see "about the user" above).

---

## known-good editing workflow

1. open the svg, edit
2. `git diff` to confirm the change is what you intended
3. `git commit && git push`
4. while waiting, check raw url to verify the actual file content:
   `curl -s https://raw.githubusercontent.com/TT1nKer/TT1nKer/main/banner.svg | head -100`
5. if you need to verify it renders, open the raw url in a browser
   (bypasses camo). don't trust github.com/TT1nKer immediately —
   that goes through camo cache.
