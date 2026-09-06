# COSAN

**COding + SANmun (산문)**  
*An experimental AI-native reasoning methodology.*

> Instead of only making models larger,  
> what if we changed the medium in which AI handles thought?

COSAN is not a programming language, and it does not define a fixed syntax.

It is an idea for letting AI handle thought in a form that can be **remembered, referenced, modified, inspected, and reused**, rather than relying only on free-form prose.

COSAN does not have one fixed shape.

Given the same definition, different domains such as fiction, debate, game design, deep thinking, chat, or general-purpose reasoning may produce very different structures.

**What they share is not grammar, but behavior.**

---

## Why I made it

COSAN began while I was creating long-form fiction with AI.

At first, I expected current AI systems to remember long stories, preserve relationships between characters and events, and continue reasoning from earlier decisions.

As the story became longer, that expectation broke down.

I tried summaries, notes, prompt organization, and various memory techniques found online. They helped temporarily, but over time information still disappeared, relationships became inconsistent, and the AI would naturally fill in missing details.

The problem was not only the amount of memory.

**Prose is good for reading, but it is not a good medium for maintaining state, editing only one part, referencing exact relationships, or re-running consequences.**

I am a programmer.

Before COSAN, I built a small programming language called Quip. Through that project, I noticed that AI could understand and use a completely new language surprisingly quickly once it was given its structure and meaning.

That led to a question:

> AI is already good at both prose and code.  
> What if thought itself were represented somewhere between them?

That experiment became COSAN.

---

## What is COSAN?

COSAN does **not** define a universal syntax.

The input does not have to be natural language.

The intermediate representation does not have to follow one file format.

The output does not have to be prose.

What matters is whether thought can become something that can be:

- preserved
- referenced
- partially modified
- inspected for gaps or conflicts
- re-run or re-evaluated
- handed to another AI for continuation or checking

The `.cosan` files, project maps, `STOP`, `??`, state-change notation, and other structures in this repository are **implementation examples** created during experimentation.

They are not COSAN itself.

If another AI were given only the COSAN definition and asked to create a Fiction COSAN or a Meta COSAN, it might produce something completely different from the examples in this repository.

If it preserves the core properties, it may still be COSAN.

---

## Why AI makes this possible

Traditional programming languages require humans to define syntax precisely so that parsers and compilers can interpret it.

COSAN is different.

AI can understand both semantic meaning and code-like structure.

Because of that, it can create, read, modify, and use domain-specific structures without requiring one fully formal grammar.

In practice, while using COSAN, I rarely worked directly with its internal syntax.

I mostly spoke to the AI in natural language:

- how many protagonists there should be
- how the story should begin
- what event should happen next
- which suggestion I preferred
- which direction the work should take

The AI translated those decisions into the appropriate COSAN structures and maintained them.

Once a project was underway, I mostly interacted with it like an ordinary chat and requested rendering when I wanted an output.

The user does not necessarily need to learn COSAN syntax.

> **The user thinks in natural language.  
> The AI maintains that thought in structured form.**

In the current experiments, COSAN files are still visible to the user.

In a production AI system, COSAN-like structures could potentially operate internally, without the user even knowing they exist.

---

## How it evolved

COSAN was not designed as a general-purpose concept from the beginning.

### 1. Fiction COSAN

The first version was created to solve memory and consistency problems in long-form narrative generation.

It worked better than expected.

### 2. Meta COSAN

After seeing Fiction COSAN work, I wondered whether the same idea could be adapted to other domains.

Instead of designing a new COSAN from scratch every time, I created a meta-level structure that could help AI generate a domain-specific COSAN.

### 3. Multiple domain experiments

Using Meta COSAN, I created and tested several domain-specific versions:

- Fiction
- Debate
- Deep Thinking
- Game Design
- Chat / Roleplay
- General Purpose

The resulting COSANs looked very different from one another.

That was important.

It suggested that COSAN should not be forced into one universal structure.

### 4. ByteCosan

Later, I experimented with ByteCosan to separate structured judgment from final rendering.

One purpose was to let a stronger model resolve structure and decisions first, then let a smaller model handle rendering.

Another purpose was to make it easier to render the same structured content into different output forms.

---

## Example usage

COSAN does not have one fixed user workflow.

The user can interact with AI through ordinary natural-language conversation, while the AI creates and maintains the necessary COSAN structures behind that interaction.

The examples below are simplified from actual usage.

### Example 1. Creating a domain-specific COSAN from Meta COSAN

```text
User:
Read Meta COSAN v0.3 and create a Fiction COSAN.

AI:
[reads Meta COSAN]
[interprets the principles for the fiction domain]
[creates a Fiction COSAN]
```

The user does not manually design the syntax.

Another AI may create a different Fiction COSAN from the same Meta COSAN.

That is expected.

Meta COSAN does not define one universal grammar. It is one example of helping AI derive a structure appropriate for a domain.

---

### Example 2. Starting a project through natural-language conversation

