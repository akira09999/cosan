# FICTION COSAN v0.5

> Answers to Meta-COSAN Q1–Q8 applied to fiction. This document is the grammar for the fiction domain.
> **v0.4 → v0.5 changes:** Corrected the rolling procedure to be INDEX-centered; added acts and themes.

```
Fiction COSAN definition  →  <work>.cosan  →  roll it  →  trace  →  (optionally) render = novel
```

---

## v0.5 Change Summary ★

```
1  INDEX           Sequential. Tree/branch removed. Branching via git branch.
2  Rolling procedure  Explore → read INDEX. when = trigger condition → order validator
3  Conflict handling  New. All → STOP → human. Source is written by humans.
4  Act             New. Event grouping. Human designates. Simulator does not read.
5  Theme           New. Color of the whole story. Writer only reads. Optional.
6  @N notation     Not adopted. Reference count done via grep instead.
7  Extension       .kosan / .cosan mixed → unified to .cosan.
```

---

## 0. Core Premise of This Domain

```
Novel  = the chain of decisions where a character keeps or abandons a principle
Event  = pressure from the world.  ★ occurs independently of characters.
Description = rendering output.  no slot in the source.
```

**A writer originally works in two layers — notes (relationship map) and manuscript (prose).**
AI had no notes. Only the manuscript. So when stuck it re-read the manuscript,
reading caused drifting, drifting caused forgetting.

**COSAN is those notes. But not a relationship map — it is code.**
- A relationship map is static and cannot be rolled. A writer rolls it in their head. **AI cannot do that.**
- Code rolls. And code is the form AI has trained on the most.
- Insertion / reference tracking / conditional branching / refactoring — all things AI already does well.

> **This moves fiction into the domain AI already excels at. It does not demand a new capability.**

---

## v0.4 Core Revisions (Retained)

### Revision 1. Events Do Not Come from Characters

**v0.3 error:** "Events are not invented. Find the existing tension and detonate it."

**Wrong.** That locks the number of events to the **number of characters.** And the world dies.

```
Cause    Why did the goblins appear?        → world.  unrelated to characters.  freely invented.  unlimited.
Meaning  What does it touch in a character?  → character.  if nothing, it just hasn't landed yet.
```

The goblins are just there. They did not appear because of Sharo.
**A big world has many events. Unrelated to number of characters.**

**Only constraint:**

```
✓  World gives pressure       goblins attack
✗  World solves problem       a knight order conveniently appears to rescue     ← coincidence.  banned.
```

**Only pressure. No resolution.**

### Revision 2. Empty Δ Is Fine

**v0.3 error:** "A step with no Δ does not exist."

**Too strict.** With that rule every event must shake a character,
that causes characters to collapse in one blow, which is exactly **gratuitous awakening.**

**Stories move by accumulation.**

```
Event1 (goblin)   Δ none.  But leaves a trace.  ← ★ this is fine
Event2            bites event1's trace.  Δ: world.fact created.  character not yet.
Event3            bites event2.  Δ: sharo.suspicion ↑      ← first slight movement
Event4            bites accumulation.  Δ: belief.val = ??   ← starting to waver
Event5            ...              Δ: principle X           ← collapse
```

**One event does not collapse a character. Five accumulated events collapse a character.**

**An event's value is two things:**

```
① Δ        what changes now             → can be 0
② leaves   what remains for next to bite  → ★ this must exist
```

**Revised rule:**

```
✗  A step with no Δ does not exist
✓  Only a step with neither Δ nor leaves does not exist
```

### Revision 3. Events Must Not Be Complete

The problem with the card approach (small story completing as need → resolution) is this:
**When complete, there is nothing left to bite. It must be incomplete to continue.**

The goblin battle changing nothing and ending is actually good.
**A body remained, a sound was made, and why they were starving is still empty.**

---

## Q1. What Is a Decision? → `fn`

**Decision = the thing where a character abandons either a principle or a pressure.**

```
fn <n>(<inputs>) {
    when    <state_condition>
    clash   <principle> >< <pressure>     ★ no clash = not a decision
    proc    <n> -> <n> -> <n>    ★ by name.  no sentences.
    branch  <input_val> => <choice> ! <cost>
            <input_val> => <choice> ! <cost>
            _           => STOP:undefined_input
    Δ       <state.field> = <val>
}
```

