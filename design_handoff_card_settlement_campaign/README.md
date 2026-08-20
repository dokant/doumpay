# Handoff: 카드가맹점정산보호협회 카드매출 정산금 누락방지 캠페인 랜딩페이지

## Overview
카드가맹점정산보호협회가 2026년 8월 24일부터 서울 강남3구(강남·서초·송파)에서 착수하는
**"자영업자 카드매출 정산금 누락방지 캠페인"** 안내 및 참여 신청을 위한 단일 페이지 랜딩(SPA-style single scroll page).

핵심 목표
1. 카드결제 후 실제 입금이 누락되는 문제(정산 사각지대)를 소상공인에게 쉽게 설명
2. 캠페인 참여 프로세스를 신뢰감 있게 안내 (무료·계약 없음 강조)
3. 참여 신청을 **구글폼**(임베드 + 새 창)으로 수집

뉴스 원문: http://news9.co.kr/bbs/board.php?bo_table=04&wr_id=562

---

## About the Design Files
이 번들의 HTML 파일은 **디자인 레퍼런스**입니다 — 최종 룩/피지컬/인터랙션을 보여주는 프로토타입이며,
그대로 프로덕션에 붙여넣기 위한 코드가 아닙니다.

개발 시에는 아래 방침을 따르세요:
- **기존 코드베이스가 있는 경우** (React/Vue/Next 등): 해당 프레임워크의 컴포넌트/스타일 시스템 규칙에 맞춰
  이 HTML의 UI를 **재구현**하세요 (Tailwind, CSS Modules, styled-components 등 프로젝트 관례 사용).
- **신규 프로젝트인 경우**: 정적 랜딩 페이지 특성상 **Next.js (App Router) + Tailwind CSS**,
  또는 **Astro + Tailwind** 조합을 권장합니다. 페이지가 1개이므로 SSG로 배포하면 성능·SEO 유리.
- HTML을 그대로 배포하는 것도 가능하지만, 폼 URL 관리·수정 편의를 고려해 프레임워크 사용을 권장합니다.

---

## Fidelity
**High-fidelity (hifi).** 색상·타이포그래피·간격·인터랙션이 모두 확정된 픽셀-정확 목업입니다.
개발자는 아래 명세된 정확한 값(hex, px, font-weight 등)을 그대로 재현해야 합니다.

---

## Screens / Views

이 디자인은 **단일 스크롤 랜딩 페이지**이며 다음 섹션으로 구성됩니다.

### 1. Sticky Nav
- **Purpose**: 브랜드 인지 + 섹션 간 앵커 이동 + 최상단 신청 CTA
- **Layout**: sticky top, 좌우 24px 패딩, max-width 1200px, `justify-content: space-between`
- **Components**:
  - Brand mark: 34×34px, radius 9px, 그라디언트 `radial-gradient(120% 120% at 20% 20%, #F0A96A 0%, #D2691E 55%, #A9430E 100%)`, 텍스트 "소" (color `#FFF6E9`, weight 900, 14px)
  - Brand name: `카드가맹점정산보호협회` (800 / 16px / letter-spacing -.02em) + subtitle `Card Merchant Settlement Protection Association` (12px / muted)
  - Nav links (5개): 캠페인 소개 / 누락 유형 / 참여 절차 / 언론 보도 / 문의·신청 — 14px / 500 / `#3A322A`, hover `#A9430E`
  - CTA button "참여 신청": `background #1F1A14`, `color #FFF6E9`, `border-radius 999px`, padding `10px 16px`, **inline `font-size: 12px`**, hover `background #A9430E` + `translateY(-1px)`
  - Mobile (<780px): nav-links 숨김

