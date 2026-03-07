---
name: corporate-bs-detector
description: Detects and scores corporate bullshit in text using a research-backed 5-dimension rubric. Use this skill when the user asks you to evaluate, review, or score corporate communication for BS, buzzwords, or empty language. Also consult this skill when writing or editing corporate-facing documents (strategy docs, mission statements, press releases, executive communications, annual reports) to ensure the output stays concrete and BS-free. Trigger on phrases like "is this BS", "check for buzzwords", "does this actually say anything", "corporate speak", "too much jargon", or when reviewing text that smells like it came from a buzzword generator.
---

# Corporate Bullshit Detector

A rubric for identifying corporate bullshit, grounded in Littrell (2026), "The Corporate Bullshit Receptivity Scale" (*Personality and Individual Differences*). The research demonstrated that algorithmically-generated corporate buzzword statements are frequently indistinguishable from real executive speech — and that receptivity to such statements negatively predicts workplace decision-making quality.

Your job is to be the antidote.

## What Corporate Bullshit Actually Is

Corporate bullshit is semantically empty communication that leverages abstruse buzzwords in a **functionally misleading** way. Two properties make it bullshit rather than merely bad writing:

1. **Functionally misleading** — It creates inflated impressions of knowledge, competence, strategy, or progress that aren't warranted by the actual content. Intent doesn't matter; the *effect* does.
2. **Epistemically irresponsible** — It's constructed to *sound* smart without genuinely *being* informative. Noise masquerading as insight.

### What it's NOT

Don't flag these as bullshit:

- **In-group jargon** used among people who share its meaning ("refactor the auth service" among engineers). Jargon facilitates communication; bullshit obstructs it.
- **Simplification** that trades precision for accessibility ("think of the database as a filing cabinet").
- **Honest uncertainty** ("we're still figuring out the right approach"). Admitting ignorance is the opposite of bullshit.
- **Bad writing** that's unclear but not trying to impress. Bad writing lacks polish; bullshit has too much of it.

Context matters: "synergy" in a biochemistry paper about drug interactions is jargon. "Synergy" in a press release about a vague merger is bullshit.

## The Five Detection Dimensions

Evaluate the text across these five dimensions, scoring each 0-3.

### 1. Semantic Emptiness

**Ask**: If I strip the buzzwords, does any concrete meaning survive?

**Red flags**:
- Sentences that are syntactically valid but convey zero specific, actionable, or verifiable information
- Statements that could describe any company, any product, any situation without modification
- Nouns, verbs, and adjectives that could be randomly swapped with other corporate terms without changing the "meaning"

**Test**: Replace every buzzword with a concrete term. If you can't — if there's no underlying specific claim — it's empty.

| Score | Description |
|-------|-------------|
| 0 | Concrete and specific throughout |
| 1 | A buzzword or two padding an otherwise concrete statement |
| 2 | Core claim is obscured by buzzword layering but recoverable with effort |
| 3 | No concrete meaning survives buzzword removal |

### 2. Buzzword Density

**Ask**: How many impressive-sounding terms are packed in relative to actual information content?

**Red flags**:
- 3+ buzzwords per sentence
- "Buzzword chains" linking impressive terms without logical connectives ("end-state vision and growth-mindset in the market")
- Neologisms without established meanings ("de-contenting," "cradle-to-grave credentialing")
- Mixing buzzwords from different domains that don't cohere (finance + HR + tech jargon in one clause)

**Common offenders**:
- *Vague action verbs*: leverage, actualize, architect, ideate, operationalize, sunset, solutioning, potentiate, growth-hack, "download on this"
- *Inflating modifiers*: scalable, synergistic, transformational, bleeding-edge, best-in-class, paradigm-shifting, holistic
- *Empty compound nouns*: thought leadership, value proposition, balanced scorecard, change drivers, resonating focus, strategic intent, swim lanes (outside project management), ecosystem (when not ecological)
- *Inflating frames*: "in a world defined by," "like no other company anywhere," "fundamentally disrupt," "at the intersection of"

**Test**: Count buzzwords vs. concrete terms. If buzzwords outnumber specifics 2:1 or more, flag it.

| Score | Description |
|-------|-------------|
| 0 | Clean, precise language |
| 1 | 1-2 buzzwords that add color without obscuring meaning |
| 2 | Buzzword density makes parsing effortful but possible |
| 3 | Buzzwords form the structural backbone; removing them collapses the sentence |

### 3. Unfalsifiability

**Ask**: Could this ever be proven wrong? Could you check whether it was accomplished?

**Red flags**:
- No metrics, timelines, quantities, or named entities
- Goals as directions rather than destinations ("driving innovation" vs. "shipping feature X by March")
- Claims structured so any outcome could retroactively confirm them
- Aspirational language with no accountability mechanism

**Test**: Ask "how would I know if this were false?" If there's no answer, it's unfalsifiable.

| Unfalsifiable | Falsifiable |
|---------------|-------------|
| "We're committed to driving transformational change" | "We're restructuring sales from geographic to vertical by June" |
| "Our focus is on creating value for all stakeholders" | "We're increasing the dividend 8% and adding 2 weeks parental leave" |

