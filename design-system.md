# org-slide 디자인 시스템 (공통)

두 프리셋(`institutional` / `event`)이 공유하는 레이아웃 원칙·컴포넌트·검증 기준.
프리셋별 컬러/폰트 토큰은 `presets/*.md` 가 `:root` 변수로 덮어쓴다.

---

## 1. 캔버스 규격

| 항목 | 값 |
|---|---|
| 슬라이드 비율 | 16:9 |
| 기준 해상도 | 1280 × 720 (px), `transform: scale()` 로 반응형 |
| 안전 여백 | 상하 56px, 좌우 80px (`--pad`) |
| 한글 줄바꿈 | `word-break: keep-all; overflow-wrap: break-word;` (단어 잘림 방지) |
| 폰트 로딩 | **CDN만 사용** (자립형). 로컬 폰트 의존 금지 |

### 필수 CDN (base.html에 포함)

```html
<!-- 공통: Pretendard (본문 표준) -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.min.css">
<!-- institutional: Noto Sans KR / Noto Serif KR -->
<!-- event: Montserrat (라틴 디스플레이) -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@600;700;800&family=Noto+Sans+KR:wght@400;500;700;900&display=swap" rel="stylesheet">
<!-- 모션 (선택, ScrollTrigger 불필요 — §7 뷰어가 전환 시 재생) -->
<script src="https://cdn.jsdelivr.net/npm/gsap@3.12.5/dist/gsap.min.js"></script>
```

---

## 2. 공통 토큰 인터페이스

각 프리셋은 아래 변수를 반드시 정의한다 (`presets/*.md` 참조).

```css
:root{
  /* 면 */
  --bg:        /* 슬라이드 베이스 */;
  --surface:   /* 카드/패널 면 */;
  --surface-2: /* 보조 면 */;
  /* 잉크(텍스트) */
  --ink:       /* 본문 강 */;
  --ink-soft:  /* 본문 약 */;
  --ink-dim:   /* 캡션/메타 */;
  /* 브랜드 */
  --brand:     /* 메인 브랜드색 */;
  --brand-2:   /* 보조 브랜드색 */;
  --accent:    /* 강조(절제 사용) */;
  --accent-2:  /* 2차 강조(프리미엄 포인트) */;
  /* 라인/하이라이트 */
  --rule:      /* 구분선 */;
  --hl:        /* 형광펜 하이라이트 */;
  /* 타이포 */
  --display:   /* 제목 폰트 스택 */;
  --sans:      /* 본문 폰트 스택 */;
  --mono:      /* 수치/코드 */;
  /* 간격 */
  --pad: 56px 80px;
}
```

---

## 3. 컴포넌트 카탈로그 (10종)

슬라이드는 아래 블록을 조합해서 만든다. 모든 블록은 두 프리셋에서 동일 클래스명으로 작동하되,
컬러는 `:root` 토큰을 통해 자동으로 프리셋 색을 띤다.

| # | 컴포넌트 | 용도 | 핵심 클래스 |
|---|---|---|---|
| 1 | **Cover** | 표지 (타이틀 + 메타 4분할) | `.slide.cover` `.cover-meta` |
| 2 | **Section Divider** | 챕터 전환 (큰 번호 + 제목) | `.slide.divider` `.divider-num` |
| 3 | **Statement** | 한 문장 핵심 메시지 | `.slide.statement` `.lede` |
| 4 | **KPI Grid** | 수치 카드 3-4개 | `.kpi-grid` `.kpi` |
| 5 | **Bullet + Lede** | 제목 + 리드 + 불릿 | `.eyebrow` `.section-h` `.bullets` |
| 6 | **Two-Col** | 좌우 2단 (텍스트/시각) | `.two-col` |
| 7 | **Callout** | 인용·강조 박스 | `.callout` |
| 8 | **Timeline** | 단계/세션 타임라인 | `.timeline` `.tl-item` |
| 9 | **Data Bar** | 막대/비교 시각화 | `.databar` `.bar` |
| 10 | **Closing** | 마무리 + CTA/연락 | `.slide.closing` |

### 공통 슬라이드 골격

```html
<section class="slide cover">
  <header class="head">
    <span class="brand"><span class="mark"></span> 기관명</span>
    <span class="chap">SECTION · 01</span>
  </header>
  <!-- 본문 컴포넌트 -->
  <footer class="foot">
    <span class="meta">행사명 · 일자</span>
    <span class="pg">01 / 12</span>
  </footer>
</section>
```

### 강조 규칙

- `.hl` = 형광펜 강조. **슬라이드당 최대 2회**. 남발 금지.
- 핵심 수치는 `--mono` + 큰 사이즈로. 단위는 작게.
- italic은 event 프리셋의 영문 라벨에만 허용. institutional는 italic 금지(기관 정제성).

