# 프리셋: consulting — 컨설팅 데이터형 (Consulting Mono)

> **스타일 정체성:** 차콜 + 단일 액센트(앰버), 표·차트 고밀도, 정연한 그리드.
> "창의성보다 명료함" — 전략 보고·IR·데이터 중심. (2026 트렌드: 엔터프라이즈 클래리티)

## 톤 키워드
**정연 · 신뢰 · 데이터 · 명료 · 전문**

화이트 베이스 + 차콜 잉크 + 앰버 단일 액센트. 표/차트가 빽빽하되 정리되게, tabular 숫자 정렬.

## 컬러 팔레트

| 이름 | HEX | 용도 |
|---|---|---|
| 차콜 | `#1F2933` | 메인(헤드라인·바) |
| 슬레이트 | `#3E4C59` | 본문·서브 |
| 앰버 | `#E0A100` | 단일 강조 |
| 스틸 블루 | `#4A6B8A` | 차트 2차 시리즈 |

## :root 토큰

```css
:root{
  /* 면 */
  --bg:        #FFFFFF;
  --surface:   #F4F5F7;   /* 패널 */
  --surface-2: #E9ECF0;
  /* 잉크 */
  --ink:       #1F2933;   /* 차콜 */
  --ink-soft:  #3E4C59;   /* 슬레이트 */
  --ink-dim:   #7B8794;
  /* 브랜드 */
  --brand:     #1F2933;   /* 차콜 (메인) */
  --brand-2:   #4A6B8A;   /* 스틸 블루 (보조/2차 시리즈) */
  --accent:    #E0A100;   /* 앰버 (단일 강조) */
  --accent-2:  #B45309;   /* 딥 앰버 (경고/대비) */
  /* 라인/하이라이트 */
  --rule:      #D7DCE2;
  --hl:        rgba(224,161,0,0.20);   /* 앰버 형광펜 */
  /* 타이포 */
  --display:   "Pretendard Variable",Pretendard,"Noto Sans KR",sans-serif;
  --sans:      "Pretendard Variable",Pretendard,"Noto Sans KR",sans-serif;
  --mono:      "JetBrains Mono",ui-monospace,monospace;
  --pad: 52px 76px;   /* 데이터 밀도용 약간 좁게 */
}
```

## 폰트 규칙
- 제목: **Pretendard 800** — 또렷하고 정연하게.
- 본문/표: Pretendard 400/500, 소형 사이즈도 가독.
- **수치: mono 또는 Pretendard 700 + `font-variant-numeric: tabular-nums`**(자릿수 정렬 필수).

## 레이아웃 시그널
- 상단 차콜 얇은 띠 + 섹션 번호. 좌측 라벨/우측 데이터의 정연한 2단.
- KPI·표·차트가 한 슬라이드에 2–3개 공존(고밀도). 그리드 라인 또렷.
- 앰버는 핵심 수치/추세선 1곳에만 — "여기를 봐" 신호.
- small-multiples(작은 차트 여러 개) 권장.

## 차트 팔레트
`#1F2933` · `#E0A100` · `#4A6B8A` · `#9AA5B1` (차콜+앰버+스틸+그레이, 단색)
text=`#3E4C59`, grid=`#D7DCE2`.

## 모션
미니멀·또렷하게. `opacity 0→1 + y 10px`, 빠른 stagger 0.04s. 화려한 효과 금지(전문성).

## 금지
- 네온, 파스텔, 과한 그라데이션·장식.
- 앰버 남용(강조는 슬라이드당 1곳 원칙).
- **특정 기관/조직명 하드코딩** — `[조직명]` 플레이스홀더.