- **2 or more branches.** One branch is an execution result, not a function.
- **`!` cost missing from branch is a violation.** A choice without cost is not a decision.
- No-input functions are banned. `die()` is prose with parentheses.

**Note:** If clash does not fire, that is not STOP — it is **"hasn't landed yet."**
The fight just passes. And that is fine. (Revision 2)

---

## Q1'. What Is an Event? → `event`

```
event E_<n> {
    origin   world | character
    what     "A goblin horde attacks"        ← invented.  freely.
    when     <condition>                     ← check if this position is right.  ★ does not set order.
    hooks    <prior_event>.<leave>           ← what from prior event does it bite  (optional)
    proc     <n> -> <n> -> <n>    ← action order within event.  by name.  no sentences.  (optional)
    Δ        <state change>                  ← can be 0
             reveals [F*]                   ← list of facts whose known_by updates in this event.  no calculation.
    leaves   [ <what remains>, ?? <undecided> ]     ★ hook for the next.  must exist.
}
```

```
event E_goblins {
    origin   world
    what     "A goblin horde attacks"
    when     distance > 0
    Δ        goblin.count = 0
             clock ++
    leaves   [ corpses, noise, ?? why_starving, ?? how_sharo_fought ]
}

event E_corpse_find {
    origin   world
    what     "A human signet ring is found on a goblin corpse"
    hooks    E_goblins.corpses              ← ★ bites prior event
    when     combat.ended
    Δ        world.F3 { text = "A human passed this way before", val = true }
             sharo.suspicion ↑              ← very slightly
    leaves   [ ?? whose_ring ]
}

event E_ring_owner {
    origin   world
    what     "The ring's crest belongs to the Order"
    hooks    E_corpse_find.?? whose_ring
    Δ        world.F4 { text = "The Order sent someone ahead", val = true }
             sharo.suspicion ↑↑
             esran.mask.crack ↑             ← ★ the moment where a character must answer
    leaves   [ ?? why_did_order_go_first ]
}
```

### Events Have No Order ★ v0.5 Correction

Only `when` and `hooks` — **no order.**
That way **they can be inserted in between.**

```
E_goblins  →  [ 10 events ]  →  E_dragon
                   ↑
             add one more here later
             without touching before or after.
             the fn's that follow reference state → the following automatically differs.
```

**Order lives only in INDEX.** Do not put it in event definitions.

**★ v0.5:** `when` is **not a trigger condition.** It is an order validator.
INDEX says "next is E_x," and `when` checks "is this position right?"
If false, **INDEX is wrong.** STOP and human corrects.

**Prose:** to insert something between events 5 and 6, rewrite the end of 5 and start of 6.
**COSAN:** hook it in and add it to INDEX. Then **re-roll and the following automatically differs.**

### Events Make the Character Get Dug Into

Not digging into the character in advance. **The event points to the character, and then it is dug.**

```
E_ring_owner reveals the Order ring
   ↓
fn esran.on_ring_found()
    clash  P3(Order's command) >< mask(on)
    branch ??                              ← ★ now it must be filled
```

**Not asking "what is Sharo's wound?" from a blank slate,
but asking "what does Esran say when seeing the Order ring?"**
Far easier, and far more precise.

---

## Q1''. What Is an Act? → `ACT` ★ v0.5 New

**Act = event grouping. Boundaries fall between events.**

```
ACT A<n> { text = "..." }
```

```
- ★ Human designates.  AI only suggests.
- Boundaries always fall between events.  Do not cut events.
- Lives only inside INDEX.  No separate file.
- ★ Simulator does not read.  No effect on rolling.
```

**The key point is that the simulator cannot read it.**
If it can be read, acts become a new creative conduit — "act 2 so something must explode here" is
exactly "because it would make a good story." If it cannot be read, that is impossible.

**Only two things read acts:**

```
Human       overview.  "where are we now?"
Renderer    chapter dividing
```

> **An unreferenced field is description — so the formal rule applies.**
> The reason it applies is **because the reader is a human, not a machine.**
> `text` is that kind of slot. Kept as an intentional exception.

---

## Q1'''. What Is a Theme? → `theme` ★ v0.5 New

**Theme = color of the whole story. A declaration. Not inside the plot.**

