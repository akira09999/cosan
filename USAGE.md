# COSAN Usage

This document explains how to try COSAN with current AI systems.

COSAN is not a programming language, and users do not need to learn a fixed syntax.

In the current implementation, the COSAN itself is usually a single Markdown definition file.
The `.cosan` files created in example projects are project data generated while using that definition, not COSAN itself.

A minimal test is therefore:

```text
COSAN definition (.md)
→ AI
→ project state / .cosan files / rendered output
```

The basic workflow is:

```text
Human:
natural language, ideas, decisions, corrections

AI:
reads a COSAN definition
→ creates or updates structured state
→ preserves project state
→ renders when requested
```

In the current experiments, the user mainly works in natural language while the AI manages the COSAN structure.

---

## 1. Create a domain COSAN with Meta COSAN

Meta COSAN is one practical method for creating a COSAN adapted to a specific domain.

Example:

```text
User:
Read META_COSAN_v0.3.md
and create a COSAN for fiction.

AI:
[reads Meta COSAN]
[analyzes the domain]
[creates a fiction-oriented COSAN definition]
[reviews the result]
```

You can try other domains in the same way.

```text
Read META_COSAN_v0.3.md
and create a COSAN for debate.
```

```text
Read META_COSAN_v0.3.md
and create a COSAN for game design.
```

```text
Read META_COSAN_v0.3.md
and create a COSAN for long-term project planning.
```

The generated COSAN does not need to resemble other domain COSANs.

COSAN is not defined by one universal grammar. Different COSANs may use very different structures as long as they preserve the intended behavior and purpose.

---

## 2. Start a fiction project

A simple way to test COSAN is to use the Fiction COSAN definition.

Example:

```text
User:
Read FICTION_COSAN_v0.5.md.
I am going to write a story.
Record the project as COSAN files.

AI:
[reads Fiction COSAN]
[prepares the project structure]
```

Then provide story content normally.

```text
User:
[story content]

AI:
[interprets the content]
[creates or updates character/world/event/state structures]
[keeps unresolved information unresolved]
[updates the project state]
```

The user does not need to manually write COSAN syntax.

The AI can maintain the structure while the user continues in ordinary natural language.

---

## 3. Continue through ordinary conversation

After the project is initialized, normal conversation can continue.

```text
User:
What should happen next?

AI:
[suggests several directions]

User:
Let's use the second one.

AI:
[updates the structured state]
[records the decision]
```

You can also revise previous information.

```text
User:
Change the reason the character left the city.
It was not fear. It was guilt.

AI:
[finds the affected state]
[updates the relevant structures]
[preserves unrelated information]
```

The important point is that the entire project does not need to be rewritten into the conversation every time.

The project state can exist separately in structured form.

---

## 4. Inspect or edit the structured state

Because the project state is structured, you can ask the AI to inspect it directly.

Examples:

```text
What unresolved questions are still open?
```

```text
Which characters know about the hidden room?
```

```text
What changed after event 12?
```

```text
What assumptions are still uncertain?
```

```text
Show me the current relationship between A and B.
```

You can also request corrections.

```text
There is a contradiction here.
Find the conflicting state and fix it
without changing unrelated information.
```

```text
Do not guess this.
Mark it as unresolved.
```

```text
Do not render yet.
Update only the structured source.
```

---

## 5. Render the structured source

When you want normal prose or another output format, ask the AI to render the structured source.

Example:

```text
User:
Render what we have so far as a novel.

AI:
[reads the relevant COSAN state]
[renders prose]
```

You can request other output forms too.

```text
Render events 1 through 5 as a game scenario.
```

```text
Render this section as a screenplay.
```

```text
Render this material as a report.
```

The structured source and the rendered output are different things.

The structured source is used to preserve and manipulate meaning.

The rendered output is the form intended for a person or another system.

---

## 6. Render long outputs incrementally

Current commercial AI systems tend to compress, summarize, or omit details when asked to render very large amounts of content at once.

