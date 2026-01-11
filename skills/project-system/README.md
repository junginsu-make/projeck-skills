# Project System

Claude Code를 위한 통합 프로젝트 워크플로우 스킬입니다.

신규 프로젝트를 **기획 → 셋업 → 거버넌스 → 태스크 → TDD 개발**까지 체계적으로 진행할 수 있습니다.

## 주요 기능

- **21개 질문 기반 기획**: 모호한 아이디어를 6개 구조화 문서로 변환
- **AI 에이전트 팀**: Backend, Frontend, Database, Test 전문가 에이전트 자동 생성
- **AGENTS.md 시스템**: 프로젝트별 AI 거버넌스 규칙 자동 생성
- **TDD 워크플로우**: RED → GREEN → REFACTOR 사이클 + Quality Gate
- **다양한 기술 스택 지원**: FastAPI, Express, Rails + React, Next.js, SvelteKit, Remix

---

## 설치 방법

### 전역 설치 (권장)

모든 프로젝트에서 사용할 수 있습니다.

```bash
# 폴더 복사
cp -r project-system ~/.claude/skills/project-system

# 또는 Windows
xcopy /E /I project-system %USERPROFILE%\.claude\skills\project-system
```

### 프로젝트별 설치

특정 프로젝트에서만 사용할 경우:

```bash
cp -r project-system <your-project>/.claude/skills/project-system
```

---

## 사용 방법

Claude Code에서 다음 키워드로 스킬을 발동합니다:

```
"새 프로젝트 시작해줘"
"프로젝트 시작"
"unified project"
```

---

## 5단계 워크플로우

```
Phase 1: 기획 (Planning)
    └→ 21개 질문 → 6개 기획 문서 생성
         - PRD, TRD, User Flow, DB Design, Design System, Coding Convention

Phase 2: 프로젝트 셋업 (Bootstrap)
    └→ 기술 스택 선택 → 스캐폴딩 + .claude/agents/
         - 백엔드/프론트엔드 자동 생성
         - AI 에이전트 팀 설치

Phase 3: AGENTS.md 시스템 (Governance)
    └→ 프로젝트 분석 → 루트 + 하위 AGENTS.md 생성
         - 500라인 제한, 이모지 금지
         - Golden Rules, Context Map

Phase 4: 태스크 생성 (Tasks)
    └→ 기획 문서 + 프로젝트 구조 → TASKS.md
         - TDD 워크플로우 포함
         - Quality Gate 체크리스트

Phase 5: 개발 실행 (Development)
    └→ Git Worktree + TDD + Quality Gate 검증
         - RED → GREEN → REFACTOR
         - 커버리지 ≥80%
```

---

## 폴더 구조

```
project-system/
├── SKILL.md                    # 메인 스킬 정의
│
├── scripts/                    # 실행 스크립트
│   ├── setup_backend.py        # 백엔드 스캐폴딩
│   ├── setup_frontend.py       # 프론트엔드 스캐폴딩
│   ├── setup_docker.py         # Docker Compose 생성
│   ├── setup_mcp.py            # MCP 서버 설정
│   └── git_init.py             # Git 초기화
│
├── templates/                  # 코드 템플릿
│   ├── backend/                # FastAPI, Express, Rails 인증 코드
│   ├── frontend/               # Next.js, React, SvelteKit, Remix 인증 UI
│   └── contracts/              # 타입 정의, API 계약
│
├── hooks/                      # Claude Code 훅 스크립트
│
└── references/                 # Phase별 가이드 문서
    ├── phase1-planning/        # 21개 질문, 6개 템플릿
    ├── phase2-bootstrap/       # 에이전트, 커맨드 템플릿
    ├── phase3-agents-md/       # AGENTS.md 생성 가이드
    ├── phase4-tasks/           # 태스크 생성 규칙
    └── phase5-development/     # TDD 워크플로우, 플랜 템플릿
```

---

## 지원 기술 스택

### 백엔드

| Framework | 언어 | 인증 템플릿 |
|-----------|------|------------|
| FastAPI | Python | O |
| Express | TypeScript | O |
| Rails | Ruby | O |
| Django | Python | - |

### 프론트엔드

| Framework | 특징 | 인증 UI |
|-----------|------|---------|
| React + Vite | React 19, Zustand | O |
| Next.js | App Router | O |
| SvelteKit | Svelte 5 runes | O |
| Remix | Loader/Action | O |

### 데이터베이스

| DB | Docker 템플릿 |
|----|--------------|
| PostgreSQL | postgres |
| PostgreSQL + PGVector | postgres-pgvector |
| MySQL | mysql |
| MongoDB | mongodb |

---

## Quality Gate

모든 Phase 완료 시 검증하는 항목:

- [ ] 빌드 성공
- [ ] 모든 테스트 통과
- [ ] 커버리지 ≥80%
- [ ] 린트 통과
- [ ] 타입 체크 통과
- [ ] 수동 테스트 완료

---

## Development History (개발 히스토리)

프로젝트 개발 진행 상황을 `CLAUDE.md`에 자동 기록합니다:

### 기록 내용

- **프로젝트 상태**: 현재 버전, Phase, 다음 마일스톤
- **Phase 진행 현황**: 시작일, 완료일, 상태
- **업데이트 로그**: 날짜별 변경 사항 (Added/Changed/Fixed)

### 업데이트 시점

| 상황 | 업데이트 내용 |
|------|-------------|
| Phase 완료 | Phase 진행 현황 테이블 |
| 마일스톤 완료 | 버전 + 업데이트 로그 |
| 기능 추가/변경 | 업데이트 로그 |
| 버그 수정 | Fixed 항목 |
| 개발 중단/재개 | 현재 상태 + 다음 작업 |

### 장점

- 프로젝트 재진입 시 즉시 상황 파악
- 개발 타임라인 추적
- AI와 사람 모두 업데이트 가능

---

## 생성되는 프로젝트 구조

스킬 실행 후 생성되는 프로젝트:

```
my-project/
├── .claude/
│   ├── agents/                 # AI 에이전트 팀
│   │   ├── backend-specialist.md
│   │   ├── frontend-specialist.md
│   │   ├── database-specialist.md
│   │   └── test-specialist.md
│   └── commands/
│       └── orchestrate.md      # 오케스트레이터
│
├── AGENTS.md                   # 루트 거버넌스 규칙
├── backend/
│   └── AGENTS.md
├── frontend/
│   └── AGENTS.md
│
├── docs/planning/              # 기획 문서
│   ├── 01-prd.md
│   ├── 02-trd.md
│   ├── 03-user-flow.md
│   ├── 04-database-design.md
│   ├── 05-design-system.md
│   ├── 06-tasks.md
│   └── 07-coding-convention.md
│
├── docker-compose.yml
└── ...
```

---

## 라이선스

MIT License

---

## 관련 링크

- [Claude Code 공식 문서](https://docs.anthropic.com/claude-code)
