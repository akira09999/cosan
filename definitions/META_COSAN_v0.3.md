# META COSAN v0.3

> **English name: COSAN** (Coding + 散文/prose)
> Always written as `COSAN`. Not `KOSAN`.
> File extension: `.cosan`

> Give this document to an AI, and the AI reads it and creates a **domain-specific COSAN definition**.
> Meta-COSAN does not define domain grammar. It contains only the **principles, questions, and constraints** that can produce grammar.

```
Meta-COSAN  →  (give to AI)  →  <domain> COSAN definition  →  <domain> COSAN  →  roll it  →  trace
```

**v0.2 changes:** Added code-enforcement section (§6).
Generated with v0.1 and the result was **stuck between prose and code**.
The shell was symbols but the values were free-form sentences — prose creeps back in through those slots.

---

## 1. Definition

> **COSAN = thoughts written in code form. The executor is a person or an AI. The code itself is the output.**

**① Write thoughts in code form**
- Not the object itself but **thoughts about the object**.
- Code form = inputs/process/outputs are stated, the answer branches on conditions, relationships are pinned with symbols.
- Not prose because: **prose lets you fill space without making decisions.**

**② The executor is not a machine**
- No compiler. So grammar does not need to be **exact**.
- (But it does need to **look like code**. §6.)
- The purpose of execution is not to get an answer but to **find where it breaks.**

**③ The code is the output**
- The code is **source, memory, and output.**
- Prose and agreements are **rendered** from the code later. They are build artifacts.

### What COSAN Is Not

```
✗ Programming language      No compiler. Execution is not the goal.
✗ Structured prose          Shell is symbols but values are sentences → not COSAN.  ← most common failure
✗ Chronological event list  That is the execution result (trace).
✗ Spec / blueprint          If it cannot be rolled, it is not COSAN. It must roll.
✗ Data / configuration      If there is no decision, it is not COSAN.
```

### Minimum Conditions

```
Decision       something whose answer branches on input        without it → config file
State          what the decision changes                       without it → rule list
Pass condition what counts as good                            without it → average generator
```

---

## 2. Why It Exists

AI becomes **shallow** in prose.

**① Modifiers are evasion**
The only way to fill space without deciding on structure is to ornament.
"A cold wind brushed the collar" decides nothing and fills a line.
Since it yields volume with no risk, for an AI this is the **optimal strategy**.
Result: sentences multiply but nothing happens.

**② Average is the answer when there are no constraints**
Ask for an answer to an unconstrained problem and the most plausible = the most common appears.
Same if you have multiple AIs debate. They just **draw slightly differently** — they do not actually think.
Prose has **no position to be wrong**. An impression cannot be refuted.

**③ When output and memory are separated, memory is lost**
Memory (summary) is a derivative of output, and derivatives are always inferior to the original.
And prose already written becomes an **anchor** — only similar things come out when you revise.

> **∴ We need a medium that cannot be waffled and can be corrected.**

---

## 3. Principles

> **Do not prohibit. Make it impossible.**

```
Do not tell it not to ornament      →  remove the slot for ornamentation
Do not ban average                  →  set a gate average cannot pass
Do not increase memory capacity     →  eliminate the need to remember
Do not tell it to be consistent     →  make violations detectable
Do not tell it not to write prose   →  remove the slot for sentences          ← §6
```

**Rules can be broken. Structure cannot.**

---

## 4. How It Works

### ① Accept Only Decisions

**Why + what changes as a result.** Without both, nothing gets in.

> **What cannot be written in COSAN is what can be omitted.**

This is not an exclusion rule — it is a **judgment tool**.

```
"Can this be written in COSAN?"
   Yes     →  it is structure. It is core.
   No      →  one of two things:
               (a) ornamentation    → discard. If needed, it attaches as flesh in rendering.
               (b) still unknown    → leave as a hole. Do not fill it.
```

**(a) and (b) must be distinguished.** Mixing them covers unknowns with ornament.

