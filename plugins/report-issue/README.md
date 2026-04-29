# report-issue

heidi-skills 플러그인 사용 중 발견한 이슈·버그·개선 제안을 GitHub Issues로 등록하는 스킬.

## 설치

```
/plugin marketplace add euni-euni/heidi-skills
/plugin install report-issue@heidi-skills
/reload-plugins
```

## 사용

자연어 또는 슬래시로 호출:

```
"이거 리포트해줘"
"craft-landing 이슈 등록해줘"
/report-issue:report-issue
```

호출하면 다음 흐름이 자동:

1. **컨텍스트 자동 추론** — 대화 맥락에서 카테고리(버그/개선/질문) · 대상 스킬 · 의도 · 실제 결과 · 재현 · 에러 모두 추출. 다시 묻지 X
2. **Issue 초안 작성** — title + body 마크다운 *전부 채워서*
3. **미리보기 + 컨펌** — "이대로 등록할까? 수정할 거 있어?" 어디든 자유롭게 정정 가능
4. **Issue 생성** — `gh issue create`로 등록 후 URL 반환

추론 못하는 게 있으면 placeholder(`{TODO}`)로 두고 미리보기에서 user가 채움. AskUserQuestion 반사적 사용 X — 진짜 모호한 경우만.

## 의무 가드레일

- user 컨펌 없이 issue 생성 X
- 대화에 없는 내용 추측·과장 X
- **민감 정보 점검** — heidi-skills는 public repo. title/body에 회사 내부 정보(콴다 PRD 슬러그·메트릭 등) 들어가면 user에게 경고

## 전제

- 로컬에 `gh` CLI 설치 + `gh auth login` 완료
- euni-euni/heidi-skills repo에 issue 생성 권한 (heidi 본인 또는 collaborator)

## Scope-out

- private repo로의 issue 등록 X (heidi-skills 전용)
- 기존 issue 검색·comment X
- PR 생성 X