---

## 4. 모션 가이드

| 프리셋 | 모션 |
|---|---|
| institutional | 절제된 `opacity 0→1 + translateY 16px→0`, stagger 0.06s. 화려한 효과 금지. |
| event | `scale 0.96→1 + glow(box-shadow)`, 수치 카운트업 허용. **솔리드 배경**(radial orb·그라데이션 미사용). |

슬라이드 전환 시 base.html의 `reveal()`로 `[data-anim]`을 1회 재생(§7 뷰어). 모션 실패해도 콘텐츠는 항상 보이게(기본 opacity 1 fallback).

---

## 6. Chart.js & 인포그래픽 (⚠️ 적극 활용)

> **원칙: "글로 설명하지 말고 보여줘라."** 수치·비교·추세·구성비·절차가 나오면
> 텍스트 나열 대신 **차트 또는 인포그래픽**으로 시각화한다.
> **고밀도 기준 — 8p 데크당 차트 3개 이상 + 인포그래픽 4개 이상.**
> 표지·마무리를 제외한 본문 슬라이드는 원칙적으로 시각 요소를 1개 이상 담는다
> (한 슬라이드에 차트 + 보조 인포그래픽을 함께 배치하는 "콤보" 권장).

### 6-1. Chart.js (CDN · 자립형)

```html
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js"></script>
```

데크 상단에서 프리셋 색으로 전역 테마를 1회 세팅한다(폰트=Pretendard, 색=토큰 hex).
**Chart.js는 CSS 변수를 못 읽으므로 실제 hex 를 넣는다.**

```js
Chart.defaults.font.family = 'Pretendard, "Noto Sans KR", sans-serif';
Chart.defaults.font.weight = 500;
Chart.defaults.plugins.legend.labels.usePointStyle = true;
Chart.defaults.plugins.legend.labels.boxWidth = 8;
// institutional:  text=#3A4A60, grid=#DBE1EA
// event:  text=#C3CCE6, grid=rgba(140,160,210,.18)
// event-light: text=#41506B, grid=#E2E7F0
```

**프리셋별 데이터 팔레트**

| 프리셋 | 시리즈 색 (순서대로) |
|---|---|
| institutional | `#003764` · `#1E5BA8` · `#4F86C6` · `#9BB8DE` (강조 1개만 `#E4032E`) |
| event (dark) | `#00C2D1` · `#5B7BF0` · `#E5267E` · `#E8B864` |
| event-light | `#0094B3` · `#3D5CD6` · `#D81E74` · `#C8922F` (라이트 위 대비 확보) |

**규칙**
- 차트 캔버스는 고정 높이 컨테이너(`<div style="height:300px">`)에 넣어 비율 깨짐 방지.
- `responsive:true, maintainAspectRatio:false`.
- 막대/도넛은 `borderRadius`·여백으로 모던하게. 격자선 최소화(`grid.display` 선별).
- fill은 **단색**(필요 시 알파). ⚠️ event 프리셋은 그라데이션 미사용 → `createLinearGradient` 금지, 단색만.
- 차트마다 **한 줄 캡션(So What)** 을 아래에 붙여 의미를 전달.
- 모션 실패/차트 미로드 시에도 제목·캡션은 보이게(차트는 보조).

### 6-2. 인포그래픽 컴포넌트 (CSS, 라이브러리 불필요)

| 유형 | 클래스 | 용도 |
|---|---|---|
| **Stat Row** | `.stat-row .stat` | 큰 수치 3-4개 가로 배열(아이콘+숫자+라벨) |
| **Process Flow** | `.flow .step` (화살표 연결) | 단계/절차 시각화 |
| **Comparison** | `.vs` (좌 Before / 우 After) | 도입 전후·A vs B |
| **Icon Grid** | `.icongrid .ic` | 항목 4-6개 카드(SVG 픽토그램) |
| **Progress / Gauge** | `.gauge` (institutional=conic-gradient 허용 / event=SVG stroke 단색) | 비율·달성도 원형 게이지 |
| **Donut Legend** | `.donut-legend` | 차트 옆 범례+수치 |

- 아이콘은 **인라인 SVG**(외부 의존 0). stroke=currentColor 로 프리셋 색 자동 적용.
- 인포그래픽도 한글 `keep-all`, 토큰 색만 사용.

### 6-3. 8페이지 표준 데크 아크