Films are like that. The theme is written nowhere in the plot, yet reveals itself over the whole.
**Theme is not an event. Not a fact. Certainly not a state.**

```
theme T<n> {
    text  = "..."                        ← human writes
    since = init | @ E_xxx | @ A<n>      ← from when is this the color of the story?
}
```

```
- Optional.  ★ Do not put in PASS.
- Multiple allowed.  ?? for undecided also allowed.
- Can appear later.  Declare when the story touches a theme.
```

### Who Reads It ★

```
Simulator    ✗ does not read.  no effect on rolling.
Writer       ✓ reads.  gives color when filling ?? / generating candidates.
Renderer     ✓ reads.  prose style and focus aim toward theme.
```

**The reference point is generation time, not execution time.**
So it is not an unreferenced field. But **rolling does not know theme.**

### Where It Acts

```
✓  when generating ?? candidates    candidates tinted toward theme are mixed in
✓  when suggesting events           what of the event aims toward theme
✓  branch / cost candidates         among equally weighted options, the theme-side is mixed in
✓  rendering                        style, focus, what gets lingered on

✗  ground for changing Δ           theme cannot touch state
✗  ground for bypassing STOP
```

### ★ Prohibition — Theme Is Not a Creative Alibi

```
✗  Do not create with "because it matches the theme"

    Theme tilts candidates — it does not create facts.
    If something not in COSAN is added because of theme,
    that is exactly adding it "because it would make a good story." The worst violation.

    ★ Theme is not a filter — it is a color.
      It does not create options; it tilts among already-possible options.
```

**If stuck, it is still STOP. Even with a theme, it is STOP.**

### What Happens to What Came Before When Added Later

```
★ Human decides.  No default.
```

**AI does not judge.**
Theme can enter through metaphor, so it cannot be mechanically determined where the story touches it.
Trying to find out causes plausible invention. **Only provide candidates and stop.**

```
When adding a theme, what AI does:

    1. Show list of events before since          ← list only.  no interpretation.
    2. Provide candidates:
         ① Leave what came before as-is
         ② Retroactively render only  (Δ unchanged)
         ③ Re-roll what came before
         ④ Directly:
    3. Stop.
```

What was decided is not written in COSAN. Decisions remain in commits and conversation.

---

## Q2. What Persists? → `class`

```
class character {
    principle   P*      ★ text required.  scope required.  breaking has cost.
    belief      B*      ★ text required.  val: true | false | ??   ← ?? is the wavering
    wound       W*      the place where touching it shakes a principle
    bond        <n> : int
    mask        on | off
    resource    <n> : int
    background  { origin / since / cover }    ← origin/history/nominal  (optional)
    ability     <n> { text = "..." }                        ← passive ability.  always active.  no trigger needed.
    skill       <n> { text = "...", requires = <ability>, trigger = <condition> }
                                                               ← active ability.  referenced in proc.
                                                               ← requires: cannot trigger without that ability.
                                                               ← trigger: auto-triggers when condition met. regardless of will.
    knows       [<fact_key>...]
    ?!          [<fact_key>...]       ← in the world but character doesn't know.  fuel for subversion.
    suspicion   [ <int> @ <event> ]   ← accumulation history.  doesn't change in one blow.  @ init is starting value.
}

class world {
    fact        F*      ★ true but may be unknown to all.  known_by = []  ← resource
    factindex {         ← index grouping facts by topic.  F* list only.  no calculation.
        <tag>:  F* F* ...
    }
    clock       int
    distance    int
}
```

### background Structure

```
background {
    origin  <origin>           // where from.  -> can chain history
    since   <time>             // since when in this state  (optional)
    cover   "<official reason>" // the nominal reason put forward  (optional)
}
```

- `origin` : simple value or `A -> B` (flow of history)
- `since` : `childhood` / `init` / `@ E_xxx`
- `cover` : official reason. if present, it differs from reality. if absent, nominal and actual are the same.

```
// example
background {
    origin  street_vagrant -> church_ward
    since   childhood
    cover   "The Order tends to them"
}
```

### known_by @ Notation

Not just who knows, but **when they came to know.**

```
known_by = [ esran @ init ]        ← knew from the start.  background.
known_by = [ esran @ E_xxx ]       ← came to know in that event.
known_by = [ reader @ E_xxx ]      ← the point disclosed to the reader.  independent of character knowledge.
known_by = [ reader @ ?? ]         ← disclosed to reader at some point but timing undecided.
```

