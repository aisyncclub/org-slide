# org-slide — 기관·이벤트 발표 슬라이드 스킬

> **[AI싱크클럽 스킬] https://litt.ly/aisyncclub**

발표용 **슬라이드(HTML)** 를 만들어 주는 Claude Code / Claude 스킬입니다.
**스타일 기반 2개 템플릿**을 제공하며, 특정 기관명에 종속되지 않습니다(실제 명칭은 입력받아 채움).
**완전 자립형**이라 이 폴더만 복사하면 어디서든 작동합니다.

| 템플릿 | 스타일 | 톤 |
|---|---|---|
| **① institutional** | 기관 신뢰형 (Institutional) | 인스티튜셔널 블루 `#003764` + 레드 액센트(절제), 라이트·플랫·신뢰형 |
| **② event** | 프리미엄 이벤트형 (Premium Event) | 시안 `#00C2D1` + 마젠타 `#E5267E` + 골드 `#E8B864`, **그라데이션 미사용 솔리드**. 라이트(기본)/다크 |

## ✨ 특징

- **PPT식 뷰어** — 한 화면에 1장, `← →` / `Space` / 화면 버튼으로 이동 (세로 스크롤 아님)
- **전체화면 발표** — `F` 키 또는 `⛶` 버튼 (Fullscreen API)
- **Chart.js + 인포그래픽 고밀도** — 수치·추세·구성비를 차트/인포그래픽으로 시각화
- **자립형(self-contained)** — 폰트·차트 모두 CDN 로드, 외부 자산 0, `file://` 단독 렌더
- **기관명 비종속** — 샘플은 `[기관명]`·`[조직명]` 플레이스홀더, 실제 명칭은 입력값으로 채움
- 한글 `word-break: keep-all`(단어 잘림 방지), 1280×720 16:9

## 📦 설치

이 저장소를 그대로 스킬 폴더로 클론하세요.

```bash
git clone https://github.com/aisyncclub/org-slide.git ~/.claude/skills/org-slide
```

또는 프로젝트 단위로 쓰려면 해당 레포의 `.claude/skills/org-slide/` 에 복사합니다.

## 🚀 사용

Claude에게 이렇게 말하면 스킬이 트리거됩니다:

> "기관 슬라이드 만들어줘" · "발표자료 만들어줘" · "이벤트 발표자료 만들어줘"

진행 순서:

1. **발표자료 확인** — 자료(문서/파일) 또는 주제를 받습니다.
2. **구성안 미리보기** — 슬라이드별 제목·간략 내용·시각요소를 표로 먼저 보여주고 확인받습니다.
3. **템플릿 선택** — ① 기관 신뢰형 / ② 이벤트형 라이트(기본) / ③ 이벤트형 다크 중 선택.
4. **제작** — 선택한 템플릿으로 단일 HTML 슬라이드를 생성합니다.

## 🖼 샘플

`templates/` 에서 바로 열어볼 수 있습니다 (브라우저). 모두 **플레이스홀더 데모**입니다.

| 파일 | 설명 |
|---|---|
| `templates/institutional-sample.html` | 기관 신뢰형 8p |
| `templates/event-light-sample.html` | 이벤트형 라이트 8p |
| `templates/event-dark-sample.html` | 이벤트형 다크 8p |
| `templates/base.html` | 의존성 없는 베이스 골조(뷰어+전체화면) |

## 📁 구성

```
org-slide/
├── SKILL.md            # 트리거 · 워크플로우 · 템플릿 선택
├── design-system.md    # 공통 디자인 토큰 · 컴포넌트 · 차트/인포 · 뷰어 규격
├── presets/
│   ├── institutional.md  # 기관 신뢰형 토큰
│   └── event.md          # 이벤트형(솔리드, 다크/라이트) 토큰
└── templates/
    ├── base.html
    ├── institutional-sample.html
    ├── event-light-sample.html
    └── event-dark-sample.html
```

## 🎨 컬러 근거 (범용)

- **institutional**: 공공기관 통합 CI/정부상징 계열의 딥블루·레드 체계를 일반화한 **기관 신뢰형** 팔레트. (특정 기관 비귀속)
- **event**: 컨벤션·이벤트 업계 일반 레퍼런스를 종합한 **프리미엄 이벤트형** 솔리드 팔레트(시안/마젠타/골드).

---

Made with ❤️ by **[AI싱크클럽](https://litt.ly/aisyncclub)** · MIT License