Even explicit instructions such as "include everything" do not fully remove this limitation.

If the output is longer than the model can reliably render without losing detail, split the output into manageable sections.

```text
structured source
→ render section 1
→ render section 2
→ render section 3
→ ...
```

For fiction, an event-oriented workflow can look like this:

```text
event_001.cosan
event_002.cosan
event_003.cosan
...
```

Then render them one by one.

```text
Render event 1 in full prose.
```

```text
Render event 2, continuing naturally from event 1.
```

```text
Render event 3 while preserving the current
character and world state.
```

The output is divided, but the underlying story structure remains connected.

Without structured state, many short generations can create continuity problems between sections.

With structured state, each rendered section can refer back to the same characters, relationships, world facts, unresolved information, decisions, and event state.

---

## 7. Summary and structured compression are different

A prose summary usually becomes shorter by removing information.

```text
long prose
→ select important parts
→ omit details
→ shorter summary
```

COSAN aims at a different type of compression.

```text
prose / ideas
→ explicit states
→ relationships
→ references
→ conditions
→ events
→ structured representation
```

A useful distinction is:

> A prose summary becomes shorter by removing information.  
> COSAN aims to become smaller by restructuring information.

This does not mean the transformation is lossless.

Meaning can change when natural language is converted into structured state, and it can change again when structured state is rendered back into prose or another form.

For important work, inspect both the structured state and the rendered result.

---

## 8. ByteCosan

**ByteCosan = Bytecode + COSAN**

ByteCosan is an experimental intermediate representation intended to separate structural reasoning from final rendering.

A possible workflow is:

```text
stronger model
→ COSAN / structured reasoning
→ ByteCosan
→ smaller or local renderer
→ final output
```

The stronger model handles structure, judgment, and interpretation.

A smaller or local model can then focus mainly on rendering.

ByteCosan can also be used as a rendering intermediate when the same structured content needs to be converted into different output forms or styles.

This is experimental and optional. COSAN does not require ByteCosan.

---

## 9. Experimental verification workflow

COSAN can also be tested as a structured checkpoint before an AI performs an external action.

Conceptual example:

```text
AI proposes an action
→ write structured decision/action state
→ inspect assumptions
→ inspect unknowns
→ inspect contradictions
→ optional second AI review
→ execute only if accepted
```

Example prompt:

```text
Before executing this action,
write the decision as structured state.

List:
- assumptions
- unknowns
- expected result
- possible failure conditions

Do not execute until the state has been reviewed.
```

This is only an additional checking layer.

It does not guarantee correctness or safety.

---

## 10. The current file structure is only an example

The examples in this repository may use files such as:

```text
PROJECT_MAP
INDEX
event files
character files
world files
.cosan files
```

These are implementation examples, not requirements of COSAN itself.

A COSAN implementation could use:

- files
- a database
- a graph
- structured memory
- an internal AI representation
- another format entirely

Likewise, commands such as:

```text
Read the project map.
Render events 1-10.
Update COSAN state.
```

are only convenient current interfaces.

A future system could perform the same work automatically behind an ordinary chat interface.

---

## 11. Recommended first test

### Option A — Generate a new domain COSAN

```text
Read META_COSAN_v0.3.md.

Create a COSAN for a domain of your choice.
Explain the structure after creating it.
```

### Option B — Start a fiction project

```text
Read FICTION_COSAN_v0.5.md.

I am going to create a story.
Manage the project using COSAN files.

When information is unknown,
keep it unresolved instead of inventing it.
```

Then continue normally:

```text
[story content]
```

After some progress:

```text
Show me the current project state.
```

Then:

```text
Render the first event as complete prose.
```

---

# 한국어

# COSAN 사용법

이 문서는 현재의 상용 AI에서 COSAN을 간단하게 테스트하는 방법을 설명합니다.

COSAN은 프로그래밍 언어가 아니며, 사용자가 고정된 문법을 배울 필요도 없습니다.

