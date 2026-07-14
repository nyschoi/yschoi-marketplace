# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 이 레포의 성격

전통적인 애플리케이션이 아니라 **Claude Code 플러그인 마켓플레이스**다. 빌드·린트·테스트 파이프라인이 없다. "산출물"은 코드 실행 결과가 아니라, 사용자가 스킬을 통해 생성하는 HTML 프레젠테이션이다.

배포 흐름: 사용자가 `/plugin marketplace add nyschoi/yschoi-marketplace` 후 `/plugin install presentation-maker@youngsoochoi-marketplace`로 설치 → Claude Code 재시작 → `/skills`에 `presentation-maker:frontend-slides`가 노출.

## 정체성 3계층 (혼동 주의)

세 가지 이름이 각각 다른 레이어를 가리킨다. 하나를 바꾸면 나머지와의 정합성을 반드시 확인할 것.

| 이름 | 정의 위치 | 용도 |
| --- | --- | --- |
| `youngsoochoi-marketplace` | `.claude-plugin/marketplace.json` `name` | 마켓플레이스 식별자 (install 명령의 `@뒤`) |
| `presentation-maker` | `plugins/.claude-plugin/plugin.json` `name` + marketplace.json plugins[].name | 플러그인 식별자 (install 대상) |
| `frontend-slides` | `plugins/skills/frontend-slides/SKILL.md` frontmatter `name` | 스킬 식별자 (`/presentation-maker:frontend-slides`) |
| `nyschoi/yschoi-marketplace` | git remote / GitHub 경로 | `marketplace add`의 인자 |

marketplace.json의 `plugins[].source`는 `./plugins`를 가리킨다 — 플러그인 본체 위치를 옮기면 이 값도 함께 바꿔야 한다.

## 핵심: frontend-slides 스킬

[zarazhangrui/frontend-slides](https://github.com/zarazhangrui/frontend-slides)를 fork·커스터마이즈한 것이 이 레포의 실질적 본체다. 위치: `plugins/skills/frontend-slides/`.

스킬은 `SKILL.md`가 오케스트레이션하는 **Phase 기반 워크플로우**(Phase 0 모드 감지 → 1 콘텐츠 → 2 스타일 → 3 생성 → 4 PPTX 변환 → 5 전달 → 6 공유/내보내기)로 동작하며, 필요한 단계에서만 아래 참조 파일을 lazy-load 한다. `SKILL.md` 하단 "Supporting Files" 표가 각 파일을 어느 Phase에서 읽는지의 단일 출처다:

- `STYLE_PRESETS.md` — 12개 프리셋 (Phase 2 스타일 선택)
- `bold-template-pack/` — canvas 포함 다수 템플릿. `selection-index.json`으로 후보 추림 → `templates/*/preview.md`(경량 카드) → 선택된 것만 `templates/*/design.md`(전체 디자인 시스템) 로드. **큰 파일이므로 전체를 무턱대고 읽지 말 것.**
- `viewport-base.css` — 모든 덱에 복사하는 고정 스테이지 CSS
- `html-template.md`, `animation-patterns.md` — Phase 3 생성
- `reference/fonts/` — Pretendard·JetBrains Mono woff2/ttf (offline 내장용)
- `scripts/` — 아래 참조

### 불변 규칙 (스킬이 강제)

- **고정 16:9 스테이지**: 모든 슬라이드는 1920×1080으로 작성, 스테이지 전체를 뷰포트에 scale. 기기에 맞춰 reflow 금지 (모바일 포함).
- **폰트는 시스템 폰트 금지** — 프리셋/템플릿이 지정한 폰트 사용.

### canvas 템플릿 (이 레포의 커스텀 추가분)

`bold-template-pack/templates/canvas/design.md`가 단일 출처. 회사 표준에 맞춘 강제 정책:

- **폰트 2종 한정**: Pretendard(한글·영문 본문/헤드라인) + JetBrains Mono(eyebrow·caption·페이지번호). 제3의 폰트나 `system-ui` fallback 금지 — 로드 실패는 "버그(임베드로 고칠 것)"이지 "generic fallback으로 넘길 것"이 아님.
- **offline 내장**: `reference/fonts/`의 폰트를 `@font-face` `src: url(data:font/...;base64,...)`로 `<style>`에 직접 임베드.
- **16px floor**: 덱 전체에서 16px 미만 텍스트 없음 (즉흥 라벨·뱃지·캡션·각주 포함). 안 맞으면 레이아웃으로 풀 것.
- **동영상은 native `<video>`**: 포스터+재생아이콘 대체 금지. 영상은 base64 인라인하지 말고 HTML 옆 상대경로(`src="demo.mp4"`)로. 슬라이드 이동 시 `showSlide()`에서 비활성 슬라이드의 `<video>`를 `.pause()`.
- **커스텀 커서**: 마젠타 dot(navy 슬라이드는 흰색). `position: fixed`로 letterbox 여백까지 추적. 터치/coarse 포인터는 native 커서 유지. `mix-blend-mode: difference`는 쓰지 않음.

## 스크립트

`plugins/skills/frontend-slides/scripts/`:

```bash
# HTML 덱 → PDF (로컬 서버 기동 후 Playwright로 슬라이드별 1920×1080 캡처 → 병합)
bash scripts/export-pdf.sh <path-to-html> [output.pdf] [--compact]

# 덱 → Vercel 공개 URL (Vercel CLI 미설치 시 설치·로그인 안내)
bash scripts/deploy.sh <path-to-slide-folder-or-html>

# 기존 PPTX → JSON+이미지 추출 (변환 워크플로우 입력). requires: pip install python-pptx
python scripts/extract-pptx.py <input.pptx> [output_dir]
```

## MCP 서버

`.mcp.json`에 정의(`atlassian-ktspace`, `atlassian-ktdevspace`, `playwright`). Confluence/Jira 문서 읽기와 PDF 캡처에 쓰이며, Claude Code에서 enable 해야 동작한다.

## Git에 올리지 않는 것

`.gitignore`: `inbox/`(원본 업무 자료), `output/`(생성 산출물), `.claude/settings.local.json`, `.claude/skills/`(로컬 심링크), `.DS_Store`. 이들은 마켓플레이스와 무관하므로 커밋 대상이 아니다.
