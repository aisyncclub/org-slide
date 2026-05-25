# 프리셋: soft-minimal — 웜 미니멀 (Soft Minimal)

> **스타일 정체성:** 따뜻한 뉴트럴 + 둥근 카드 + 차분한 흐름. 인지부하↓, 접근성 친화.
> 사람 중심의 부드럽고 친근한 발표. (2026 트렌드: 웜 미니멀리즘)

## 톤 키워드
**따뜻 · 친근 · 차분 · 명료 · 배려**

샌드/크림 베이스 + 웜 차콜 잉크 + 세이지/테라코타 소프트 액센트. 둥근 모서리, 넉넉한 여백.

## 컬러 팔레트

| 이름 | HEX | 용도 |
|---|---|---|
| 샌드 | `#F6F1EA` | 베이스 |
| 페이퍼 화이트 | `#FFFFFF` | 카드(둥근) |
| 웜 차콜 | `#2E2A25` | 본문 |
| 세이지 | `#6B8F71` | 메인 액센트 |
| 테라코타 | `#C8755A` | 보조 액센트 |

## :root 토큰

```css
:root{
  /* 면 */
  --bg:        #F6F1EA;   /* 샌드 */
  --surface:   #FFFFFF;   /* 카드 (둥근 모서리) */
  --surface-2: #EFE8DD;
  /* 잉크 */
  --ink:       #2E2A25;   /* 웜 차콜 */
  --ink-soft:  #5C554C;
  --ink-dim:   #938B7E;
  /* 브랜드 */
  --brand:     #6B8F71;   /* 세이지 (메인) */
  --brand-2:   #88A98D;
  --accent:    #C8755A;   /* 테라코타 */
  --accent-2:  #D9A441;   /* 허니 골드 (2차) */
  /* 라인/하이라이트 */
  --rule:      #E5DDD0;
  --hl:        rgba(107,143,113,0.20);   /* 세이지 형광펜 */
  --radius:    18px;       /* 둥근 카드 기본 반경 */
  /* 타이포 */
  --display:   "Pretendard Variable",Pretendard,"Noto Sans KR",sans-serif;
  --sans:      "Pretendard Variable",Pretendard,"Noto Sans KR",sans-serif;
  --mono:      "JetBrains Mono",ui-monospace,monospace;
  --pad: 60px 84px;
}
```

## 폰트 규칙
- 제목: **Pretendard 700/800** — 둥글고 친근하게(과하게 무겁지 않게).
- 본문: Pretendard 400/500, 줄간 넉넉히(1.6+).
- 숫자: Pretendard 700 + tabular-nums.

## 레이아웃 시그널
- **둥근 카드**(border-radius `--radius` 18–24px) + 부드러운 그림자(낮은 대비).
- 넉넉한 여백, 큰 줄간. 아이콘은 둥근 배경 칩 안에.
- 액센트는 세이지(메인)·테라코타(포인트) 소프트하게. 강한 대비 지양.
- 차트: 둥근 막대(borderRadius 크게), 파스텔 톤 단색.

## 차트 팔레트
`#6B8F71` · `#C8755A` · `#A8B58C` · `#D9A441` (웜·소프트)
text=`#5C554C`, grid=`#E5DDD0`.

## 모션
부드럽게. `opacity 0→1 + y 14px + 약한 scale 0.98→1`, ease out, stagger 0.06s. 급격한 효과 금지.

## 금지
- 다크 배경, 네온, 채도 높은 원색.
- 날카로운 직각 카드(둥근 모서리 정체성 훼손).
- **특정 기관/조직명 하드코딩** — `[기관명]`·`[팀명]` 플레이스홀더.
