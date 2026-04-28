# 디자인 토큰 스키마

ai-study-manager `foundation.html`에서 추출한 v0 스키마. **이름·구조만** reference. 값은 매 프로젝트마다 Phase 2에서 채운다.

> v0 주의: 케이스 1개(ai-study-manager) 기반이라 그 프로젝트에 약간 종속될 수 있다. 케이스 누적되면서 abstract.

## Color

```
--color-bg              /* 페이지 베이스 */
--color-bg-alt          /* 섹션 alt (대비용) */
--color-fg              /* 본문 text */
--color-fg-muted        /* 서브 text */
--color-line            /* divider, border */
--color-accent          /* 메인 액센트 (3% 미만 사용 룰) */
--color-accent-soft     /* 액센트 보조 (배경 tint 등) */
```

**액센트 3% 룰** (memory `feedback_accent_color_3pct_rule.md`): 포인트 컬러 화면 면적 3% 미만. 중립색 베이스 + 레이아웃으로 위계.

## Typography

```
--font-display          /* hero, h1 */
--font-body             /* 본문 */
--font-mono             /* 데이터/숫자 강조 */

--fz-hero               /* clamp(desktop, fluid, mobile) */
--fz-h2
--fz-h3
--fz-body
--fz-sub
--fz-caption

--lh-tight              /* 1.1 - 1.2 hero */
--lh-normal             /* 1.5 본문 */

--ls-tight              /* hero letter-spacing */
```

**clamp range는 desktop / mobile 동시 정의** (cross-cutting).

## Spacing

```
--space-1   /* 4px */
--space-2   /* 8px */
--space-3   /* 12px */
--space-4   /* 16px */
--space-6   /* 24px */
--space-8   /* 32px */
--space-12  /* 48px */
--space-16  /* 64px */
--space-24  /* 96px */
```

## Radius

```
--radius-sm
--radius-md
--radius-lg
--radius-pill
```

## Section

```
--section-pad-y         /* 섹션 위아래 패딩 */
--section-pad-x         /* 섹션 좌우 패딩 (모바일/데스크탑 다름) */
--max-w-content         /* 본문 max-width */
--max-w-narrow          /* 좁은 본문 (hero, CTA) */
```

## Motion (선택)

```
--ease-out
--dur-fast      /* 150ms */
--dur-normal    /* 300ms */
--dur-slow      /* 600ms */
```

---

## 사용 흐름

**토큰화 시점 = 톤 1안 결정 후**. 후보 비교 단계에서 토큰화 X.

1. Phase 2 후보 비교 단계 — *임시 값*으로 결 차이만 보여줌. 토큰화 X.
2. user 컨펌으로 1안 선택 후 → 이 스키마에 최종값 채움.
3. 이후 모든 수정은 토큰만 바꾸면 일관성 유지.

후보 단계에서 토큰화하면 *결 비교* 대신 *세부 값 비교*로 변질됨. 결정 전 토큰 작업 = 낭비.
