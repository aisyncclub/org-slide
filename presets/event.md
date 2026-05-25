# 프리셋: event — 프리미엄 이벤트형 (Premium Event)

> **스타일 정체성:** 국제회의·전시·컨퍼런스 등 **비즈니스 이벤트 발표용** 프리미엄 톤.
> 시안(연결·역동) + 마젠타(활력) + 골드(프리미엄) 솔리드 액센트. 라이트(기본)/다크 2모드.
> (색 근거: 컨벤션·이벤트 업계 일반 레퍼런스 종합 — 특정 조직명 비귀속, 범용)

> ⚠️ **그라데이션 미사용 원칙:** linear-/radial-/conic-gradient 및
> background-clip:text 그라데이션 텍스트를 **쓰지 않는다.** 모든 색은 **솔리드(단색)**.
> 깊이감은 그라데이션 대신 **솔리드 컬러 블록 + 그림자(glow) + 반투명 패널**로 만든다.

## 톤 키워드
**글로벌 · 역동 · 네트워킹 · 프리미엄 · 몰입**

## 컬러 팔레트

| 이름 | HEX | 의미 |
|---|---|---|
| 미드나잇 인디고 | `#141B34` | 다크 베이스 |
| 딥 인디고 패널 | `#1E2746` | 카드/패널 면 |
| 네트워크 시안 | `#00C2D1` | 연결·역동 (메인 액센트) |
| 에너지 마젠타 | `#E5267E` | 이벤트 활력 |
| 골드 샌드 | `#E8B864` | 프리미엄 포인트 |

## :root 토큰 (다크)

```css
:root{
  /* 면 */
  --bg:        #141B34;   /* 미드나잇 인디고 (솔리드) */
  --bg-2:      #0E1428;
  --surface:   #1E2746;   /* 카드 면 (솔리드) */
  --surface-2: #19223E;
  --glass-brd: rgba(120,150,220,0.22);
  /* 잉크 */
  --ink:       #F2F5FF;
  --ink-soft:  #C3CCE6;
  --ink-dim:   #8893B5;
  /* 브랜드 (단색) */
  --brand:     #00C2D1;   /* 네트워크 시안 (메인) */
  --brand-2:   #4FE0EA;
  --accent:    #E5267E;   /* 에너지 마젠타 */
  --accent-2:  #E8B864;   /* 골드 샌드 */
  /* 라인/하이라이트 (솔리드 단색 밴드) */
  --rule:      rgba(140,160,210,0.20);
  --hl:        rgba(0,194,209,0.24);   /* 시안 형광펜 (단색 배경) */
  --glow:      0 0 22px rgba(0,194,209,0.35);  /* 그라데이션 대신 글로우 그림자 */
  /* 타이포 */
  --display:   "Montserrat","Pretendard Variable",Pretendard,sans-serif;
  --sans:      "Pretendard Variable",Pretendard,"Noto Sans KR",sans-serif;
  --mono:      "JetBrains Mono",ui-monospace,monospace;
  --pad: 56px 80px;
}
```

> 큰 수치/키커는 `color:var(--brand)`(또는 `--accent`) **단색**. 그라데이션 텍스트 금지.

## 라이트 변형 (event-light, 기본 ⭐)

같은 이벤트 정체성을 **밝은 베이스**로 — 범용·인쇄물·밝은 회의실 프로젝션에 적합.
여기서도 **그라데이션 미사용**. 액센트는 라이트 대비를 위해 약간 진하게.

```css
:root{
  /* 면 (솔리드) */
  --bg:#FFFFFF; --bg-2:#F5F7FC;
  --surface:#FFFFFF; --surface-2:#F2F5FB; --glass-brd:#E2E7F0;
  /* 잉크 */
  --ink:#16203A; --ink-soft:#41506B; --ink-dim:#7A88A6;
  /* 브랜드 (단색, 라이트 대비용 톤다운) */
  --brand:#0094B3; --brand-2:#0E7FA0;
  --accent:#D81E74; --accent-2:#C8922F;
  /* 라인/하이라이트 */
  --rule:#E2E7F0; --hl:rgba(0,148,179,.16);
  --glow:0 8px 24px rgba(0,148,179,0.14);
  /* 타이포 동일 */
  --display:"Montserrat","Pretendard Variable",Pretendard,sans-serif;
  --sans:"Pretendard Variable",Pretendard,"Noto Sans KR",sans-serif;
  --mono:"JetBrains Mono",ui-monospace,monospace;
  --pad:64px 80px;
}
```

라이트 변형에서는:
- 카드는 백색 면 + 1px `--rule` 테두리 + 부드러운 그림자(솔리드).
- 상단 띠/포인트는 **솔리드 시안**(그라데이션 띠 금지).
- 큰 수치는 **단색**(`--brand`/`--accent`).
- Chart.js: text=`#41506B`, grid=`#E2E7F0`, 데이터 팔레트 `#0094B3·#3D5CD6·#D81E74·#C8922F` (단색 fill).

## 폰트 규칙
- 영문 디스플레이/숫자: **Montserrat 700/800**.
- 한글 제목: **Pretendard 800**.
- 본문: Pretendard 400/500, 다크 위 `--ink`(#F2F5FF) 이상 대비.
- 큰 수치: **단색** `color:var(--brand)` 또는 `var(--accent)`.

## 레이아웃 시그널 (그라데이션 없이)
- 배경: **솔리드** `--bg`. 깊이감은 단색 원/바 블록(낮은 opacity) 또는 굵은 컬러 키라인으로.
- 표지: 솔리드 베이스 + 큰 단색 키워드 + 시안/마젠타 컬러 블록·키라인.
- 카드: 반투명/솔리드 면 + 1px 라인 + **box-shadow 글로우**.
- 타임라인/세션: 시안 **단색** 라인 + 노드 글로우.
- KPI 수치: **단색**(시안/마젠타) + 카운트업 모션.
- 차트: 막대/도넛/라인 모두 **단색 fill**.
- 조직·행사장은 `[조직명]`·`[행사장]` 플레이스홀더로 둔다.

## 모션
`scale 0.96→1 + opacity + glow(box-shadow)`. 수치 카운트업. 실패 시 fallback opacity 1.

## 금지
- **그라데이션 일절(linear/radial/conic, background-clip:text)** — 솔리드 단색만.
- 라이트 변형 외 라이트/백색 풀배경(다크 프리미엄 톤 깨짐).
- 대비 낮은 회색 본문(다크 위 #8893B5 미만 본문 금지).
- **특정 조직명 하드코딩** — 실제 명칭은 입력받아 채우고, 샘플/기본값은 `[조직명]` 플레이스홀더.
- 시안/마젠타/골드 외 무지개색 남발.
