# Case 1 — AI 학습매니저 학생 사전등록 랜딩

> **기간**: 2026-04-20 ~ 2026-04-21 (2일)
> **타겟**: 한국 중위권 중고등학생
> **전환 목표**: 사전등록 (waitlist)
> **production URL**: https://student-study-manager.vercel.app/
> **source**: vibe-monorepo `vibe-faketest-ai-study-manager-student/src/App.jsx + index.css`
> **원본 회고**: `backlog/2026/04/ai-study-manager/student-landing/discussion-log.md` (37 섹션)

## Input

- PRD: `.wizard/output/ai-study-manager/`
- 제품 정체: **두 코어 동등** — (1) 메타인지 진단(이미 아는 것 빼기), (2) 학습 행정 자동화(오답·계획·복습 자동 처리)
- 태그라인: "안 해도 되는 거 다 치워줄게. 시간 아까우니까"

## 산출 skeleton (6 섹션)

1. **Hero** (`hero-text`) — 약속
2. **Moment** (`#assistant`) — 공감/문제 ("시간 잡아먹는 일들, 전부 네가 해야 해?")
3. **How** (`how`) — Step 01/02/03 메커니즘
4. **Reveal** (`#tutor`) — 두 번째 코어 (메타인지 진단)
5. **CTA** (`#join`) — 전환 + social bar
6. **FAQ**

## 4-D 레퍼런스 매트릭스 (실제 사용)

- **타겟 visual diet**: 토스, 무신사, 디스코드, 카카오웹툰, Cake
- **같은 도메인 강자**: openclaw.ai (코랄 #ff4d4d 액센트 차용), Brilliant (차별화)
- **다른 도메인 내러티브**: Linear (arc 구조), Granola (1인칭 톤)
- **부분 UI**: Apple iOS 캘린더 (Step 02), Unsplash 갤러리 (Step 01)

## Phase별 주요 의사결정

### Phase 2 — 톤앤매너
- 컬러 4-안 (lime / blue / red / yellow) 비교 → coral red 채택
- 액센트 3% 룰 적용
- Foundation 토큰화 (`foundation.html`)

### Phase 3 — 내용
- v1 카피 ("AI 학습매니저는 너의 학습 위에 깔린 관리 레이어야") → 공급자 관점 ❌
- 최종 hero: "공부 잘하는 애는 / 사실 혼자 다 안 해" + "귀찮은 일은 맡겨버리고, 뭘 빼야 하는지 알게 된 거야"
- 두 코어 균형 (행정 + 진단) 양쪽 시그널
- 학술 stat (CHI 2025 8.9% / IJASSR 2025 20%) → 학생 매력 부재로 제거

### Phase 4 — 에셋
- Step 01 갤러리: unsplash → 수학·로그·어법 SVG 일러스트로 교체
- Step 02 월뷰 (Apple iOS 캘린더 차용)
- Step 03 narrative — user 제안이 Claude 방안보다 우수 (sequential보다 cross-fade가 "restart" 자연)

## 예외 사건 (스킬화 X)

- **Day 2 v3 → v4 큰 리디자인**: Day 1 v3 완성 후 user "제품 정체성을 한 랜딩에 담는 구조적 긴장"으로 근본 질문 → Phase 2부터 재진입. 매 프로젝트 재현 보장 X.
- **PR #279 머지 + Vercel 배포 복구 사건**: Claude가 CSR/Next.js 앱을 curl 검증만으로 "사이트 깨짐" 단정 → memory `feedback_verify_before_alarm_csr.md`에 보존.

## 회고 요약

- **잘 된 것**: 4-D 매트릭스로 학생 visual diet 강제 / 두 코어 균형 점검 / 토큰화로 일관성
- **반복 실수**: selection bias (Anthropic 톤) 1차에 등장 / PRD 언어 그대로 사용 / 학술 stat 일반론
- **메타 교훈**: discussion-log 71개 ID에서 의미 있는 phase는 4개로 압축 가능. 즉 *과정의 micro 결정*과 *프로세스 phase*는 다른 레이어.
