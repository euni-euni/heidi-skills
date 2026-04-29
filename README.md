# heidi-skills

Heidi의 Claude Code 스킬 모음. Claude Code marketplace로 publish.

## 설치

Claude Code 안에서 marketplace 등록 → 원하는 스킬 설치:

```
/plugin marketplace add euni-euni/heidi-skills
/plugin install <skill-name>@heidi-skills
/reload-plugins
```

`<skill-name>`은 아래 표 참조. 각 스킬의 자세한 사용법은 스킬별 README 링크 참조.

## 스킬 목록

| 스킬 | 버전 | 설명 | 가이드 |
|---|---|---|---|
| `craft-landing` | 0.1.0 | 랜딩 페이지를 input(define.md/prd.md/대화)에서 출발해 4-phase 프로세스로 빚는 의사결정·톤앤매너 스킬 | [README](./plugins/craft-landing/README.md) |

## 업데이트 / 제거

```
/plugin update <skill-name>@heidi-skills
/plugin uninstall <skill-name>@heidi-skills
/plugin marketplace remove heidi-skills
```

## 구조

```
heidi-skills/
├── .claude-plugin/
│   └── marketplace.json         ← marketplace 메타데이터
└── plugins/
    └── {skill-name}/
        ├── .claude-plugin/
        │   └── plugin.json      ← plugin 메타데이터
        ├── README.md            ← 스킬 사용 가이드
        └── skills/
            └── {skill-name}/    ← 스킬 본체 (SKILL.md + 보조 파일)
```

## 새 스킬 추가

1. `plugins/{name}/` 디렉토리 + `.claude-plugin/plugin.json` + `README.md` + `skills/{name}/SKILL.md` 생성
2. `.claude-plugin/marketplace.json`의 `plugins` 배열에 항목 추가
3. branch + PR

## 피드백

이슈 / PR / 메시지 환영.
