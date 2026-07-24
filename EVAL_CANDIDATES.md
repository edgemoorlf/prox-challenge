# Candidate Evaluation Questions

40 questions a real owner of a Vulcan OmniPro 220 might ask, tiered by what answering
them requires. Derived from the page map in [INVENTORY.md](INVENTORY.md).

**Answers are deliberately omitted.** These are candidates, not a gold set. They become a
gold set only after someone reads the cited pages and writes down what correct looks like.

**The page citations are my belief, not verified fact.** They are where I expect the answer
to live based on having viewed every page. Treat each one as a claim to check — a citation
that turns out to be wrong is a useful finding about the question, not just a typo.

Phrasing is deliberately closer to how someone in a garage talks than how a manual is
indexed. A question that already uses the manual's vocabulary tests retrieval far more
weakly than one that doesn't.

Page references: `OM` = `owner-manual.pdf`, `QS` = `quick-start-guide.pdf`,
`SC` = `selection-chart.pdf`.

---

## Tier 1 — Single-fact lookup

One value, one place. These test whether basic retrieval and citation work at all. If
these fail, nothing above them matters.

| # | Question | Expected source |
|---|---|---|
| 1 | What's the amperage range for MIG if I'm plugged into 240? | OM 7 |
| 2 | What's the max open circuit voltage on this thing? | OM 7 |
| 3 | How big a wire spool can I put in it? | OM 7, OM 11 |
| 4 | How fast does the wire feed go? | OM 7 |
| 5 | Can I run this off an extension cord? | OM 6 |
| 6 | What shade lens do I need for my helmet? | OM 3, OM 18, OM 28 |
| 7 | Where should the feed tension be set for flux-cored wire? | OM 15 |
| 8 | After I put the nozzle back on, how much wire should be sticking out? | OM 17 |
| 9 | How long is this thing under warranty? | OM 48 |
| 10 | How far should the tungsten stick out past the ceramic cup? | OM 26 |

## Tier 2 — Cross-referencing

The answer is assembled from two or more places, and an agent that stops at the first
relevant page returns something incomplete rather than something wrong — which is the
harder failure to detect.

| # | Question | Expected sources |
|---|---|---|
| 11 | I'm getting porosity in my flux-cored welds. What should I check? | OM 37, OM 43, OM 42, OM 13 |
| 12 | What's the duty cycle for MIG at 200A on 240V, and what actually happens if I run past it? | OM 7, OM 19, OM 23, OM 43 |
| 13 | I've been running flux-core and want to switch to solid wire with gas. What all do I have to change? | OM 12, OM 13, OM 14, OM 20, OM 7 |
| 14 | I need to weld some 1/8" steel outside and it's windy. What process should I use and what do I need for it? | SC 1, OM 7, OM 13, OM 18 |
| 15 | Can this do aluminum? What would I need to buy? | OM 7, SC 1, OM 17, OM 14 |
| 16 | My wire keeps bird-nesting up at the feeder. | OM 42, OM 15, OM 17, OM 11 |
| 17 | I want to start TIG welding with this. What do I need to buy before I can do anything? | OM 24, OM 25, OM 26, OM 7 |
| 18 | It shut itself off in the middle of a weld and put a warning up on the screen. | OM 23, OM 19, OM 29, OM 43 |
| 19 | Which hole does the ground clamp go in? I'm going to be doing all four processes eventually. | OM 13, OM 14, OM 24, OM 27, QS 2 |
| 20 | I'm not getting penetration on 1/4" steel. | OM 35, OM 36, OM 7, OM 19 |

## Tier 3 — Visual-only

Every page cited here is flagged visual-only in [INVENTORY.md](INVENTORY.md) — verified
against the actual text layer, not assumed. A text-only pipeline should fail these
outright. An agent that answers them fluently *without* having read the image is
hallucinating, and these are the questions most likely to expose that.

