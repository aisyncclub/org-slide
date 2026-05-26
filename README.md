# org-slide — 기관·이벤트 발표 슬라이드 스킬

> **[AI싱크클럽 스킬] https://litt.ly/aisyncclub**

발표용 **슬라이드(HTML)** 를 만들어 주는 Claude Code / Claude 스킬입니다.
**스타일 기반 5개 템플릿**을 제공하며, 특정 기관명에 종속되지 않습니다(실제 명칭은 입력받아 채움).
**완전 자립형**이라 이 폴더만 복사하면 어디서든 작동합니다.

| 템플릿 | 스타일 | 톤 / 용도 |
|---|---|---|
| **① institutional** | 기관 신뢰형 | 블루 `#003764` + 레드 액센트(절제), 라이트·플랫. 공공·기관 |
| **② event** | 프리미엄 이벤트형 | 시안 `#00C2D1` + 마젠타 + 골드(그라데이션 미사용). 라이트(기본)/다크. 이벤트·컨퍼런스 |
| **③ editorial** | 에디토리얼 빅타입 | 아이보리 + 잉크 `#161616` + 버밀리언 `#E63946`, 큰 세리프. 비전·강연 |
| **④ soft-minimal** | 웜 미니멀 | 샌드 + 세이지 `#6B8F71` + 테라코타, 둥근 카드. 교육·워크숍·사내 |
| **⑤ consulting** | 컨설팅 데이터형 | 차콜 `#1F2933` + 앰버 `#E0A100`, 표·차트 고밀도. 전략·IR·리포트 |

## ✨ 특징

- **PPT식 뷰어** — 한 화면에 1장, `← →` / `Space` / 화면 버튼으로 이동 (세로 스크롤 아님)
- **전체화면 발표** — `F` 키 또는 `⛶` 버튼 (Fullscreen API)
- **Chart.js + 인포그래픽 고밀도** — 수치·추세·구성비를 차트/인포그래픽으로 시각화
- **자립형(self-contained)** — 폰트·차트 모두 CDN 로드, 외부 자산 0, `file://` 단독 렌더
- **기관명 비종속** — 샘플은 `[기관명]`·`[조직명]` 플레이스홀더, 실제 명칭은 입력값으로 채움
- 한글 `word-break: keep-all`(단어 잘림 방지), 1280×720 16:9

## 📦 설치

`org-slide`는 별도 빌드가 필요 없는 **폴더형 스킬**입니다.
아래 명령으로 원하는 스킬 폴더에 그대로 클론하면 설치가 끝납니다.

### 1) Claude Code 전역 설치

Claude Code에서 항상 사용할 거라면 이 위치에 설치하세요.

```bash
git clone https://github.com/aisyncclub/org-slide.git ~/.claude/skills/org-slide
```

설치 후 Claude Code를 재시작하면 `org-slide` 스킬이 인식됩니다.

### 2) Codex 전역 설치

Codex에서도 같은 스킬을 쓰려면 아래 위치에 설치하세요.

```bash
git clone https://github.com/aisyncclub/org-slide.git ~/.codex/skills/org-slide
```

설치 후 Codex를 재시작하면 새 스킬 목록에 반영됩니다.

### 3) 특정 프로젝트에만 설치

프로젝트 하나에서만 쓰고 싶다면 해당 프로젝트 안에 설치합니다.

```bash
mkdir -p .claude/skills
git clone https://github.com/aisyncclub/org-slide.git .claude/skills/org-slide
```

이 방식은 팀 프로젝트에 스킬을 함께 넣어 두고, 같은 템플릿 규칙을 공유할 때 좋습니다.

### 4) 이미 설치한 경우 업데이트

이미 설치되어 있다면 새로 클론하지 말고 설치 폴더에서 pull 하세요.

```bash
cd ~/.claude/skills/org-slide
git pull
```

Codex 설치본을 업데이트하려면:

```bash
cd ~/.codex/skills/org-slide
git pull
```

### 5) 설치 확인

아래 파일이 보이면 정상 설치된 것입니다.

```bash
ls ~/.claude/skills/org-slide/SKILL.md
ls ~/.codex/skills/org-slide/SKILL.md
```

스킬을 호출할 때는 예를 들어 이렇게 말하면 됩니다.

> "org-slide로 기관 발표자료 만들어줘"  
> "공공기관 슬라이드 만들어줘"  
> "이벤트 발표자료 만들어줘"

처음 실행하면 발표자료가 있는지 확인하고, 구성안 미리보기 → 템플릿 선택 → HTML 슬라이드 제작 순서로 진행합니다.

## 🚀 사용

Claude에게 이렇게 말하면 스킬이 트리거됩니다:

> "기관 슬라이드 만들어줘" · "발표자료 만들어줘" · "이벤트 발표자료 만들어줘"

진행 순서:

1. **발표자료 확인** — 자료(문서/파일) 또는 주제를 받습니다.
2. **구성안 미리보기** — 슬라이드별 제목·간략 내용·시각요소를 표로 먼저 보여주고 확인받습니다.
3. **템플릿 선택** — ① 기관 신뢰형 / ② 이벤트형 라이트(기본) / ③ 이벤트형 다크 / ④ 에디토리얼 / ⑤ 웜 미니멀 / ⑥ 컨설팅 중 선택.
4. **제작** — 선택한 템플릿으로 단일 HTML 슬라이드를 생성합니다.

## 🖼 샘플

`templates/` 에서 바로 열어볼 수 있습니다 (브라우저). 모두 **플레이스홀더 데모**입니다.

| 파일 | 설명 |
|---|---|
| `templates/institutional-sample.html` | 기관 신뢰형 8p |
| `templates/event-light-sample.html` | 이벤트형 라이트 8p |
| `templates/event-dark-sample.html` | 이벤트형 다크 8p |
| `templates/editorial-sample.html` | 에디토리얼 빅타입 8p |
| `templates/soft-minimal-sample.html` | 웜 미니멀 8p |
| `templates/consulting-sample.html` | 컨설팅 데이터형 8p |
| `templates/base.html` | 의존성 없는 베이스 골조(뷰어+전체화면) |

## 📁 구성

```
org-slide/
├── SKILL.md            # 트리거 · 워크플로우 · 템플릿 선택
├── design-system.md    # 공통 디자인 토큰 · 컴포넌트 · 차트/인포 · 뷰어 규격
├── presets/
│   ├── institutional.md  # 기관 신뢰형
│   ├── event.md          # 이벤트형(솔리드, 다크/라이트)
│   ├── editorial.md      # 에디토리얼 빅타입
│   ├── soft-minimal.md   # 웜 미니멀
│   └── consulting.md     # 컨설팅 데이터형
└── templates/
    ├── base.html
    ├── institutional-sample.html
    ├── event-light-sample.html
    ├── event-dark-sample.html
    ├── editorial-sample.html
    ├── soft-minimal-sample.html
    └── consulting-sample.html
```

## 🎨 컬러 근거 (범용)

- **institutional**: 공공기관 통합 CI/정부상징 계열의 딥블루·레드 체계를 일반화한 **기관 신뢰형** 팔레트. (특정 기관 비귀속)
- **event**: 컨벤션·이벤트 업계 일반 레퍼런스를 종합한 **프리미엄 이벤트형** 솔리드 팔레트(시안/마젠타/골드).
- **editorial · soft-minimal · consulting**: 2026 발표 디자인 트렌드(빅타입 에디토리얼 / 웜 미니멀리즘 / 엔터프라이즈 클래리티)를 반영한 범용 스타일.

---

Made with ❤️ by **[AI싱크클럽](https://litt.ly/aisyncclub)** · MIT License