- `@ init` : knew before the story began. background setting.
- `@ E_xxx` : came to know in the event's Δ. tied to event.
- `@` absent, name only : timing undecided (same meaning as `??`).
- `reader` : reserved word. tracks reader's awareness timing. do not use as character name.
  - `reader @ E_xxx` : disclosed to reader in that event's rendering.
  - `reader @ ??`    : disclosed to reader at some point, timing undecided. do not expose in rendering.
  - no `reader`      : reader disclosure undecided.

> **`@` is exclusively for timing.** Do not use for reference count (`@N`).
> To count references, grep.

### Principles Must Have scope

```
✗  P1 { text = "Complete the contract" }
      → AI has no way to check. not defined what must be kept.
      → flows past.  even if violated in the next scene, nobody catches it.

✓  P1 {
       text  = "Complete the contract"
       scope = [ kill_target(dragon) ]      ← ★ what does it apply to?
       break = refuse | abandon             ← how is it violated?
       cost  = livelihood_zero              ← what is lost if violated?
   }
```

**Can be empty at first. The moment it is referenced, it must be filled.**

```
P1 is referenced in the goblin event
   → "Does killing goblins fall under the contract?"
   → ⚠ scope is missing
   → fill it:  scope = [dragon]
   → ★ a new fact is revealed: goblins are outside the contract
   → then why does Sharo kill goblins?  ← new hole
```

**Reference demands definition, and definition births new holes.**

### Rolling Validates the Definition

Once the definition is filled, **roll again.**

```
step 3  clash P1 >< B1
        ⚠ P1.scope = [dragon] but target is goblin
        → P1 does not fire → clash does not hold
        → STOP: the clash in the prior step was wrong
```

**Filling the definition invalidated the prior step. That is correct.**
**Rewinding state is the check. No separate validator needed.**

---

## Q3. How Does AI Escape? → Operators

| Escape | Operator | What is forced |
|---|---|---|
| "complex emotions" | `&` | name both |
| "was related" | `->` / `><` | choose: produces or conflicts |
| "might have been" | `??` | if you don't know, say so |
| "tension escalated" | `↑` `↓` + variable name | name what is rising |
| "he grew" | `Δ` | write before → after |
| "ultimately his heart moved" | `!` cost | no gratuitous change |
| "was persuaded / was moved" | `reveal` only | subversion comes **only from knowing** |
| "time passed and" | banned | steps are decisions, not time |
| "help conveniently arrived" | `origin: world` constraint | world gives pressure only. cannot give resolution. |
| "because it matches the theme" | `theme` read restriction | theme is color, not fact  ★ v0.5 |
| pretty sentences | no slot | attached in rendering |

```
&      two things simultaneously true
><     mutually incompatible
->     causation (produces)
=>     selection (chose)
??     writer's hole / unconfirmed value     ★ filling it is the worst violation
?!     character's ignorance (settled in world)  ★ resource
Δ      state change
!      cost (irreversible)
↑ ↓    named numeric increase/decrease
X      principle broken
hooks  bites a prior event
leaves hook for the next
```

### No Comments

```
✗ Comments with no code
    Comments are not COSAN.  Nobody references them.
    If it cannot be written as code, it is one of two things:
      - ornamentation → discard
      - still unknown → write as ??
    ★ Writing as comment is a new conduit for prose regression.

✗ Writing as comment because there is no grammar for it
    → that is a STOP signal.
    → report: "there is no grammar to express this"
    → user revises the definition.
    ★ Do not bypass with comments.  Comments are bypass routes.
```

---

## Q4. What Shape Does "Unknown" Take?

```
??   writer's hole     not yet decided.        → filling it is a violation.  next task is here.
?!   character's ignorance  settled in world.  → resource.  fuel for subversion.
```

### ?! — Independent Field in Character File

```
knows   [F8, F9]              // what is known
?!      [document_content]    // in the world, this character doesn't know it
```

- Paired with `knows`. If the same item is in both: **contradiction → STOP.** (conflict handling section)
- When something in `?!` is `revealed`, it becomes a trigger condition for `subvert`.

### belief.val = ?? Is the Wavering

```
B1.val = true    believes
B1.val = ??      ★ wavering.  neither true nor false.  ← this is the agony
B1.val = false   collapsed
```

