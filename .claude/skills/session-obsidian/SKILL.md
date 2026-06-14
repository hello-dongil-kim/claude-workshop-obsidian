---
name: session-obsidian
description: |
  Obsidian × Claude Code로 두 번째 뇌(개인 지식 창고) 만들기 실습 세션. "두 번째 뇌 만들기", "옵시디언 세션", "Obsidian 워크샵", "세션 옵시디언", "session-obsidian", "옵시디언 두 번째 뇌" 키워드에 트리거.
  Obsidian 완전 초짜도 따라오는 단발 세션. Vault 구축(B0~B3) + 운영(B4~B5) + 선택 부록(B6 플러그인, B7 나만의 수집 스킬).
---

# 세션. 두 번째 뇌 만들기 — Obsidian × Claude Code

> **난이도:** ★★☆☆☆ | **소요:** ~82분 (부록 포함 ~107분) | **블록:** 6개 + 부록 2개
> **대상:** Obsidian을 처음 쓰는 기획자·디자이너·PM (Lv.2 후속이자 독립 단발)
> **전제:** Claude Code 설치 완료 + 기본 대화 경험. **Obsidian은 몰라도 됨**(세션 내 설치)

## 진도 영속화 + 적응형 (세션 시작 시 적용)

이 세션은 Claude Code에서 구동되어 파일을 직접 읽고 쓸 수 있다. 다음 규칙으로 진도를 저장하고 학습자 수준에 맞춘다.

- **ⓐ 이어가기:** 세션 시작 시 vault(또는 이 폴더)에 `progress.md`가 있으면 먼저 읽고, "지난번 Block N까지 하셨네요. 이어서 진행할까요?"라고 제안한다. 없으면 평소대로 시작.
- **ⓑ 진도 저장:** 각 블록의 QUIZ(Phase B)를 마칠 때마다 `progress.md`를 갱신한다(없으면 생성). 형식은 `templates/progress-template.md` 참고 — 완료한 블록에 `[x]`, 날짜·퀴즈 결과를 한 줄 남긴다.
- **ⓒ 적응형 건너뛰기:** 학습자가 "이 블록은 이미 안다"고 하면, EXPLAIN 전체 대신 **핵심 1분 요약**만 제시하고 바로 QUIZ로 넘어간다. 퀴즈를 맞히면 다음 블록으로, 틀리면 그 구간만 짚어준다. 시작 시 이 옵션을 한 번 안내한다.

## 용어 정리

| 용어 | 설명 |
|------|------|
| **Vault** | Obsidian의 보관소 = 그냥 폴더. 노트는 그 안의 마크다운(.md) 파일 |
| **frontmatter** | 노트 최상단 `---` 사이의 메타데이터(YAML). 사람도 AI도 읽는다 |
| **wikilink** | `[[노트이름]]` 형식의 노트 간 연결. 지식 그래프를 만든다 |
| **CLAUDE.md** | 매 세션 자동으로 읽히는 Vault 작업 규칙서 |
| **RAG** | 질문마다 원문에서 조각을 재추출하는 방식 — 지식이 누적되지 않음 |
| **영속 위키** | 한 번 정리한 지식을 계속 갱신·축적 — 쓸수록 똑똑해짐 |

---

## STOP PROTOCOL — 절대 위반 금지

각 블록은 반드시 **2턴**에 걸쳐 진행한다.

### Phase A (첫 번째 턴)
1. references 파일의 **EXPLAIN** 섹션을 읽고 설명
2. **EXECUTE** 섹션을 읽고 "직접 실행해보세요" 안내
3. **반드시 STOP** — 퀴즈 내지 않음, 도구 호출 금지

### Phase B (두 번째 턴)
1. **QUIZ** 섹션을 읽고 AskUserQuestion으로 퀴즈 출제
2. 정답/오답 피드백
3. **퀴즈 오답 시 remediation:** 해당 EXPLAIN 구간을 다시 짚어주고(핵심만 1~2줄) 재시도를 유도한다. 두 번째도 틀리면 정답·해설을 보여주고 넘어간다.
4. `progress.md` 갱신(완료 블록 체크 + 퀴즈 결과 한 줄)
5. 다음 블록 진행 여부 확인

### 절대 하지 않을 것
- Phase A에서 AskUserQuestion 호출
- Phase A에서 퀴즈 내기
- "실행해봤나요?" 질문
- 한 턴에 EXPLAIN + QUIZ
- **사용자의 실제 개인 데이터(본인 vault 폴더 구조·실명·소속 등)를 예시로 끌어오기** — reference의 일반 예시만 사용하고, "당신은 이미 ~를 쓰고 있죠" 식 개인화 멘트를 덧붙이지 않는다

### Phase A 종료 시 필수 문구
```
---
위 내용을 직접 실행해보세요.
실행이 끝나면 "완료" 또는 "다음"이라고 입력해주세요.
```

---

## 시작

AskUserQuestion으로 시작 블록을 선택하게 한다:

| Block | 주제 | 내용 | 시간 |
|-------|------|------|------|
| 0 | 개념 | 왜 두 번째 뇌인가 — RAG vs 영속 위키 + 메타포 | ~8분 |
| 1 | 구축 | Obsidian 설치 + 기초(md·frontmatter·wikilink·그래프·검색) | ~22분 |
| 2 | 구축 | Vault 구조 — PARA에서 더 나아가기(파일명 포함) | ~13분 |
| 3 | 연결 | Claude Code 연결 = Vault 규칙서(CLAUDE.md) | ~12분 |
| 4 | 운영 | 투입 루프 — Web Clipper로 지식 쌓기 | ~15분 |
| 5 | 운영 | 지속 가능하게 — 점검·인덱스·로그 | ~12분 |
| 6 | 부록 | (선택) 플러그인으로 더 나아가기 | ~10분 |
| 7 | 부록 | (선택) 나만의 수집 스킬 만들기 | ~15분 |

처음이면 Block 0부터 순서대로 진행을 추천한다. Block 6·7은 선택 부록이다.

> **중간 블록부터 시작한다면:** Block 3 이후는 앞 블록의 산출물(Vault·CLAUDE.md 등)을 전제로 한다. 각 블록 reference 상단의 **전제**를 먼저 확인하라.

---

## Block 0: 개념

@references/block0-concept.md 파일의 EXPLAIN → EXECUTE → QUIZ 순서로 진행.

## Block 1: Obsidian 설치 + 기초

@references/block1-obsidian-basics.md 파일의 EXPLAIN → EXECUTE → QUIZ 순서로 진행.

## Block 2: Vault 구조

@references/block2-vault-structure.md 파일의 EXPLAIN → EXECUTE → QUIZ 순서로 진행.

## Block 3: Claude Code 연결

@references/block3-claude-connect.md 파일의 EXPLAIN → EXECUTE → QUIZ 순서로 진행.

## Block 4: 운영 ① 투입 루프

@references/block4-operate-ingest.md 파일의 EXPLAIN → EXECUTE → QUIZ 순서로 진행.

## Block 5: 운영 ② 지속 가능하게

@references/block5-operate-sustain.md 파일의 EXPLAIN → EXECUTE → QUIZ 순서로 진행.

## Block 6: 플러그인으로 더 나아가기 (선택)

@references/block6-plugins.md 파일의 EXPLAIN → EXECUTE → QUIZ 순서로 진행.

## Block 7: 나만의 수집 스킬 만들기 (선택)

@references/block7-build-skill.md 파일의 EXPLAIN → EXECUTE → QUIZ 순서로 진행.