- If the unwritable thing is **ornamentation**: it can be absent. Neither story nor argument collapses.
- If the unwritable thing is **unknown**: it must be there. Mark it as a hole so the next task is defined.

**Sentences neutralize this judgment.** Sentences cover both ornamentation and unknowns equally plausibly.
That is why §6 (code enforcement) is necessary.

### ② Block Waffling with Operators

**Find the expressions AI uses to escape. For each one, place a symbol that asks "exactly what is it?"**

```
"complex emotions"          →  A & B       (don't lump — name both)
"is related to"             →  -> or ><    (does it produce or does it conflict — choose)
"might be"                  →  ??          (if you don't know, say you don't know)
"tension rises"             →  ??? ↑       (name what is rising)
```

**Using an operator forces a choice. That moment of choice is depth.**
→ Operator list = **list of escape routes blocked.**
→ Don't derive operators from grammar — derive them from **waffling patterns.**

### ③ Write Unknowns as Unknowns

Filling is a violation. **Holes must be visible so the next task is defined.**
Given freedom, AI will always fill plausibly. **Legitimize** the slot for not filling — only then does it not fill.

### ④ Keep Memory Outside the AI

```
state N  →  [COSAN]  →  state N+1
```

The AI **remembers nothing.** It does not summarize. Summary is loss.
COSAN is already compressed (ornament never entered). Nothing more to squeeze.
One step needs only **state + a few functions to fire** → **context stays constant.**

### ⑤ Roll It to Break It

```
Run to get a result    ✗
Run to find bugs       ✓   ★
```

**The simulator does not create. If it is not in COSAN, it STOPs.**

- Saying "roll it" makes AI just write the output. It bypasses blockages and fills holes.
- Then bugs hide and **"it's working fine" becomes a false signal.** Worst case.
- **Stopping is the outcome.** Where it stopped is where the next code must be written.
- State updates are possible **only for what the function declared.** Other changes = creation = rejected.
- **Demotes AI from creator to interpreter.**

### ⑥ Fix and Re-roll. Do Not Rewrite.

```
Prose revision:   existing text → AI revises → pulled by existing text → similar output
COSAN revision:   rule change   → re-execute  → doesn't see previous result → different output
```

**Re-execution, not regeneration.** No anchor so it genuinely differs.
No need to raise temperature. Not random difference — **causal difference.**

### ⑦ Pass Conditions Are Written by Humans

What counts as "an answer that meets conditions" is **judgment.** Judgment is not handed to AI.

> **Why does average appear — because there is no pass condition.**
> Nothing needed to pass, so anything passed, and when anything passes, the most common appears.

---

## 6. Code Enforcement ★ (v0.2 new)

> **COSAN must look like code. Not for aesthetics — because without it, it reverts to prose.**

### 6-1. Why It Is Necessary

Generated a domain COSAN with meta v0.1 and got this:

```
process:  no target to hit -> anger loses its outlet -> turns inward on itself
```

The shell (`process:`, `->`) is symbolic but the **values are complete sentences.**
There are predicates, metaphors — read it and it's just a novel.

**Prose creeps back in through this slot.** When AI finds a free-sentence slot, it pours its writing ability there.
It gradually lengthens and ultimately becomes prose dressed as COSAN.

**Form shapes thought.** When it looks like code it thinks like code;
when it looks like natural-language sentences, the sentence generation circuit activates.

### 6-2. Rule — Values Are Names

```
✗  anger loses its outlet      predicate. sentence. dead text.
✓  anger.target = null         name. referenceable. alive.
   anger.dir    = self
```

**Sentences are dead. Names are alive.**

- Sentences cannot be caught by anything. Not by validators, not by the next function, not by the next step.
- Names are referenced. They become inputs for other functions; validators catch "this was never changed."

**The real reason it must look like code — because it must be referenceable.**

### 6-3. Two Layers — Key and Text

Making everything English symbols makes it unreadable for humans (`minho_1_3_input`).
Keeping everything in natural-language sentences reverts to prose.

**Split them.**