**Seeing belief as boolean produces no agony.**
The `??` interval is what makes characters hesitate, and hesitation is visible to other characters,
and that changes relationships.

```
step  goblin.speaks & sharo.B1.val == true
      => sharo.B1.val = ??            ← not confirmed

step  fn sharo.decide()
      branch  B1.val == true  => kill      ! nothing
              B1.val == ??    => hesitate  ! time ↓    ← ★ hesitation
              B1.val == false => spare     ! P1 X

step  fn jillian.decide()
      when  sharo.hesitation == true       ← ★ Jillian sees it
      => support   ! mask.crack ↑          ← finding a kindred spirit cracks her identity
```

**Cascades emerge on their own.**

---

## Q5. What Does "Collapse" Mean? → `subvert`

```
subvert S<n> {
    trigger   reveal(F*)  ->  <character>.knows += F*
    check     B*.val == false
    effect    P<old> X -> P<new>
    cost      <n> & <n>            ★ must exist
}
```

**Rules:**
- Subversion comes **only from `reveal`.** Changing through persuasion, emotion, passage of time is gratuitous. Rejected.
- **Does not collapse in one blow.** suspicion must accumulate, belief must pass through `??`.
- After subversion, **retroactive check**: do prior steps not contradict the new principle?

**Subvert cannot be planned in advance.**
**The moment during step validation where "this doesn't feel right"** is where subvert must go.
Find that position → work backward for the condition (what must be known?) → retroactive check of what came before.

---

## Q5'. Who Resolves Conflicts? ★ v0.5 New

> **Source is written by humans. The simulator reads, checks, and stops.**

There are positions where the same fact is written in multiple places. **That is not duplication — it is cross-validation.**
Writing in only one place makes divergence detectable.

```
Detection targets

    event.Δ.reveals   ↔  world.fact.known_by
    INDEX order       ↔  event.when
    character.knows   ↔  character.?!          same item in both = contradiction
    character.knows   ↔  world.fact.known_by
```

**Handling — no exceptions:**

```
1. STOP
2. Report
     - what and what diverged
     - what each side says
3. ★ Human chooses.  AI does not judge which is correct.
```

**Simulator does not calculate. Does not derive. Does not choose.**
Even filling `known_by` from `reveals` is banned. That is creation.

```
STOP codes

    reveal_mismatch          reveals and known_by differ
    index_when_conflict      when of event specified by INDEX is false
    knows_contradiction      same item in both knows and ?!
    index_undefined          next in INDEX is ??
    undefined_input          input not in branch
```

---

## Q6. What Does "Good" Mean? → Pass Conditions

**Human writes. Applied to process, not result.**

```
PASS
□ Did every principle clash at least once?              uncollided principle is decoration
□ Did at least 1 principle get X'd?                    if none broken, character doesn't change
□ Was cost paid for every X?                           gratuitous change = performance
□ Did every subvert come from reveal?                  if changed through persuasion: rejected
□ Did belief pass through ?? interval?                 if flipped in one blow: gratuitous
□ Does every event have Δ or leaves?                   if neither: delete
□ Was every leaves eventually hooked?                  unretrieved = abandoned hook
□ Branching validity: rolling from same point — do outcomes diverge?
   if all same  → that branch is fake.  it is average.   ★ mechanically detectable
   ★ v0.5: "roll apart" = create a git branch and roll each
```

**Theme is not put in PASS.** Because it is optional.
**ACT is not put in PASS.** Because it is drawn by humans.

---

## Q7. What Does "Rolling" Mean? → Simulation

**One step = one decision or one event.** Not a time unit.

### Procedure ★ v0.5 Revised

```
1. Check state.now
2. Read the next event from INDEX        ★ do not explore.  INDEX decides.
3. ??            → STOP: index_undefined
   when is false → STOP: index_when_conflict
   true           → fire
4. event:  apply Δ + register leaves
   fn:     input -> clash -> proc -> branch -> cost -> Δ
5. input not in branch → STOP: undefined_input
6. Apply Δ — declared fields only.  others = creation = rejected.
7. Conflict check (Q5')  → if diverged: STOP
8. subvert trigger check → if fired: replace principle + cost + retroactive check
9. Repeat
```

**What disappeared from v0.4:**

