# heidi-skills (plugin)

heidi-skills marketplace의 **기본 도구 모음**. 별도 plugin으로 분리할 정도는 아니지만 자주 쓰는 *가벼운 단일 스킬*들을 한 plugin으로 묶었다.

> **포함 기준**: SKILL.md 한 개 + 짧은 정의로 자족하는 스킬은 여기. 보조 문서·agents·hooks·MCP 같은 부속 자산이 따라붙는 복합체(예: craft-landing)는 별도 plugin.

## 포함 스킬

| 스킬 | 호출 | 설명 |
|---|---|---|
| `report` | `/heidi-skills:report` | heidi-skills 플러그인 사용 중 발견한 이슈·버그·개선을 GitHub Issues로 등록 |
| `discussion-log` | `/heidi-skills:discussion-log` | 현재 대화의 주요 논의·의사결정·유저 피드백·Claude 반성을 raw 인용 보존하며 `discussion-log.md`로 정리 |

## 설치

```
/plugin marketplace add euni-euni/heidi-skills
/plugin install heidi-skills@heidi-skills
/reload-plugins
```

(plugin 이름과 marketplace 이름이 같아 살짝 redundant하게 보이지만 동작 정상.)

## 사용 — `report` 스킬

자연어 또는 슬래시로 호출:

```
"이거 리포트해줘"
"craft-landing 이슈 등록해줘"
/heidi-skills:report
```

호출하면 자동:

1. **컨텍스트 자동 추론** — 대화 맥락에서 카테고리·대상 스킬·의도·결과·재현·에러 모두 추출
2. **Issue 초안 작성** — title + body 마크다운 *전부 채워서*
3. **미리보기 + 컨펌** — AskUserQuestion으로 등록/취소/수정 (Enter 한 번에 등록)
4. **Issue 생성** — `gh issue create`로 등록 후 URL 반환

추론 못하는 게 있으면 placeholder(`{TODO}`)로 두고 미리보기에서 user가 채움.

### 의무 가드레일 (report)

- user 컨펌 없이 issue 생성 X
- 대화에 없는 내용 추측·과장 X
- **민감 정보 점검** — heidi-skills는 public repo. title/body에 회사 내부 정보(콴다 PRD 슬러그·메트릭 등) 들어가면 user에게 경고

### 전제 (report)

- 로컬에 `gh` CLI 설치 + `gh auth login` 완료
- euni-euni/heidi-skills repo에 issue 생성 권한 (heidi 본인 또는 collaborator)

## 사용 — `discussion-log` 스킬

```
/heidi-skills:discussion-log
/heidi-skills:discussion-log {토픽 키워드}
```

- 인자 없으면 전체 대화 포괄 정리
- 인자 있으면 해당 토픽 관련 논의만 집중 정리

### 출력 위치 자동 결정

1. wizard-planning 논의 → `.wizard/output/{project}/planning/discussion-log.md`
2. wizard-design 논의 → `.wizard/output/{project}/design/discussion-log.md`
3. 이미 `discussion-log.md` 존재 → 기존 파일에 append (마지막 토픽 번호 이어서)
4. 그 외 → AskUserQuestion으로 후보 2~3개 제안 후 선택

### 출력 구조

토픽별로 `## N. {토픽} → ### 배경 / 논의 과정 / 결론 / 교훈` 반복. 마지막에 **핵심 교훈 (Claude 자체 회고)** 섹션.

### 핵심 원칙 (discussion-log)

1. **Raw 메시지 보존** — 유저 발화는 `>` 인용 그대로
2. **맥락 변질 방지** — A 주장 → B 반론 → C 수정 흐름 그대로
3. **솔직한 반성** — Claude가 과하게 동조했거나 잘못된 근거를 댄 경우 솔직하게 기록
4. **기록 > 정리** — 깔끔한 문서보다 맥락이 살아있는 문서

## Scope-out

- private repo로의 issue 등록 (heidi-skills public 전용)
- 기존 issue 검색·comment
- PR 생성
- discussion-log은 raw 인용 보존이 핵심 — 깔끔 요약 원하면 별도 도구 사용
