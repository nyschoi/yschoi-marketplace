# yschoi-marketplace

Claude Code용 개인 플러그인 마켓플레이스.

## 목표

Claude Code용 marketplace를 만들어, 발표자료(HTML 프레젠테이션) 생성 스킬을 팀/개인이 손쉽게 설치·사용하도록 함.

## 구성

```
yschoi-marketplace
├── .claude-plugin/marketplace.json   # 마켓플레이스 정의 (youngsoochoi-marketplace)
├── .mcp.json                         # MCP 서버 (Atlassian, Playwright)
└── plugins/                          # presentation-maker 플러그인
    ├── .claude-plugin/plugin.json
    └── skills/
        └── frontend-slides/          # 발표자료 생성 스킬
            ├── SKILL.md
            ├── STYLE_PRESETS.md
            ├── bold-template-pack/   # canvas 등 템플릿 팩
            ├── reference/fonts/       # Pretendard · JetBrains Mono 내장
            └── scripts/               # PDF 내보내기 · Vercel 배포 · PPTX 추출
```

- **마켓플레이스 이름**: `youngsoochoi-marketplace` (설치 시 사용)
- **플러그인 이름**: `presentation-maker`
- **스킬 이름**: `frontend-slides`

## skill 관련

[zarazhangrui/frontend-slides](https://github.com/zarazhangrui/frontend-slides) 기반 스킬을 커스터마이즈했다.

- 내가 원하는 design을 위해 추가로 정의한 **canvas 템플릿** (`bold-template-pack/templates/canvas/`)
- 회사 기본 폰트가 pretendard이므로, **Pretendard와 JetBrains Mono를 스킬에 내장**(`reference/fonts/`)하여 offline에서도 이용 가능

## 사전 준비

- Claude Code
- (선택) PDF 내보내기·배포용: Playwright(MCP로 자동), Vercel CLI(배포 시 자동 설치 안내)
- (선택) PPTX 변환용: `pip install python-pptx`

## 설치 방법

```
/plugin marketplace add nyschoi/yschoi-marketplace
/plugin install presentation-maker@youngsoochoi-marketplace
```

설치 후 **Claude Code 재시작**.

### 설치 확인

`/skills` 실행 시 아래처럼 보여야 함:

```
presentation-maker:frontend-slides · plugin · ~120 tok · locked by plugin
```

## 사용 방법

### 1) 스킬 직접 호출

```
/presentation-maker:frontend-slides
```

### 2) 자연어로 요청 (친절 모드)

먼저 원본 자료를 inbox에 준비한다. 예를 들어 Confluence 문서를 읽어 저장:

```
https://ktdevspace.atlassian.net/wiki/spaces/KTPAY/pages/462586968/... 를 읽고 md로 inbox에 저장해줘.
```

> Confluence 읽기는 `.mcp.json`의 Atlassian MCP 서버를 이용한다.

이후 저장한 자료를 근거로 발표자료 생성을 요청:

```
@inbox/marketplace-test/KTPAY_통합결제AM_대고객_오픈_채널_CX_개선_추진.md
@frontend-slides 스킬을 이용해서 presentation 생성.
1. 폰트와 이미지는 내장하여 offline 이용 가능해야 함
2. 폰트는 pretendard와 JetBrainsMono를 반드시 사용. 파워포인트 기준 최소 16pt 이상이어야 함
3. 스타일은 canvas
4. 출력형식: output/ktpay-cx-presentation-marketplace.html
```

## Canvas 스타일 정책

내가 커스터마이즈한 `canvas` 템플릿은 다음 규칙을 강제한다 (`bold-template-pack/templates/canvas/design.md`):

- **폰트**: Pretendard(한글/영문 본문·헤드라인)와 JetBrains Mono(eyebrow·caption·페이지 번호) **2종만** 사용. offline 대비 `reference/fonts/`의 폰트를 `@font-face`에 base64로 내장.
- **최소 크기**: 화면 어디에도 **16px 미만 텍스트 없음** (뱃지·캡션·각주 포함).
- **동영상**: 실제 `<video>` 태그로 native 임베드(포스터 이미지 대체 금지). 영상 파일은 HTML 옆 상대경로(`src="demo.mp4"`)로 두고 base64 인라인은 하지 않음. 다른 슬라이드로 이동 시 재생 자동 정지.
- **커서**: 시스템 포인터를 마젠타(navy 슬라이드에서는 흰색) dot 커서로 대체. 터치 기기에서는 native 커서 유지.

## 산출물 공유 / 내보내기

스킬 스크립트를 이용한다 (경로: `plugins/skills/frontend-slides/scripts/`).

```bash
# PDF로 내보내기 (Playwright로 슬라이드별 1920×1080 캡처 후 병합)
bash scripts/export-pdf.sh ./output/presentation.html ./output/presentation.pdf

# Vercel로 공개 URL 배포
bash scripts/deploy.sh ./output/presentation.html

# 기존 PPTX에서 콘텐츠 추출 (변환용)
python scripts/extract-pptx.py input.pptx output_dir/
```

## 폴더 규칙

`inbox/`, `output/`, `.claude/settings.local.json`, `.claude/skills/`는 업무 자료·로컬 설정·산출물이므로 `.gitignore` 처리되어 마켓플레이스에 포함되지 않는다.

## MCP 서버

`.mcp.json`에 정의됨. 사용하려면 Claude Code에서 해당 서버를 enable 해야 한다.

| 서버 | 용도 |
| --- | --- |
| `atlassian-ktspace`, `atlassian-ktdevspace` | Confluence/Jira 문서 읽기 |
| `playwright` | PDF 내보내기, 슬라이드 스크린샷 |