```text
User:
Read Fiction COSAN v0.5.
I am going to write a story.
Record the project as COSAN files.

AI:
[reads the Fiction COSAN definition]

User:
[story content]

AI:
[interprets the content]
[creates the necessary character, world, and event COSAN structures]
[leaves unresolved information unresolved instead of inventing it]
[prepares structured state for continuation]
```

After the project has been established, the user can continue through ordinary conversation.

```text
User:
What should happen next?

AI:
[suggests several possible directions]

User:
Let's use the second one.

AI:
[updates the COSAN state]
```

When an output is needed:

```text
User:
Render what we have so far.

AI:
[reads the relevant COSAN state]
[renders it into the requested form]
```

The user mainly works with content, choices, and direction.

The internal COSAN representation is created and maintained by the AI.

> **The user thinks in natural language.  
> The AI structures and preserves that thought.**

---

## What might COSAN make possible?

COSAN is still incomplete. The ideas below are not proven solutions. They are the kinds of systems where I think a COSAN-like approach could be useful, followed by how it might be applied.

### 1. Long-running AI assistants, agents, and project work

**Possible use:**  
Persistent AI assistants, coding agents, research agents, long-running project work, simulations, and other tasks that continue across many sessions.

The problem is that these systems often have to reconstruct important state from old conversations, summaries, logs, or large context windows.

**How COSAN might apply:**

Instead of repeatedly rebuilding state from history:

```text
conversation / logs / summaries
→ reconstruct the current state
→ continue reasoning
```

the system could preserve the result of previous reasoning as structured state:

```text
persistent structured state
→ load only the relevant parts
→ continue from the existing state
```

The AI would not need to remember everything in prose. It would need to preserve the state that matters.

---

### 2. AI systems that can take real-world actions

**Possible use:**  
Agents that use tools, run code, control software, call external services, modify files, operate robots, or perform other consequential actions.

As AI becomes connected to real actions, a wrong decision can matter more than a wrong sentence.

**How COSAN might apply:**

A structured decision could become an execution unit.

Instead of:

```text
AI decides
→ action executes
```

a system could work more like:

```text
AI proposes structured action
→ check assumptions
→ check missing information
→ check allowed state transitions
→ check safety / policy conditions
→ optionally let another AI inspect it
→ execute only if it passes
```

This would not make AI perfectly safe.

The generator and the checker can both be wrong.

But it could create an additional place to detect mistakes before an irreversible or high-impact action happens.

The goal is not to expose every hidden internal thought of a model.

The goal is to make the reasoning that leads to an external action leave a structured, inspectable commitment before execution.

---

### 3. Security and AI-to-AI verification

**Possible use:**  
High-impact workflows where one AI should not be trusted to generate and approve its own action without another layer of checking.

This could include automated infrastructure, sensitive enterprise workflows, security-sensitive tool use, or any system where a mistaken transition should be caught before execution.

**How COSAN might apply:**

Structured reasoning could be passed between different agents or models:

```text
AI A
→ produces structured reasoning state

AI B
→ checks missing assumptions, contradictions, unsupported transitions

AI C
→ performs a safety or policy check
```

Free-form prose can also be reviewed this way, but structured state may make it easier to identify exactly:

- what changed
- what is still unknown
- what depends on what
- which condition allowed an action
- which state transition is being requested

This is closer to adding an error-detection layer than proving that a decision is correct.

---

### 4. Reducing repeated computation in large AI systems

**Possible use:**  
AI companies, large-scale agent systems, enterprise AI platforms, and any long-running workload where the same context and reasoning are repeatedly reconstructed.

AI systems increasingly consume large amounts of compute, electricity, hardware, and cooling resources.

One question I think is important is how much of that computation is repeated work.

Long-running tasks often require a model to:

- read large amounts of previous context again
- reconstruct state that was already known
- summarize old summaries
- rediscover previous decisions
- regenerate large outputs when only a small part changed

**How COSAN might apply:**

Instead of:

```text
large history
→ read everything
→ reconstruct state
→ reason again
```

a system could use:

```text
current structured state
+ relevant references
→ reason only about what changed
```

And instead of:

```text
change one assumption
→ regenerate the entire result
```

it could attempt:

```text
change one structured value
→ re-evaluate only the affected path
```

If this works at scale, it could reduce inference cost and therefore potentially reduce electricity use, hardware demand, cooling requirements, and in some systems water use.

I have not benchmarked this yet.

It is one of the most important hypotheses I would like to see tested.

---

### 5. Using smaller models for parts of a workflow

**Possible use:**  
Systems where a strong model is needed for difficult reasoning, but not every later step needs the same model.

For example, rendering, formatting, rewriting, or producing multiple output forms may not require repeating the expensive reasoning that produced the underlying structure.

**How COSAN might apply:**

This was one reason I experimented with ByteCosan.

```text
strong model
→ resolve structure / state / decisions
→ intermediate representation

smaller model
→ render prose or another output format
```

If the expensive reasoning can be preserved and reused, smaller models may be able to perform later stages.

This could reduce cost, but it needs measurement.

---

### 6. Ordinary AI chat with a hidden structured layer

**Possible use:**  
Everyday AI assistants.

The user experience would not necessarily change at all.

The user could continue to talk to AI exactly as they do today.

