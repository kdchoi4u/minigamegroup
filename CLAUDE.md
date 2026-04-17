# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 프로젝트 개요

순수 HTML/CSS/JavaScript로 제작된 정적 미니 게임 모음 웹앱. 빌드 도구, 패키지 매니저, 프레임워크 없이 브라우저에서 직접 실행된다.

- **배포 URL**: https://kdchoi4u.github.io/minigamegroup/
- **저장소**: https://github.com/kdchoi4u/minigamegroup

## 파일 구조

```
index.html        — 게임 허브 홈페이지 (게임 선택 카드 목록)
minesweeper.html  — 지뢰찾기
snake.html        — 뱀 게임
2048.html         — 2048 숫자 퍼즐
memory.html       — 카드 매칭
mole.html         — 두더지 잡기
```

각 게임은 독립된 단일 HTML 파일이며, CSS와 JavaScript가 인라인으로 포함된다. 파일 간 공유 코드나 의존성은 없다.

## 개발 방법

별도 빌드 없이 HTML 파일을 브라우저에서 직접 열면 된다.

```bash
# 로컬에서 파일 열기 (예시)
start index.html
```

## Git / 배포 워크플로

- 파일 수정 시 `.claude/settings.json`의 PostToolUse 훅이 자동으로 `git commit` + `git push`를 실행한다.
- push 후 약 1~2분 내에 GitHub Pages에 자동 반영된다.
- 커밋 메시지 형식: `auto: update [파일명]` (훅 자동 생성) / `feat|fix|chore: ...` (수동 커밋)

## 디자인 시스템

모든 페이지가 공유하는 CSS 변수 (각 파일 내 `:root`에 정의):

```css
--dark: #1a1a2e    /* 기본 배경 */
--mid:  #16213e    /* 섹션 배경 */
--deep: #0f3460    /* 보더, 강조 배경 */
--text: #e0e0e0    /* 본문 텍스트 */
--muted: #8899aa   /* 보조 텍스트 */
```

게임별 accent 색상: 지뢰찾기 `#e94560`, 뱀 `#4ade80`, 2048 `#f59e0b`, 카드 `#a78bfa`, 두더지 `#38bdf8`

각 게임 페이지 상단에는 `← 홈으로` 링크(`index.html`)가 포함된 공통 nav 구조가 있다.

## 게임 추가 시 체크리스트

1. `게임명.html` 파일 생성 — 기존 게임 파일의 nav/score-board/btn 구조를 따를 것
2. `index.html`의 `.games-grid`에 게임 카드(`<a href="게임명.html" class="game-card cN">`) 추가
3. accent 색상 클래스 `c1`~`c5` 중 미사용 번호 할당 (현재 c1~c5 모두 사용 중이면 새 클래스 추가)
