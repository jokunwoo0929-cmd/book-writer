# 📚 Book Writer — 7인 AI 에이전트 협업 집필 시스템

> 7개의 전문 AI 에이전트가 역할을 분담하여 한국어 책을 기획부터 출판까지 자동으로 집필하는 다중 에이전트 시스템입니다.

---

## 목차

- [프로젝트 개요](#프로젝트-개요)
- [시스템 아키텍처](#시스템-아키텍처)
- [7개 에이전트 역할](#7개-에이전트-역할)
- [3단계 워크플로우](#3단계-워크플로우)
- [핵심 설계 원칙](#핵심-설계-원칙)
- [파일 구조](#파일-구조)
- [실행 방법](#실행-방법)
- [실제 실행 결과](#실제-실행-결과)
- [최종 산출물](#최종-산출물)

---

## 프로젝트 개요

이 시스템은 **Claude Code**의 다중 에이전트(Multi-Agent) 기능을 활용하여 책 한 권을 완성합니다.
중앙 관리자(오케스트레이터)가 7개의 전문 에이전트를 순서대로 호출하고, 각 에이전트는 역할에 맞는 작업만 수행합니다.

### 주요 특징

| 특징 | 설명 |
|---|---|
| **역할 분리** | 7개 에이전트가 기획·조사·집필·검증·검토·편집·출판을 독립 수행 |
| **Lazy Loading** | 에이전트는 호출될 때만 활성화, 다른 에이전트 지침 파일 미참조 |
| **Progressive Disclosure** | 핸드오프 파일로 최소 정보만 전달, 챕터 단위 순차 처리 |
| **Why-First** | 모든 에이전트가 작업 이유(Why)를 산출물 첫머리에 명시 |
| **챕터 단위 호출** | writer·fact-checker는 챕터마다 별도 호출 (일괄 처리 금지) |
| **3분리 출력** | `TOC.md`(목차) → `SUMMARY.md`(요약) → `BOOK.md`(본문) |

---

## 시스템 아키텍처

```
사용자 요청 (주제, 분량, 독자)
        │
        ▼
  오케스트레이터 (Claude Code)
        │
        ├─[1단계]─▶ planner ──────────────────────────────────┐
        │                 └─▶ handoff/planner-to-researcher.md │
        │                                                       │
        ├─[1단계]─▶ researcher ◀──────────────────────────────┘
        │                 └─▶ handoff/researcher-to-writer.md
        │
        ├─[1단계]─▶ writer (챕터 1) ◀── 챕터 단위 별도 호출
        ├─[1단계]─▶ writer (챕터 2)
        ├─[1단계]─▶ writer (챕터 3) ──▶ handoff/writer-to-factchecker.md
        │
        ├─[2단계]─▶ fact-checker (챕터 1) ◀── 챕터 단위 별도 호출
        ├─[2단계]─▶ fact-checker (챕터 2)
        ├─[2단계]─▶ fact-checker (챕터 3) ──▶ handoff/factchecker-to-reviewer.md
        │
        ├─[2단계]─▶ reviewer ──▶ handoff/reviewer-to-editor.md
        │
        ├─[2단계]─▶ editor ──▶ handoff/editor-to-publisher.md
        │
        └─[3단계]─▶ publisher ──▶ output/BOOK.md
                                   output/TOC.md
                                   output/SUMMARY.md
```

---

## 7개 에이전트 역할

### 1. planner
> **역할**: 책의 전체 구조를 설계하고 작업 계획을 수립한다.

- 주제·독자층·목적을 정의하고 전체 목차를 작성
- 챕터별 핵심 메시지와 분량 목표를 결정
- `workflows/handoff/planner-to-researcher.md`에 조사 요청 항목 전달
- **도구**: Read, Write, Edit
- **출력**: `output/BOOK.md`(목차), `handoff/planner-to-researcher.md`

### 2. researcher
> **역할**: 챕터별 자료를 수집하고 writer가 활용할 수 있는 형태로 정리한다.

- `handoff/planner-to-researcher.md`를 읽어 조사 항목 확인
- 공신력 있는 출처 우선, 최소 2개 출처 교차 확인
- 불확실 항목은 `[미확인]` 태그로 명시
- **도구**: Read, Write, WebSearch, WebFetch
- **출력**: `workflows/research-notes.md`, `handoff/researcher-to-writer.md`

### 3. writer
> **역할**: 조사 자료를 바탕으로 챕터별 초고를 작성한다. 원고를 새로 생성하는 **유일한 에이전트**.

- **챕터마다 별도 호출** — 단일 호출로 전체를 작성하지 않음
- `handoff/researcher-to-writer.md`에서 해당 챕터 핵심 정보만 참조
- 각 챕터 도입부에 Why 문장 필수 포함
- 불확실 내용은 `[검증 필요: ...]` 태그로 표시
- **도구**: Read, Write, Edit
- **출력**: `output/BOOK.md`(챕터별 추가), 마지막 챕터 후 `handoff/writer-to-factchecker.md`

### 4. fact-checker
> **역할**: 초고의 사실 관계를 외부 출처와 교차 검증하고 오류를 표시한다. 원고 직접 수정 불가.

- **챕터마다 별도 호출** — 단일 호출로 전체를 검증하지 않음
- 검증 결과를 `[확인됨]` / `[수정 필요]` / `[미확인]` 3등급으로 분류
- **도구**: Read, Write, WebSearch, WebFetch
- **출력**: `workflows/fact-check-report.md`, 마지막 챕터 후 `handoff/factchecker-to-reviewer.md`

### 5. reviewer
> **역할**: 초고 전체를 독자 관점에서 검토하고 의견서를 작성한다. 원고 직접 수정 불가.

- `handoff/factchecker-to-reviewer.md`로 우선 검토 항목 파악
- 흐름·논리·문체·가독성·구조 5개 항목 평가
- **도구**: Read, Write (Edit 없음 — 의도적 권한 제한)
- **출력**: `workflows/review-report.md`, `handoff/reviewer-to-editor.md`

### 6. editor
> **역할**: reviewer와 fact-checker의 의견을 원고에 반영하여 수정한다.

- `handoff/reviewer-to-editor.md`에서 필수 처리·권고·유지 항목 확인
- reviewer가 유지 권고한 항목은 수정하지 않음
- 챕터 전체 재작성 수준이면 writer에게 위임
- **도구**: Read, Write, Edit
- **출력**: `output/BOOK.md`(수정), `workflows/edit-log.md`, `handoff/editor-to-publisher.md`

### 7. publisher
> **역할**: 편집 완료 원고를 출판 규격에 맞게 정리하고 최종 산출물 3개를 생성한다. 내용 수정 불가.

- `handoff/editor-to-publisher.md`로 포맷 주의 사항 파악
- 메타데이터 헤더·목차·앵커 링크·챕터 번호 통일
- **도구**: Read, Write, Bash (인코딩 확인·글자 수 집계용)
- **출력**: `output/BOOK.md`(최종), `output/TOC.md`(신규), `output/SUMMARY.md`(신규)

---

## 3단계 워크플로우

### 1단계: 기획 ~ 초고 작성 (`workflows/01-writing.md`)

```
STEP 1  planner      목차 + 챕터별 핵심 메시지 + 조사 요청 항목 확정
           │
           └─▶ handoff/planner-to-researcher.md

STEP 2  researcher   챕터별 자료 조사 + 출처 명시
           │
           └─▶ handoff/researcher-to-writer.md

STEP 3  writer × N   챕터 하나씩 초고 작성 (챕터 수만큼 별도 호출)
           │
           └─▶ handoff/writer-to-factchecker.md (마지막 챕터 완료 후)
```

### 2단계: 검토 ~ 편집 (`workflows/02-review.md`)

```
STEP 4  fact-checker × N   챕터별 사실 검증 (챕터 수만큼 별도 호출)
           │
           └─▶ handoff/factchecker-to-reviewer.md (마지막 챕터 완료 후)

STEP 5  reviewer       전체 흐름·논리·문체 검토 의견서 작성
           │
           └─▶ handoff/reviewer-to-editor.md

STEP 6  editor         검증·검토 의견 반영, 원고 수정
           │
           └─▶ handoff/editor-to-publisher.md
```

### 3단계: 최종 출판 (`workflows/03-finalize.md`)

```
STEP 7  publisher      포맷 정리 + TOC.md + SUMMARY.md 생성
           │
           └─▶ output/BOOK.md  (최종본)
               output/TOC.md   (목차 독립 파일)
               output/SUMMARY.md (챕터별 요약)
```

### 롤백 절차

| 발견된 문제 | 롤백 대상 | 처리 |
|---|---|---|
| 사실 오류 | fact-checker → editor | 재검증 후 재편집 |
| 논리·문체 문제 | reviewer → editor | 추가 검토 후 재편집 |
| 조사 자료 부족 | researcher → writer → editor | 보완 조사 후 챕터 재작성 |
| 목차 구조 문제 | planner → 이후 전 단계 | 목차 수정 후 전체 재작업 |

---

## 핵심 설계 원칙

### Lazy Loading (지연 로딩)
에이전트는 호출될 때만 활성화됩니다. 오케스트레이터가 명시적으로 호출하기 전까지 에이전트는 대기 상태이며, 자신의 지침 파일(`.claude/agents/<이름>.md`) 외의 다른 에이전트 파일을 읽지 않습니다.

```
❌ 나쁜 예: 오케스트레이터가 이전 결과물 전체를 프롬프트에 삽입
✅ 좋은 예: 오케스트레이터가 "handoff 파일 경로"만 전달, 에이전트가 직접 파일 읽기
```

### Progressive Disclosure (단계적 정보 공개)
각 에이전트는 다음 에이전트에게 **최소 필요 정보만** 전달합니다. 전체 조사 노트 대신 핵심 수치·비유·주의 사항만, 전체 검증 보고서 대신 필수 수정 항목만 핸드오프 파일에 기록합니다.

```
독자용 정보 공개 순서:
output/TOC.md (목차) → output/SUMMARY.md (챕터별 요약) → output/BOOK.md (본문)
```

### Why-First (이유 우선)
오케스트레이터는 에이전트에게 지시할 때 이유(Why)를 먼저 설명합니다. 각 에이전트도 산출물 첫머리에 작업 목적을 한 줄로 명시합니다.

```
예: "독자의 신뢰를 유지하기 위해(Why) 수치와 인용의 정확성을
     출처와 대조 확인한다(What)."  — fact-checker 보고서 첫머리
```

---

## 파일 구조

```
book-writer/
├── README.md                       # 이 파일
├── CLAUDE.md                       # 공통 지침 (오케스트레이터 규칙 포함)
│
├── .claude/
│   └── agents/                     # 에이전트별 개별 지침
│       ├── planner.md
│       ├── researcher.md
│       ├── writer.md
│       ├── fact-checker.md
│       ├── reviewer.md
│       ├── editor.md
│       └── publisher.md
│
├── workflows/                      # 단계별 절차 및 작업 기록
│   ├── 01-writing.md               # 1단계 절차 + 기록 (planner·researcher·writer)
│   ├── 02-review.md                # 2단계 절차 + 기록 (fact-checker·reviewer·editor)
│   ├── 03-finalize.md              # 3단계 절차 + 기록 (publisher)
│   ├── research-notes.md           # researcher 상세 조사 노트
│   ├── fact-check-report.md        # fact-checker 상세 검증 보고서
│   ├── review-report.md            # reviewer 검토 의견서
│   ├── edit-log.md                 # editor 수정 내역 로그
│   ├── final-check.md              # publisher 최종 점검 결과
│   └── handoff/                    # 에이전트 간 인수인계 파일 (최소 정보)
│       ├── planner-to-researcher.md
│       ├── researcher-to-writer.md
│       ├── writer-to-factchecker.md
│       ├── factchecker-to-reviewer.md
│       ├── reviewer-to-editor.md
│       └── editor-to-publisher.md
│
└── output/                         # 최종 산출물
    ├── BOOK.md                     # 최종 본문 (version 1.0.0, status: final)
    ├── TOC.md                      # 목차 독립 파일 (앵커 링크 포함)
    └── SUMMARY.md                  # 챕터별 1~2문장 요약
```

---

## 실행 방법

### 사전 요구 사항

- [Claude Code](https://claude.ai/code) CLI 설치
- Claude API 키 설정 (`ANTHROPIC_API_KEY` 환경 변수)

### 기본 실행 순서

Claude Code에서 오케스트레이터 역할로 다음 순서로 에이전트를 호출합니다.

```
# 1단계: 기획 ~ 초고 작성
1. planner  호출 → 주제·분량·독자 전달
2. researcher 호출 → handoff/planner-to-researcher.md 읽도록 지시
3. writer 호출 (챕터 1) → handoff/researcher-to-writer.md 읽도록 지시
4. writer 호출 (챕터 2) → 동일
5. writer 호출 (챕터 N) → 동일 + 마지막 챕터이면 handoff 출력 지시

# 2단계: 검토 ~ 편집
6. fact-checker 호출 (챕터 1) → handoff/writer-to-factchecker.md 읽도록 지시
7. fact-checker 호출 (챕터 N) → 동일 + 마지막 챕터이면 handoff 출력 지시
8. reviewer 호출 → handoff/factchecker-to-reviewer.md 읽도록 지시
9. editor 호출 → handoff/reviewer-to-editor.md 읽도록 지시

# 3단계: 출판
10. publisher 호출 → handoff/editor-to-publisher.md 읽도록 지시
```

### 오케스트레이터 프롬프트 원칙

```
❌ 금지: 이전 에이전트의 결과물 내용을 프롬프트에 직접 삽입
✅ 권장: 읽어야 할 파일 경로만 지정, 에이전트가 직접 파일 읽기

예시:
"workflows/handoff/planner-to-researcher.md를 읽어 조사 항목을 확인하고
 workflows/research-notes.md에 챕터별 조사 결과를 정리하세요."
```

### 새 주제로 실행하기

1. `output/BOOK.md` 기존 내용은 planner 호출 시 덮어씌워집니다.
2. `workflows/handoff/` 파일들은 각 에이전트가 실행 시 자동으로 갱신합니다.
3. `workflows/*.md`의 작업 기록은 누적 추가됩니다 (삭제하지 않아도 됩니다).

---

## 실제 실행 결과

### 테스트 실행 개요

- **주제**: 스위칭 전원공급장치(SMPS)의 기본 작동 원리
- **독자**: 전자공학 입문 대학교 1~2학년생
- **챕터 수**: 3챕터 (소제목 6개)
- **목표 분량**: 약 1,500자

### 에이전트별 실행 결과

| STEP | 에이전트 | 주요 결과 |
|---|---|---|
| 1 | planner | 3챕터 목차 확정: AC/DC 개념·LPS→SMPS, 스위칭·PWM·핵심 부품, 응용·EMI·안전 인증 |
| 2 | researcher | 11개 조사 항목 완료, `[미확인]` 항목 18% (스위칭 주파수 상한·LPS 효율 하한) |
| 3×3 | writer | 챕터별 3회 독립 호출, 파도/강물·선풍기·기어변속·수문·저수지 비유 활용 |
| 4×3 | fact-checker | 17건 검증, 오류 0건, `[검증 필요]` 태그 1건 발견 (CE 마크 세부 절차) |
| 5 | reviewer | 필수 수정 3건, 권고 수정 5건, 유지 권고 6건 |
| 6 | editor | 필수 3건 + 권고 4건 반영, `[검증 필요]` 태그 전체 제거 |
| 7 | publisher | 앵커 링크·메타데이터 정리, `TOC.md`·`SUMMARY.md` 신규 생성 |

### 에이전트 간 품질 개선 이력

| 발견 위치 | 문제 | 수정 에이전트 |
|---|---|---|
| fact-checker | `[검증 필요]` 태그 잔존 (CE 마크 절차) | editor |
| fact-checker | 다이오드 항목에 `researcher 정리 자료` 내부 출처 — 독자 검증 불가 | editor |
| reviewer | 소제목 의문문 통일 미반영 | editor |
| reviewer | 챕터 2→3 연결 브리지 문장 누락 | editor |
| publisher | `version: editing-complete` → `version: final` 메타데이터 갱신 | publisher |

---

## 최종 산출물

테스트 실행 후 생성된 파일들입니다.

| 파일 | 설명 |
|---|---|
| [`output/BOOK.md`](output/BOOK.md) | 최종 본문 (version 1.0.0, status: final) |
| [`output/TOC.md`](output/TOC.md) | 목차 독립 파일 (앵커 링크 포함) |
| [`output/SUMMARY.md`](output/SUMMARY.md) | 챕터별 1~2문장 요약 |

---

## 라이선스

이 프로젝트의 코드·지침 파일은 MIT License를 따릅니다.
`output/` 디렉터리의 콘텐츠(집필 결과물)는 별도 저작권이 적용될 수 있습니다.

---

*이 시스템은 [Claude Code](https://claude.ai/code)의 다중 에이전트 기능으로 구동됩니다.*