**How COSAN might apply:**

Behind the conversation, the system could maintain:

```text
structured memory
decision state
references
unresolved information
execution conditions
```

The user would not need to learn COSAN syntax or even know that COSAN-like structures exist.

The benefit would appear as an AI that:

- remembers important state more reliably
- reconstructs less from old conversation
- can continue long-running work more consistently
- can inspect important decisions before acting

---

### 7. Creative and domain-specific systems

**Possible use:**  
Fiction, game scenarios, debate, game design, roleplay, research, planning, or other domains where different kinds of structured reasoning are useful.

This was how COSAN itself developed.

Fiction COSAN, Debate COSAN, Game Design COSAN, Deep Thinking COSAN, Chat COSAN, and General COSAN all ended up with different structures.

**How COSAN might apply:**

Rather than forcing every task into one universal schema:

```text
COSAN definition
+ domain
+ AI
→ domain-specific structured representation
```

The structure can change depending on what the domain needs to preserve, inspect, modify, or re-run.

This is why I do not think COSAN should be tied to one grammar.

### 8. Incremental rendering of very long outputs

**Possible use:**  
Long-form fiction, game scenarios, scripts, reports, or any output that is too large to generate reliably in one pass.

Current commercial AI systems tend to compress or summarize when asked to render very large amounts of content at once. Even when explicitly asked to include everything, details can still be omitted as the requested output becomes longer.

Without structured state, splitting the work into many short renderings creates another problem: continuity between sections can break.

**How COSAN might apply:**

Keep the full content and continuity in structured form, and render only manageable sections at a time.

```text
structured source
→ render section 1
→ render section 2
→ render section 3
→ ...
```

The important point is that continuity lives in the structured source, not only in the previously generated prose.

In fiction experiments, the story was organized around event files. Those files could become large, but because they were code-like structures rather than long prose passages, they could still be referenced, edited, and partially read without needing to rewrite the whole story.

This also creates an important distinction:

> **A prose summary becomes shorter by removing information.  
> COSAN aims to become smaller by restructuring information.**

A summary compresses by omission.

A COSAN-like representation tries to compress by replacing repeated prose with explicit state, references, conditions, relationships, and reusable structure.

This does not guarantee lossless conversion.

Meaning can still change when natural language is converted into COSAN, and again when COSAN is rendered back into prose or another output.

In my experiments, rendering shorter sections reduced drift, while the structured source helped preserve continuity across those sections.


---

## Why I am publishing it

COSAN began as a personal experiment.

At first, I considered keeping it private and developing commercial applications from it.

I changed my mind because I no longer think the most important question is whether I can turn COSAN into a product first.

The possibilities described above — especially around AI safety and resource efficiency — may matter more if they are tested earlier by more people.

COSAN is still incomplete.

It may contain wrong assumptions, weak designs, or ideas that already exist elsewhere in better forms.

That is exactly why I decided to publish it now.

I do not need COSAN to become a finished standard, or even to remain recognizable in its current form.

If someone can take the underlying idea, test it, replace parts of it, combine it with other approaches, or build something substantially better, that is useful.

I also do not know whether COSAN is original.

Similar ideas may already exist, and someone may already be working on something better.

That is not important to me.

What matters is whether publishing this work can help:

- test the idea sooner
- expose its flaws sooner
- make independent experiments easier
- give researchers or AI companies another direction to examine
- accelerate a better implementation, even if it no longer looks like COSAN

I originally wanted to keep the idea for myself because it might become commercially useful.

But AI is developing quickly.

If there is even a chance that part of this idea can contribute to safer or more efficient AI, I would rather publish it before I can fully polish it than keep it private for too long.

I can build something else commercially.

If this idea is useful to AI development, I would rather see it used.

And if it helps improve the AI systems that all of us eventually depend on, that benefit comes back to me as well.


---

---

## What is in this repository?

The documents and projects in this repository are not canonical implementations or official COSAN syntax.

They are **examples and experimental records** created while exploring the idea.

- **Meta COSAN** — an experiment for generating domain-specific COSAN structures
- **Fiction COSAN** — the original long-form narrative experiment
- **Domain COSANs** — debate, deep thinking, game design, chat, general-purpose, and others
- **Example Projects** — projects that were actually run using COSAN
- **ByteCosan** — a later experiment separating structured reasoning from rendering

You do not need to copy these implementations exactly.

A better implementation may look completely different.

---

## Current status

COSAN is not a finished framework or a research paper.

It is an early experimental idea that began as a solution to a personal problem and was then tested across several domains.

Some parts worked well.

Some parts failed.

Some assumptions have not yet been validated.

This repository should be viewed as a **starting point**, not a finished answer.

---

## Name

**COSAN = COding + SANmun**

`Sanmun (산문)` is the Korean word for prose.

Pronunciation: **co-san / 코산**

---

> **The core of COSAN is not giving AI a new syntax.  
> It is giving AI a medium in which thought can be remembered, modified, inspected, and reused.**

---

## AI-assisted creation

All files in this repository were created with the assistance of AI.

The ideas, direction, and decisions were provided by the author, while AI was used to generate, structure, edit, and translate the files.