### 2. Hero
- **Purpose**: 캠페인 요지 즉시 전달 + 주요 CTA
- **Layout**: 2-col grid `1.15fr .95fr`, gap 56px, 상단 padding 72px, 하단 100px. 모바일(<940px)은 1열
- **Components**:
  - Pill 배지: `2026년 8월 24일 · 강남3구 시범 시작`, 배경 `#F6DFC4`, 텍스트 `#A9430E`, 좌측 6px dot (`#D2691E` + `box-shadow 0 0 0 4px rgba(210,105,30,.18)`)
  - H1: 1문장, "사장님 <span accent>카드매출</span>,결재는 됐는데 정산은 어디 갔을까요?"
    - font: Noto Sans KR 900, size `clamp(34px, 5.4vw, 64px)`, letter-spacing `-0.035em`, line-height 1.2
    - `.accent`는 밑줄 하이라이트: `background: linear-gradient(180deg, transparent 62%, rgba(210,105,30,.35) 62%, ... 92%, transparent 92%)`
  - Lede 문단: `#3A322A`, 17px, max-width 52ch
  - Primary CTA "캠페인 참여 신청하기": `background #D2691E`, `color #FFF6E9`, radius 12px, padding `14px 22px`, `box-shadow 0 10px 24px -10px rgba(210,105,30,.6)`, hover `background #A9430E` + `translateY(-1px)`, 우측 화살표 SVG
  - Ghost CTA "자세히 알아보기": transparent bg, border `1px solid #D8C7A6`, hover `background #F5EDDE`
  - Meta strip 3항목: `100% 무료 · 회원가입비 없음` / `단말기 교체 요구하지 않음` / `지역 상인회와 협력 진행`
  - Hero visual: aspect-ratio 4/5, radius 24px, overflow hidden, box-shadow depth
    - 이미지 `assets/hero-cafe.jpg` object-fit cover
    - overlay gradient: `linear-gradient(180deg, transparent 55%, rgba(31,26,20,.5) 100%)`
    - Badge (좌하): kicker `Campaign 2026` (12px / opacity .85 / uppercase / tracking .08em) + title `사장님이 놓치고 있는 매출을 찾아드립니다` (20px / 800)
  - Stat float card (우상단, absolute): 260px, `background #FFFDF8`, border `1px solid #E7DBC5`, radius 16px, box-shadow depth
    - k: "공식 집계된 피해규모" (12px / 600 / muted)
    - v: "미집계 · 실태조사 착수" (20px / 900), "· 실태조사 착수" 부분 `#A9430E` / 13px
    - note: 설명 문구 (11px / muted)

### 3. Marquee Band
- **Purpose**: 정산 누락 관련 키워드를 리듬감 있게 반복 노출
- **Layout**: 전폭, `background #1F1A14`, `color #FFF6E9`, padding `14px 0`, 상하 1px border
- **Behavior**: `@keyframes slide` 30s linear infinite, `transform: translateX(0) → -50%` (같은 콘텐츠 2회 반복하여 seamless)
- **Content items** (한/영 조합, `<em>`은 `color #F6DFC4` / 800):
  - 망취소 NET-CANCEL
  - 중복결제 DOUBLE-CHARGE
  - 매입 미전송 VAN ERROR
  - 정산 지연 SETTLEMENT DELAY
  - 사장님이 놓치는 매출 UNCLAIMED SALES

### 4. What Is (정산 누락이란?)
- **Layout**: `background #FFFDF8`, 상하 1px border, 96px padding. 2-col `1fr 1fr` gap 56px. 모바일 <900px 1열.
- **Left**: 이미지 `assets/calculator.jpg`, aspect 5/4, radius 18px, box-shadow
- **Right**:
  - Eyebrow (좌측정렬): "카드매출 정산금 누락이란?" — 13px / 700 / `#A9430E` / letter-spacing .14em / uppercase
  - H2: "결제는 승인, 입금은 누락. 보이지 않는 사각지대." (2줄)
  - 본문 2문단 (16px, `#3A322A`)
  - Callout box: `background #F5EDDE`, dashed border `1px dashed #D8C7A6`, radius 14px, padding `20px 22px`, 15px 텍스트, `<b>` 부분은 `#A9430E`
    - 내용: "협회는 이번 캠페인에서 참여 가맹점의 결제/입금 내역을 대조하여 누락의 발생 유형·빈도·금액대를 파악하고, 결과를 토대로 제도 개선안을 정부·유관기관에 건의합니다."

