# CLAUDE.md — Prox Founding Engineer Challenge

Project-level context for this repo. Global standards in `~/.claude/CLAUDE.md` still apply;
this file adds the domain.

---

## 1. WHAT PROX IS BUILDING

Prox exists for complicated physical products that nobody knows how to use out of the box.
The pattern: an expensive machine ships with a dense technical manual, the owner has neither
the time nor the background to read it, and there is no expert in the room. Prox is the expert
in the room — expert-level product support delivered at the moment of use.

The consequence for this build: the target is not "a chatbot over a PDF." It is a support
experience that behaves like someone who has actually used the machine, standing next to you.

## 2. THE PRODUCT

**Vulcan OmniPro 220** — multiprocess welding system (Harbor Freight).

- Four processes: MIG, Flux-Cored, TIG, Stick
- Dual input voltage: 120V and 240V
- LCD-based synergic control system

Source material lives in `files/`:

| File | Contents |
|---|---|
| `owner-manual.pdf` | ~48 pages — duty cycle matrices, per-process polarity setup, wire feed and tensioner calibration, wiring schematics, troubleshooting matrices, weld diagnosis diagrams, parts list |
| `quick-start-guide.pdf` | ~2 pages |
| `selection-chart.pdf` | ~1 page — welding process selection chart |

Product photos at repo root: `product.webp`, `product-inside.webp`.
Reference video: https://www.youtube.com/watch?v=kxGDoGcnhBw

Critical information exists **only in images** — the process selection chart, the weld
diagnosis photos, the wiring schematic. Text extraction alone loses the answer.

## 3. WHAT THE CHALLENGE ASKS FOR

Build a multimodal reasoning agent for the Vulcan OmniPro 220 using the Claude Agent SDK,
capable of answering deep technical questions accurately, helpfully, and **not just in text**.

Representative test questions:

- "What's the duty cycle for MIG welding at 200A on 240V?"
- "I'm getting porosity in my flux-cored welds. What should I check?"
- "What polarity setup do I need for TIG welding? Which socket does the ground clamp go in?"

Evaluation questions will require cross-referencing multiple manual sections, reading visual
content, and asking for clarification when the question is ambiguous.

There is no ceiling. Voice, full interactive experiences, anything — more ambitious and more
polished is better.

## 4. THE FOUR EVALUATION AXES

### Axis 1 — Deep technical accuracy
Answers must be correct across cross-section lookups, visual content, and ambiguous inputs.
An ambiguous question gets a clarifying question, not a guess.

### Axis 2 — Multimodal responses *(stated as the most important)*
The agent must not be text-only.
- Polarity question → draw/show which cable goes in which socket.
- Answer tied to a manual image (wire feed mechanism, front panel, weld diagnosis) → surface
  that image.
- Complex enough question → generate interactive content: duty cycle calculator,
  troubleshooting flowchart, settings configurator (process + material + thickness → wire
  speed and voltage).

When something is too cognitively hard to explain in words, draw it — real-time diagrams,
interactive schematics, visual walkthroughs generated through code. This requires reverse
engineering how Claude artifacts render in chat.
Starting points: https://claude.ai/artifacts ·
https://www.reidbarber.com/blog/reverse-engineering-claude-artifacts

### Axis 3 — Tone and helpfulness
The user just bought this welder and is standing in their garage trying to set it up. Not an
idiot, not a professional welder. Write for that person.

### Axis 4 — Knowledge extraction quality
The manual mixes text, tables, labeled diagrams, schematics, and decision matrices. The bar is
demonstrating that the agent *understands and presents the visual content* — not that it
scraped the text layer.

## 5. TECH CONSTRAINTS

- **Claude Agent SDK** is the foundation of the agent. Non-negotiable.
- **Single API key via `.env`.** `.env.example` already defines the contract:
  `ANTHROPIC_API_KEY=your-api-key-here`. No second key, no extra service credential, no
  external vector DB requiring signup. Any capability we add must work from that one key.
- **Runs locally.**
- **2-minute clone-to-run.** The reviewer's path is exactly:

  ```bash
  git clone <fork>
  cd <fork>
  cp .env.example .env    # they plug in their own key
  # one install command
  # one run command
  ```

  Longer than that is a failure, not a rough edge. Implication: no heavyweight index build at
  install time on the reviewer's machine — any expensive extraction is done by us and
  committed as an artifact.
- We pay our own API costs during development.

## 6. SUBMISSION REQUIREMENTS

Presentation is graded, not just code.

1. Fork the repo, build the solution, submit the fork URL at
   https://useprox.com/join/challenge
2. **Frontend required** — clean, simple UI runnable immediately. Stated as realistically the
   only way to properly demo an agent like this.
3. **Hosting is a plus** — not required; removes friction and signals initiative.
4. **Clear README, and it is evaluated** — how the agent works, design decisions, how knowledge
   is extracted and represented, how to run it. They are reading it for how we think and
   communicate.
5. **Video walkthrough is a huge plus** — demo the hard questions, show multimodal responses,
   explain the architecture.

Reviewed on a rolling basis; every submission gets a response within a few days.

---

## 7. WORKING AGREEMENT

**We define correctness before we write code.**
For any capability, we first write down what a correct answer looks like — the exact expected
output, the manual pages it must come from, and the failure modes that count as wrong. That
definition is the acceptance criterion, and it exists before the implementation does. A gold
query set precedes the system going live, not the other way around. No feature is "done"
because it produced plausible output.

**Every factual claim about the welder must cite a manual page.**
Duty cycles, amperage ranges, polarity configurations, socket assignments, wire diameters,
tensioner settings, part numbers, troubleshooting steps — each traces to a specific page in
`files/`. This applies to the agent's answers to users *and* to our own statements in code
comments, README, planning docs, and conversation. If a claim cannot be traced to a page, it
does not get stated. An uncited number is a bug.

**You do not invent technical values.**
If the manual does not contain the value, the correct output is "the manual doesn't specify
this" plus the closest thing it does say — never an interpolation, never a plausible number
from general welding knowledge, never a value carried over from a similar machine. This is a
piece of equipment that runs at 240V and melts metal; a confidently wrong setting is a real
hazard, not a bad answer. Same rule for the agent at runtime: below the retrieval confidence
threshold, decline gracefully rather than calling the model to fill the gap.

---

## 8. CURRENT STATE

No application code written yet. Repo contains the challenge README, the source PDFs in
`files/`, product images, `.env.example`, and this file.