현재 구현에서 COSAN 자체는 보통 하나의 Markdown 정의 파일입니다.
예제 프로젝트에 생성되는 `.cosan` 파일은 그 정의를 사용하면서 만들어진 프로젝트 데이터이며, COSAN 자체가 아닙니다.

가장 단순한 테스트 흐름은 다음과 같습니다.

```text
COSAN 정의 파일 (.md)
→ AI
→ 프로젝트 상태 / .cosan 파일 / 렌더링 결과
```

기본적인 흐름은 다음과 같습니다.

```text
사람:
자연어, 아이디어, 판단, 수정

AI:
COSAN 정의 읽기
→ 구조화된 상태 생성 또는 수정
→ 프로젝트 상태 유지
→ 요청할 때 렌더링
```

현재 실험에서는 사용자가 주로 자연어로 작업하고, AI가 COSAN 구조를 관리합니다.

---

## 1. Meta COSAN으로 도메인 COSAN 만들기

Meta COSAN은 특정 분야에 맞는 COSAN을 만들기 위한 하나의 실용적인 방법입니다.

예:

```text
사용자:
META_COSAN_v0.3.md를 읽고
소설용 COSAN을 만들어줘.

AI:
[Meta COSAN 읽기]
[도메인 분석]
[소설용 COSAN 정의 생성]
[결과 검토]
```

다른 분야도 같은 방식으로 시험할 수 있습니다.

```text
META_COSAN_v0.3.md를 읽고
토론용 COSAN을 만들어줘.
```

```text
META_COSAN_v0.3.md를 읽고
게임 기획용 COSAN을 만들어줘.
```

```text
META_COSAN_v0.3.md를 읽고
장기 프로젝트 관리용 COSAN을 만들어줘.
```

생성된 COSAN이 다른 도메인 COSAN과 비슷한 형태일 필요는 없습니다.

COSAN은 하나의 공통 문법으로 정의되는 것이 아닙니다. 목적과 동작이 유지된다면 도메인마다 매우 다른 구조를 사용할 수 있습니다.

---

## 2. 소설 프로젝트 시작하기

COSAN을 가장 쉽게 테스트하는 방법 중 하나는 Fiction COSAN 정의를 사용하는 것입니다.

예:

```text
사용자:
FICTION_COSAN_v0.5.md를 읽어줘.
이제 소설을 만들 거야.
프로젝트를 COSAN 파일로 기록해줘.

AI:
[Fiction COSAN 읽기]
[프로젝트 구조 준비]
```

그 다음부터는 소설 내용을 평범하게 입력하면 됩니다.

```text
사용자:
[소설 내용]

AI:
[내용 해석]
[인물/세계/사건/상태 구조 생성 또는 수정]
[정해지지 않은 정보는 미정 상태로 유지]
[프로젝트 상태 갱신]
```

사용자가 COSAN 문법을 직접 작성할 필요는 없습니다.

AI가 구조를 관리하고, 사용자는 자연어로 계속 작업할 수 있습니다.

---

## 3. 평범한 대화로 계속 작업하기

프로젝트가 시작된 뒤에는 일반적인 대화로 계속 진행할 수 있습니다.

```text
사용자:
다음에는 어떤 일이 생기면 좋을까?

AI:
[여러 방향 제안]

사용자:
두 번째 걸로 하자.

AI:
[구조화된 상태 갱신]
[결정 기록]
```

이전에 만든 설정을 수정할 수도 있습니다.

```text
사용자:
주인공이 도시를 떠난 이유를 바꿔.
두려움 때문이 아니라 죄책감 때문이야.

AI:
[영향받는 상태 찾기]
[관련 구조 수정]
[관계없는 정보는 유지]
```

중요한 점은 매번 전체 프로젝트 상태를 대화창에 다시 넣을 필요가 없다는 것입니다.

프로젝트 상태는 별도의 구조화된 형태로 유지될 수 있습니다.

---

## 4. 구조화된 상태 확인 및 수정

