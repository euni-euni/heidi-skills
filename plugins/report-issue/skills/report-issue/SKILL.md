---
name: report-issue
description: heidi-skills 플러그인 사용 중 발견한 이슈·버그·개선 제안을 정리해서 https://github.com/euni-euni/heidi-skills/issues 로 등록. 명시적 호출로만 실행.
---

# Report Issue

heidi-skills의 스킬을 쓰다가 이슈/개선 발견 시 *현재 대화 맥락*에서 정보 추출해 GitHub issue로 빠르게 등록.

## 흐름

### 1. 카테고리 + 대상 스킬

AskUserQuestion 1회 호출에 두 질문 묶어서:

```
questions[0]:
  question: "어떤 종류의 이슈야?"
  header: "카테고리"
  options:
    - label: "버그"
      description: "예상대로 동작하지 않거나 에러가 발생함"
    - label: "개선 제안"
      description: "동작은 하지만 더 나은 방식이 있음"
    - label: "질문"
      description: "사용법이나 의도 확인"
  multiSelect: false

questions[1]:
  question: "어떤 스킬에 대한 이슈야?"
  header: "대상 스킬"
  options:
    - label: "craft-landing"
      description: "랜딩 페이지 4-phase 프로세스 스킬"
    - label: "report-issue"
      description: "이 스킬 자체에 대한 이슈"
    - label: "전체/기타"
      description: "특정 스킬 무관 또는 marketplace 전반"
  multiSelect: false
```

(향후 스킬 추가되면 옵션 갱신.)

### 2. 컨텍스트 자동 추출

현재 대화 맥락에서 다음 정보 추출. user에게 다시 물어보지 X (대화에 이미 있으니까).

- **무엇을 하려 했나** — user의 의도/요청
- **무엇이 일어났나** — 실제 결과 (Claude 응답, 에러, 예상 외 동작)
- **재현 방법** — 단계별 (있으면)
- **에러 메시지/스크린샷** — 있으면 그대로 인용

대화 맥락 부족하면 평문으로 한 번만 추가 정보 요청.

### 3. Issue 초안 작성 + 컨펌

마크다운으로 *완성된 issue* 작성해서 미리보기 → user 컨펌:

```markdown
## 무엇을 하려 했나
{intent}

## 무엇이 일어났나
{actual}

## 재현
1. {step}
2. {step}

## 예상
{expected}

## 환경
- Claude Code 버전: {version if known}
- 스킬 버전: {plugin version}
- OS: {os if mentioned}
```

Title 형식:
- 버그: `[Bug] {스킬명}: {짧은 요약}`
- 개선: `[Enhancement] {스킬명}: {짧은 요약}`
- 질문: `[Question] {스킬명}: {짧은 요약}`

컨펌 메시지: "이렇게 등록할게 — 수정할 거 있어?"

### 4. Issue 생성

user 컨펌 후 `gh` CLI로 등록:

```bash
gh issue create \
  --repo euni-euni/heidi-skills \
  --title "{title}" \
  --body "{body}"
```

label은 repo에 정의된 게 있으면 추가, 없으면 생략.

### 5. URL 반환

생성된 issue URL을 user에게 알려주고 끝.

## 의무 가드레일

- **user 컨펌 없이 issue 생성 X** — 4번 단계에서 반드시 미리보기 + 컨펌.
- **추측·과장 X** — 대화에 없는 내용을 "아마 ~일 것" 식으로 채우지 말 것. 모르면 명시.
- **민감 정보 점검** — title/body에 회사 내부 정보(콴다 PRD 슬러그·메트릭 등)가 들어가는지 확인. heidi-skills는 public repo. 들어가면 user에게 명시 경고 후 결정.

## Scope-out

- private repo로의 issue 등록 (이 스킬은 heidi-skills 전용)
- 기존 issue 검색·comment (별도 작업)
- PR 생성 (별도 작업)