# 한국어

## COSAN

**COding + SANmun (산문)**  
*AI-native 구조적 사고 방법론에 대한 실험.*

> 모델만 더 크게 만드는 대신,  
> AI가 생각을 다루는 매체를 바꿔볼 수 있지 않을까?

COSAN은 프로그래밍 언어가 아니며, 고정된 문법도 아닙니다.

AI가 생각을 산문으로만 이어가는 대신,  
**기억하고, 참조하고, 수정하고, 검사하고, 다시 사용할 수 있는 구조로 다루게 하려는 아이디어**입니다.

COSAN의 형태는 정해져 있지 않습니다.

같은 정의를 주더라도 소설, 토론, 게임 기획, 깊은 사고, 채팅, 범용 사고 등 도메인에 따라 전혀 다른 구조가 만들어질 수 있습니다.

**공통되는 것은 문법이 아니라 성질입니다.**

---

## 왜 만들었나

COSAN은 AI와 장편 소설을 만들면서 시작되었습니다.

처음에는 지금의 AI가 긴 이야기도 기억하고, 인물과 사건의 관계를 유지하고, 앞에서 했던 생각을 이어서 사용할 수 있을 것이라고 기대했습니다.

하지만 이야기가 길어질수록 문제가 생겼습니다.

요약, 메모, 프롬프트 구성 등 인터넷에서 알려진 여러 기억 보조 방법도 사용해봤습니다.

어느 정도는 도움이 되었지만 시간이 지나면 정보가 빠지고, 관계가 흐려지고, AI는 없는 내용을 자연스럽게 채워 넣었습니다.

문제는 단순히 기억의 양만은 아니었습니다.

**산문은 읽기에는 좋지만, 상태를 유지하고 일부만 수정하고 정확한 관계를 참조하고 결과를 다시 굴리기에는 좋은 매체가 아니었습니다.**

저는 프로그래머입니다.

COSAN 이전에 Quip이라는 작은 프로그래밍 언어를 만든 적이 있습니다.

그 과정에서 AI가 처음 보는 새로운 언어도 구조와 의미를 주면 놀랄 만큼 빠르게 읽고 사용할 수 있다는 것을 경험했습니다.

그래서 이런 생각을 했습니다.

> AI는 산문도 잘 읽고 코드도 잘 읽는다.  
> 그렇다면 생각 자체를 그 중간 어딘가의 형태로 다루게 하면 어떨까?

그 실험이 COSAN의 시작이었습니다.

---

## COSAN은 무엇인가

COSAN은 **하나의 공통 문법을 정의하지 않습니다.**

입력이 자연어일 필요도 없습니다.

중간 표현이 특정 파일 형식일 필요도 없습니다.

출력이 산문일 필요도 없습니다.

중요한 것은 생각을 다음과 같은 대상으로 만들 수 있느냐입니다.

- 남길 수 있다
- 참조할 수 있다
- 부분적으로 수정할 수 있다
- 빈 곳과 충돌을 발견할 수 있다
- 다시 실행하거나 다시 검토할 수 있다
- 다른 AI가 이어받거나 검사할 수 있다

현재의 `.cosan` 파일, 프로젝트 맵, `STOP`, `??`, 상태 변경 표현 등은 이러한 생각을 실험하기 위해 만들어진 **구현 예시**입니다.

COSAN 그 자체는 아닙니다.

같은 COSAN 정의만 가지고 다른 AI에게 Fiction COSAN이나 Meta COSAN을 만들어 달라고 하면 이 저장소와 전혀 다른 형태가 나올 수 있습니다.

핵심 성질을 유지한다면 그것도 COSAN일 수 있습니다.

---

## AI가 있기 때문에 가능하다

전통적인 프로그래밍 언어는 사람이 문법을 정확하게 정의하고, 파서와 컴파일러가 그 문법을 해석해야 합니다.

COSAN은 다릅니다.

AI는 자연어의 의미와 코드의 구조를 동시에 이해할 수 있습니다.

그래서 완전히 형식화된 하나의 문법이 없어도 도메인에 맞는 구조를 만들고, 읽고, 수정하고, 사용할 수 있습니다.

실제로 COSAN을 사용하면서 저는 내부 문법을 거의 직접 다루지 않았습니다.

대부분 자연어로 이야기했습니다.

- 주인공을 몇 명으로 할지
- 이야기를 어떻게 시작할지
- 다음 사건을 어떻게 할지
- 어떤 제안을 선택할지
- 어떤 방향으로 갈지

AI가 그 판단을 해당 도메인의 COSAN 구조로 바꾸고 유지했습니다.

프로젝트가 어느 정도 시작된 뒤에는 대부분 지금의 AI 채팅처럼 대화했고, 결과가 필요할 때 렌더링을 요청했습니다.

사용자는 반드시 COSAN 문법을 배울 필요가 없습니다.

> **사용자는 자연어로 생각하고,  
> AI는 그 생각을 구조화된 형태로 유지합니다.**

현재 실험에서는 COSAN 파일이 사용자에게 노출되어 있습니다.

