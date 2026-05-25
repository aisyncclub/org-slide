# 프리셋: institutional — 기관 신뢰형 (Institutional)

> **스타일 정체성:** 공공·기관 발표용 **라이트·플랫·신뢰형**.
> 딥 인스티튜셔널 블루를 메인으로, 레드는 강조 1점만. 화려함보다 정직·명료.
> (색 근거: 공공기관 통합 CI/정부상징 계열의 딥블루·레드 체계 — 특정 기관명 비귀속, 범용)

## 톤 키워드
**신뢰 · 공공 · 정제 · 명료 · 안정**

라이트(백색) 베이스의 플랫·기관 신뢰형. 그라데이션·글로우 자제.
레드는 "강조 1점"으로만 — 면적을 넓게 쓰지 않는다(경고/위험 인상 방지).

## 컬러 팔레트

| 이름 | HEX | Pantone | 용도 |
|---|---|---|---|
| 인스티튜셔널 블루 | `#003764` | 2955C 계열 | 메인 (신뢰·안정) |
| 시그널 레드 | `#E4032E` | 1935C 계열 | 강조 1점 only |
| 뉴트럴 그레이 | `#575757` | Cool Gray 11C | 서브 |
| White | `#FFFFFF` | — | 베이스 |

## :root 토큰

```css
:root{
  /* 면 */
  --bg:        #FFFFFF;
  --surface:   #F4F6F9;   /* 카드/패널 */
  --surface-2: #EAEEF4;
  --paper-tint:#F8FAFC;
  /* 잉크 */
  --ink:       #0F1B2D;   /* 본문 강 (딥블루 계열) */
  --ink-soft:  #3A4A60;
  --ink-dim:   #6B7888;   /* 캡션/메타 */
  /* 브랜드 */
  --brand:     #003764;   /* 인스티튜셔널 블루 (메인) */
  --brand-2:   #1E5BA8;   /* 밝은 청 (보조/링크) */
  --brand-soft:#DDE7F2;   /* 블루 10% 틴트 */
  --accent:    #E4032E;   /* 시그널 레드 (강조 1점) */
  --accent-soft:#FCE3E8;
  --neutral:   #575757;
  /* 라인/하이라이트 */
  --rule:      #DBE1EA;
  --hl:        #CFE0F2;   /* 블루 형광펜 */
  /* 타이포 */
  --display:   "Noto Sans KR","Pretendard Variable",Pretendard,sans-serif;
  --sans:      "Pretendard Variable",Pretendard,"Noto Sans KR",-apple-system,sans-serif;
  --mono:      "JetBrains Mono",ui-monospace,monospace;
  /* 간격 */
  --pad: 56px 80px;
}
```

## 폰트 규칙
- 제목: **Noto Sans KR 900** 또는 Pretendard 800 — 굵고 또렷한 기관용 고딕.
- 본문: **Pretendard 400/500**.
- italic **금지**(기관 정제성). 수치는 mono 또는 Pretendard 700 + tabular-nums.

## 레이아웃 시그널
- 상단 **블루 4–6px 띠(top accent bar)** — 전 슬라이드 일관.
- head 좌측에 **심볼 마크 자리**(`.mark`) + "[기관명]" 플레이스홀더.
- 표지에 **4분할 메타 그리드**(일시/장소/주관/대상), 블루 키라인. 기관·부서·대상은 `[기관명]`·`[주관 부서]`·`[대상 직군]` 플레이스홀더로 둔다.
- KPI 카드: 백색 면 + 상단 블루 4px 보더 + 옅은 그림자.
- 구분선·키라인은 `--rule` 1px, 강조 키라인만 블루.

## 모션
절제된 `opacity 0→1 + translateY(16px→0)`, stagger 0.06s. orb/글로우/회전 금지.

## 금지
- 다크 배경, 네온, 과한 그라데이션
- 시그널 레드를 배경·큰 면적으로 사용
- **특정 기관명 하드코딩** — 실제 기관명은 입력받아 채우고, 샘플/기본값은 `[기관명]` 플레이스홀더.
- 캐주얼 이모지 남발(공공 문서 톤 유지)
