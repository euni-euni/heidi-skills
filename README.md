# heidi-skills

Heidi의 개인 Claude Code 스킬 모음. Claude Code marketplace로 publish됨.

## 설치

```bash
# 1. marketplace 등록
/plugin marketplace add euni-euni/heidi-skills

# 2. plugin 설치
/plugin install craft-landing@heidi-skills
```

## 구조

```
heidi-skills/
├── .claude-plugin/
│   └── marketplace.json                 ← marketplace 메타데이터
├── plugins/                             ← marketplace install 영역
│   └── craft-landing/
│       ├── .claude-plugin/
│       │   └── plugin.json              ← plugin 메타데이터
│       └── skills/
│           └── craft-landing/
│               ├── SKILL.md
│               ├── phases.md
│               ├── references-matrix.md
│               ├── tokens-schema.md
│               └── anti-patterns.md
└── notes/                               ← 레포에만 보존, install 제외
    └── craft-landing/
        ├── discussion-log.md
        └── cases/
            ├── ai-study-manager-student.md
            └── edu-ai-os-student.md
```

## 스킬

### craft-landing (`v0.1.0`)

제품/마케팅 랜딩 페이지를 input(define.md, prd.md, 또는 대화)에서 출발해 4-phase로 빚는 프로세스 스킬. 시각 originality는 별개의 `wizard-design:landing-design-create`가 담당하고, 이 스킬은 의사결정 흐름·카피·구조·톤앤매너 도출을 다룬다.

**Phase 1**: 시작 prompt + 첫 draft (originality starting point)
**Phase 2**: 톤앤매너 교정 (외부 리서치 → 4-D 매트릭스 → 후보 → 토큰화)
**Phase 3**: hero + 내러티브 (타겟 일상 언어로 번역)
**Phase 4**: 에셋 (placeholder → 실제 자산)

작업 회고는 `notes/craft-landing/discussion-log.md` + `notes/craft-landing/cases/`.