| p | 슬라이드 | 시각화 |
|---|---|---|
| 1 | Cover | — |
| 2 | 아젠다 / 핵심 질문 | 인포그래픽(번호 리스트·아이콘) |
| 3 | 현황·배경 | **Chart**(추세 line/bar) |
| 4 | 프레임워크·개념 | 인포그래픽(Process Flow) |
| 5 | 데이터 심화 | **Chart**(도넛/그룹 bar) + Donut Legend |
| 6 | 사례·적용 | 인포그래픽(Stat Row / Comparison) |
| 7 | 로드맵·타임라인 | 인포그래픽(Timeline) |
| 8 | 마무리 + CTA | Callout |

---

## 7. 프레젠테이션 뷰어 (⚠️ 필수 — PPT식 화살표 네비게이션)

슬라이드는 **세로 스크롤로 쌓지 않는다.** 항상 **한 번에 1장만 표시**하고
**← → / Space / 화면 버튼**으로 PPT처럼 이동한다. (베이스 골조 `base.html` 참조)

### 구조
```html
<div class="stage"><div class="deck" id="deck">
  <section class="slide active"> … 1장 … </section>
  <section class="slide"> … 2장 … </section>
  … (8장)
</div></div>
<nav class="deck-nav"><button id="prev">‹</button><span class="ind" id="ind">1 / 8</span><button id="next">›</button></nav>
```

### 핵심 규칙
- `.stage` 는 화면 중앙에 `.deck`(1280×720)을 두고 창 크기에 맞춰 `transform:scale()` (비율 유지).
- `.slide{position:absolute;inset:0;opacity:0;visibility:hidden}` → `.slide.active{opacity:1;visibility:visible}`.
  **`display:none` 금지** (Chart.js 캔버스 레이아웃이 깨짐). opacity/visibility 토글만.
- **`.body{justify-content:center}` 로 콘텐츠 세로 중앙 정렬** — 위로 쏠리지 않게(과도한 top padding 금지).
- 차트는 **로드 시 전부 init** (스크롤 트리거 사용 금지). 슬라이드 전환 시 `[data-anim]` 만 GSAP로 재생.
- 키보드 `ArrowLeft/ArrowRight/Space/PageUp/PageDown` + 화면 ‹ › 버튼 + `n / 8` 인디케이터.
- **전체화면(필수)**: nav에 `⛶` 버튼 + `F` 키 → Fullscreen API(`requestFullscreen`/`exitFullscreen`, webkit 폴백).
  전체화면 진입·해제 시 `fit()` 재실행(`fullscreenchange` 리스너 또는 resize 디스패치)으로 스케일 재계산.
- 좌상단 `.cap` 작은 식별 라벨(선택).

> base.html 의 `<script>` 네비게이션 블록을 그대로 사용/복사한다(검증된 동작).

---

## 5. 자가 검증 체크리스트 (생성 후 필수)

- [ ] 프리셋 토큰이 `:root`에 정확히 주입되었는가 (institutional=라이트/blue, event=다크/cyan)
- [ ] 폰트가 CDN으로 로드되는가 (로컬 의존 0)
- [ ] 한글 `word-break: keep-all` 적용 — 단어 중간 잘림 없는가
- [ ] `.hl` 슬라이드당 2회 이하인가
- [ ] institutional: 시그널 레드 #E4032E 를 강조에만 절제 사용했는가 (면적 과다 금지)
- [ ] event: 텍스트 대비비 충분한가 (다크 위 본문 #E8ECF6 이상)
- [ ] 모든 슬라이드에 head(기관/브랜드 마크) + foot(페이지) 일관 적용
- [ ] 모션 비활성 시에도 모든 텍스트가 보이는가 (fallback)
- [ ] 슬라이드 1280×720 안에 콘텐츠가 넘치지 않는가
- [ ] 파일 단독 열기(file://)로 외부 자산 없이 렌더링되는가
- [ ] **Chart.js 2개 이상** 사용했는가 (수치·추세·구성비를 차트로)
- [ ] **인포그래픽 3개 이상** (Stat Row / Flow / Comparison / Icon Grid / Gauge)
- [ ] 차트 색이 프리셋 데이터 팔레트(§6-1)와 일치하는가
- [ ] 차트 캔버스가 고정 높이 컨테이너 안에 있는가 (비율 깨짐 방지)
- [ ] 차트마다 So What 캡션 한 줄이 붙었는가
- [ ] **PPT식 뷰어** — 한 번에 1장, ← → / 버튼 이동이 작동하는가 (세로 스크롤 아님)
- [ ] **전체화면** — ⛶ 버튼 / F 키로 진입·해제되고 스케일이 맞게 재계산되는가
- [ ] 본문이 **세로 중앙 정렬**되어 위로 쏠리지 않는가
- [ ] 차트가 opacity로 숨은 슬라이드에서도 정상 렌더되는가 (`display:none` 미사용)