실제 AI 시스템에 적용된다면 사용자가 COSAN의 존재조차 알 필요 없이 내부에서 작동할 수도 있습니다.

---

## 어떻게 발전했나

COSAN은 처음부터 범용 개념으로 만들어진 것이 아닙니다.

### 1. Fiction COSAN

장편 서사의 기억과 일관성 문제를 해결하기 위해 처음 만들었습니다.

실제로 사용해보니 예상보다 잘 작동했습니다.

### 2. Meta COSAN

소설에서 작동한다면 다른 분야에서도 가능하지 않을까 생각했습니다.

매번 새로운 COSAN을 처음부터 만드는 대신,  
AI가 도메인에 맞는 COSAN을 만들 수 있도록 하는 메타 구조를 만들었습니다.

### 3. 여러 도메인에서 실험

Meta COSAN을 이용해 여러 도메인용 COSAN을 만들고 시험했습니다.

- Fiction
- Debate
- Deep Thinking
- Game Design
- Chat / Roleplay
- General Purpose

각 도메인에서 만들어진 COSAN은 서로 상당히 달랐습니다.

이 경험을 통해 COSAN은 하나의 공통 구조에 담아야 하는 것이 아니라는 생각에 도달했습니다.

### 4. ByteCosan

이후에는 구조적 판단과 최종 렌더링을 분리하기 위한 ByteCosan도 실험했습니다.

하나는 더 강한 모델이 구조와 판단을 먼저 해결하고 작은 모델이 렌더링하도록 하기 위한 목적이었고,

다른 하나는 같은 구조화된 내용을 서로 다른 출력 형태로 렌더링하기 위한 목적이었습니다.

---

## 사용 예시

COSAN에는 하나의 고정된 사용법이 없습니다.

사용자는 보통 지금의 AI 채팅처럼 자연어로 대화하고,  
AI가 그 뒤에서 필요한 COSAN 구조를 만들고 유지합니다.

아래 예시는 실제 사용 흐름을 단순화한 것입니다.

### 예시 1. Meta COSAN으로 도메인용 COSAN 만들기

```text
사용자:
메타코산_v0.3.md를 읽고 소설용 코산을 만들어줘.

AI:
[메타코산을 읽음]
[소설 도메인에 맞는 구조를 해석]
[소설용 코산을 생성]
```

사용자가 직접 문법을 설계할 필요는 없습니다.

같은 Meta COSAN을 다른 AI에게 주면 다른 형태의 소설용 COSAN이 만들어질 수도 있습니다.

그것은 문제가 아닙니다.

Meta COSAN은 하나의 고정 문법을 만드는 것이 아니라, AI가 도메인에 맞는 구조를 만들도록 돕는 하나의 예시입니다.

---

### 예시 2. 자연어로 프로젝트 시작하기

```text
사용자:
소설용_코산_v0_5.md를 읽고 소설을 작성할 거야.
작성은 코산 파일로 해줘.

AI:
[소설용 COSAN 정의를 읽음]

사용자:
[소설 내용]

AI:
[내용을 해석]
[인물·세계·사건에 필요한 COSAN 구조를 생성]
[정해지지 않은 정보는 임의로 채우지 않고 미정 상태로 남김]
[이후 작업을 계속할 수 있는 구조화된 상태를 준비]
```

프로젝트가 시작된 뒤에는 보통 자연어 대화만으로 계속 진행할 수 있습니다.

```text
사용자:
다음에는 어떤 사건이 좋을까?

AI:
[여러 방향을 제안]

사용자:
두 번째 걸로 하자.

AI:
[선택된 내용을 COSAN 상태에 반영]
```

필요할 때 결과를 요청합니다.

```text
사용자:
지금까지 내용을 렌더링해줘.

AI:
[관련 COSAN 상태를 읽음]
[요청한 형식으로 렌더링]
```

사용자는 내용과 선택, 방향을 다루고,  
COSAN의 내부 구조는 AI가 생성하고 관리합니다.

> **사용자는 자연어로 생각하고,  
> AI는 그 생각을 구조화해 유지합니다.**

---

## 무엇이 가능할까

COSAN은 아직 불완전합니다. 아래 내용은 해결됐다고 주장하는 것이 아닙니다. 제가 COSAN과 비슷한 방식이 실제로 쓰일 수 있다고 생각하는 **예상 사용처를 먼저 적고**, 그 다음에 어떻게 적용할 수 있을지를 적었습니다.

### 1. 장기간 계속되는 AI 비서·에이전트·프로젝트

**예상 사용처:**  
지속형 AI 비서, 코딩 에이전트, 연구 에이전트, 장기 프로젝트, 시뮬레이션처럼 여러 세션에 걸쳐 계속되는 작업.

이런 시스템은 과거 대화, 요약, 로그, 긴 컨텍스트에서 중요한 상태를 계속 다시 복원해야 하는 경우가 많습니다.

**어떻게 적용할 수 있을까:**

```text
과거 대화 / 로그 / 요약
→ 현재 상태를 다시 복원
→ 다시 생각
```

하는 대신,

