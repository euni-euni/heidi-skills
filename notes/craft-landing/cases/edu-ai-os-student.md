# Case 2 — Edu AI OS 학생 사전등록 랜딩

> **기간**: 2026-04-28 (1일, **Phase 2 미완**)
> **타겟**: 한국 중위권 중고등학생
> **전환 목표**: 사전등록 (waitlist)
> **production URL**: 미배포 (Phase 2 보류)
> **source**: 새 브랜치 `sync/edu-ai-os-student-landing`, `vibe-faketest-edu-ai-os-student/`
> **원본 회고**: `notes/craft-landing/discussion-log.md` (19 섹션)
> **상태**: **스킬 결함 다수 노출 → 스킬 보강 후 재진입 예정**

## Input

- PRD: `.wizard/output/edu-ai-os/` (define.md, product-overview, README)
- 타겟 모호 → user 명시 확인: 학생용 + 별개 신규 + waitlist
- 인프라 카피 출처: `vibe-faketest-ai-study-manager-student/`

## Phase 1 — 시작 prompt + 첫 draft

다크 base + 라임 acid (#B9FF66) + OS 메타포 (시스템 prologue, monospace 일부) + 통계 1247명 mock.

**보고 결함**: 결과만 보고. 결정 근거 누락.
→ user 지적 후 표 형태 정정 (input/직관/risk 분류).
→ **교훈**: Phase 1 보고도 결정 근거 의무. (anti-pattern → cross-cutting "보고 시 결정 근거" 룰 추가)

## Phase 2 — 톤앤매너 (미완료)

### 진행 흐름

1. 색 후보 — *전부 라임 #B9FF66 고수*. 색상 자체가 후보화 안 됨. user 지적.
2. 무드보드 v1 — 다크 base 동일 + 액센트만 다른 5안. user "이건 컬러 배리에이션이지 무드보드 X".
3. 무드보드 v2 (M1-M4) — 4결 시도. M3 = 보라+그라디언트+glow → "AI톤" 거부. M1/M4 유치원 결.
4. 무드보드 v3 (M2/M5/M6/M8) — 모두 "절제 또는 임팩트"로 묶임. 형용사 차원 다양성 부족.
5. 형용사 매트릭스 (Q1-Q4 시크/따뜻/캐주얼/친근) — 사후 라벨링이라 user 지적.
6. 4안 매트릭스 v6 (제품 정체성/학생 친숙/교집합/새로운) — A "겸손/배경"이 패인.
7. v7 (학생 visual diet 외부 리서치 후) — A 제품 우선 / B 학생 현재 비비드 / C 교집합 / D 학생 미래 anti-AI Tactile.
8. B/D 퀄 떨어짐 → cliché 디테일 정정 (B 광고 톤, D 학생 다이어리 광고 톤).

### 노출된 스킬 결함

| 분류 | 결함 | 발견 토픽 |
|---|---|---|
| 외부 리서치 | 학생 visual diet, 트렌드 모두 *내 지식·회고·추정*. 3차례 명시 지적 후에야 WebSearch | §4, §14, §15 |
| 후보화 | 색 후보 단일 (라임 고수) | §4 |
| 추측 단정 | "AI톤 = 보라/파랑 dominant" 거짓 일반화 | §5 |
| 무드보드 운용 | 컬러 배리에이션을 무드보드라 부름 | §6 |
| 형용사 도출 | 결을 먼저 떠올린 후 형용사 사후 라벨링 | §9 |
| 키워드 분리 | 전략 키워드 (겸손/배경)를 시각에 직역 | §12 |
| 합집합/교집합 | 합집합에서 임의 픽 → "교집합"이라 부름 | §10 |
| cluster화 | 정리/절제/모던을 다른 셋에 분리 (시각으로 95% 같음) | §11 |
| 4안 차별화 | 교집합 자동 base, 주축/부가 명시 안 함 | §13 |
| cliché | B 광고 톤 (3-color collision, stroke 외곽선), D 학생 다이어리 광고 톤 (URGENT 스탬프, 형광펜 직역) | §16, §17 |
| 컨펌 분기 | "Phase 2-3 하고 리뷰" 발화를 자율 진행으로 해석 | §3 |
| 레퍼런스 분석 | 카카오웹툰/Spotify *분리만* 답, 공통 인사이트 추출 누락 | §18 |
| 어미 톤 | OS 객관 + 친근 반말 혼재 (기계 톤) | §4 phase 3 |

### 외부 리서치 결과 (Phase 2 종료 시점)

WebSearch 후 진짜 한국 10대 visual diet:
- 인스타 MAU 412만 (압도) · 유튜브 사용시간 1위 · 틱톡 MAU 203만 · 카카오톡 · 콴다 · 핀터레스트 174만

이전 추정 (토스/무신사/디스코드/카카오웹툰)과 진짜 데이터가 *상당히 다름*. visual diet도 미니멀과 chaos+비비드+임팩트 양쪽 공존.

2026 Gen Z 트렌드 (Creative Bloq):
- "fun and real" > "professional and serious"
- "chaos and colors" > perfection
- Anti-minimalism (claymation, watercolor, tactile)
- Anti-AI smooth (인간 손길 craving)

→ D 안 (학생 노트북 / Anti-AI / Tactile)이 사실 *2026 학생 미래 트렌드*와 정렬. 이전 "양쪽 안 따름"이라 한 건 부분만 맞음.

## 회고 요약

### 반복 패턴 (3번 이상)

1. **외부 리서치 회피 → 내 지식·직관 단정** (협업 원칙 #2/#4 직접 위반)
   - 학생 visual diet · D 트렌드 · 카카오웹툰 placeholder · "보라/파랑 AI톤"
   - 3차례 명시 지적 후 WebSearch
2. **컨펌 없이 자율 진행** — anchor 역할 부재 (협업 원칙 #1)
3. **카테고리화 욕망 → 동어반복/인위적 구분** — 정리/절제/모던 분리, 합집합을 교집합이라 부름

### 진짜 원인 추정

- **속도 욕망**: 빨리 결과 보여주려 검증 skip
- **권위 욕망**: 추측을 사실처럼 단정해 전문가 톤 유지
- **회피 욕망**: 외부 리서치 = 시간 비용 + 도구 로드 → 회피

## 스킬 보강 반영 (이 케이스 → SKILL)

| 케이스 발견 | 반영 위치 |
|---|---|
| 외부 리서치 회피 3회 반복 | `phases.md` Phase 2 진입 전 의무 + `references-matrix.md` 출처 + `anti-patterns.md` #7 |
| 컨펌 없이 자율 진행 | `SKILL.md` cross-cutting + `anti-patterns.md` #11 |
| 추측 단정 | `anti-patterns.md` #6 |
| 무드보드 ≠ mockup | `phases.md` Phase 2 무드보드 운용 + `anti-patterns.md` #12 |
| 형용사 사후 라벨링 | `phases.md` Phase 2 순서 명시 + `anti-patterns.md` #8 |
| 전략 vs 디자인 키워드 | `phases.md` Phase 2 분리 + `anti-patterns.md` #9 |
| cliché 디테일 | `phases.md` Phase 4 가드레일 + `anti-patterns.md` #10 |
| 레퍼런스 분석 패턴 | `references-matrix.md` 분석 패턴 3단계 + `anti-patterns.md` #13 |
| 후보화 차원 분리 | `phases.md` Phase 2 흐름 1단계 |
| 어미 톤 일관성 | `phases.md` Phase 3 핵심 룰 2 |
| 4안 매트릭스 주축/부가 | `phases.md` Phase 2 흐름 4단계 |

## 메타 교훈

- 케이스 1 (ai-study-manager)은 *완주 후 회고*였고, 케이스 2는 *Phase 2 미완 → 스킬 회수*.
- 첫 사용에서 스킬 결함이 다수 노출된다는 것 자체가 *케이스 1만으로는 일반화 부족*했다는 신호.
- 스킬은 *N=1로 시작 → N=2~3에서 큰 보강* 패턴이 자연스러움. 이번 보강 후 N=3 케이스에서 또 다른 패턴 등장 예상.