### 5. Types (누락 발생 유형 3가지)
- **Layout**: 3-col grid, gap 20px. 모바일 <900px 1열.
- **Card style**: `background #FFFDF8`, border `1px solid #E7DBC5`, radius 18px, padding `28px 26px`, hover `translateY(-3px)` + box-shadow
- **Card content**:
  - Big serif number (44px / Nanum Myeongjo 800 / `#D2691E`): 01, 02, 03
  - H3 title
  - Body (15px / `#3A322A`)
  - Tag pill (배경 `#F6DFC4` / 텍스트 `#A9430E` / 12px / 700 / radius 999px / padding 5px 10px)
- **3 items**:
  1. **매입 자료 미전송** — VAN사 매입 자료가 카드사로 정상 전송되지 않는 경우 / Tag: `VAN · 매입 오류`
  2. **망취소 (통신장애 자동취소)** — 통신 장애로 시스템이 승인을 자동 취소 / Tag: `Net-Cancel · 망취소`
  3. **중복결제 인식 처리** — 정상 결제가 중복결제로 오인되어 취소·환불 / Tag: `Duplicate · 중복결제 오인`

### 6. Process (참여 절차 4단계)
- **Layout**: `background #F5EDDE`. 4-col grid, border `1px solid #D8C7A6`, radius 18px, `background #FFFDF8`, cell 사이 1px border-right. 모바일 <900px 2열, <560px 1열.
- **Step content**: (padding 32px 24px)
  - Step number 배지: 32×32 circle, `background #1F1A14`, `color #F6DFC4`, JetBrains Mono 800 14px
  - H3 (19px)
  - Body (14px / `#3A322A`)
- **4 steps**:
  01. 참여 신청 — 구글폼으로 매장 정보 접수
  02. 내역 대조 조사 — 결제 내역 vs 실제 입금 내역
  03. 확인·안내 — 누락 시 카드사·밴사 직접 확인 요청 절차 안내
  04. 제도 개선 건의 — 관계 기관 정책 제안

### 7. Trust Strip
- **Layout**: 3-col, gap 24px. 모바일 <780px 1열. Padding 56px.
- **Item**: 44×44 icon box (`background #F6DFC4`, `color #A9430E`, radius 12px) + h4(16/800) + p(14/muted)
- **3 items** (with Lucide-style stroke SVG icons):
  1. **100% 무료 · 별도 계약 없음** — Shield-check icon
  2. **지역 상인회와 협력** — Users icon
  3. **제도 개선까지** — Trending-up icon

### 8. Quote
- **Layout**: `background #F5EDDE`, padding 88px 0, max-width 820px, 중앙 정렬
- **Blockquote**: Nanum Myeongjo 400, size `clamp(22px, 2.6vw, 30px)`, line-height 1.5, letter-spacing -.02em, `#1F1A14`
  - `::before` "“" + `::after` "”" — Nanum Myeongjo 800, `#D2691E`, 3em size, vertical-align 조정 (before -.35em, after -.6em)
- **Cite**: "정충교 · 카드가맹점정산보호협회 협회장" — 14px / muted, 이름만 `#1F1A14` bold

### 9. Press
- **Layout**: max-width 960px 중앙. Press card 2-col `1.4fr 1fr` gap 36px, `background #FFFDF8`, border/radius/shadow. 모바일 <820px 1열.
- **Body 좌측**:
  - Source: "뉴스9 · 2026" (12px / 700 / `#A9430E` / uppercase / tracking .12em)
  - H3: "카드가맹점정산보호협회, 강남3구서 '카드매출 정산금 누락방지 캠페인' 착수"
  - 본문 요약
  - Link "뉴스9 원문 보기 →" — `#A9430E` 700, hover 밑줄 (external-link SVG 포함)
    - `href`: `http://news9.co.kr/bbs/board.php?bo_table=04&wr_id=562` (new tab)
- **Image 우측**: `assets/receipt.jpg`, cover, min-height 220px

