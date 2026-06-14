# Obsidian × Claude Code

> **대상:** Obsidian을 처음 쓰는 기획자·디자이너·PM (Lv.2 후속이자 독립 단발)
> **전제:** Claude Code 설치 완료 + 기본 대화 경험. Obsidian은 몰라도 됨(세션 내 설치)
> **총 소요:** 약 82분 (6블록) + 선택 부록 B6·B7 ~25분
> **핵심 메타포:** Obsidian=작업대, Claude=정리하는 동료, Vault=쌓이는 자산

> **이 세션의 범위:** "AI가 읽는 두 번째 뇌"를 세팅·운영하는 데 초점을 둔다. 옵시디언을 손으로 다루는 기본기(노트·링크·그래프·검색·캡처 습관)까지 다루되, **동기화·모바일, 고급 노트법(Zettelkasten 등)은 범위 밖** — [공식 도움말](https://help.obsidian.md/) 참고.

---

## 핵심 요약 — 꼭 할 것 vs 하지 말 것

| 구분 | 항목 | 이유 |
| ---- | ---- | ---- |
| ✅ DO | **원문(클리핑)은 불변으로 두기** | '진실의 원천'. 가공물은 별도 노트로 쌓아 검증 가능하게 |
| ✅ DO | **frontmatter를 일관되게** | AI는 본문 전에 frontmatter로 관련성 판단 → 검색 정확도↑ |
| ✅ DO | **첫 요청은 "보고만 해줘"** | 분석→보고→diff→반영. 되돌리기 어려운 사고 예방 |
| ✅ DO | **vault 구조를 CLAUDE.md에 적기** | AI가 폴더를 추론하지 않고 읽고 시작 |
| ✅ DO | **작은 루프 반복(투입→가공→환원)** | 한 번에 완벽 대신 복리 누적 |
| ✅ DO | **좋은 답변은 노트로 환원** | 채팅에 흘려보내면 사라짐 |
| ❌ DON'T | **민감정보(키·토큰·고객정보) vault에 넣기** | Claude가 읽는 폴더 |
| ❌ DON'T | **vault 전체를 한 번에 수정시키기** | 먼저 분석 보고, 특정 파일만 |
| ❌ DON'T | **`.obsidian/` 폴더 수정** | 앱 설정 손상 위험 |
| ❌ DON'T | **점검 없이 방치** | 끊긴 링크·고아·모순이 쌓임 |
| ❌ DON'T | **폴더를 깊고 세밀하게 나누기** | AI는 폴더 트리를 안 뒤짐. 얕게+frontmatter |
| ❌ DON'T | **로컬 vault를 클라우드 에이전트로 자동화** | 원격은 로컬 접근 불가 → 로컬 cron |

---

## 이 과정을 마치면

- Obsidian Vault가 왜 "AI의 장기기억"인지 설명할 수 있다 (RAG vs 영속 위키)
- Obsidian을 설치하고 직접 노트·링크·그래프뷰·검색을 다룰 수 있다 (손 + Claude 양쪽)
- PARA를 출발점 삼아 내 일에 맞는 Vault 구조를 스스로 설계할 수 있다
- Vault용 CLAUDE.md로 Claude와 안전하게 협업할 수 있다
- Web Clipper로 자료를 투입하고 Claude로 가공·환원하는 루프를 돌릴 수 있다
- 점검·인덱스·로그로 Vault를 지속 가능하게 운영할 수 있다
- (선택) AI 협업을 강화하는 플러그인을 골라 쓸 수 있다
- (선택) Web Clipper 외 다양한 경로로 MD를 수집하고, 나만의 수집 스킬을 만들 수 있다

## 기대 효과

| Block | Before | After |
| ---- | ------ | ----- |
| **0** | 지식이 북마크·메모앱·머릿속에 흩어짐 | "AI가 읽는 DB"라는 관점 + RAG vs 누적 이해 |
| **1~2** | Obsidian 막막, 폴더 정답 찾기 | 설치+첫 노트 + 얕은 구조를 스스로 변형 |
| **3** | 매번 같은 맥락 반복 설명 | CLAUDE.md로 규칙·지도 자동 적용 + 안전 순서 |
| **4~5** | 자료만 쌓고 방치 | 투입→가공→환원 루프 + 점검·로그로 복리 운영 |
| **6**(선택) | 플러그인 뭘 깔지 막막 | AI 협업 강화 기준으로 큐레이션해 선택 |

---

## 사전 준비

| 항목 | 요구사항 |
| ---- | -------- |
| Claude Code | 설치 완료 (IDE 확장 / 데스크톱 앱 / CLI 중 하나) |
| 계정 | Claude Pro, Max, Teams, Enterprise 중 하나 |
| 인터넷 | 필요 |
| Obsidian | **세션 내 설치** (Block 1) — 미리 안 깔아도 됨 |
| Web Clipper | **세션 내 설치** (Block 4) |

---

## 사용 방법

이 폴더(`claude-workshop-obsidian`)를 Claude Code에서 열고:

```text
/session-obsidian
```

또는 자연어로:

```text
세션 시작해줘
```

시작 블록 선택지가 뜨면, 처음이면 Block 0부터 진행하세요.

---

## 커리큘럼

```text
Block 0  →  Block 1  →  Block 2  →  Block 3  →  Block 4  →  Block 5
 개념        설치+기초    구조         연결         투입         지속운영
 ~8분        ~22분        ~13분        ~12분        ~15분        ~12분
 (구축 ────────────────────────────)  (운영 ──────────────────)

 + 선택 부록:  Block 6 (플러그인, ~10분) · Block 7 (나만의 수집 스킬, ~15분)
```

| Block | 주제 | 핵심 한 줄 | 산출물 |
| ---- | ---- | ---------- | ------ |
| **0** | 왜 두 번째 뇌인가 | RAG vs 영속 위키 — 갈수록 똑똑해지는 이유 | (개념) |
| **1** | Obsidian 설치 + 기초 | vault=폴더, note=.md, frontmatter, wikilink, 그래프·검색 | Vault + 손/Claude 노트 + 그래프 확인 |
| **2** | Vault 구조 | 폴더·파일명·frontmatter — PARA에서 내 식으로 변형 | 얕은 폴더 골격 + 파일명 규칙 |
| **3** | Claude Code 연결 | CLAUDE.md = 규칙서 + vault 지도, 안전 순서 | vault용 CLAUDE.md |
| **4** | 운영 ① 투입 루프 | 다양한 입력경로(Web Clipper·pdf2md·wiki2md·meeting-log) → 가공 → 환원 | 클리핑→정리노트 1사이클 |
| **5** | 운영 ② 지속 가능하게 | 점검 · index.md · log.md | 점검 1회 + 로그 1줄 |
| **6** | (선택) 플러그인으로 더 나아가기 | AI 협업 강화 플러그인 큐레이션 | 플러그인 1개 설치 |
| **7** | (선택) 나만의 수집 스킬 만들기 | wiki2md·pdf2md·meeting-log처럼 직접 (Claude 스캐폴딩) | 수집 스킬 1개 |

---

## 추천 플러그인 (Block 6 부록)

플러그인은 필수가 아니다. **"AI가 읽는 DB를 강화하는가"** 기준으로 골라 쓴다.

| 묶음 | 플러그인 | 두 번째 뇌에 왜 |
| ---- | ---- | ---- |
| **자료 투입** | Text Extractor · PDF++ | 이미지·PDF 속 글자도 텍스트화 → Claude가 읽음 |
| **구조·자동화** | Dataview · Templater · *(core) Templates·Daily notes* | frontmatter를 대시보드로 — "정밀 필터"를 눈으로 |
| **검색·탐색** | Omnisearch · *(core) 백링크* | 사람용 빠른 검색(Claude의 grep 보완) |
| **AI 작성** | Smart Composer | Obsidian 내장 AI — 가벼운 편집용, 대량·구조는 Claude Code |
| **취향** | Excalidraw · Google Calendar · Typewriter Mode | 주제와 약결합, 필요하면 |

> Dataview 쿼리 문법이 어렵다면 Claude에게 "이 조건으로 Dataview 쿼리 짜줘"라고 하면 된다.

---

## 진행 방법

### 2-Phase 진행

각 블록은 **2턴**으로 진행됩니다:

| Phase | 내용 | 사용자 액션 |
| ----- | ---- | ---------- |
| **A** | 개념 설명 + 실습 안내 | 직접 실행해보기 |
| **B** | 퀴즈(회상형 + 적용형) | 정답 선택 → 피드백(오답 시 해당 구간 다시 짚고 재시도) → 진도 저장 → 다음 블록 |

실행이 끝나면 "완료" 또는 "다음"이라고 입력하세요.

### 학습 진도 추적

```text
[ ] Block 0: 왜 두 번째 뇌인가 (RAG vs 영속 위키)
[ ] Block 1: Obsidian 설치 + 기초
[ ] Block 2: Vault 구조 (PARA → 변형)
[ ] Block 3: Claude Code 연결 (CLAUDE.md)
[ ] Block 4: 운영 ① 투입 루프 (Web Clipper)
[ ] Block 5: 운영 ② 지속 가능하게 (점검·인덱스·로그)
[ ] Block 6: (선택) 플러그인으로 더 나아가기
[ ] Block 7: (선택) 나만의 수집 스킬 만들기
```

> **팁:** 이 체크리스트를 복사해 Vault(또는 이 폴더)에 `progress.md`로 저장하면, 다음에 이어서 진행할 때 어디까지 했는지 바로 보입니다(`templates/progress-template.md` 그대로 써도 됩니다). 세션은 시작 시 `progress.md`가 있으면 읽고 **"이어서 할까요?"**라고 묻고, 각 블록을 마치면 자동으로 갱신합니다. "이미 아는 블록은 핵심 1분 요약 후 바로 퀴즈로 건너뛰기"도 됩니다. "좋은 건 노트로 환원"하는 이 세션의 원칙과도 같습니다.

---

## 파일 구조

```text
claude-workshop-obsidian/
├── README.md                          ← 이 파일 (자가학습 핸드북)
└── .claude/skills/session-obsidian/
    ├── SKILL.md                       (튜터 라우터)
    ├── references/ (8)                (블록별 EXPLAIN→EXECUTE→QUIZ, B6=플러그인·B7=수집 스킬 부록)
    └── templates/ (8)                 (claude-md·note·clipping·index·log·collector-skill·sample-broken·progress)
```

---

## 문제 해결

| 증상 | 해결 |
| ---- | ---- |
| 스킬이 인식되지 않음 | Claude Code에서 `claude-workshop-obsidian` 폴더를 열었는지 확인 (File → Open Folder) |
| `/session-obsidian`가 안 됨 | `/` 입력 후 자동완성 목록 확인, 또는 "세션 시작해줘" |
| 퀴즈가 Phase A에서 나옴 | "STOP PROTOCOL을 따라줘"라고 리마인드 |
| 블록을 건너뛰고 싶음 | 시작 시 원하는 블록 번호를 선택 |
| Web Clipper 저장이 안 됨 | 확장 설정에서 대상 Vault·폴더가 지정됐는지 확인 |

---

## 만든 사람

**김동일 (Dongil Kim)**

- Email: <hello@dongil.kim>
- LinkedIn: <https://www.linkedin.com/in/hellodongilkim/>
- GitHub: <https://github.com/hello-dongil-kim/>
