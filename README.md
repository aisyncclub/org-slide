# org-slide — 기관용 발표 슬라이드 스킬

> **[AI싱크클럽 스킬] https://litt.ly/aisyncclub**

기관 브랜드 정체성에 맞춘 **발표 슬라이드(HTML)** 를 만들어 주는 Claude Code / Claude 스킬입니다.
두 가지 내장 템플릿(프리셋)을 제공하며, **완전 자립형**이라 이 폴더만 복사하면 어디서든 작동합니다.

| 프리셋 | 대상 | 톤 |
|---|---|---|
| **① knih** | 국립보건연구원 / 공공기관 | 정부상징 통합 CI(정부청색 `#003764` + 정부적색 `#E4032E`), 라이트·플랫·기관 신뢰형 |
| **② mice** | MICE 임직원 / 국제회의·전시 | 네트워크 시안 `#00C2D1` + 마젠타 `#E5267E` + 골드 `#E8B864`, **그라데이션 미사용 솔리드**. 라이트(기본)/다크 |

## ✨ 특징

- **PPT식 뷰어** — 한 화면에 1장, `← →` / `Space` / 화면 버튼으로 이동 (세로 스크롤 아님)
- **전체화면 발표** — `F` 키 또는 `⛶` 버튼 (Fullscreen API)
- **Chart.js + 인포그래픽 고밀도** — 수치·추세·구성비를 차트/인포그래픽으로 시각화
- **자립형(self-contained)** — 폰트·차트 모두 CDN 로드, 외부 자산 0, `file://` 단독 렌더
- 한글 `word-break: keep-all`(단어 잘림 방지), 1280×720 16:9

## 📦 설치

이 저장소를 그대로 스킬 폴더로 클론하세요.

```bash
git clone https://github.com/aisyncclub/org-slide.git ~/.claude/skills/org-slide
```

또는 프로젝트 단위로 쓰려면 해당 레포의 `.claude/skills/org-slide/` 에 복사합니다.

## 🚀 사용

Claude에게 이렇게 말하면 스킬이 트리거됩니다:

> "기관 슬라이드 만들어줘" · "보건연구원 발표자료 만들어줘" · "MICE 발표 슬라이드 만들어줘"

진행 순서:

1. **발표자료 확인** — 자료(문서/파일) 또는 주제를 받습니다.
2. **구성안 미리보기** — 슬라이드별 제목·간략 내용·시각요소를 표로 먼저 보여주고 확인받습니다.
3. **템플릿 선택** — ① 국립보건연구원 / ② MICE 라이트(기본) / ③ MICE 다크 중 선택.
4. **제작** — 선택한 템플릿으로 단일 HTML 슬라이드를 생성합니다.

## 🖼 샘플

`templates/` 에서 바로 열어볼 수 있습니다 (브라우저).

| 파일 | 설명 |
|---|---|
| `templates/knih-sample.html` | 국립보건연구원 8p (AI 세미나) |
| `templates/mice-light-sample.html` | MICE 라이트 8p (MICE TRENDS) |
| `templates/mice-sample.html` | MICE 다크 8p (MICE TRENDS) |
| `templates/base.html` | 의존성 없는 베이스 골조(뷰어+전체화면) |

## 📁 구성

```
org-slide/
├── SKILL.md            # 트리거 · 워크플로우 · 템플릿 선택
├── design-system.md    # 공통 디자인 토큰 · 컴포넌트 · 차트/인포 · 뷰어 규격
├── presets/
│   ├── knih.md         # 국립보건연구원(정부상징) 토큰
│   └── mice.md         # MICE(솔리드, 다크/라이트) 토큰
└── templates/
    ├── base.html
    ├── knih-sample.html
    ├── mice-sample.html
    └── mice-light-sample.html
```

## 🎨 컬러 근거

- **knih**: 국립보건연구원은 자체 CI 없이 대한민국 정부상징(GOV.KR) 통합 CI를 따릅니다. 정부청색 `#003764`(Pantone 2955C) / 정부적색 `#E4032E`(1935C) / 정부회색 `#575757`.
- **mice**: 단일 공식 CI가 없는 산업군. COEX(마젠타)·K-MICE(글로벌 블루) 등 컨벤션 레퍼런스와 MICE 트렌드를 종합한 솔리드 팔레트.

---

Made with ❤️ by **[AI싱크클럽](https://litt.ly/aisyncclub)** · MIT License