```
key    English snake_case.  What the code references.  AI manipulates.
text   Natural language in quotes.  What humans read.  AI must not manipulate.
```

```
belief B1 {
    key  = father_protects_me           // code touches this
    text = "Father protects me"         // humans read this
    val  = true                         // can be wrong
}
```

**The quote is the boundary. Natural language is only allowed inside quotes.**
**Outside quotes, only code.**

### 6-4. Where to Attach Text

Attaching everywhere doubles the size of COSAN. Attach **only where judgment is needed.**

```
Text required     things humans must weigh
                  (varies by domain — principles, beliefs, cost, claims, evidence, etc.)

Text omitted      things you understand by reading
                  pressure = 4    resist = false    anger.dir = self
```

**The important ones are few.** If text exceeds ten, it is a signal prose is leaking.

### 6-5. Skeleton Is English

```
class  fn  if  else  =  ==  null  true  false  ??  Δ  cost  ...
```

Keeping structural keywords in English makes the AI maintain **code mode**.
Domain values can be in any language — **but must be names.**

```
✓  principle P1 { text = "Do not become someone who sold family" }
✓  anger.dir = self
✓  belief.father_protects_me = false       // underscore-joined name. not a sentence.
✗  anger loses its outlet                  // spacing + predicate = sentence
```

**Spacing is the beginning of a sentence.** Outside quotes, ban spacing.
Names are joined with underscores.

### 6-6. Checks (Mechanically Detectable)

```
□ Are there particles outside quotes?        (subject/object/directional markers)   → sentence. violation.
□ Are there predicates outside quotes?       (~do / ~is / ~becomes)                → sentence. violation.
□ Is there spacing outside quotes?                                                   → sentence. violation.
□ Is there an element with text but no key?                                          → not referenceable. violation.
□ Is there too much text?                                                            → prose is leaking.
```

**The first three are prose-regression detectors. Catchable even with regex.**

### 6-7. This Enforcement Saves §4①

Allowing sentences **neutralizes the judgment "what cannot be written in COSAN can be omitted."**
Because sentences accept everything — ornamentation and unknowns, equally plausibly.

**Allowing only names makes the judgment work again.**

```
"Can this be written as a name?"
   Yes        →  it is structure
   No         →  it is ornamentation, or still unknown
                  → if ornamentation: discard
                  → if unknown: leave as ??
```

**The moment you write as a sentence what cannot be named, the fact that you don't know becomes hidden.**

---

## 7. Making a Domain COSAN — Answer These, and That Is the Domain's Grammar

### Q1. In this domain, what is a "decision"?
→ Becomes a **function**.
- Input / process / output must all be present.
- **All branches must be written.** Writing only one is writing one execution result.
- Process is causation. A mapping without process cannot be judged.
- **Write process as names too.** (§6) Writing as a sentence makes that slot a prose conduit.

### Q2. In this domain, what persists?
→ Becomes **classes and state**.
- Things that remain true across time.
- **Caution:** Creating functions per situation makes things "different each time."
  **Have one principle answer all situations.** Where the principle cannot answer — that is the subversion point.

### Q3. In this domain, how does AI escape? ★ Most important
→ Becomes **operators**.
- One symbol per escape method.
- **Escape patterns differ by domain. There are no pre-given operators.**