### 10. Apply (문의·신청)
- **Layout**: `background #1F1A14`, `color #FFF6E9`. 상단 radial glow overlay. 2-col `.8fr 1.2fr` gap 32px. 모바일 <940px 1열.
- **Section head**: eyebrow `#F0B37A`, h2 `#FFF6E9`, p `#EADFC8`
- **Left — Info panel**:
  - `background rgba(255,255,255,.04)`, border `1px solid rgba(255,255,255,.1)`, radius 18px, padding 30px
  - Contact rows (4개): 36×36 icon box (`background rgba(240,169,106,.15)`, `color #F0B37A`, radius 10px) + k(12px muted uppercase) + v(15px `#FFF6E9` 600)
    - Phone icon: **010-7128-8192** (`tel:01071288192`)
    - Mail icon: **cirrus01@naver.com** (`mailto:`)  ⚠️ *현재 index.html에서는 Cloudflare email-protection으로 난독화되어 있으며, decoder 런타임이 없는 로컬에서는 `[email protected]` 라니명으로 보입니다. 재구현 시에는 일반 `mailto:` 링크로 교체 권장.*
    - Grid icon: 언론 문의 **jebo@news9.co.kr** (뉴스9 제보 라벨)  ⚠️ *상동 처리.*
    - Map-pin icon: 1차 시범 지역 **서울 강남구 · 서초구 · 송파구**
  - Note box: `background rgba(240,169,106,.08)`, dashed border, radius 12px, padding 16px, 13px 텍스트, `<b>` `#F0B37A`
- **Right — Form embed shell**:
  - `background #FFFDF8`, radius 18px, overflow hidden, deep box-shadow
  - Top bar: `background #F5EDDE`, padding 14px 20px, `border-bottom 1px solid #E7DBC5`
    - 좌측: 3개 dots (10px circle, colors `#E8A17A / #E8C87A / #E8CDA7`) + 라벨 "캠페인 참여 신청서" (12px / 700)
    - 우측: "새 창에서 열기 ↗" 링크 (12px / 700 / `#A9430E`)
  - iframe (`.form-frame`): width 100%, height 720px, border 0
    - `src`는 JS에서 주입 (아래 GOOGLE_FORM_URL 참조)
  - fallback: URL 미설정 시 표시 (현재는 URL 있어 숨김)

### 11. FAQ
- **Layout**: `background #FBF6EE`, max-width 820px, gap 12px 세로 스택
- **Item**: `<details>` — `background #FFFDF8`, border, radius 14px, overflow hidden
  - Summary: padding 20px 24px, 16px 700, 우측 `+` (22px / 900 / `#A9430E`), `[open]` 시 45deg 회전 (transition .2s)
  - Answer: padding `0 24px 22px`, 15px / `#3A322A` / line-height 1.7
- **4 questions** (첫 번째만 default open):
  1. 정말 무료인가요? 숨겨진 비용은 없나요?
  2. 강남3구가 아닌 지역도 신청할 수 있나요?
  3. 어떤 자료를 준비해야 하나요?
  4. 조사 결과는 어떻게 활용되나요?

### 12. Footer
- **Layout**: `background #1F1A14`, `color #B5A891`, padding `56px 0 40px`. 3-col grid `1.4fr 1fr 1fr` gap 36px. 모바일 <820px 1열.
- **Col 1**: Brand mark + name + 캠페인 요약 문구 (max-width 44ch)
- **Col 2 — 바로가기**: 4개 앵커 링크 (h4 14px `#FFF6E9`, 링크 13px)
- **Col 3 — Contact**: 전화 / 이메일 / 언론 문의
- **Legal bar**: 상단 border `1px solid rgba(255,255,255,.08)`, `justify-content: space-between`, 12px / `#7A6E5F`
  - Left: `© 2026 카드가맹점정산보호협회 · All rights reserved.`
  - Right: `본 페이지는 카드매출 정산금 누락방지 캠페인 안내용으로 제작되었습니다.`

---

## Interactions & Behavior

### Navigation
- Nav 링크와 CTA는 모두 **앵커** (`#what`, `#types`, `#process`, `#press`, `#apply`)
- `html { scroll-behavior: smooth }` 로 부드러운 스크롤
- Nav는 sticky, `backdrop-filter: saturate(1.4) blur(10px)`, `background rgba(251,246,238,.85)`