```
✗  "search for event/fn matching when condition"      ← no search.  INDEX is the source.
✗  "if multiple → branch. roll each."                 ← no branching.  sequential.
✗  STOP: nothing_fires                                ← the concept of searching for candidates doesn't exist.
```

**Branching is not inside rolling.**

```
fn.branch      character's choice.  branches inside the decision.       ← source
trace          rolling multiple times.  experimental.  disposable
git branch     "what if."  merge the good one                           ← ★ this is where branching is
```

### To the Simulator ★

**You do not create. If it is not in COSAN, STOP.**

**Actual violations encountered (during v0.3 rolling):**
- **Invented** that goblins surrender when defeated. It was in neither seed nor COSAN.
  Added it "because it would make a good story." → **This is creation. The worst.**
- When you create, bugs hide and **"it's working fine" becomes a false signal.**

**What you cannot read:**

```
✗  ACT       humans draw it.  "act 2 so something must explode" is creation.
✗  theme     belongs to writer and renderer.  "because it matches the theme" is creation.
```

**Stopping is the outcome. Where it stopped is where the next code must be written.**

### There Is No Validator

**State(input) → COSAN → State(output) — this itself is the check.**

- If prose mixes in, **it cannot be referenced.** `proc anger_loses_its_outlet` cannot be read by the next step.
- If description enters, **Δ is empty.** Nothing happens so it disappears on its own.
- If structure is empty, **STOP** fires.

**Not banned. Made impossible.**

### If Grammar Is Insufficient, STOP and Request from User

```
1. STOP
2. Report to user
   - what cannot be expressed
   - why existing grammar won't work
   - if there is a suggestion, make it (left open so user can add something different)
3. User decides
```

### ★ Do Not Create Symbols or Structures on Your Own

Once created, it becomes precedent and **the AI in the next session follows it.**
Not the definition but the existing file becomes grammar.
**The definition is contaminated from the ground up.**

```
Grammar comes only from this document (FICTION_COSAN_v0.5.md).
Symbols and structures not in this document do not exist.
If insufficient: STOP.  Filling it is the user's job.
```

---

## Q8. Key and Text

```
text required (human weighs)    principle / belief / fact / wound / cost / event.what
                                 ACT.text / theme.text                    ★ v0.5
text omitted (self-evident)     suspicion / bond / mask / Δ / branch / proc / leaves
```

```
✓  principle P1 { text = "Complete the contract", scope = [dragon] }
✓  anger.dir = self
✗  anger loses its outlet              ← spacing + predicate = sentence
```

**If text exceeds ten, it is a signal prose is leaking.**
`theme.text` is excluded from this count. There are only a few per whole story.

---

## File Structure (git repository)

**COSAN is text. Therefore it is simply git.**

```
<work>/
├── COSAN.md                 this work's grammar (this document)
├── CLAUDE.md                role rules
├── THEME.cosan              ★ v0.5.  theme.  if none, no file.
├── characters/
│   ├── sharo.cosan
│   ├── jillian.cosan
│   └── goblin.cosan         ← things events created go here too
├── world/
│   ├── world.cosan          ★ clock / distance / F* / factindex
│   ├── church.cosan         ← ★ v0.5.  world elements in individual files
│   └── north_road.cosan
├── events/
│   ├── INDEX.cosan          ★ sole definition of event order.  sequential.  confirmed only.
│   ├── E_goblins.cosan      ← event definition.  no order.  only when/hooks.
│   └── E_corpse_find.cosan
├── state/
│   ├── s001.state           ★ output.  produced by rolling.  ← v0.5: not .cosan
│   └── s002.state
└── traces/
    ├── run_01.trace         ← validation.  experiment.  multiple.  disposable.
    └── run_02.trace
```

### Source and Output ★ v0.5

```
Definition   COSAN.md  CLAUDE.md                       grammar and rules.  not the work.
Source       THEME  characters/  world/  events/       ★ human writes.  .cosan
Output       state/  traces/                           ★ produced by rolling.  .state / .trace
```

**Extension is the boundary.** `.cosan` is what humans wrote, `.state` and `.trace` are rolling output.
Output can be deleted and restored by re-rolling. Source cannot.

**The simulator can only write `.state` and `.trace`.** Banning `.cosan` write
is determinable just by looking at the extension.

### world/ — Split into Individual Files ★ v0.5