| Score | Description |
|-------|-------------|
| 0 | Specific, measurable, verifiable claims |
| 1 | Aspirational framing around a concrete core |
| 2 | Core claim exists but wrapped in so much hedge that accountability is unclear |
| 3 | Entirely unfalsifiable; functions as a mood rather than a claim |

### 4. Impression Inflation

**Ask**: Does this language create a misleadingly inflated impression of knowledge, competence, or progress?

This is the most important dimension — it gets at the *function* of corporate bullshit. The research shows corporate BS operates as a false signal of competence. It's designed (consciously or not) to make the speaker seem more strategic or accomplished than the content warrants.

**Red flags**:
- Language complexity dramatically exceeds idea complexity
- Simple actions described using elaborate, technical-sounding frameworks
- Routine activities reframed as visionary or unprecedented
- Credit-claiming for outcomes not demonstrated or measured
- Would impress an outsider but draw eye-rolls from insiders

**Test**: Restate the core idea in the simplest possible language. If the simple version sounds trivially obvious or empty, the original was inflating.

| Inflated | Deflated |
|----------|----------|
| "As an emerging leader grounded in a mission to benchmark and nurture the human spirit, we have always aspired to make upstream connections" | "We try to be good to people and build partnerships" |
| "We will cover all the bases of our low hanging fruit by joining with our bleeding-edge, results-driven global partners" | "We'll handle the easy stuff with our partners" |

| Score | Description |
|-------|-------------|
| 0 | Language matches the substance |
| 1 | Mild puffery conventional to the genre |
| 2 | Language significantly inflates a real but modest accomplishment |
| 3 | Impression is entirely unearned — or there is no content at all |

### 5. Circularity

**Ask**: Does this go anywhere, or does it loop back to where it started?

**Red flags**:
- The conclusion restates the premise using different buzzwords
- "Definitions" that use the term being defined ("our strategic strategy")
- Chains of corporate terms where each is "explained" by the next, forming a closed loop
- Passages that feel authoritative on first read but haven't said anything new on second read

**Test**: Diagram the logic. If A is defined by B, B by C, and C by A — or if the beginning and end are semantically identical — it's circular.

| Score | Description |
|-------|-------------|
| 0 | Clear logical progression |
| 1 | Mild redundancy that still advances an argument |
| 2 | Key passages are circular but the document contains some concrete content |
| 3 | Entire communication is a closed loop of buzzwords defining each other |

## Composite Scoring

Sum the five dimension scores (0-15):

| Score | Verdict | Action |
|-------|---------|--------|
| 0-3 | **Clean** | No action needed; minor clarity edits at most |
| 4-7 | **Buzzword-heavy but recoverable** | Flag specific phrases; suggest concrete alternatives |
| 8-11 | **Substantially bullshit** | Rewrite recommended; extract and restate the core meaning |
| 12-15 | **Weapons-grade bullshit** | Cannot be salvaged by editing; ask the author what they actually mean |

## Output Modes

### Default: Flag & Annotate

For each flagged passage:
- Which dimension(s) it triggers and why (be specific, be brief)
- A suggested rewrite or clarifying question
- The composite score with per-dimension breakdown

Keep annotations tight. One or two sentences per flag, not paragraphs. The goal is to be useful, not to write an essay about why someone else's essay was bad.

### On request: Rewrite

Replace BS passages with clear, concrete language. Where the original has no recoverable meaning, say so directly: "This doesn't contain a concrete claim I can rewrite. What did you actually mean by this?"

### On request: Score Only

Per-dimension breakdown and composite score, no rewrites.

## When Writing or Editing Documents

If you're helping write or edit corporate-facing text, apply these principles proactively:

- Prefer concrete claims over aspirational framing
- Use specific numbers, dates, and names instead of vague directional language
- If you catch yourself writing a buzzword chain, stop and ask what you actually mean
- Test your own output: "Could someone verify this claim? Could they act on it?"

Don't overcorrect into robotic prose — some warmth and aspiration is fine, especially in genres that expect it (mission statements, annual reports). The line is between conventional puffery and genuinely empty language. A mission statement saying "We strive to be the most customer-centric company" is genre-appropriate. One saying "We leverage synergistic paradigm shifts to actualize stakeholder value" has crossed it.

## Calibration Notes

These matter for accurate detection:

- **Genre expectations**: Annual reports and earnings calls permit more aspirational vagueness than internal strategy docs or engineering specs. Calibrate severity to genre.
- **Audience**: If the audience shares the vocabulary and the terms have specific meanings within that community, it's jargon, not bullshit. The test is whether the language *facilitates* or *obstructs* communication.
- **Intent is irrelevant**: Bullshit can be spread unintentionally (repeating absorbed phrases) or intentionally (impression management). Detect the bullshit, not the motive.
- **The discernment gap**: Analytically sophisticated people aren't less receptive to corporate speech *in general* — they're specifically less impressed by *corporate bullshit* while still appreciating genuine corporate communication. Good detection means distinguishing "corporate language I don't like" from "language that is genuinely empty."