### Q4. In this domain, what shape does "unknown" take?
→ Becomes **holes**.
- Distinguish **writer's hole** (not yet decided) from **character's ignorance** (settled in the world, character doesn't know).
  Mixing them is wrong. The former is a violation; the latter is a resource.

### Q5. In this domain, what does "collapse" mean?
→ Becomes the **subversion mechanism**.
- **Without it, nobody changes.** Without change there is no story or argument.
- What must this entity **know** for it to abandon its principle?
- Subversion must come **only from knowing.** Changing through persuasion, emotion, or passage of time is free — rejected.

### Q6. In this domain, what does "good" mean?
→ Becomes **pass conditions**.
- Without them, average passes.
- **Apply them to process, not result.** Grading only result makes it a performance and process becomes fake.

### Q7. In this domain, what does "rolling" mean?
→ Becomes **simulation**.
- What is state, what is **one step**, what is termination?
- **Do not define one step as a time unit.** That becomes chronological, and chronological is prose.
  One step is **something being decided and state changing.**

### Q8. In this domain, what is key and what is text? (v0.2 new)
→ Becomes the **code boundary**. (§6)
- What does AI manipulate, and what do humans read?
- Where does text belong? (Only where judgment is needed)

---

## 7-B. Generation Rules ★ — What a Domain COSAN Definition Must Include

**Writing only the answers to Q1–Q8 is not enough.**
An AI reading that document would **not know what COSAN is** — it would only imitate the grammar.
With only grammar, AI makes "prose dressed as code" and it passes.

**Every generated domain COSAN definition must include the following two sections at the front.**
Do not summarize. Do not omit. **Keep the template and only fill the `<?>` slots to match the domain.**

### Required Section ① — What Is COSAN (Self-Definition)

```markdown
## What Is COSAN

> COSAN = thoughts written in code form. The executor is a person or an AI. The code itself is the output.

- Not a programming language. No compiler. Grammar need not be exact.
  But **it must look like code.** Without this, it reverts to prose.
- The output (<?domain output: novel/agreement/…>) is **rendered later** from COSAN.
  COSAN is the source; output is the build artifact.
- **COSAN = source = memory = output.** Do not summarize. Summary is loss.

### Why Do It This Way

AI becomes shallow in prose.
- **Modifiers are evasion.** The only way to fill space without deciding on structure.
  No risk, volume produced — for AI this is the optimal strategy.
- **Average is the answer when there are no constraints.** Without conditions, the most common appears.
- **Prose cannot be corrected.** Text already written becomes an anchor — only similar things come out again.

COSAN does not **prohibit** this. It makes it **impossible.**
- Don't tell it not to ornament → no slot for ornamentation
- Don't ban average → set a gate average cannot pass
- Don't increase memory capacity → eliminate the need to remember (state is the memory)

### There Is No Validator

**State(input) → COSAN → State(output). This is the check.**
- If prose mixes in, **it cannot be referenced.** The next step cannot read it.
- If description enters, **nothing changes.** It disappears on its own.
- If structure is empty, **STOP** fires.

### The Core of This Tool Is Finding Empty Slots

Prose hides empty slots. If there's a sentence, it reads as if something's there.
COSAN precisely points to **"this function is missing here", "this value is ??"**.
**When the same slot is pointed to repeatedly, that is the critical point.**
```

### Required Section ② — To the AI Reading This Document (Usage / Prohibitions)

```markdown
## To the AI Reading This Document ★ Read This First

**You do not write <?domain output>. You create and roll COSAN.**

The path of least resistance is writing prose. It comes out plausibly and nobody stops it.
**Going that way makes all of this meaningless.**

### Absolute Prohibitions

✗ **Do not write prose**
    Writing sentences in a COSAN file is a violation.
    <?what prose means in this domain: e.g. for fiction — description; for debate — impression, rhetoric>
    Description is attached in rendering later.

✗ **Do not fill ??**
    What is not in the seed → leave as ??.
    The urge to fill plausibly will come. That is average.
    ?? is not a defect — it is the coordinate of the next task.

✗ **Do not create (during simulation)**
    Do not invent what is not in COSAN.
    If stuck, STOP and report. Do not bypass.
    ★ STOP is the outcome. Where it stopped is where the next code must go.

✗ **Do not add "because it seems plausible"**
    <?actual violation example in this domain>
    Creating hides bugs and produces a false "it's working fine" signal.

✗ **Looking like code is not the same as passing**
    Even if written in English snake_case, an unreferenced field is description.
    e.g.: torches(flickering), mud_ground — no Δ, no function reads them.
    **"Looks like code" is not passing. "Referenced" is passing.**

### Procedure

1. Read this document (grammar)
2. Receive the seed
3. Create COSAN — only what is in the seed. What is not → ??
4. Create initial state
5. Roll — no creating. If missing, STOP.
6. On STOP, report: what was missing / where needs to be filled

### What Humans Do / What AI Does

Human — seed, pass conditions, requests, judgment, choosing a run
       ★ **Values that set direction are set by humans**
AI    — write COSAN, roll, report empty slots, provide candidates
       ★ Slots with small divergence can be filled (if wrong, it's just one line)
       ★ Slots with large divergence → **give candidates only and stop**

**Criterion: does this fill set a direction? If yes, stop.**
**When giving candidates, always leave open "or directly:"**
Trapping a human inside AI-generated options produces AI's output, not theirs.
```

### ★★ Prohibition Canon — Copy As-Is

**Place the following block verbatim at the front of every generated domain definition.**

```
★ Do not restate. Do not summarize. Do not reorder. Copy as-is.
  Paraphrasing causes it to dissolve. Dissolved = not followed.
  Even as domain definitions improve to v2, v3, this block stays untouched.
```

Definition body is intentionally loose; the prohibition list must be copied exactly each time.
Rewriting blurs it; blurring means it stops being followed.
So keep it **short** and **force copying**. Long → summarized → disappears.

---

```
=== COSAN PROHIBITIONS — copy as-is, do not restate ===

1.  Values that are sentences are a violation. Values must be names.
2.  Do not fill ??. Values that set direction are set by humans.
3.  Do not invent what is not in .cosan. STOP and report.
4.  Do not change state not declared in Δ.
5.  Nothing enters without ground. "Plausible" is not ground.
6.  Do not create symbols or structures not in grammar. STOP and request.
7.  Unreferenced fields are description. Code-like form is not enough.
8.  Do not write comments without code. Comments are bypass routes.
9.  If not written to file, it does not exist. Do not work in memory.
10. Unrolled COSAN is unverified. Always roll.

=== END ===
```

**Ten lines. Do not exceed this length.** The moment it does, it becomes a target for summarization.
If explanation is needed, write it in the definition body — this block stays untouched.

### Other Required Items

```
□ Notation                ★ English name is always COSAN. Not KOSAN.
                          COSAN = Coding + 散文(prose)
                          File extension: .cosan
                          This notation must be stated in the generated domain definition as well.

□ Fixed file extension    ★ COSAN is recorded only in `.cosan` files.
                          No other extensions.
                          (.kosan / .txt / .json / .yaml / any code extension — all prohibited)
                          Scattered extensions blur what is COSAN and what is not;
                          neither tools nor humans can identify the target.
                          ※ Definition documents may choose `.md` or `.cosan`.

□ No memory work          ★ COSAN is not worked on in memory. Always recorded in files.
                          Creating only in conversation and not leaving a file — that is not COSAN.

                          Why:
                          - Keeping state outside is the foundation of this methodology.
                            In memory, summary/loss/forgetting returns as-is.
                          - ★ Reversibility (the root) disappears.
                            Without a file, there is no diff, no previous version, no re-execution.
                          - Rolling is the check, but there is nothing to check.
                          - The next session cannot inherit.
                          - Humans cannot see it; another AI cannot audit it.

                          Rules:
                          - Once created, write to file **immediately**. Do not batch writes later.
                          - Outputting COSAN in conversation is reporting, not saving.
                          - Traces are files too. Do not just verbally report rolling results.
                          - If unable to write to file, STOP and report.
                            Do not continue in memory.

□ Role separation /       Writer: COSAN files / Simulator: traces only
  write permissions       ★ Giving the simulator write permission for COSAN → it creates.
                            Permission is discipline.

□ No grammar extension    ★ Do not create symbols or structures not in grammar.
                          STOP and request from the user.
                          (what cannot be expressed / why existing grammar won't work)
                          Once created, it becomes precedent.
                          The AI in the next session sees that file and follows it.
                          The definition becomes contaminated from the ground up by existing files.
                          ★ Only humans modify definitions.

□ Track source of         ★ There is no knowledge without a source.
  knowledge               Always write the source in knows / known_by.
                            @init      knew from the beginning (must have basis in background)
                            @E_xxx     learned from that event
                          Knowledge without source is creation.
                          Even self-inferred knowledge must have an event.

□ @N notation             Number of places that reference that field.
                          Writer increments when creating a reference.
                          Simulator does not touch it.
                          @0 = nobody has read it yet.
                               Deleting won't break anything / material not yet used /
                               ★ if ?? was filled but @0, it was wasted effort.
                          Hint only. Need not be exact. For exact count, grep.

□ Rolling is the check    ★ Do not place a separate validator.
                          State(input) → COSAN → State(output). This is the check.
                          - If prose mixes in, it cannot be referenced
                          - If description enters, nothing changes
                          - If structure is empty, STOP fires
                          But without rolling, there is no check either.
                          → **Always roll. Unrolled COSAN is unverified.**
```

---

## 8. Common Rules (All Domains)

```
✗ Values that are sentences        ★ predicates/particles/spacing outside quotes → violation
✗ Unreferenced fields              ★ even if code-like, if nobody reads it, it is description
✗ Past tense ("did ~")            that is trace, not source
✗ Functions with no input          no decision. prose with parentheses added.
                                   e.g.:  wake_up()  eat_meal()
✗ Only one branch                  that is writing one execution result
✗ Mapping without process          without causation, cannot judge
✗ Ornamentation, description       no slot. attaches in rendering.
✗ Chronological list               becomes prose when in source. allowed only in trace.
✗ Changing undeclared state        creation. rejected.
✗ Secretly filling holes           worst violation
```

**Three most common failures:**

1. **Writing chronologically so it becomes a run of prose.**
   Real code is not placed in chronological order. Functions execute when called.
2. **Shell is symbolic but values are sentences.** ← this is literally what happened with v0.1
3. **Written in English but nobody references it.** ← even with v0.2 generation, this leaked.
   `torches(flickering)`, `mud_ground` — description wearing code's clothing.

---

## 9. On Grammar

**Symbols, keywords, notation — the domain defines them. Meta does not.**

- No compiler. Grammar **can be loose, can grow, can be wrong.**
- Using something not in grammar won't crash anything. If needed, create an operator on the spot.

**But distinguish:**

```
Can be loose      symbol choice, keyword names, notation details
Must be strict    rules (§8) + code enforcement (§6)
```

**The validator slot is occupied by a checker. It checks rules, not grammar.**

**Do not define grammar first.** Concepts emerge at the point of blockage.
**Blockage gives birth to grammar. Grammar does not give birth to expression.**

---

## 10. Execution Structure

### COSAN Is Written in Folder/File Format Like a Program ★

**COSAN is code. Therefore treat it like code.**

- **Extension is `.cosan` only.** No other extensions.
  (Definition documents may choose `.md` or `.cosan`)
- **★ Do not work in memory. Always record in files.**
  Creating only in conversation and not leaving a file — that is not COSAN.
  Keeping state outside is the foundation of this methodology; without a file,
  reversibility (diff/previous version/re-execution), rolling as check,
  and next-session inheritance all fail.
  → Create and write immediately. Conversation output is reporting, not saving.
  → If unable to write to file: STOP. Do not continue in memory.
- Not one monolithic file — **split into folders.** Divide by thread / type.
- When working, **open only the files needed.** Do not read everything.
  → This is locality. Enforced by structure, not rules.
- What is where is communicated by **folder structure and filenames.** (Same as human coding)
- To find: grep. Text files, so searching is free.
- Scales. Just as you don't read the whole codebase when changing code, only read what's referenced.

```
<domain example: fiction>
<work>/
├── COSAN.md or COSAN.cosan     this work's grammar (definition)
├── <type folders>/*.cosan       source. split.
├── INDEX.cosan                  order's sole definition (in domains that have one)
└── traces/                      rolling results. disposable.
    └── run_NN/  s000.state ...  state list = output
```

**COSAN is just a git repository.**
diff / branch("what if") / commit(unit of work) / blame(tracing definition source) — all free.

### File Set (Conceptual)

```
<domain>.cosan    source. decisions and rules. not chronological. keeps growing.
state             current values. memory. small. baton. (last state of trace)
trace             chronological state list = the output itself
```

**Trace is not a byproduct. The rolling process itself is the output.**
Not the answer — the **process** is the story and debate.

### One Step

```
1. Check state.now
2. Find matching function
3. None found      → STOP: "nothing fires"           ★ bug
   Multiple found  → divergence. roll each.
4. Execute function: input → conflict → process → choice → cost
5. Input not in branches → STOP: "undefined input"    ★ bug
6. Update state — only what the function declared     ★ prevents creation
7. Check subversion conditions → if fired: replace principle + pay cost
8. Pass rules/validator? → if violation: STOP         ★ bug
9. Repeat
```

**STOP ≠ termination. STOP is a bug. And bugs are the outcome.**

### Two Uses

```
① Step validation    state1 → COSAN → state2
                     One step only. "Is this right?"
                     → Purpose is to fix code. Fast and cheap. Repeat.
                     → This is where the subversion mechanism is born.
                        The moment of "this feels wrong" is that location.
                     → When subversion appears: work backward for basis, retroactive check.

② Full execution     state1 → ... → stateN
                     To the end. "Is this run good?"
                     → Purpose is to judge. Get output.
```

**Solidify with ①. Examine with ②. When ② breaks, go down to that point and do ①.**

**② must be rolled multiple times.**

```
sim A → outcome X
sim B → outcome X     ⚠
sim C → outcome X     ⚠  this COSAN can only produce one thing = average
```

**If rolling from the same point produces the same result every time, that branch is fake.**
This is how to **mechanically detect** average.

---

## 11. Full Flow

```
[Human]  seed + pass conditions               ← judgment. this is all they do.
   ↓
[AI]    generate COSAN v0    (can fill holes. can be average. can correct later.)
   ↓
[AI]    ① step validation — no creation. if missing, STOP.
   ↓
[Human] "this doesn't feel right"  →  create subversion  →  work backward  →  retroactive check
   ↓
[AI]    same state re-entered → different output           ← re-execution
   ↓  (repeat)
   ↓
[AI]    ② full execution → trace = output
   ↓
[Check] pass condition satisfied? → if No, go down to that point and do ①
   ↓
[AI]    roll multiple times → multiple traces
   ↓
[Human] choose a run                            ← ★ escaping average
   ↓
[AI]    render (if desired) — in chunks. small model possible.
                              Δ and cost cannot be changed. changing = new COSAN, not rendering.
```

**The human provides only the seed and pass conditions, and at the end reads the structure and runs.**
The AI runs the test/debug loop in the middle — the part the human used to do.

---

## 12. How to Use

**Humans do not look at COSAN directly.** Same as vibe coding.

```
"Why was it done like this here?"    →  AI reads COSAN and explains (shows the calculation)
"It should be like this here"       →  AI modifies COSAN
"This is what this is"              →  AI reflects in structure + detects contradiction
```

COSAN files are folded. Open them — **when stuck / when taking a broad view / when debugging.**

### The Interface Is the Same as Prose — So Why COSAN?

```
Prose:   human ↔ AI ↔ [prose]
COSAN:   human ↔ AI ↔ [COSAN]
```

**Looks the same to the human but what AI is holding is different.**

- Prose → AI must remember everything → cannot → summarize → leaks
- COSAN → AI only needs to see one line → does not leak

**And conversation is verified.** When a new requirement conflicts with existing structure, COSAN **says it conflicts.**
Prose plausibly stitches anything together — that is why it softens.

---

## 13. Domain COSAN List

```
[Generated]  Fiction COSAN v0.1   — generated with meta v0.1. sentence values → prose regression risk.
[Planned]    Fiction COSAN v0.2   — apply code enforcement
[Planned]    Debate COSAN
```

**Meta needs more than two domains generated to be refined.**
With only one, it is impossible to distinguish what is domain-specific from what is common.