### Google Form 처리 (핵심 로직)
```js
const GOOGLE_FORM_URL = "https://forms.gle/f4QKDgAzptZafcrA6";

// 초기화
if (GOOGLE_FORM_URL) {
  const embedUrl = GOOGLE_FORM_URL.includes("?")
    ? GOOGLE_FORM_URL + "&embedded=true"
    : GOOGLE_FORM_URL + "?embedded=true";
  frame.src = embedUrl;      // iframe에 임베드 모드로 로드
  frame.style.display = 'block';
  openNew.href = GOOGLE_FORM_URL; // "새 창에서 열기" 링크
  fallback.style.display = 'none';
} else {
  // URL 미설정 시 fallback UI 표시
  frame.style.display = 'none';
  fallback.style.display = 'block';
  openNew.style.display = 'none';
}
```
- `forms.gle` 단축 URL은 브라우저가 실제 `docs.google.com/forms/...` 로 리다이렉트
- `?embedded=true` 파라미터로 구글폼 임베드 UI 활성화 (헤더/푸터 축소)
- "새 창에서 열기" 버튼은 원본 URL(embedded 파라미터 없이)로 새 탭 이동

### Reveal on Scroll
```js
const io = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('in');
      io.unobserve(e.target);
    }
  });
}, { threshold: 0.12 });
document.querySelectorAll('.reveal').forEach(el => io.observe(el));
```
- `.reveal` 초기: `opacity 0; transform: translateY(14px)`
- `.reveal.in`: `opacity 1; transform: translateY(0)`
- Transition: `opacity .7s ease, transform .7s ease`

### Hover / Active states
- 모든 primary CTA: `translateY(-1px)` + 색상 변화 (`.15s ease`)
- Type card: `translateY(-3px)` + box-shadow 등장
- Nav CTA / Primary CTA hover 색: `#A9430E`

### Marquee
- 무한 슬라이드 (30s linear infinite). `prefers-reduced-motion` 대응은 미구현 — **개발 시 추가 권장**
  ```css
  @media (prefers-reduced-motion: reduce) {
    .band-track { animation: none; }
  }
  ```

### FAQ Accordion
- 순수 `<details>`/`<summary>` 사용 (JS 불필요)
- Summary `.plus`가 `[open]` 시 `rotate(45deg)` 애니메이션

### Responsive breakpoints
- 940px: hero 1열, apply 1열
- 900px: what-grid 1열, types 1열, steps 2열
- 820px: press-card 1열, footer 1열
- 780px: nav-links 숨김, trust-grid 1열
- 620px: hero-meta의 `.hide-sm` 항목 숨김
- 560px: steps 1열

---

## State Management

정적 페이지로 실제 상태 관리 필요 없음. 다만 React/Vue로 재구현 시 다음이 필요할 수 있습니다:

- `GOOGLE_FORM_URL` — 환경변수(`NEXT_PUBLIC_GOOGLE_FORM_URL` 등)로 분리 권장
- FAQ 아이템 배열 — 데이터 분리
- 이미지 경로 — CDN/next/image 최적화 적용
- Nav 활성 섹션 하이라이트(선택) — IntersectionObserver로 현재 뷰포트 섹션 감지

폼 제출 결과는 구글이 처리하므로 클라이언트 측 상태 관리 불필요.

---

## Design Tokens

