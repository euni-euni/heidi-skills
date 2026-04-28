# heidi-skills

Heidi의 개인 Claude Code 스킬 모음. 작업 회고 + 케이스 자료 포함.

## 구조

```
heidi-skills/
├── plugins/                              ← marketplace publish 시 install되는 영역
│   └── craft-landing/
│       └── skills/
│           └── craft-landing/            ← 스킬 본체
│               ├── SKILL.md
│               ├── phases.md
│               ├── references-matrix.md
│               ├── tokens-schema.md
│               └── anti-patterns.md
└── notes/                                ← 레포에만 보존, install 제외
    └── craft-landing/
        ├── discussion-log.md             ← 작업 회고 + 스킬 개선사항
        └── cases/
            └── ai-study-manager-student.md
```

## 스킬

### craft-landing

제품/마케팅 랜딩 페이지를 input(define.md, prd.md, 또는 대화)에서 출발해 단계별로 빚는 프로세스 스킬. 시각 originality는 별개의 `wizard-design:landing-design-create`가 담당하고, 이 스킬은 의사결정 흐름·카피·구조·톤앤매너 도출을 다룬다.

**상태**: 첫 사용 (edu-ai-os 학생 랜딩) Phase 2 미완. 스킬 자체의 결함이 다수 노출되어 *현 상태 사용 불가*. `notes/craft-landing/discussion-log.md` 참조 — 다음 사용 전 보강 필수 사항 정리.

## marketplace publish

현재는 backup 형태로 manifest 없이 푸시. 향후 marketplace publish 결정 시:
- `marketplace.json` (root) 추가
- `plugins/{name}/.claude-plugin/plugin.json` 추가
- 그 시점에 `notes/`는 자동으로 install 제외 (디렉토리 구조상)