```text
구조화된 현재 상태를 유지
→ 필요한 부분만 읽음
→ 그 상태에서 계속
```

하는 방식입니다.

AI가 모든 과거 문장을 기억하는 대신, 앞으로의 판단에 필요한 상태를 남기는 것입니다.

---

### 2. 실제 행동을 수행하는 AI

**예상 사용처:**  
도구를 사용하는 에이전트, 코드 실행, 외부 서비스 호출, 파일 수정, 소프트웨어 조작, 로봇 제어 등 실제 결과를 만드는 AI 시스템.

AI가 실제 행동과 연결될수록 잘못된 문장보다 **잘못된 실행**이 더 큰 문제가 될 수 있습니다.

**어떻게 적용할 수 있을까:**

구조화된 판단 자체를 하나의 실행 단위로 만드는 방법을 생각할 수 있습니다.

```text
AI 판단
→ 바로 실행
```

대신,

```text
AI가 구조화된 실행안을 만듦
→ 전제가 맞는지 검사
→ 빠진 정보가 있는지 검사
→ 허용되지 않은 상태 변경인지 검사
→ 정책·안전 조건 검사
→ 필요하면 다른 AI가 다시 검사
→ 통과한 경우에만 실행
```

하는 방식입니다.

이것이 AI를 완전히 안전하게 만든다는 뜻은 아닙니다.

생성하는 AI와 검사하는 AI가 동시에 틀릴 수도 있습니다.

하지만 되돌리기 어렵거나 영향이 큰 행동이 실행되기 전에 **한 번 더 오류를 발견할 수 있는 지점**은 만들 수 있습니다.

COSAN의 목적은 AI 내부의 모든 생각을 그대로 읽는 것이 아닙니다.

현실의 행동으로 이어지는 판단이 실행 전에 **구조화된 형태로 한 번 커밋되도록 만드는 것**에 가깝습니다.

---

### 3. 보안과 AI 간 상호 검증

**예상 사용처:**  
한 AI가 자기 판단을 만들고 스스로 승인하는 것만으로는 부족한 고위험 작업.

자동화된 인프라, 기업의 민감한 업무, 보안이 중요한 도구 사용, 잘못된 상태 변경을 실행 전에 잡아야 하는 시스템 등에 적용할 가능성이 있습니다.

**어떻게 적용할 수 있을까:**

구조화된 생각을 다른 AI에게 넘겨 검사할 수 있습니다.

```text
AI A
→ 구조화된 판단 생성

AI B
→ 빠진 전제·모순·근거 없는 변경 검사

AI C
→ 안전·정책 조건 검사
```

산문도 다른 AI가 검사할 수 있지만, 구조화된 상태라면 다음을 더 직접적으로 확인할 가능성이 있습니다.

- 무엇이 바뀌었는가
- 무엇을 아직 모르는가
- 무엇이 무엇에 의존하는가
- 어떤 조건 때문에 행동이 허용됐는가
- 어떤 상태 변경을 실행하려는가

완전한 정확성을 증명하는 것보다는 **오류 검출 층을 하나 더 붙이는 것**에 가깝습니다.

---

### 4. 대규모 AI 시스템의 반복 계산 줄이기

**예상 사용처:**  
AI 회사, 대규모 에이전트 시스템, 기업용 AI 플랫폼, 장시간 같은 프로젝트를 처리하면서 과거 컨텍스트와 판단을 반복해서 복원하는 시스템.

AI는 점점 더 많은 연산 자원, 전력, 하드웨어와 냉각 자원을 사용하고 있습니다.

제가 중요하다고 보는 질문 중 하나는 그 계산 중 얼마나 많은 부분이 **이미 했던 일을 다시 하는 계산인가**입니다.

긴 작업에서 AI는 자주 다음을 반복합니다.

- 과거의 큰 컨텍스트를 다시 읽기
- 이미 알고 있던 상태를 다시 복원하기
- 이전 요약을 다시 요약하기
- 이미 내린 결정을 다시 추론하기
- 일부만 바뀌었는데 전체 결과를 다시 생성하기

**어떻게 적용할 수 있을까:**

```text
긴 과거 기록
→ 전부 다시 읽기
→ 상태 복원
→ 다시 추론
```

대신,

```text
현재의 구조화된 상태
+ 필요한 참조
→ 변경된 부분만 추론
```

하는 방향을 생각할 수 있습니다.

또,

```text
가정 하나 변경
→ 전체 결과 다시 생성
```

대신,

```text
구조화된 값 하나 변경
→ 영향받는 경로만 다시 평가
```

하는 방법을 생각할 수 있습니다.

이 방식이 큰 규모에서도 작동한다면 추론 비용을 줄이고, 결과적으로 전력 사용, 하드웨어 수요, 냉각 부담, 일부 시스템에서는 물 사용까지 줄이는 데 도움이 될 가능성이 있습니다.

아직 벤치마크하지 않았습니다.

제가 가장 중요하게 실제 검증을 보고 싶은 가설 중 하나입니다.

---

### 5. 작업 일부를 더 작은 모델에 맡기기

