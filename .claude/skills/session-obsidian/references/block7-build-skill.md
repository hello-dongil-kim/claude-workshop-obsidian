# Block 7: 나만의 수집 스킬 만들기 (선택)

## EXPLAIN

B4에서 봤듯 vault 입구는 여러 개다. 그중 **내가 자주 쓰는 입구**는 한 줄 명령으로 자동화할 수 있다 — 그게 **수집 스킬**이다.

> 스킬(SKILL.md)이란? 특정 작업을 **자동 트리거**하는 마크다운 설명서. (Lv.2 Session 2에서 깊게 다룸 — 처음이면 그쪽 참고)

### 사례 해부 — 직접 만든 수집 스킬 3개

| 스킬 | 입력 | 변환 | 저장 |
|---|---|---|---|
| **pdf2md** | PDF·PPTX | Vision으로 텍스트+이미지 추출 | vault에 임베드 MD |
| **wiki2md** | Confluence URL | 본문+첨부 변환 | vault에 MD + 첨부 |
| **meeting-log** | 오디오 파일 | 전사 → 회의록 구조화 | vault에 회의록 MD |

**공통 구조 = 입력 → 변환 → frontmatter 붙여 vault 저장.** 수집 스킬은 전부 이 골격이다.

### 핵심 — 직접 코딩하지 않는다

비개발자도 만들 수 있다. **Claude에게 "이런 수집 스킬 만들어줘"라고 시키면** SKILL.md를 짜준다. *AI가 내 지식을 정리할 뿐 아니라, 내 도구까지 만들어준다* — 이 세션의 thesis가 한 단계 올라가는 지점이다.

### 최소 SKILL.md 골격

```markdown
---
name: my-collector
description: (무엇을) 수집해 vault에 MD로 저장. "트리거 키워드" 들어오면 작동.
---
# 언제: ~한 소스를 받으면
# 무엇을: MD로 변환하고 frontmatter(title/type/source/created)를 붙인다
# 어디에: 20_resources/ 에 저장한다
```

`templates/collector-skill-template.md`에 그대로 쓸 수 있는 골격이 있다.

---

## EXECUTE

다음을 직접 실행해보세요:

**Step 1: 내가 자주 넣는 소스 1개 정하기**
- 예: 특정 뉴스레터, 유튜브 자막, 특정 폴더의 캡처 이미지, 즐겨 읽는 블로그

**Step 2: Claude에게 스킬 스캐폴딩 시키기**
```
내 vault에 [내가 정한 소스]를 마크다운으로 수집하는 스킬을 만들어줘.
.claude/skills/ 아래 SKILL.md로, frontmatter(name, description에 트리거 키워드)를 갖추고,
수집 결과는 20_resources/에 frontmatter(title/type/source/created)를 붙여 저장하도록 해줘.
templates/collector-skill-template.md를 참고해.
```

**Step 3: 만든 스킬 한 번 돌려보기**
- 실제 소스 하나로 호출 → vault에 노트가 생기는지 확인
- 안 되면 Claude에게 "이 부분이 안 돼" 보고하고 함께 고친다

---
위 내용을 직접 실행해보세요.
실행이 끝나면 "완료" 또는 "다음"이라고 입력해주세요.

---

## QUIZ

**문제:** 비개발자가 수집 스킬을 만드는 가장 현실적인 방법은?

| 선택지 | 내용 |
|--------|------|
| A | 파이썬을 깊게 배운 뒤 처음부터 직접 코딩한다 |
| B | 남이 만든 스킬을 복사만 하고 손대지 않는다 |
| C | Claude에게 "이런 수집 스킬 만들어줘"라고 시켜 스캐폴딩하고, 안 되는 부분만 함께 고친다 |

**정답:** C — 수집 스킬은 입력→변환→저장이라는 단순 골격이라, Claude에게 스캐폴딩을 맡기고 동작을 확인하며 다듬는 게 가장 빠르다. wiki2md·pdf2md·meeting-log도 그렇게 "필요해서" 만들어진 것이다.
