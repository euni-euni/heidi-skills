---
name: craft-landing
description: 제품/마케팅 랜딩 페이지를 input(define.md, prd.md, 또는 대화)에서 출발해 단계별로 만들어가는 프로세스 스킬. 시각 originality는 별개의 wizard-design:landing-design-create가 담당하고, 이 스킬은 의사결정 흐름·카피·구조·톤앤매너 도출을 다룬다. 명시적 호출로만 실행.
---

# Craft Landing

`define.md` / `prd.md` / 또는 즉석 대화 input을 받아, 4개 phase + cross-cutting 가드레일을 따라 랜딩 페이지를 빚는다.

## 4 Phases

### Phase 1 — 시작 prompt + 새 브랜치/페이지

input 정리(define.md/prd.md/대화)된 상태에서 다음 prompt로 시작한다:

> ~한 랜딩을 만들거야.
> 어떠한 스킬도 사용하지 마. 너의 독창성을 최대한 뽐내고, 현대적인 감각으로, 모바일 퍼스트 랜딩 페이지를 그려줘.
> 이 세션에서는 지침이나 메모리가 하나도 없는 깔끔한 상태로 작업을 시작하고 싶어. 만약 가지고 있는 게 있어도 무시하고 바닐라 상태인 것처럼 작업해줘.

→ 첫 산출물(draft 1) 생성. 이 단계는 *시각 originality*에 집중하는 단계로, 이후 phase에서 비판적으로 교정한다.

### Phase 2 — 디자인 톤앤매너 교정

`references-matrix.md`의 4-D 레퍼런스 매트릭스로 톤 후보 수집 → 후보 3안 비교 → 선택 → `tokens-schema.md`로 토큰화.

**핵심 룰**: 색상/타이포/모티프/레이아웃 매 결정에 *이유* 명시. "도파민 컬러", "현대적" 같은 패턴 언급만으로는 불충분 — 4-D 레퍼런스 중 무엇이 받치는지 명시.

### Phase 3 — 내용 (hero + 내러티브)

Hero에서 가장 전달할 한 가지 + 랜딩 전반 내러티브 arc 잡기. prompt 패턴:

> 너는 이미 유명 에이전시의 시니어 마케터처럼 현대적·독창적으로 다시 고심해서 [내용/카피]을 잡아줘

**핵심 룰**: PRD 내부 용어를 *타겟 일상 언어*로 번역. "공급자적 관점"의 카피는 즉시 거부. 타겟이 매일 쓰는 말로 다시.

### Phase 4 — 에셋 추가/수정

그래픽/애니메이션/일러스트. **placeholder 먼저**, 실제 에셋 작업은 별도 단계로 분리. (v0에서 세부는 미정)

## Cross-cutting

**모바일 분기는 처음부터, 그리고 매 수정 단계마다.** 데스크탑 우선으로 짜고 나중에 모바일 맞추기 X.

## Scope-out (이 스킬에서 다루지 않음)

- **카피 fine-tuning** (어미·단어 단위 미세 조정) — 개인 능력에 맡김
- **production화** (vibe-monorepo 이관 + Vercel 배포) — `wizard-vibecoding` 스킬 사용
- **시각 originality 가드레일** — `wizard-design:landing-design-create` 스킬이 담당
- **근본 재시작** (예: ai-study-manager Day 2 v3 → v4 같은 큰 리디자인) — 예외 사건, 스킬화 X

## Reference 파일

- `phases.md` — 각 phase 상세
- `references-matrix.md` — 4-D 레퍼런스 매트릭스
- `tokens-schema.md` — 디자인 토큰 스키마 (값은 매 프로젝트 채움)
- `anti-patterns.md` — Claude 반복 실수 5종 가드레일
- `cases/ai-study-manager-student.md` — 첫 케이스
