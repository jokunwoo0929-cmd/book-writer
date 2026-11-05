# Skills 폴더 구성

## 구조

```
.claude/skills/
├── skill.md                   # 현재 파일 — 폴더 구성 안내
└── workflows/
    ├── 01-writing.md          # 기획~초고 작성 절차 및 기록
    ├── 02-review.md           # 검토~편집 절차 및 기록
    ├── 03-finalize.md         # 최종 출판 절차 및 기록
    ├── edit-log.md            # 편집 이력
    ├── fact-check-report.md   # 팩트체크 보고서
    ├── final-check.md         # 최종 점검 기록
    ├── research-notes.md      # 조사 메모
    ├── review-report.md       # 검토 보고서
    └── handoff/               # 에이전트 간 인수인계 파일
        ├── planner-to-researcher.md
        ├── researcher-to-writer.md
        ├── writer-to-factchecker.md
        ├── factchecker-to-reviewer.md
        ├── reviewer-to-editor.md
        └── editor-to-publisher.md
```

## 파일 설명

### workflows/

| 파일 | 용도 |
|------|------|
| `01-writing.md` | 기획(planner) → 조사(researcher) → 초고(writer) 단계 절차 및 기록 |
| `02-review.md` | 팩트체크(fact-checker) → 검토(reviewer) → 편집(editor) 단계 절차 및 기록 |
| `03-finalize.md` | 출판(publisher) 단계 절차 및 기록 |
| `edit-log.md` | editor가 수행한 수정 이력 |
| `fact-check-report.md` | fact-checker의 사실 검증 결과 보고서 |
| `final-check.md` | publisher의 최종 점검 체크리스트 |
| `research-notes.md` | researcher가 수집한 조사 자료 메모 |
| `review-report.md` | reviewer의 원고 검토 의견서 |

### workflows/handoff/

에이전트 간 작업을 넘길 때 사용하는 인수인계 파일입니다.
전체 산출물이 아닌 **다음 에이전트가 작업에 필요한 최소 정보만** 포함합니다.

| 파일 | 전달 방향 |
|------|-----------|
| `planner-to-researcher.md` | planner → researcher |
| `researcher-to-writer.md` | researcher → writer |
| `writer-to-factchecker.md` | writer → fact-checker |
| `factchecker-to-reviewer.md` | fact-checker → reviewer |
| `reviewer-to-editor.md` | reviewer → editor |
| `editor-to-publisher.md` | editor → publisher |