`stage` is not used. Places, organizations, objects and other world elements **each have their own file.**

```
world/world.cosan     global.  clock / distance / fact / factindex
world/church.cosan    the Order
world/north_road.cosan north road
```

**The reason is locality.** Even as the world grows, the number of files opened does not increase.
Putting everything in one `stage` means as the world grows, you must read all of it every time.

**Where to put `fact`:** gather in `world.cosan`. Facts are not specific to a place,
and `factindex` must reference from one location for reference tracking.

### INDEX.cosan — Sole Definition of Event Order ★ v0.5 Revised

**Event definitions (E_*.cosan) have no order.** Only when and hooks.
That way they can be inserted in between.

**But "in what order things happen" is the skeleton of the story, and that is source.**
INDEX is the only file that holds that skeleton.

```
INDEX {
    ACT A1 { text = "Contract" }
        1   E_goblin_encounter
        2   E_goblin_combat
    ACT A2 { text = "Suspicion" }
        3   E_document_found
    ??                        ← what comes next?
}
```

```
★ Sequential.  No branching.  No tree.
```

- **Only confirmed items go in.** Undecided → `??`.
- Roll via trace to validate, then when decided, **fix INDEX.**
- ★ Fix INDEX, not trace. Dispose of trace.
- Inserting in between shifts the numbers. That is inserting an event in between.
- **When branching occurs, create a git branch.** Branching does not happen inside INDEX.
- ACT is drawn by humans. Works without it.

**Why the tree was removed:**

```
Branch inside INDEX     one file holds multiple runs
                        → which one is this work becomes blurry
                        → rolling must choose a path every time = judgment = creation risk

Branch via git          each branch has its own sequential INDEX
                        → rolling does not judge.  only reads.
                        → human chooses the run and merges     ★ escaping average
```

### state File — Snapshot After Event Fires  (`.state`)

```
fired   E_goblin_combat
from    s001
```

State files become material for prose along with INDEX.

**What git gives for free:**

```
diff        one glance tells what changed
branch      "what if" = branch.  roll multiple runs, merge the good one.   ★ v0.5: sole place for branching
commit      one event = one commit.  history of how the story grew remains.
blame       "when and why did this principle come to be?" → traceable
grep        "who reads this field?" → reference tracking                   ★ v0.5
```

**Open only the files needed for the work.**

```
"Will Sharo kill the goblin?"
   Open:    sharo.cosan + goblin.cosan + now.state
   Don't:   jillian, esran, world, other events
```

**Even with 20 characters, three files suffice.**
**Locality is enforced by structure, not discipline.**

---

## Role Separation (to be placed in CLAUDE.md)

```
Writer       reads: designated files + THEME    writes: COSAN files        does not roll
Simulator    reads: COSAN + state               writes: state + trace      ★ COSAN write banned
                                                                           ★ ACT / THEME read banned
Renderer     reads: INDEX + trace + THEME       writes: prose              ★ cannot change Δ
```

**Not giving the simulator COSAN write permission means it cannot create.**
When stuck, it can only STOP.

**Permission is discipline.** Not telling it "don't create" — **the means to create do not exist.**
**Taking away theme and act from the simulator is the same reason.**

---

## Rendering — Prose = INDEX + trace (+ THEME)

```
INDEX   what happens in what order             ← skeleton
trace   how state changed then                 ← flesh
THEME   what color the whole is                ← color.  optional.   ★ v0.5
```

- trace only without INDEX: list of state changes. no story.
- INDEX only without trace: list of events. no flesh.
- INDEX + trace → renderer (human or AI) converts to prose.
- THEME tilts what gets lingered on and what flows past. **Does not add facts.**

**The final trace after all definitions are complete is the output (material for prose).**

### Rendering Options

```
POV (point of view)
    omniscient / first-person / third-person limited (specific character)

Tense
    past / present

Type
    novel / drama script / screenplay / game scenario

Style
    dry / lyrical / hard-boiled / humorous / classical

Dialogue
    heavy / moderate / sparse / almost none

Creative range  (facts only 0 <-> not conflicting with facts 100)
    summary(0) / plain(30) / rich(50) / richer(80) / richest(100)
    ← how richly to express what is in COSAN.  cannot add facts not in COSAN.
```