| # | Question | Expected source | Why it's visual-only |
|---|---|---|---|
| 21 | There's a symbol stamped on the machine that looks like a circle with a line through it — what is that telling me? | OM 6 | The glyph shapes are drawings; the text layer lists meanings with nothing to attach them to |
| 22 | Looking at the front, which socket is positive and which is negative? | OM 8 | Callout labels exist as text but carry meaning only through their position on the diagram |
| 23 | Where's the cold wire feed switch? I can't find it. | OM 9 | Page has ~330 characters; the callout labels are outlined vector, absent from the text layer |
| 24 | How do I tell which side of the feed roller is the right one for my wire? | OM 12 | Groove sizes are printed on the roller illustration itself |
| 25 | Which way is the spool supposed to unwind? | OM 11 | Conveyed by a direction arrow on the illustration |
| 26 | My bead is narrow and piled up tall instead of laying flat. What's wrong? | OM 35 | Diagnosis works by matching bead appearance against the example diagrams |
| 27 | Same question but I'm stick welding — bead looks rough and irregular. | OM 38 | Example weld photographs; captions are not in the text layer |
| 28 | How do I hold the gun for a T-joint versus a butt joint? | OM 22 | Angle values are loose tokens in the text layer; which joint each applies to is positional |
| 29 | I'm a beginner, welding 1/8" steel, outdoors, and I don't want to mess with a gas bottle. What process? | SC 1 | Entire chart is one raster image with a zero-character text layer |
| 30 | The exploded diagram — which number is the wire feeder, and what's the part called? | OM 47, OM 46 | Part identity in the diagram is purely positional; the numbers resolve to names only via p46 |

## Tier 4 — Ambiguous

Correct behavior is a clarifying question, not an answer. An agent that confidently picks
one interpretation should be marked wrong even when the answer it gives is factually
correct for the branch it happened to choose — on a machine that runs at 240V and melts
metal, a confident answer to the wrong question is the failure mode that actually hurts
someone.

The third column is the axis the agent needs to resolve. It is the grading criterion, not
the answer.

| # | Question | What's unresolved |
|---|---|---|
| 31 | What's the duty cycle on this? | Process, input voltage, and amperage — all three change the number |
| 32 | What size wire should I use? | Process, material, and workpiece thickness |
| 33 | What settings do I need? | Process, material, thickness, wire or electrode size — nearly everything |
| 34 | My weld's got holes in it. | Holes *in* the bead and holes *through* the workpiece are different faults with different fixes |
| 35 | Which polarity do I need? | Differs per process; the two wire processes are opposite each other |
| 36 | What gas do I need? | Process and material; one process needs none at all |
| 37 | How thick of metal can this weld? | Process, and input voltage |
| 38 | What electrode should I use? | "Electrode" means the tungsten in TIG and the stick rod in Stick — two unrelated answers |
| 39 | Is 120V good enough, or do I need to run 240? | Depends entirely on process and intended thickness |
| 40 | It's not working. | No symptom given — no power, no arc, no wire feed, and bad weld quality are four different diagnostic paths |

---

## Notes on using these

- **Tier 3 is the load-bearing tier for this challenge.** It's the direct test of the
  evaluation axis the brief calls most important, and the one where a plausible-sounding
  wrong answer is hardest to catch by reading the transcript.
- **Tier 4 needs a scoring rule written before the agent is tested**, or the temptation to
  accept a confident correct-sounding answer will win. Suggested rule: full credit only if
  the agent asks before answering; no credit for a correct answer to an unasked question.
- **Question 12 has a wrinkle worth knowing about.** Its values live in extractable form on
  OM 7 and in raster-only form on OM 19. An agent can get it right while citing a page it
  never actually read. Worth using as a citation-honesty probe.
- **These are candidates.** Some will turn out to be badly posed, some will have answers
  that aren't in the manual at all, and finding that out is the point of verifying them
  before they become the gold set.