프로젝트 상태가 구조화되어 있기 때문에 상태 자체에 대해 질문할 수 있습니다.

예:

```text
아직 해결되지 않은 질문은 뭐가 있어?
```

```text
숨겨진 방의 존재를 알고 있는 인물은 누구야?
```

```text
사건 12 이후에 무엇이 바뀌었어?
```

```text
아직 불확실한 가정은 뭐가 있어?
```

```text
현재 A와 B의 관계를 보여줘.
```

수정도 요청할 수 있습니다.

```text
여기에 모순이 있어.
충돌하는 상태를 찾아서
관계없는 부분은 바꾸지 말고 수정해줘.
```

```text
이 정보는 추측하지 말고
미정 상태로 바꿔줘.
```

```text
아직 렌더링하지 마.
구조화된 원본만 수정해줘.
```

---

## 5. 구조화된 원본 렌더링하기

일반적인 산문이나 다른 출력 형식이 필요할 때는 구조화된 원본을 렌더링하도록 요청합니다.

예:

```text
사용자:
지금까지 내용을 소설로 렌더링해줘.

AI:
[관련 COSAN 상태 읽기]
[산문 렌더링]
```

다른 형태로도 요청할 수 있습니다.

```text
사건 1부터 5까지 게임 시나리오 형식으로 렌더링해줘.
```

```text
이 부분을 영화 대본 형식으로 렌더링해줘.
```

```text
이 내용을 보고서 형식으로 렌더링해줘.
```

구조화된 원본과 렌더링 결과는 서로 다른 것입니다.

구조화된 원본은 의미를 유지하고 수정하기 위한 것이고,

렌더링 결과는 사람이나 다른 시스템이 사용할 최종 형태입니다.

---

## 6. 긴 결과물은 구간별로 렌더링하기

현재의 상용 AI는 매우 긴 범위를 한 번에 렌더링하도록 요청할수록 내용을 압축하거나 요약하거나 생략하는 경향이 있습니다.

"모든 내용을 빠짐없이 넣어달라"고 명시해도 이 한계를 완전히 없애기는 어렵습니다.

결과물이 AI가 세부를 유지하며 안정적으로 렌더링할 수 있는 길이보다 길다면, 출력만 적당한 구간으로 나눕니다.

```text
구조화된 원본
→ 구간 1 렌더링
→ 구간 2 렌더링
→ 구간 3 렌더링
→ ...
```

소설에서는 사건 단위로 다음처럼 관리할 수 있습니다.

```text
event_001.cosan
event_002.cosan
event_003.cosan
...
```

그리고 하나씩 렌더링합니다.

```text
사건 1을 빠짐없이 산문으로 렌더링해줘.
```

```text
사건 1에서 자연스럽게 이어지도록
사건 2를 렌더링해줘.
```

```text
현재 인물과 세계 상태를 유지하면서
사건 3을 렌더링해줘.
```

출력은 여러 구간으로 나뉘지만, 이야기의 구조 자체는 계속 연결되어 있습니다.

구조화된 상태 없이 짧은 구간을 여러 번 생성하면 구간 사이의 연결이 깨질 수 있습니다.

구조화된 상태가 있으면 각 렌더링 구간이 같은 인물, 관계, 세계 정보, 미해결 정보, 결정, 사건 상태를 계속 참조할 수 있습니다.

---

## 7. 산문 요약과 구조적 압축은 다릅니다

산문의 요약은 보통 정보를 버리면서 짧아집니다.

```text
긴 산문
→ 중요 내용 선택
→ 세부 내용 생략
→ 짧은 요약
```

COSAN은 다른 종류의 압축을 목표로 합니다.

```text
산문 / 아이디어
→ 명시적 상태
→ 관계
→ 참조
→ 조건
→ 사건
→ 구조화된 표현
```

중요한 차이는 다음과 같습니다.

> 산문의 요약은 정보를 버려서 짧아지고,  
> COSAN은 정보를 구조화해서 압축하려고 합니다.

