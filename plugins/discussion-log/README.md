# discussion-log

현재 대화에서 이루어진 **주요 논의·의사결정·유저 피드백·Claude 반성**을 구조화된 `discussion-log.md`로 정리하는 Claude Code 스킬.

대화 중간이든 끝이든 실행 가능. 깔끔한 요약보다 *맥락이 살아있는 기록*이 목표 — 유저의 실제 발화를 인용으로 보존하고, 어떤 대안이 있었고 왜 기각됐는지까지 드러낸다.

## 언제 쓰나

- wizard-planning / wizard-design 같은 긴 세션에서 의사결정 흐름을 남기고 싶을 때
- 유저 챌린지·반론으로 방향이 바뀐 지점을 기록해두고 싶을 때
- Claude의 잘못된 근거·과한 동조 패턴을 회고로 남기고 싶을 때
- 다음 세션의 컨텍스트로 쓸 raw 디스커션 로그가 필요할 때

## 전제

- [Claude Code](https://code.claude.com) 설치
- GitHub 접근만 되면 OK (heidi-skills는 public)

## 설치

Claude Code 안에서:

```
/plugin marketplace add euni-euni/heidi-skills
/plugin install discussion-log@heidi-skills
/reload-plugins
```

설치 확인: `/help`에서 `discussion-log:discussion-log` 보이면 OK.

## 사용

### 호출

```
/discussion-log
/discussion-log {토픽 키워드}
```

- 인자 없으면 전체 대화 포괄 정리
- 인자 있으면 해당 토픽 관련 논의만 집중 정리 (예: `/discussion-log 세션 구조`)

### 출력 위치 결정

다음 순서로 자동 판단:

1. wizard-planning 논의 → `.wizard/output/{project}/planning/discussion-log.md`
2. wizard-design 논의 → `.wizard/output/{project}/design/discussion-log.md`
3. 이미 `discussion-log.md` 존재 → 기존 파일에 append (마지막 토픽 번호 이어서)
4. 그 외 → AskUserQuestion으로 후보 2~3개 제안 후 선택

### 출력 구조

토픽별로 다음 섹션 반복:

```
## N. {논의 토픽}
### 배경        — 어떤 맥락에서 시작됐는지
### 논의 과정   — 유저 발화 raw 인용 + Claude 대응 + 챌린지 + 수정
### 결론        — 최종 결정 + 기각된 대안
### 교훈        — 있을 때만
```

마지막에 **핵심 교훈 (Claude 자체 회고)** 섹션 — 전체 대화에서 Claude가 개선할 패턴.

## 핵심 원칙

1. **Raw 메시지 보존** — 유저 발화는 `>` 인용으로 그대로. 요약 변환 X
2. **맥락 변질 방지** — A 주장 → B 반론 → C 수정 흐름 그대로 드러나게
3. **솔직한 반성** — Claude가 과하게 동조했거나 잘못된 근거를 댄 경우 솔직하게 기록
4. **기록 > 정리** — 깔끔한 문서보다 맥락이 살아있는 문서

## 알아둘 거

- 사소한 인사·단순 확인은 포함 X. 의사결정·논의가 있었던 부분만
- 대화가 길수록 풍부한 로그가 생성됨 — 짧은 세션은 빈약할 수 있음
- 유저가 챌린지한 내용은 반드시 원문 인용 포함

## 업데이트

```
/plugin update discussion-log@heidi-skills
/reload-plugins
```

## 제거

```
/plugin uninstall discussion-log@heidi-skills
```

## 상태

**v0.1.0**. 개인 워크플로용으로 시작 — heidi-skills repo의 다른 스킬(craft-landing 등)과 함께 사용.

## 피드백

이슈 / PR / 메시지 환영. heidi-skills repo 또는 Slack DM.