### Colors
| Token | Value | Usage |
|---|---|---|
| `--bg` | `#FBF6EE` | 페이지 기본 배경 (warm cream) |
| `--bg-2` | `#F5EDDE` | 섹션 대체 배경 |
| `--paper` | `#FFFDF8` | 카드/폼 배경 |
| `--ink` | `#1F1A14` | 본문 텍스트, dark 섹션 배경 |
| `--ink-2` | `#3A322A` | 서브 텍스트 |
| `--muted` | `#7A6E5F` | 캡션/부가 정보 |
| `--line` | `#E7DBC5` | 기본 구분선 |
| `--line-2` | `#D8C7A6` | 강조 구분선/보더 |
| `--brand` | `#D2691E` | 브랜드 오렌지 (primary) |
| `--brand-2` | `#A9430E` | 다크 오렌지 (hover/accent 텍스트) |
| `--brand-soft` | `#F6DFC4` | 브랜드 배경 톤 (pill, tag) |
| `--accent` | `#2E5D4E` | 신뢰 그린 (선언은 있으나 현재 미사용) |
| `--danger` | `#B44A2A` | 경고 (선언은 있으나 현재 미사용) |
| Dark inline: `#FFF6E9` | 다크 섹션 위 텍스트 (크림) |
| Dark inline: `#B5A891` | 다크 섹션 위 서브 텍스트 |
| Dark inline: `#F0B37A` | 다크 섹션 위 브랜드 강조 |
| Dark inline: `#EADFC8` | 다크 섹션 위 본문 |

### Spacing scale (실제 사용값)
- 컨테이너 좌우 padding: `24px`
- 섹션 상하 padding: `96px` (기본), `88px` (quote), `56px` (trust, footer)
- 카드 내부 padding: `28px 26px` (type), `32px 24px` (step), `30px` (apply info)
- 그리드 gap: `20px / 24px / 32px / 36px / 56px`
- max-width: `1200px` (기본), `960px`, `820px` (좁은 콘텐츠)

### Typography
- **본문**: `"Noto Sans KR", system-ui, -apple-system, "Apple SD Gothic Neo", sans-serif`
  - Weights used: 300 / 400 / 500 / 700 / 800 / 900
- **세리프 강조**: `"Nanum Myeongjo", serif` (h2/따옴표/타입 카드 번호)
- **모노스페이스**: `"JetBrains Mono", ui-monospace, monospace` (스텝 번호, marquee `<em>`, 표 숫자)
  - `font-feature-settings: "tnum" 1` (숫자 폭 통일)

Type scale:
| Element | Size | Weight | Letter-spacing |
|---|---|---|---|
| H1 | `clamp(34px, 5.4vw, 64px)` | 900 | -0.035em |
| H2 | `clamp(26px, 3.4vw, 40px)` | 800 | -0.02em |
| H3 | `clamp(18px, 2vw, 22px)` | 800 | -0.02em |
| Body | 16px | 400 | — |
| Hero lede | `clamp(16px, 1.4vw, 18px)` | 400 | — |
| Section head p | 17px | 400 | — |
| Eyebrow | 13px | 700 | 0.14em, uppercase |
| Small caption | 12–14px | 500–600 | — |
| Body line-height | 1.65 | | |
| Heading line-height | 1.2 | | |

### Border radius
- `--radius: 18px` (기본 카드/이미지)
- `9px` — brand mark
- `10px` — small icon box
- `12px` — icon box (medium), button, apply-note
- `14px` — callout, faq item
- `16px` — stat float
- `24px` — hero visual
- `999px` — pill / tag / nav-cta

### Shadows
- `--shadow`: `0 1px 0 rgba(31,26,20,.04), 0 20px 40px -20px rgba(120,70,20,.18)` — 기본 카드
- Hero visual: `0 1px 0 rgba(31,26,20,.04), 0 20px 40px -20px rgba(120,70,20,.18)`
- Primary button: `0 10px 24px -10px rgba(210,105,30,.6)`
- Stat float: `0 20px 40px -20px rgba(31,26,20,.25)`
- Form shell: `0 30px 60px -20px rgba(0,0,0,.4)` (다크 섹션 위)

### Transitions
- 버튼/카드 hover: `transform .12–.15s ease`, `background .2s`, `box-shadow .2s`
- FAQ plus 회전: `.2s`
- Reveal: `opacity .7s ease, transform .7s ease`

---

## Assets

모든 이미지는 **CC / Public Domain 라이선스**(PickPik, Public Domain Pictures)로 확보되었으며 초상권·상표권 이슈 없음.