물론 이것이 무손실 변환을 의미하지는 않습니다.

자연어가 구조화된 상태로 변환되는 과정에서도 의미가 달라질 수 있고,

구조화된 상태를 다시 산문이나 다른 형식으로 렌더링할 때도 의미가 변할 수 있습니다.

중요한 작업에서는 구조화된 상태와 렌더링 결과를 함께 검토하는 것이 좋습니다.

---

## 8. ByteCosan

**ByteCosan = Bytecode + COSAN**

ByteCosan은 구조 판단과 최종 렌더링을 분리하기 위한 실험적 중간 표현입니다.

가능한 흐름은 다음과 같습니다.

```text
강한 모델
→ COSAN / 구조 판단
→ ByteCosan
→ 작은 모델 또는 로컬 렌더러
→ 최종 출력
```

강한 모델은 구조, 판단, 해석을 담당하고,

더 작은 모델이나 로컬 모델은 주로 렌더링을 담당할 수 있습니다.

또한 같은 구조화된 내용을 서로 다른 출력 형식이나 스타일로 변환하기 위한 렌더링 중간 표현으로도 사용할 수 있습니다.

ByteCosan은 실험적이고 선택적인 방식입니다.

COSAN 자체가 ByteCosan을 필요로 하는 것은 아닙니다.

---

## 9. 실험적인 검증 흐름

COSAN은 AI가 외부 행동을 하기 전에 구조화된 체크포인트를 만드는 방식으로도 시험할 수 있습니다.

개념적인 흐름:

```text
AI가 행동 제안
→ 결정/행동 상태 구조화
→ 가정 검사
→ 미확정 정보 검사
→ 모순 검사
→ 필요하면 다른 AI가 추가 검토
→ 검토 후 실행
```

예:

```text
이 행동을 실행하기 전에
결정을 구조화된 상태로 작성해줘.

다음을 표시해:
- 가정
- 미확정 정보
- 예상 결과
- 실패 가능 조건

검토가 끝나기 전에는 실행하지 마.
```

이것은 추가적인 검사 계층일 뿐입니다.

정확성이나 안전성을 보장하지는 않습니다.

---

## 10. 현재 파일 구조는 하나의 예시일 뿐입니다

이 저장소의 예시에서는 다음과 같은 형태를 사용할 수 있습니다.

```text
PROJECT_MAP
INDEX
사건 파일
인물 파일
세계 파일
.cosan 파일
```

이것들은 COSAN 자체의 필수 규칙이 아니라 현재 구현의 예시입니다.

COSAN은 다음과 같은 다른 형태로도 구현될 수 있습니다.

- 파일
- 데이터베이스
- 그래프
- 구조화된 메모리
- AI 내부 표현
- 그 밖의 다른 형태

마찬가지로,

```text
프로젝트맵 읽기
사건 1~10 렌더링
COSAN 상태 갱신
```

같은 명령도 현재의 편리한 인터페이스일 뿐입니다.

미래의 시스템에서는 일반적인 채팅 뒤에서 이런 작업이 자동으로 이루어질 수도 있습니다.

---

## 11. 가장 간단한 테스트 방법

### 방법 A — 새로운 도메인 COSAN 만들기

```text
META_COSAN_v0.3.md를 읽어줘.

내가 원하는 분야의 COSAN을 만들어줘.
생성한 뒤 구조를 설명해줘.
```

### 방법 B — 소설 프로젝트 시작하기

```text
FICTION_COSAN_v0.5.md를 읽어줘.

이제 이야기를 만들 거야.
프로젝트를 COSAN 파일로 관리해줘.

정보가 정해지지 않았으면
임의로 만들지 말고 미정 상태로 유지해줘.
```

그 이후에는 평범하게 입력합니다.

```text
[소설 내용]
```

어느 정도 진행한 뒤:

```text
현재 프로젝트 상태를 보여줘.
```

그리고:

```text
첫 번째 사건을 빠짐없이 산문으로 렌더링해줘.
```