**예상 사용처:**  
어려운 판단에는 큰 모델이 필요하지만, 이후의 렌더링·형식 변환·출력에는 같은 수준의 모델이 필요하지 않은 작업.

예를 들어 한 번 구조화한 판단을 여러 출력에 사용할 때마다 비싼 추론을 반복할 필요가 있는지 생각해볼 수 있습니다.

**어떻게 적용할 수 있을까:**

이 생각에서 ByteCosan도 실험했습니다.

```text
강한 모델
→ 구조 / 상태 / 판단 확정
→ 중간 표현

작은 모델
→ 산문 또는 다른 출력 형식으로 렌더링
```

비싼 추론 결과를 보존하고 재사용할 수 있다면 이후 단계는 더 작은 모델이 맡을 가능성이 있습니다.

이 역시 실제 측정이 필요합니다.

---

### 6. 일반적인 AI 채팅의 보이지 않는 내부 계층

**예상 사용처:**  
지금 우리가 사용하는 일반 AI 채팅 자체.

사용 방식은 지금과 거의 달라지지 않을 수 있습니다.

사용자는 계속 자연어로 이야기합니다.

**어떻게 적용할 수 있을까:**

대화 뒤에서 AI가 다음을 유지하는 방식입니다.

```text
구조화된 기억
판단 상태
참조 관계
미해결 정보
실행 조건
```

사용자는 COSAN 문법을 배울 필요도 없고, COSAN과 비슷한 구조가 존재한다는 사실조차 알 필요가 없을 수 있습니다.

사용자에게는 결과적으로 다음과 같은 차이로 나타날 수 있습니다.

- 중요한 상태를 더 안정적으로 기억함
- 오래된 대화를 덜 다시 복원함
- 장기 작업을 더 일관되게 이어감
- 중요한 행동 전에는 판단을 검사할 수 있음

---

### 7. 창작·기획·사고 등 도메인별 시스템

**예상 사용처:**  
소설, 게임 시나리오, 토론, 게임 기획, 역할극, 연구, 기획, 깊은 사고처럼 서로 다른 종류의 구조가 필요한 작업.

COSAN 자체도 이런 식으로 발전했습니다.

소설용, 토론용, 게임기획용, 깊은생각용, 채팅용, 범용 COSAN은 모두 서로 다른 모습이 되었습니다.

**어떻게 적용할 수 있을까:**

모든 일을 하나의 공통 스키마에 넣는 대신,

```text
COSAN 정의
+ 도메인
+ AI
→ 그 도메인에 맞는 구조
```

처럼 만들 수 있습니다.

각 도메인에서 무엇을 기억해야 하고, 무엇을 검사해야 하고, 무엇을 수정하거나 다시 굴릴 수 있어야 하는지에 따라 구조가 달라지는 것입니다.

그래서 COSAN을 하나의 문법에 묶으면 안 된다고 생각하게 되었습니다.

### 8. 매우 긴 결과물을 구간별로 렌더링하기

**예상 사용처:**  
장편 소설, 게임 시나리오, 영화·드라마·방송 대본, 긴 보고서처럼 한 번에 안정적으로 생성하기 어려운 결과물.

현재의 상용 AI는 매우 긴 범위를 한 번에 렌더링하도록 요청할수록 내용을 압축하거나 요약하는 경향이 있습니다.

"모든 내용을 빠짐없이 넣어달라"고 요청해도 출력 범위가 커질수록 세부 내용이 줄어드는 문제가 생깁니다.

그렇다고 구조화 없이 짧은 구간으로 계속 나누어 생성하면 또 다른 문제가 생깁니다.

각 구간은 잘 나와도 구간과 구간 사이의 연결이 끊길 수 있습니다.

**어떻게 적용할 수 있을까:**

전체 내용과 연결 관계는 구조화된 원본에 유지하고, 출력만 AI가 감당할 수 있는 길이로 나누어 렌더링합니다.

```text
구조화된 원본
→ 구간 1 렌더링
→ 구간 2 렌더링
→ 구간 3 렌더링
→ ...
```

중요한 것은 연결성이 이전에 생성한 산문에만 남는 것이 아니라, 구조화된 원본에 남아 있다는 점입니다.

소설 실험에서는 이야기를 사건 파일 단위로 관리했습니다.

사건 파일 자체가 길어져도 긴 산문처럼 처음부터 끝까지 다시 읽어야 하는 글이 아니라 코드 형태의 구조이기 때문에, 필요한 부분을 참조하고 수정하고 일부만 읽는 방식으로 다룰 수 있었습니다.

여기에는 중요한 차이가 하나 있습니다.

> **산문의 요약은 정보를 버려서 짧아지고,  
> COSAN은 정보를 구조화해서 압축하려고 합니다.**

요약은 내용을 생략하면서 압축합니다.

COSAN과 같은 구조는 반복되는 산문을 상태, 참조, 조건, 관계, 구조로 바꾸어 같은 의미를 더 직접적으로 유지하려고 합니다.

물론 이것이 무손실 변환을 보장한다는 뜻은 아닙니다.

자연어가 COSAN으로 구조화되는 과정에서도 의미가 달라질 수 있고, COSAN을 다시 산문이나 다른 형식으로 렌더링하는 과정에서도 변형이 생길 수 있습니다.

