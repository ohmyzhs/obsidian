---
title: Hermes WebUI-only Install + Obsidian Power Workflow Setup
slug: hermes-webui-install-and-obsidian-power-workflow
status: draft
visibility: public-ready
created: 2026-04-24
updated: 2026-04-24
tags:
  - hermes
  - webui
  - obsidian
  - telegram
  - workflow
summary: Hermes Agent를 이미 쓰고 있는 환경에서 WebUI를 점검하고, Telegram 연결을 복구하고, Obsidian Power Workflow까지 이어 붙인 과정을 공개용 노트 초안으로 정리했다.
share_url:
telegram_handoff: true
public_notes:
  - 민감한 토큰/개인 비밀값은 제외
  - 로컬 경로와 내부 세션 정보는 공개본에서 제거
---

# Hermes WebUI-only Install + Obsidian Power Workflow Setup

## 한줄 요약
Hermes Agent를 이미 사용 중인 환경에서 WebUI 실행 상태를 점검하고, Telegram 연결 문제를 복구한 뒤, Obsidian note → posting → ShareNote → Telegram handoff 흐름까지 이어지는 실사용형 작업 루프를 정리했다.

## 요약
이번 세션에서는 단순히 WebUI를 띄우는 데서 끝내지 않고, 실제 사용자가 다음 작업으로 자연스럽게 넘어갈 수 있는 환경을 만드는 데 집중했다.

핵심은 세 가지였다.
- Hermes for Web이 `localhost:8788` 기준으로 정상 작동하는지 확인
- Telegram bot이 실제로 응답 가능한 상태인지 복구
- Obsidian을 중심으로 note 작성, posting 초안, 향후 ShareNote 공개, Telegram handoff까지 이어지는 흐름을 준비

그 결과, WebUI와 Telegram은 현재 바로 사용 가능한 상태가 되었고, Obsidian Power Workflow도 실제 파일·템플릿·스크립트 기준으로 재사용 가능한 형태로 정리되었다. 아직 ShareNote는 설치되지 않았지만, 공개 링크를 나중에 붙일 수 있도록 frontmatter와 handoff 구조는 미리 준비해두었다.

## 이번에 정리된 핵심 포인트

### 1. WebUI는 단순 채팅창이 아니라 워크플로우 콘솔에 가깝다
현재 구성에서 WebUI는 다음 역할을 한다.
- 채팅 인터페이스
- Setup Packs 실행 진입점
- Artifact 생성/관리
- Workspace 파일 기반 작업
- note / posting / research 흐름의 출발점

즉, “AI와 대화하는 화면”보다 “작업 루프를 조립하는 운영 화면”에 더 가깝다.

### 2. Telegram 문제는 설정이 아니라 연결 디테일에서 막히는 경우가 많다
이번 세션에서 Telegram이 처음에는 반응하지 않았던 이유는 크게 두 가지였다.
- `python-telegram-bot` 의존성이 빠져 있었음
- 허용 사용자 설정이 username 기반(`@...`)이라 실제 Telegram user id 인증과 맞지 않았음

이 문제를 정리한 뒤에는 실제 Telegram DM으로 테스트 메시지를 성공적으로 보낼 수 있었다.

### 3. Obsidian Power Workflow는 “글 쓰기”보다 “이어쓰기”를 쉽게 만든다
이번에 만든 흐름의 핵심은 다음이다.
1. Obsidian에 아이디어를 seed note로 저장
2. 그 노트를 posting draft로 확장
3. 나중에 ShareNote 링크를 붙일 수 있게 구조를 미리 준비
4. Telegram으로 다음 액션을 handoff

이 방식의 장점은 작업이 한 번에 끝나지 않아도 흐름이 끊기지 않는다는 점이다.

## 현재 준비된 환경

### WebUI / Hermes
- Hermes WebUI health check 정상
- Setup Packs UI 노출 확인
- Workspace / Artifact / Setup Pack 흐름 점검 완료

### Telegram
- Hermes Telegram bot 연결 정상
- 허용 사용자 설정을 실제 Telegram user id 기준으로 정리
- 테스트 메시지 전송 성공
- Telegram continuation 가능

### Obsidian
- 기본 vault 준비 완료
- Obsidian 앱 설치 완료
- note / posting / handoff용 템플릿 생성 완료
- Power workflow helper script 생성 완료

