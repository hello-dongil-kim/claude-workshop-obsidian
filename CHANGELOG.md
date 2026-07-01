# Changelog

이 워크샵의 주요 변경 이력. 형식은 [Keep a Changelog](https://keepachangelog.com/) 기반. 시리즈 공통 표준은 제작자 내부 문서 `workshop-series-standard`를 따른다.

## [2026-07-01] — 튜터 UX 개선 (설명 압축·단축키 견고화·자동 진행)

### Changed (변경)

- **STOP PROTOCOL Phase A:** EXPLAIN을 각 블록 상단 **🎙️ 설명 대본(≤6줄)** 기준으로 압축 설명하도록 명시. reference 원문 복붙·낭독 금지 → 장황한 설명 해소.
- **STOP PROTOCOL Phase B:** 퀴즈 채점·`progress.md` 갱신 후 **확인 없이 같은 턴에서 다음 블록 자동 진행**. 학습자가 "다음"을 직접 타이핑하던 마찰 제거(선택 부록 Block 6·7·마지막 블록만 1회 확인, "그만/멈춰"로 언제든 정지).
- **단축키 일괄 제거:** 개별 단축키(`Cmd+O`·`Cmd+Shift+F` 등)를 Block 1 표·EXECUTE·설명대본에서 **전부 삭제**. 유일하게 남긴 키 = 명령 팔레트 `Cmd/Ctrl+P`. 나머지 기능은 팔레트에서 이름으로 검색하거나 리본/메뉴로 연다.

### Added (추가)

- 전 8블록 EXPLAIN 상단에 **🎙️ 설명 대본** 콜아웃(낭독용 3~5불릿 요약, 세부는 학습자가 물을 때만).
- SKILL "절대 하지 않을 것"에 **reference 밖 단축키 지어내기 금지** 가드레일.

> 근거: 실제 구동 피드백 3건(장황한 설명 / 무효 단축키 안내 / 퀴즈 후 '다음' 수동 입력). block1 단축키 값 자체는 [공식 문서](https://obsidian.md/help/plugins/search)상 유효했으나, OS·버전·본인 재설정으로 계속 어긋나므로 **개별 키를 아예 안 가르치기로**(팔레트 키 1개만 유지). knowledge 편과 STOP PROTOCOL 동기화.

## [2026-06-29] — B2 통찰 1줄 보강

### Added (추가)

- Block 2: "일관된 frontmatter 표준 = AI가 구조적으로 추출하는 틀(Schema)" 콜아웃 1줄. 기능은 기존에 커버됨 — *왜*(구조적 추출)를 명시. 별도 schema 파일은 의도적으로 만들지 않음(규칙은 CLAUDE.md).

## [2026-06-14] — 9+ 품질 개선

### Added (추가)

- 모든 EXECUTE에 `✅ 이렇게 되면 성공` 성공 기준(P1)
- 각 블록 QUIZ에 적용형(시나리오) 문항 + 오답 이유 해설(P3)
- 진도 영속화·적응형 건너뛰기·오답 remediation 규칙과 `templates/progress-template.md`(P4)
- 버전 의존 정보용 변동 정보 박스(P2, Block 1·6)
- `LICENSE`(All rights reserved, 개인 학습 이용 허용), `.markdownlint.jsonc` 하우스 스타일
- README 제작자 푸터, `progress.md` 진도 저장 안내

### Changed (변경)

- SKILL.md description 트리거를 세션 의도 키워드로 한정(일반어 제거)
- Block 3~7에 전제(prerequisite) 콜아웃 추가
- Block 5 점검 실습(sample-broken-note)을 선택 → 권장 필수 1회로 강화

### Removed (삭제)

- 무출처 주장(통계·일화·외부 인용·사내 문서 참조) 제거
