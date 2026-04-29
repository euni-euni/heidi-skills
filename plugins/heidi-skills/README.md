# heidi-skills (plugin)

heidi-skills marketplace 자체에 대한 메타 도구 모음. 현재는 issue report 스킬 1개. 향후 marketplace 운영·관리 관련 스킬 추가 시 이 plugin에.

## 포함 스킬

| 스킬 | 호출 | 설명 |
|---|---|---|
| `report` | `/heidi-skills:report` | heidi-skills 플러그인 사용 중 발견한 이슈·버그·개선을 GitHub Issues로 등록 |

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

## 의무 가드레일

- user 컨펌 없이 issue 생성 X
- 대화에 없는 내용 추측·과장 X
- **민감 정보 점검** — heidi-skills는 public repo. title/body에 회사 내부 정보(콴다 PRD 슬러그·메트릭 등) 들어가면 user에게 경고

## 전제

- 로컬에 `gh` CLI 설치 + `gh auth login` 완료
- euni-euni/heidi-skills repo에 issue 생성 권한 (heidi 본인 또는 collaborator)

## Scope-out

- private repo로의 issue 등록 (heidi-skills 전용)
- 기존 issue 검색·comment
- PR 생성