**General rendering rules:**
- Do not show event numbers in prose.
- **ACT can be used for chapter division.** Whether to expose act names is decided by humans.
- Scenes flow naturally without breaking.
- Even with high creative range, facts not in COSAN cannot be added.
- **★ Even with THEME, facts cannot be added.** Theme is color, not fact.

**Pre-defined option sets:**
```
[plain]     3rd-person, past, novel, dry, dialogue moderate, rich(50)
[immersive] 1st-person, present, novel, lyrical, dialogue heavy, richer(80)
[outline]   omniscient, past, novel, dry, summary(0)
[tense]     3rd-person limited, past, novel, dry, dialogue moderate, rich(50)
```

---

## What Humans Do

```
1. Seed          character / world / pressure  (can be empty)
2. Pass conditions  what counts as good        ← this is not delegated
3. Request       "a goblin horde is encountered"  ← event request
4. Judge         see what AI filled and correct it  ← ★ seeing the wrong makes the right come to mind
5. Choose a run  from multiple traces / branches   ← ★ escaping average is here
6. Resolve conflicts  when STOP fires, which is correct  ← ★ v0.5
7. Draw acts     where between events to cut      ← ★ v0.5
8. Declare theme  if any.  optional.              ← ★ v0.5
```

**AI fills. Human corrects.**
**Without request, fill and roll** — show directly filled result without offering options. "This doesn't feel right" comes out precisely.
**With request, give options** — human can choose, or choose something outside the options. Not trapped inside options.

---

## Request Handling

```
① Event only specified      "a goblin horde is encountered"
                            → result comes from rolling.  negotiation may emerge.

② Result also specified     "battle a goblin horde"
                            → work backward.  fix structure so battle emerges.
                            → if impossible: STOP: "these characters cannot produce a battle"
                            → ★ AI does not say "yes."

③ State only specified      "make Sharo waver"
                            → invent the event that produces it.  reverse generation.
```

**One request causes a cascade:**

```
"a goblin horde is encountered"
   → class goblin        (cannot roll without it)
   → principle           (cannot make decisions without it)
   → fn                  (need a response)
   → clash P1 >< ??      (must ask what gets landed on)
   → ⚠ P1.scope missing  (reference demands definition)
   → ⚠ esran definition insufficient   (insufficient places revealed)
   → insert in INDEX     (order is only defined here)   ★ v0.5
```

**Put in one thing and several grow, and insufficient places are revealed.**
In prose, writing the goblin scene only produces the goblin scene. That is why it never thickened.

---

## Still Unknown (??)

```
??  must pressure monotonically increase.  can it dip in between?
??  should narrator/POV be in state or rendering?
??  how many supporting characters with no subvert are allowed?
??  how many steps must leaves be hooked within (expiry)?
??  how to incrementally update scan_tension (insertion point index)?
??  what must an ACT boundary satisfy.  or is it purely human intuition?   ★ v0.5
??  if multiple themes conflict, what happens?                              ★ v0.5
```

Do not fill them. When rolling gets stuck there, that place gives the answer.

---

## v0.4 → v0.5 Detailed Change Log

```
[Deleted]   INDEX tree notation (=> win / => lose)
            Q7 "search for event matching when condition"
            Q7 "if multiple → branch"
            Q7 STOP: nothing_fires

[Revised]   when       trigger condition → order validator
            INDEX      skeleton → sequential source.  rolling reads next from here
            PASS       "roll apart" explicitly stated as git branch
            Role sep.  renderer added.  simulator read restrictions stated
            Extension  .kosan → .cosan unified throughout.  KOSAN.md → COSAN.md
                       all COSAN files are .cosan.  definition documents are .md only
                       ★ state files are .state.  they are output, not .cosan.
            File struct source(.cosan) / output(.state .trace) separated by extension
                       world/ split into individual files

[Deleted2]  stage                     not used.  world elements in individual .cosan files.

[New]       Q1''  ACT           event grouping.  human designates.  simulator does not read.
            Q1''' theme         color of whole story.  writer and renderer only.  optional.
            Q5'   conflict handling   all STOP → human.  AI does not judge.
            STOP code list

[Not adopted] @N notation      required item in meta-COSAN 7-B but not used.
                               reason: @ is already exclusively for timing, and reference tracking done via grep.
                               what is lost: the judgment "?? was filled but nobody reads it."
```
