---
name: report-issue
description: heidi-skills 플러그인 사용 중 발견한 이슈·버그·개선 제안을 정리해서 https://github.com/euni-euni/heidi-skills/issues 로 등록. 명시적 호출로만 실행.
---

# Report Issue

heidi-skills 스킬을 쓰다가 이슈/개선 발견 시 *현재 대화 맥락*에서 자동 추출해 GitHub issue로 빠르게 등록.

## 핵심 원칙

**추론 → 미리보기 컨펌**. AskUserQuestion 반사적 사용 X. 대화 맥락에서 추론 가능한 건 다시 묻지 말 것 — 추론값으로 issue 초안 *전부 채운 뒤* 미리보기로 user 컨펌.

## 흐름

### 1. 컨텍스트 자동 추론

대화 맥락에서 다음을 추출. user에게 다시 묻지 X:

| 항목 | 추론 방법 |
|---|---|
| **대상 스킬** | 가장 최근 호출되거나 명시 언급된 스킬. 예: 직전에 craft-landing 썼으면 default = craft-landing |
| **카테고리** | 맥락에서 추론. "에러"·"안 됨"·"이상함" → 버그 / "~했으면 좋겠다"·"~면 좋을 텐데" → 개선 / "어떻게"·"왜"·"의미" → 질문 |
| **무엇을 하려 했나** | user의 의도/요청 |
| **무엇이 일어났나** | 실제 결과 (Claude 응답, 에러, 예상 외 동작) |
| **재현 방법** | 단계별 (대화에 있으면) |
| **에러 메시지/스크린샷** | 있으면 그대로 인용 |
| **환경** | Claude Code 버전·OS·스킬 버전 (대화에서 알 수 있으면) |

대화 맥락 *진짜 부족*하면 평문 한 번만 추가 정보 요청 (AskUserQuestion 아님).

### 2. Issue 초안 작성

Title 형식:
- 버그: `[Bug] {스킬명}: {짧은 요약}`
- 개선: `[Enhancement] {스킬명}: {짧은 요약}`
- 질문: `[Question] {스킬명}: {짧은 요약}`

Body markdown:
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

### 3. 미리보기 + 컨펌

*완성된* issue 전체를 보여주고:

> 이렇게 등록할게.
> [title + body 마크다운]
> 수정할 거 있어? (카테고리/대상 스킬/제목/본문 어디든)

**user는 자유롭게 어디든 정정** — 카테고리·대상 스킬·title·body 항목별로 고침. 정정되면 다시 미리보기 → 컨펌 반복.

### 4. Issue 생성

user 컨펌 후 `gh` CLI:

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

- **user 컨펌 없이 issue 생성 X** — 3번 단계 미리보기 + 컨펌 의무.
- **추측·과장 X** — 대화에 없는 내용을 "아마 ~일 것" 식으로 채우지 말 것. 모르면 placeholder (`{TODO}`) 또는 미리보기에서 명시.
- **민감 정보 점검** — title/body에 회사 내부 정보(콴다 PRD 슬러그·메트릭 등)가 들어가는지 확인. heidi-skills는 public repo. 들어가면 user에게 명시 경고 후 결정.
- **AskUserQuestion 반사적 사용 X** — 추론 가능한 건 추론, 미리보기로 컨펌.

## Scope-out

- private repo로의 issue 등록 (이 스킬은 heidi-skills 전용)
- 기존 issue 검색·comment (별도 작업)
- PR 생성 (별도 작업)