### ShareNote
- 아직 플러그인 미설치
- 공개 링크 생성은 추후 연결 예정
- 다만 `share_url` 필드를 frontmatter에 미리 넣어두어 나중에 자연스럽게 이어붙일 수 있게 해둠

## 공개용으로 공유할 만한 구조

### A. 문제 인식
기존 Hermes 사용자는 “설치는 되어 있는데 실제 활용 루프가 이어지지 않는 상태”에 머무르는 경우가 많다.

예를 들면:
- WebUI는 떠 있지만 다음에 뭘 해야 할지 모름
- Telegram bot은 있으나 응답이 안 옴
- Obsidian은 쓰고 싶지만 note 이후 흐름이 끊김
- 공유 가능한 결과물로 발전시키는 루프가 없음

### B. 이번 세션의 해결 방식
이번에는 기능 하나씩이 아니라 흐름 전체를 기준으로 정리했다.
- WebUI 점검
- Telegram 복구
- Obsidian note 템플릿화
- posting draft 확장 구조화
- ShareNote를 나중에 붙일 수 있는 공개용 필드 확보
- Telegram handoff까지 연결

### C. 결과
지금은 다음 루프가 가능하다.
- WebUI에서 작업 시작
- Obsidian에 note 저장
- posting draft 생성
- Telegram으로 다음 액션 전달
- 나중에 ShareNote URL 추가 후 공개 공유

## 실사용 워크플로우

### 1) note 작성
- 위치: `01-Inbox/`
- 템플릿: `00-System/Templates/Power Note Template.md`
- 목적: 아이디어, 출처, 다음 액션을 빠르게 기록

### 2) posting 초안 확장
- 위치: `02-Projects/Posting/`
- 템플릿: `00-System/Templates/Posting Draft Template.md`
- 목적: note를 게시 가능한 구조로 확장

### 3) ShareNote 연결
- 현재는 수동 보류
- 나중에 공개 링크를 만들면 frontmatter의 `share_url:`에 추가

### 4) Telegram handoff
- 템플릿: `00-System/Templates/Telegram Handoff Template.md`
- 목적: 저장 경로, Obsidian URI, 다음 액션을 Telegram으로 넘겨서 작업 연속성 확보

## 공개용 핵심 메시지 후보
- Hermes는 “대화형 AI”보다 “작업 루프를 이어주는 개인 운영 환경”에 가깝다.
- WebUI, Telegram, Obsidian이 이어지면 생각보다 빠르게 개인용 생산 파이프라인이 된다.
- 중요한 것은 기능 수가 아니라 handoff가 자연스럽게 이어지는 구조다.

## 공유용 문안 뼈대

### 제목 후보
- Hermes WebUI를 그냥 띄우는 데서 끝내지 않고, Obsidian과 Telegram까지 이어 붙인 방법
- Hermes Agent 사용자용 WebUI 실전 세팅: Telegram 복구부터 Obsidian Power Workflow까지
- Hermes WebUI + Obsidian + Telegram으로 개인 작업 루프 만들기

### 소개 문단 후보
Hermes Agent를 이미 쓰고 있는 사람이라면, 다음 단계는 단순 설치가 아니라 “작업이 실제로 이어지는 흐름”을 만드는 일이다. 이번에는 WebUI를 점검하고, Telegram bot 연결을 복구하고, Obsidian note에서 posting draft와 향후 ShareNote 공개까지 이어지는 실사용형 루프를 정리해봤다.

## 다음에 보강하면 좋은 것
- [ ] ShareNote 플러그인 설치 및 공개 링크 생성 검증
- [ ] Advanced URI 플로우 확인
- [ ] 이 초안을 실제 Blogger draft로 보내는 publishing adapter 연결
- [ ] `gpt-image-2.0` 기반 인포그래픽 생성 및 본문 포함 흐름 추가
- [ ] Telegram handoff 메시지를 더 짧고 읽기 쉽게 다듬기

## 연결 노트
- [[00-System/Workflows/Obsidian Power Workflow Guide]]
- [[01-Inbox/Power Workflow Demo Note]]
- [[02-Projects/Posting/Power Workflow Demo Posting]]
- [[00-Start Here]]
