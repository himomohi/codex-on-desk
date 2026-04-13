<p align="center">
  <img src="assets/tray-icon.png" width="128" alt="Clawd">
</p>
<h1 align="center">Clawd on Desk</h1>
<p align="center">
  <a href="README.md">English</a>
  ·
  <a href="README.zh-CN.md">中文版</a>
</p>

AI 코딩 에이전트의 세션 상태를 실시간으로 반응하는 데스크톱 펫입니다. Clawd는 화면 위에서 프롬프트를 입력하면 생각하고, 도구가 실행되면 타이핑하고, 서브에이전트가 작업하면 저글링하며, 권한 요청이 오면 카드로 보여주고, 작업이 끝나면 기뻐하고, 자리를 비우면 잠듭니다. 기본 테마는 **Clawd**(픽셀 크랩)와 **Calico**(삼색 고양이) 2종이며, 커스텀 테마도 완전히 지원합니다.

> Windows 11, macOS, Ubuntu/Linux 지원. Node.js 필요. **Claude Code**, **Codex CLI**, **Copilot CLI**, **Gemini CLI**, **Cursor Agent**, **Kiro CLI**, **opencode**와 동작합니다.

## 주요 기능

### 멀티 에이전트 지원
- **Claude Code** — command hooks + HTTP permission hooks 완전 지원
- **Codex CLI** — `~/.codex/sessions/` JSONL 로그 자동 폴링(추가 설정 불필요)
- **Copilot CLI** — `~/.copilot/hooks/hooks.json` 기반 command hooks
- **Gemini CLI** — `~/.gemini/settings.json` hooks 자동 등록(또는 `npm run install:gemini-hooks`)
- **Cursor Agent** — `~/.cursor/hooks.json` hooks 자동 등록(또는 `npm run install:cursor-hooks`)
- **Kiro CLI** — `~/.kiro/agents/`에 hooks 주입 + `clawd` 에이전트 자동 생성/동기화
- **opencode** — `~/.config/opencode/opencode.json` plugin 연동, 실시간 이벤트/권한 버블/병렬 task 애니메이션
- **멀티 에이전트 공존** — 여러 에이전트를 동시에 실행해도 세션별로 독립 추적

### 애니메이션 & 상호작용
- 실시간 상태 인식(생각, 타이핑, 빌드, 저글링, 에러, 수면 등 12개 상태)
- 아이 트래킹(마우스 추적), 더블 클릭/연타 반응
- 어떤 상태에서도 드래그 가능
- 오른쪽 가장자리 미니 모드(hover 시 peek)

### 권한 버블
- Claude Code 권한 요청을 터미널 대신 데스크톱 플로팅 카드로 표시
- **Allow / Deny / Suggestions** 한 번에 처리
- 전역 단축키: `Ctrl+Shift+Y`(허용), `Ctrl+Shift+N`(거부)
- 여러 요청 스택 표시 + 터미널 선처리 시 자동 닫힘

### 세션 인텔리전스
- 다중 세션 우선순위 상태 자동 해석
- 서브에이전트 개수 기반 애니메이션 전환
- 우클릭 Sessions 메뉴에서 해당 터미널 포커스 이동
- 에이전트 비정상 종료 감지 및 고아 세션 정리

### 시스템
- 투명 영역 클릭 스루
- 위치/미니 모드 기억
- 싱글 인스턴스 락
- 자동 시작
- 방해 금지(DND) 모드
- 완료/권한 이벤트 사운드
- 트레이 메뉴(S/M/L, 언어, 자동 시작, 업데이트)
- 영어/중국어 UI 지원
- GitHub 릴리즈 기반 자동 업데이트

## 빠른 시작

```bash
# 저장소 클론
git clone https://github.com/rullerzhou-afk/clawd-on-desk.git
cd clawd-on-desk

# 의존성 설치
npm install

# 실행 (시작 시 Claude Code hooks 자동 등록)
npm start
```

**Claude Code**와 **Codex CLI**는 바로 사용 가능합니다. 나머지 에이전트는 1회 설정이 필요합니다.
자세한 설정(원격 SSH, WSL, macOS/Linux 포함): **[docs/setup-guide.md](docs/setup-guide.md)**

## 알려진 제한 사항

에이전트별 기능 차이(권한 버블 미지원, 폴링 지연, 터미널 포커스 제한 등)는 다음 문서를 참고하세요.
**[docs/known-limitations.md](docs/known-limitations.md)**

## 커스텀 테마

직접 만든 캐릭터와 애니메이션으로 테마를 교체할 수 있습니다.

1. `themes/template/`를 테마 디렉터리로 복사
   - Windows: `%APPDATA%/clawd-on-desk/themes/my-theme/`
   - macOS: `~/Library/Application Support/clawd-on-desk/themes/my-theme/`
   - Linux: `~/.config/clawd-on-desk/themes/my-theme/`
2. `theme.json`과 에셋(SVG, GIF, APNG, WebP) 작성
3. Clawd 우클릭 → Theme → 새 테마 선택

## 라이선스

MIT