| File | Description | Source License |
|---|---|---|
| `assets/hero-cafe.jpg` | 히어로 — 빈 카페 카운터 인테리어 (인물·특정 페이 로고 없음) | PickPik / CC |
| `assets/calculator.jpg` | What Is 섹션 — 계산기와 서류 (매출·입금 대조 은유, 인물 없음) | PickPik / CC |
| `assets/receipt.jpg` | Press 섹션 — 영수증 이미지 | Public Domain Pictures |
| `assets/hero-terminal.jpg` | (구버전, 미사용) | — |
| `assets/market.jpg` | (구버전, 미사용) | — |
| `assets/merchant.jpg` | (구버전, 미사용 — 초상권 이슈로 교체됨) | — |
| `assets/cafe-terminal.jpg` | (구버전, 미사용) | — |

**아이콘**: 모두 인라인 SVG (Lucide-style stroke). 별도 파일 없음.
- Nav CTA: arrow-right
- Trust strip: shield-check / users / trending-up
- Apply info: phone / mail / grid / map-pin
- 외부 링크: external-link (↗)

**폰트**: Google Fonts CDN
```html
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@300;400;500;700;900&family=Nanum+Myeongjo:wght@400;700;800&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
```
프로덕션 배포 시 self-host 또는 `next/font` 사용 권장.

---

## Google Form Integration

- **폼 URL**: `https://forms.gle/f4QKDgAzptZafcrA6`
- **임베드 방식**: URL 뒤에 `?embedded=true` 붙여 iframe `src`로 로드
- **새 창 버튼**: 원본 URL (임베드 파라미터 없이) 사용
- **폼 응답 수집**: 구글폼 관리자 콘솔에서 확인 (별도 백엔드 불필요)

---

## Contact Info (페이지에 노출된 실제 값 — 그대로 사용)

| Type | Value |
|---|---|
| 협회 대표 전화 | 010-7128-8192 |
| 협회 이메일 (푸터 · 일반 문의) | **on@news0.net** |
| 협회 이메일 (푸터 · 언론 문의) | **biz@news0.net** |
| 협회 이메일 (apply 섹션 · 난독화됨) | cirrus01@naver.com |
| 언론 제보 (apply 섹션 · 난독화됨) | jebo@news9.co.kr |
| 1차 시범 지역 | 서울 강남구 · 서초구 · 송파구 |
| 캠페인 시작일 | 2026-08-24 |

---

## Files in this handoff

- `index.html` — 전체 랜딩페이지 (HTML + CSS + JS 인라인). 참고용 프로토타입.
- `assets/hero-cafe.jpg` — 히어로 이미지 (사용 중)
- `assets/calculator.jpg` — What Is 섹션 이미지 (사용 중)
- `assets/receipt.jpg` — Press 섹션 이미지 (사용 중)
- 구버전 이미지들은 실제 페이지에서 참조되지 않으므로 필요 시 제거 가능

---

## Implementation Checklist (권장 순서)

- [ ] 프로젝트 스캐폴딩 (Next.js/Astro 등) + Tailwind 셋업
- [ ] Design tokens 등록 (Tailwind config `theme.extend.colors` 등)
- [ ] Google Fonts 로드 (또는 `next/font`)
- [ ] 이미지 assets 이관 + `next/image` 최적화 적용
- [ ] 섹션별 컴포넌트 분리: `<Nav>`, `<Hero>`, `<Marquee>`, `<WhatIs>`, `<Types>`, `<Process>`, `<Trust>`, `<Quote>`, `<Press>`, `<Apply>`, `<FAQ>`, `<Footer>`
- [ ] `GOOGLE_FORM_URL`을 환경변수로 분리
- [ ] IntersectionObserver 기반 reveal 애니메이션
- [ ] `prefers-reduced-motion` 대응 (marquee, reveal)
- [ ] 접근성: 스킵 링크, ARIA landmark, iframe `title`, 대비 검증
- [ ] SEO: `<meta description>`, OG 태그, sitemap
- [ ] 반응형 QA (940 / 900 / 820 / 780 / 620 / 560 브레이크포인트)
- [ ] Lighthouse ≥ 95 목표