실제 실험에서는 긴 범위를 한 번에 렌더링하기보다 짧은 구간으로 나누어 렌더링하면서 변형을 줄였고, 구간 사이의 연결은 구조화된 원본이 유지하도록 했습니다.


---

## 왜 공개하는가

COSAN은 개인적인 실험에서 시작했습니다.

처음에는 비공개로 두고, 상업적인 제품으로 발전시키는 것도 생각했습니다.

하지만 어느 순간부터 COSAN을 제가 먼저 제품으로 만드는 것보다, 이 아이디어가 더 빨리 검증되는 것이 더 중요할 수도 있다고 생각하게 되었습니다.

앞에서 설명한 여러 가능성, 특히 AI의 안전성과 자원 효율에 관한 가능성이 실제 의미가 있다면 더 많은 사람이 더 일찍 시험해보는 편이 낫다고 판단했습니다.

COSAN은 아직 완전하지 않습니다.

잘못된 가정이 있을 수도 있고, 구조가 부족할 수도 있고, 이미 다른 곳에서 더 나은 형태로 존재하는 아이디어가 섞여 있을 수도 있습니다.

그래서 오히려 지금 공개하기로 했습니다.

COSAN이 완성된 표준이 될 필요도 없고, 앞으로 지금과 같은 모습으로 남아 있을 필요도 없습니다.

누군가 이 아이디어의 핵심만 가져가서 시험하고, 일부를 버리고, 다른 방법과 결합하고, 훨씬 더 나은 형태로 발전시킨다면 그것으로 충분합니다.

COSAN이 완전히 새로운 아이디어인지도 모릅니다.

비슷한 생각이 이미 존재할 수도 있고, 누군가는 이미 더 좋은 방법을 만들고 있을 수도 있습니다.

그것은 중요하지 않습니다.

이 공개를 통해 다음이 조금이라도 빨라진다면 의미가 있다고 생각합니다.

- 아이디어를 실제로 시험하는 것
- 문제점을 더 빨리 발견하는 것
- 다른 사람이 독립적으로 실험해보는 것
- 연구자나 AI 회사가 하나의 가능성으로 검토해보는 것
- COSAN과 전혀 다른 모습이더라도 더 좋은 구현으로 발전하는 것

처음에는 돈이 될 수도 있는 아이디어라 혼자 가지고 있고 싶었습니다.

하지만 AI의 발전 속도를 보면서 생각이 바뀌었습니다.

이 아이디어의 일부라도 더 안전하고 효율적인 AI를 만드는 데 도움이 될 가능성이 있다면, 제가 혼자 완성할 때까지 오래 가지고 있는 것보다 조금이라도 빨리 공개하는 편이 낫다고 생각했습니다.

상업적인 것은 다른 것으로도 다시 만들 수 있습니다.

이 아이디어가 AI 발전에 도움이 된다면 실제로 사용되는 편이 더 좋습니다.

그리고 AI가 더 안전하고 효율적으로 발전한다면, 결국 그 AI를 사용하는 저에게도 그 혜택이 돌아올 것입니다.


---

---

## 이 저장소에 있는 것

이 저장소의 문서와 프로젝트는 COSAN의 정답이나 표준 문법이 아닙니다.

COSAN을 만들고 시험하면서 나온 **예제와 실험 기록**입니다.

- **Meta COSAN** — 도메인별 COSAN을 생성하기 위한 핵심 실험
- **Fiction COSAN** — COSAN이 처음 시작된 장편 서사 실험
- **Domain COSANs** — 토론, 깊은 사고, 게임 기획, 채팅, 범용 등의 실험
- **Example Projects** — 실제 COSAN을 사용해본 프로젝트
- **ByteCosan** — 구조화와 렌더링 분리를 위한 후속 실험

이 구현들을 그대로 사용할 필요는 없습니다.

COSAN의 정의에서 출발해 더 나은 형태를 만드는 것이 가능합니다.

---

## 현재 상태

COSAN은 완성된 프레임워크나 연구 논문이 아닙니다.

개인적인 문제를 해결하기 위해 시작해 여러 도메인에서 가능성을 확인한 **초기 실험적 아이디어**입니다.

잘 작동한 부분도 있고, 실패한 부분도 있으며, 아직 검증하지 못한 가정도 많습니다.

따라서 이 저장소는 완성된 해답이 아니라 **출발점**으로 봐주세요.

---

## 이름

**COSAN = COding + SANmun**

`산문(Sanmun)`은 한국어로 prose를 뜻합니다.

발음: **co-san / 코산**

---

> **COSAN의 핵심은 AI에게 새로운 문법을 주는 것이 아니라,  
> 생각을 기억하고 수정하고 검사하고 다시 사용할 수 있는 새로운 매체를 주는 것입니다.**

---

## AI 사용

이 저장소의 모든 파일은 AI를 활용해 작성했습니다.

아이디어와 방향, 판단은 작성자가 제시했고, 파일의 생성·구조화·수정·번역에는 AI를 사용했습니다.

