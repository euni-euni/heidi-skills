# craft-landing

랜딩 페이지를 input(define.md/prd.md/대화)에서 출발해 4-phase 프로세스로 빚는 Claude Code 스킬.

시각 originality는 별개의 `wizard-design:landing-design-create`가 담당하고, 이 스킬은 *의사결정 흐름·카피·구조·톤앤매너 도출*을 다룬다. 명시적 호출로만 실행.

## 전제

- [Claude Code](https://code.claude.com) 설치
- GitHub 접근만 되면 OK (heidi-skills는 public)

## 설치

Claude Code 안에서:

```
/plugin marketplace add euni-euni/heidi-skills
/plugin install craft-landing@heidi-skills
/reload-plugins
```

설치 확인: `/help`에서 `craft-landing:craft-landing` 보이면 OK.

## 사용

### 호출

세 가지 방식 (편한 거 선택):

1. 슬래시 직접: `/craft-landing:craft-landing`
2. 자연어: `"craft-landing으로 [제품명] 랜딩 만들어줘"`
3. SKILL.md에 *명시적 호출만* 룰 박혀 있어서 자율 invoke 안 됨 — 위 둘 중 하나로 직접 호출 필요

### Phase 1 — Input gathering (자동 진행)

호출 후 첫 단계에서 다음 흐름이 자동:

| Round | 내용 |
|---|---|
| 1 | 맥락 source — wizard 산출물 / 노션 / 현재 대화 (객관식) |
| 1.5 | 분기 후속 — slug / 노션 링크 / skip (자유 입력) |
| (자동) | Claude가 input 문서 읽기 |
| 컨펌 | 제품 한 줄 요약 + 타겟 + wow point + 전환 후보를 *Claude가 정리* → "빠진 내용·강조하고 싶은 거 있어?" |
| 2 | 전환 목표 + 작업 위치 묶음 (객관식) |
| 2.5 | vibe-monorepo 폴더명 컨펌 / 다른 위치 자유 입력 |

이후 Phase 2~4 순차 진행. **각 phase 분기점에서 user 컨펌 받음 (자율 진행 X)**.

### Phase 흐름 (개요)

| Phase | 무엇 | 핵심 룰 |
|---|---|---|
| 1 | 시작 prompt + 첫 draft (originality starting point) | 결정 근거 표 형태로 보고 |
| 2 | 톤앤매너 교정 — 외부 리서치 → 4-D 매트릭스 → 4안 → 토큰화 | 매 결정에 *왜* 명시. 직관/추측 X |
| 3 | hero + 내러티브 — 타겟 일상 언어로 번역 | "공급자적 관점" 카피 거부, 어미·화자 톤 일관성 |
| 4 | 에셋 (placeholder → 실제) | cliché 디테일(스탬프·형광펜·generic 손글씨) 가드레일 |

자세한 phase 명세 + anti-patterns + 토큰 스키마는 스킬 안에 포함 (`phases.md`, `references-matrix.md`, `tokens-schema.md`, `anti-patterns.md`).

## 알아둘 거

### Scope-out (이 스킬에서 안 다룸)

- **카피 fine-tuning** (어미·단어 단위 미세 조정) — 개인 능력
- **시각 originality 가드레일** — `wizard-design:landing-design-create`
- **production 배포** (vibe-monorepo + Vercel) — `wizard-vibecoding:vibe-vercel-migrate`
- **근본 재시작** (큰 리디자인) — 예외 사건

### 의무 가드레일

- **Phase 2 진입 전 외부 리서치 의무** — 타겟 visual diet (와이즈앱·한국언론진흥재단 등) / 트렌드 (Creative Bloq 등) / 경쟁사. 회고·추정으로 채우면 anti-pattern #7.
- **분기점 user 컨펌 의무** — Phase 진입/완료, 후보 1안 선택, hero single message 등 큰 분기는 자율 X.

## 업데이트

```
/plugin update craft-landing@heidi-skills
/reload-plugins
```

## 제거

```
/plugin uninstall craft-landing@heidi-skills
/plugin marketplace remove heidi-skills
```

## 상태

**v0.1.0 베타**. 첫 케이스(ai-study-manager 학생 랜딩)는 완주, 두 번째 케이스(edu-ai-os 학생 랜딩)는 Phase 2 미완 후 스킬 보강. N=3 케이스에서 또 다른 보강 패턴 등장 예상.

회고·케이스 자료는 별도 private repo (heidi-notes)에 보관.

## 피드백

이슈 / PR / 메시지 환영. heidi-skills repo 또는 Slack DM.
