# 프리셋: knih — 국립보건연구원 / 공공기관

> 근거: 국립보건연구원은 자체 CI가 없고 **대한민국 정부상징(GOV.KR) 통합 CI**를 따른다.
> 색상은 국립보건연구원 공식 기관상징(CI) 페이지 + 정부상징 디자인 가이드 기준.
> (출처: nih.go.kr 기관상징 / 행안부 정부상징체계 디자인 가이드 2017)

## 톤 키워드
**신뢰 · 과학 · 공공 · 정제 · 명료**

라이트(백색) 베이스의 플랫·기관 신뢰형. 화려함보다 정직·명료. 그라데이션·글로우 자제.
정부적색은 "강조 1점"으로만 — 면적을 넓게 쓰지 않는다(경고/위험 인상 방지).

## 공식 컬러 (정부상징)

| 이름 | HEX | Pantone | RGB |
|---|---|---|---|
| 정부청색 GOK Blue | `#003764` | 2955C | 0, 55, 100 |
| 정부적색 GOK Red | `#E4032E` | 1935C | 228, 3, 46 |
| 정부회색 GOK Gray | `#575757` | Cool Gray 11C | 87, 87, 87 |
| White | `#FFFFFF` | — | 255,255,255 |

## :root 토큰

```css
:root{
  /* 면 */
  --bg:        #FFFFFF;
  --surface:   #F4F6F9;   /* 카드/패널 */
  --surface-2: #EAEEF4;   /* 보조 면 */
  --paper-tint:#F8FAFC;
  /* 잉크 */
  --ink:       #0F1B2D;   /* 본문 강 (정부청 계열 딥) */
  --ink-soft:  #3A4A60;
  --ink-dim:   #6B7888;   /* 캡션/메타 */
  /* 브랜드 */
  --brand:     #003764;   /* 정부청색 (메인) */
  --brand-2:   #1E5BA8;   /* 밝은 청 (보조/링크) */
  --brand-soft:#DDE7F2;   /* 청색 10% 틴트 */
  --accent:    #E4032E;   /* 정부적색 (강조 1점 only) */
  --accent-soft:#FCE3E8;
  --gov-gray:  #575757;
  /* 라인/하이라이트 */
  --rule:      #DBE1EA;
  --hl:        #CFE0F2;   /* 청색 형광펜 */
  /* 타이포 */
  --display:   "Noto Sans KR","Pretendard Variable",Pretendard,sans-serif;
  --sans:      "Pretendard Variable",Pretendard,"Noto Sans KR",-apple-system,sans-serif;
  --mono:      "JetBrains Mono",ui-monospace,monospace;
  /* 간격 */
  --pad: 56px 80px;
}
```

## 폰트 규칙
- 제목: **Noto Sans KR 900** 또는 Pretendard 800 — 굵고 또렷한 기관용 고딕. (정부상징체 사용 가능 시 우선)
- 본문: **Pretendard 400/500**.
- italic **금지**(기관 정제성). 수치는 mono 또는 Pretendard 700 + tabular-nums.

## 레이아웃 시그널
- 상단 **정부청색 4px 띠(top accent bar)** — 전 슬라이드 일관.
- head 좌측에 **정부상징 마크 자리**(태극 원형 도트 `.mark`) + "국립보건연구원 / 질병관리청".
- 표지에 **4분할 메타 그리드**(일시/장소/주관/대상), 청색 키라인.
- KPI 카드: 백색 면 + 상단 정부청 4px 보더 + 옅은 그림자.
- 구분선·키라인은 `--rule` 1px, 강조 키라인만 청색.

## 모션
절제된 `opacity 0→1 + translateY(16px→0)`, stagger 0.06s. orb/글로우/회전 금지.

## 금지
- 다크 배경, 네온, 과한 그라데이션
- 정부적색을 배경·큰 면적으로 사용
- 캐주얼 이모지 남발(공공 문서 톤 유지)
