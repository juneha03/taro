---
name: 오늘의 타로
version: 2 (명지대학교 타로 디자인 팩 기준)
theme: light
base: shadcn/ui (base) · Next.js App Router · Tailwind v4
source: 명지대학교 타로 디자인 팩.fig (2026-11-07 내보냄)
colors:
  bg: "#F3F3F5"
  surface: "#FFFFFF"
  surface-sub: "#F6F6F8"
  text-primary: "#000000"
  text-secondary: "#4D4D4E"
  text-tertiary: "#979F9B"
  text-on-accent: "#000000"   # 팩 #FFFFFF → 대비 보완
  border: "#DCDCDD"
  accent: "#00D959"
  accent-strong: "#007A35"    # 팩 #00D959 → 대비 보완
  accent-soft: "#E6FAEF"
  accent-illust: "#00DE00"
  disabled: "#D7D7D7"
  danger: "#E5484D"
  danger-text: "#C62828"      # 대비 보완으로 추가
  inverse: "#232427"
typography:
  family: "Noto Sans KR"
  letter-spacing: "-2%"
rounded:
  input: 12px
  button-m: 14px
  button-l: 16px
  sheet: 20px
  chip: 22px (pill)
  result-card: 24px
  tarot-front: 10px
  tarot-back: 12px
layout:
  frame: 375 × 812
  gutter: 20px
  app-bar: 56px
components: [App Bar, Button, Input, Topic Chip, Privacy Notice, Tarot Card Back, Tarot Card Front, Deck Card, Result Card, Toast, Bottom Sheet, Icons]
---

# 오늘의 타로 — 디자인 가이드 v2

> 연회색 배경 위의 흰 라운드 카드, 연두 강조색 하나. 카드 그림이 주인공.

선배가 준 **「명지대학교 타로 디자인 팩」**을 기준으로 다시 쓴 가이드입니다. 팩의 색 · 글씨 · 간격 · 컴포넌트 값을 그대로 옮겼고, 팩에 없거나 고쳐야 하는 부분은 **[보완]**으로 표시했습니다. 기준 기획 문서는 [TARO_01_PRD](TARO_01_PRD.md) · [TARO_02_기능명세서](TARO_02_기능명세서.md) · [TARO_03_유저플로우](TARO_03_유저플로우.md) · [TARO_04_와이어프레임](TARO_04_와이어프레임.md)입니다.

## 0. v1에서 바뀐 것

| 항목 | v1 (레퍼런스 흑백) | v2 (디자인 팩) |
|---|---|---|
| 분위기 | 흰 종이 · 흑백 · 얇은 선 | 연회색 배경 + 흰 라운드 카드 + 연두 강조 |
| 강조색 | 보라 #5B3FA6 | 연두 #00D959 (글자는 #007A35) |
| 글꼴 | Pretendard + Geist Mono | **Noto Sans KR 하나**, 자간 -2% |
| 굵기 | 제목 600, 700 이상 금지 | 제목 **Bold(700)** |
| 모서리 | 6px 고정 | 요소별 12 · 14 · 16 · 20 · 22 · 24px |
| 카드 그림 | 자리 표시 그림 | **Rider-Waite-Smith(1909) 메이저 아르카나 22장** |
| 버튼 높이 | 48px 하나 | L 56px · M 48px |
| 카드 뽑기 | 버튼을 누르면 바로 결과 | **부채꼴 덱에서 직접 골라 뒤집기** (S-03-P · P2 · D 추가) |
| 결과 화면 주 버튼 | [이미지 저장] | **[결과 공유]** |
| 공유 글 머리 | ✦ | **🔮** |

## 1. 디자인 방향

- **연회색 바탕(#F3F3F5) 위에 흰 카드**를 올려 영역을 나눕니다. 선보다 면으로 구분합니다.
- 강조색은 **연두 하나**입니다. 주 버튼 · 선택 상태 · 카드 이름 · 카드 뒷면에만 씁니다.
- 화면에서 가장 화려한 것은 **카드 그림**입니다. 그 밖의 장식(그라디언트 · 일러스트 · 배경 패턴)은 넣지 않습니다.
- 레퍼런스(uibowl 타로 화면)에서는 **배경 · 카드 · 강조색의 구조만** 참고했습니다. 레퍼런스의 카드 그림 · 캐릭터 · 브랜드 요소는 쓰지 않습니다.

## 2. 색

### 2-1. 색 토큰

| 토큰 | 값 | 쓰는 곳 |
|---|---|---|
| `color/bg` | `#F3F3F5` | 화면 배경 |
| `color/surface` | `#FFFFFF` | 결과 카드, 입력칸, 보조 버튼, 바텀시트 |
| `color/surface-sub` | `#F6F6F8` | 개인정보 안내, 공유 글 상자 |
| `color/text/primary` | `#000000` | 제목, 해석 본문, 입력값 |
| `color/text/secondary` | `#4D4D4E` | 입력 라벨, 설명, 개인정보 안내, 미선택 칩 |
| `color/text/tertiary` | `#979F9B` | 도움말 · 애니메이션 안내처럼 **안 읽어도 되는** 보조 글자만 |
| `color/text/on-accent` | `#000000` **[보완]** | 연두 버튼 위 글자 |
| `color/border` | `#DCDCDD` | 입력칸 · 보조 버튼 · 미선택 칩 테두리 |
| `color/accent` | `#00D959` | 주 버튼 배경, 선택 칩 테두리, 카드 뒷면 선 |
| `color/accent-strong` | `#007A35` **[보완]** | 연두 **글자**(카드 이름 · 선택 칩 글자), 입력 포커스 테두리 |
| `color/accent-soft` | `#E6FAEF` | 선택 칩 배경, 카드 뒷면 원, 공유 글 템플릿 배경 |
| `color/accent-illust` | `#00DE00` | 스와이프 안내 일러스트(화살표 · "Swipe!")에만 |
| `color/disabled` | `#D7D7D7` | 비활성 버튼 배경 |
| `color/danger` | `#E5484D` | 오류 입력칸 테두리 |
| `color/danger-text` | `#C62828` **[보완]** | 오류 문구("날짜를 다시 확인해 주세요") |
| `color/inverse` | `#232427` | 토스트 배경, 바텀시트 뒤 어둡게(dim) |

### 2-2. 대비 보완 [보완]

팩의 값 몇 개는 WCAG 대비 기준에 못 미쳐서 아래처럼 바꿨습니다.

| 조합 | 팩 그대로 | 바꾼 것 | 대비 |
|---|---|---|---|
| 주 버튼 글자 | 흰색 on #00D959 = **1.9:1** | **검정** on #00D959 | 11.1:1 |
| 선택 칩 글자 | #00D959 on #E6FAEF = **1.7:1** | **#007A35** on #E6FAEF | 5.0:1 |
| 카드 이름(Meta) | #00D959 on 흰색 = **1.9:1** | **#007A35** on 흰색 | 5.5:1 |
| 오락용 안내 | #979F9B on 흰색 = **2.7:1** | **#4D4D4E** | 8.4:1 |
| 오류 문구 | #E5484D on #F3F3F5 = 3.5:1 | **#C62828** | 5.1:1 |
| 입력 포커스 테두리 | #00D959 2px = 1.9:1 | **#007A35** 2px | 5.5:1 |

- 연두 **면**(버튼 배경 · 칩 테두리 · 카드 뒷면)은 #00D959 그대로 씁니다.
- 연두 **글자 · 얇은 선으로 상태를 알리는 곳**은 #007A35를 씁니다.
- `text/tertiary`(#979F9B)는 "탭한 카드가 가운데로 올라와요"처럼 몰라도 되는 안내에만 씁니다. **오락용 안내 · 개인정보 안내 · 오류 문구는 tertiary로 쓰지 않습니다.**
- 비활성 버튼(#D7D7D7 위 흰 글자 1.4:1)은 WCAG 예외(비활성 요소)라 팩대로 둡니다.

## 3. 글씨

### 3-1. 글꼴

- **Noto Sans KR** 하나만 씁니다. 모든 스타일 **자간 -2%**.
- Next.js에서는 `next/font/google`의 `Noto_Sans_KR`(weight 400 · 500 · 700)로 불러옵니다.
- v1의 Geist Mono(영문 라벨 · 로마 숫자)는 쓰지 않습니다. 로마 숫자도 Noto Sans KR로 씁니다(예: "XIX 태양").

### 3-2. 글씨 스타일 (`Taro/*`)

| 스타일 | 굵기 | 크기 / 줄 높이 | 쓰는 곳 |
|---|---|---|---|
| **Display** | Bold | 28 / 38 | 시작 화면 타이틀 "오늘의 타로" |
| **Title** | Bold | 22 / 32 | 화면 질문 "어떤 주제가 궁금한가요?", 카드 고르기 안내 |
| **Headline** | Bold | 18 / 26 | 앱바 제목, 카드 이름 "XIX 태양 · 사자자리" |
| **Body** | Regular | 16 / 26 | 해석 본문(가운데 정렬), 입력값, 설명 |
| **Body Bold** | Bold | 16 / 24 | L 버튼 |
| **Label** | Medium | 15 / 22 | M 버튼, 주제 칩, 토스트 |
| **Caption** | Regular | 13 / 19 | 개인정보 안내, 오락용 안내, 도움말 |
| **Caption Bold** | Bold | 13 / 19 | 입력 라벨, 결과 카드 제목 "지민님의 타로 · 커리어" |

- 해석 본문은 **Body 가운데 정렬, 3줄 · 90자 이내**입니다. 줄 사이 간격 2px.
- 선택된 주제 칩 글자는 Label 대신 **Bold 15 / 22**입니다.
- 한글 줄바꿈은 `word-break: keep-all`.

## 4. 간격 · 배치

### 4-1. 화면 틀

| 항목 | 값 |
|---|---|
| 화면 | 375 × 812 (결과 화면은 스크롤, 876까지) |
| 상태 표시줄 영역 | 위 44px |
| 홈 인디케이터 영역 | 아래 34px |
| 좌우 여백 | **20px** (내용 너비 335px) |
| 앱바 | 높이 56px, 좌우 16px, 뒤로 가기 아이콘 20px, 제목 Headline 가운데 |
| 하단 CTA 영역 | 위 12 · 좌우 20 · 아래 34px, L 버튼 1개 |

### 4-2. 간격 단위

팩은 4px 단위 위주에 일부 2px 단위를 씁니다.

| 값 | 쓰는 곳 |
|---|---|
| 2px | 해석 줄 사이 |
| 6px | 버튼 아이콘과 라벨 |
| 8px | 입력 라벨 ↔ 입력칸 ↔ 도움말 |
| 10px | 주제 칩 사이(가로 · 세로), 개인정보 아이콘 ↔ 글 |
| 11px | M 버튼 2개 사이 (162 + 11 + 162 = 335) |
| 12px | M 버튼 줄 사이 |
| 14px | 결과 화면 요소 사이, 바텀시트 안 |
| 16px | 입력 화면 요소 사이, 결과 카드 안 |
| 20px | 화면 좌우 여백, 카드 고르기 화면 요소 사이 |
| 24px | 시작 화면 요소 사이 |

### 4-3. 화면별 배치

- **S-01 시작:** 위아래 여백(spacer) 사이에 가운데 정렬. 카드 부채(앞면 3장 겹침) → "오늘의 타로"(Display) → 설명(Body, secondary) → [타로 시작](L Primary) → "※ 오락용 타로 · 정보는 저장 안 해요"(Caption).
- **S-02 내 정보 · 주제:** 앱바 "나에 대해 알려 주세요" → 이름 · 생년월일 입력 → **개인정보 안내(입력칸 바로 아래 고정)** → 전공 입력 → "어떤 주제가 궁금한가요?"(Title) → 주제 칩 3×2 → 하단 CTA [카드 한 장 뽑기].
- **S-03-P 카드 고르기:** 앱바 → "{주제}를 떠올리며 카드 한 장을 골라 주세요"(Title) → 부채꼴 덱 22장 → 스와이프 안내 → "좌우로 넘기고, 끌리는 카드를 탭하세요"(Caption, tertiary).
- **S-03-P2 카드 선택됨:** 고른 카드가 가운데로 올라오고(180×300, 연두 3px 선 + 연두 그림자) "선택한 카드를 뒤집어 볼게요".
- **S-03-D 카드 공개:** 앞면(208×348) → "XIX 태양이 나왔어요"(Title) → 0.4초 뒤 결과 화면.
- **S-03 결과:** 앱바 → 결과 카드 → M 버튼 2×2 → 개인정보 안내.

## 5. 모양 · 깊이

### 5-1. 모서리

| 대상 | 값 |
|---|---|
| 입력칸, 개인정보 안내, 토스트, 색 견본 | 12px |
| M 버튼 | 14px |
| L 버튼 | 16px |
| 바텀시트(위 모서리), 안내 시트 | 20px |
| 주제 칩 | 22px (높이 44의 절반 = 알약) |
| 결과 카드 | 24px |
| 타로 앞면 | 10px (160 너비 기준, 크기에 비례: 208 너비 → 13px) |
| 타로 뒷면 | 12px, 안쪽 선 8px (120 너비 기준) |
| 덱 카드 | 10.8px (108 너비 기준) |

### 5-2. 그림자

그림자는 **카드에만** 씁니다. 버튼 · 입력칸 · 결과 카드에는 그림자가 없습니다.

| 대상 | 값 |
|---|---|
| 타로 앞면 | `0 6px 16px rgba(0,0,0,0.12)` (크기에 비례) |
| 선택된 뒷면(S-03-P2) | `0 10px 28px rgba(0,217,89,0.35)` |

## 6. 컴포넌트

### 6-1. 아이콘

20 × 20px, 선 굵기 1.67px, 검정 선(lucide 스타일).

| 이름 | 쓰는 곳 |
|---|---|
| `icon/chevron-left` | 앱바 뒤로 가기 |
| `icon/lock` | 개인정보 안내 |
| `icon/download` | [이미지 저장] |
| `icon/share` | [결과 공유] |
| `icon/refresh` | [다시 뽑기] |
| `icon/home` | [처음으로] |
| `icon/copy` | 복사 |

- 주제 칩의 이모지(💼 💰 💕 🌿 📚 ✨)는 시안용입니다. 구현할 때는 SVG 아이콘으로 바꿉니다.

### 6-2. App Bar

375 × 56, 가로 배치, 좌우 16px, 간격 8px. [← 20px] [제목 Headline 가운데, 남는 너비 전부] [20px 빈칸]. 배경 없음(화면 배경이 비침).

### 6-3. Button

| 속성 | L | M |
|---|---|---|
| 크기 | 335 × 56 | 162 × 48 |
| 모서리 | 16px | 14px |
| 글씨 | Body Bold 16/24 | Label 15/22 |
| 아이콘 | 20px, 라벨과 6px | 20px, 라벨과 6px |

| Type | 배경 | 글자 | 테두리 |
|---|---|---|---|
| **Primary** | `accent` #00D959 | `text/on-accent` **#000000** [보완] | 없음 |
| **Secondary** | `surface` #FFFFFF | `text/primary` | 1px `border` |
| **Disabled** | `disabled` #D7D7D7 | #FFFFFF | 없음 |

- **Primary는 화면당 1개.** L은 화면의 주요 행동, M은 결과 화면 2×2 버튼.
- [카드 한 장 뽑기]는 이름 · 생년월일 · 주제 중 하나라도 비면 Disabled.
- **결과 화면:** [이미지 저장](Secondary · download) [결과 공유](**Primary** · share) / [다시 뽑기](Secondary · refresh) [처음으로](Secondary · home).
- 누름 상태 · 포커스 상태는 팩에 없습니다 → [보완] 누름: 배경을 8% 어둡게(`brightness(0.92)`), 포커스: `accent-strong` 2px 링 + 2px 간격.

### 6-4. Input

세로 배치, 간격 8px, 너비 335.

| 부분 | 값 |
|---|---|
| 라벨 | Caption Bold 13/19, `text/secondary` |
| 입력칸 | 높이 52, 흰 배경, 1px `border`, 모서리 12, 좌우 16 |
| 값 | Body 16/26, 입력 전 `text/tertiary`(자리 표시 글자), 입력 후 `text/primary` |
| 도움말 | Caption 13/19, **오류일 때만** 보임 |

| State | 테두리 | 도움말 |
|---|---|---|
| Default | 1px `border` | 없음 |
| Filled | 1px `border` | 없음 |
| Focused | **2px `accent-strong`** [보완] | 없음 |
| Error | 1.5px `danger` | "날짜를 다시 확인해 주세요" `danger-text` [보완] |

- 이름 최대 10자, 닉네임 권장(이미지 · 공유 글에 들어감). 생년월일은 실제 날짜만.
- 모든 입력칸 `autoComplete="off"`. 값은 화면 메모리에만 둡니다(아래 9장).

### 6-5. Topic Chip

105 × 44, 모서리 22, 3개씩 2줄, 간격 10(가로 · 세로). 하나만 고를 수 있습니다(shadcn `ToggleGroup type="single"`).

| State | 배경 | 테두리 | 글자 |
|---|---|---|---|
| Default | `surface` | 1px `border` | Label, `text/secondary` |
| Selected | `accent-soft` | 1.5px `accent` | **Bold 15/22, `accent-strong`** [보완] |

### 6-6. Privacy Notice

335 너비, `surface-sub` 배경, 모서리 12, 안쪽 위아래 14 · 좌우 16, 간격 10. [lock 20px] + Caption `text/secondary`. 문구는 기능명세서 원문 그대로:

> 입력한 이름 · 생년월일 · 전공은 해석을 만드는 데만 쓰고, 서버로 보내거나 저장하지 않아요. 창을 닫거나 [처음으로]를 누르면 바로 지워져요.

- S-02: **이름 · 생년월일 입력칸 바로 아래에 고정**. S-03: 버튼 아래.

### 6-7. Tarot Card

| 종류 | 크기 | 모양 |
|---|---|---|
| **Back** | 120 × 200 | 흰 배경, 2px `accent` 선, 모서리 12. 안쪽 8px에 1px `accent` 선(모서리 8). 가운데 64px 원(`accent-soft` + 1px `accent`) 안에 별(#1DBF5A, 30px). 위아래 8px 점 2개(`accent`) |
| **Front** | 160 × 268 | 카드 그림을 꽉 채움(FILL), 모서리 10, 그림자. 그림 아래 영문 이름이 그림 안에 있음 |
| **Deck card** | 108 × 180 | Back을 작게 줄인 것, 1.8px `accent` 선 |

- 카드 비율은 **500 × 836(약 3:5)**, 원본 그림 비율 그대로입니다. v1의 2:3이 아닙니다.
- 앞면은 **22장 중 무작위, 정방향만**.
- 뒷면 별 색 #1DBF5A는 팩에 토큰이 없는 값입니다 → [보완] 구현 시 `accent-strong` 대신 이 값을 `--tarot-star`로 따로 둡니다.

### 6-8. Result Card

335 × 534, 흰 배경, 모서리 24, 안쪽 위아래 28 · 좌우 24, 세로 간격 16, 가운데 정렬.

1. 제목 "지민님의 타로 · 커리어" — Caption Bold, `text/secondary`
2. 카드 앞면 160 × 268
3. Meta "XIX 태양 · 사자자리" — Headline, **`accent-strong`** [보완]
4. 해석 3줄 — Body 가운데, 줄 간격 2. 줄1 = 카드 × 주제(이름 포함), 줄2 = 별자리, 줄3 = 전공 계열(전공이 없거나 못 맞추면 숨김: `Show Major Line` 끔)
5. "※ 오락용 타로 해석입니다" — Caption, **`text/secondary`** [보완]

- 이 카드 영역이 그대로 **저장 이미지(1080 × 1350 PNG)**가 됩니다(F-5). 생년월일 · 전공 원문은 넣지 않습니다.

### 6-9. Toast

`inverse` 배경, 모서리 12, 안쪽 위아래 14 · 좌우 20, Label 흰 글자. 화면 아래 가운데, 2~3초.

| 상황 | 문구 |
|---|---|
| 이미지 저장 성공 | 이미지를 저장했어요 |
| 자동 복사 성공 | 결과를 복사했어요. 원하는 앱에 붙여 넣어 주세요 |

### 6-10. Bottom Sheet (대체 화면)

- 뒤 화면을 `inverse`로 어둡게 덮고, 아래에서 흰 시트가 올라옵니다. 시트 위 모서리 20, 안쪽 위 24 · 좌우 20 · 아래 34, 간격 16.
- 제목은 Headline. 마지막에 L Secondary [닫기].
- **이미지 저장 안 됨(인앱 브라우저):** "이미지를 길게 눌러 저장해 주세요" + 결과 카드 축소본(208 × 335).
- **복사 실패:** "아래 글을 길게 눌러 복사해 주세요" + `surface-sub` 상자(모서리 12, 안쪽 14)에 공유 글.

### 6-11. shadcn 컴포넌트 매핑

| 디자인 팩 | shadcn |
|---|---|
| Button | `Button` (variant: default = Primary, outline = Secondary; size: lg = L, default = M) |
| Input | `Field` + `FieldLabel` + `Input` + `FieldDescription` (`data-invalid` / `aria-invalid`) |
| Topic Chip | `ToggleGroup` + `ToggleGroupItem` (single) |
| Privacy Notice | `Alert` |
| Result Card | `Card` + `CardHeader` + `CardContent` + `CardFooter` |
| Toast | `toast`(base) / `sonner`(radix) |
| Bottom Sheet | `Drawer` (+ `DrawerTitle` 필수) |

## 7. 카드 뽑기 움직임 (F-3)

| 단계 | 움직임 |
|---|---|
| 진입 | 22장 뒷면이 아래 → 위로, 가운데부터 0.02초 간격(stagger) |
| 펼침 | 부채꼴, 반지름 430, 카드 간격 8° |
| 스와이프 | 바퀴(wheel) 하나만 회전, `quickTo` 0.45초. 놓으면 속도를 반영한 뒤 8° 단위로 맞춤 |
| 탭 | 고른 카드가 가운데로 0.5초(scale 1.7) → Y축 180° 뒤집기 0.6초 |
| 결과로 | 0.4초 뒤 결과 화면. 카드가 결과 카드 자리로 FLIP 0.5초 → 해석 줄 0.08초 간격으로 나타남 |

- `transform` · `opacity`만 움직입니다.
- 움직임 줄이기 설정(`prefers-reduced-motion`)이면 **4배속**으로 재생합니다.

## 8. 저장 · 공유

### 8-1. 저장 이미지 (F-5)

- 결과 카드 영역을 **1080 × 1350 PNG**로 기기 안에서 만듭니다(`html-to-image`, 폰트 로딩 후). 서버로 보내지 않습니다.
- 들어가는 것: 이름 · 주제 · 카드 그림 · 카드 이름 · 별자리 · 해석 3줄 · 오락용 안내 · 서비스 이름.
- 넣지 않는 것: 생년월일, 전공 원문.

### 8-2. 공유 (F-6)

순서: **기기 공유 메뉴 → (없으면) 자동 복사 → (실패하면) 바텀시트에 글 표시**. 공유 메뉴를 취소해도 결과 화면은 그대로입니다.

공유 글 템플릿:

```
🔮 {이름}님의 타로 · {주제}
{카드 이름} · {별자리}
{해석 3줄}
※ 오락용 타로 해석입니다
나도 한 장 뽑기 → {시작 링크}
```

- 생년월일 · 전공 원문 없음(PRD 원칙 2). 링크는 시작 화면이고, 이름 · 결과를 담지 않습니다(원칙 5).

## 9. 개인정보 · 문구 원칙

- 이름 · 생년월일 · 전공은 React 상태(메모리)에만 둡니다. localStorage · 쿠키 · URL · 분석 도구로 보내지 않습니다.
- [처음으로] → 정보 삭제 후 S-01. [다시 뽑기] → 정보는 유지하고 S-02 주제 선택부터.
- 해요체로 짧게. 건강 · 재물은 단정하지 않고 돌아볼 관점으로 씁니다. (✕ "돈을 벌게 됩니다" → ○ "지출 우선순위를 돌아볼 때예요")

## 10. 해야 할 것 · 하지 말 것

### 해야 할 것

- 배경은 `bg`, 영역은 흰 카드(`surface`)로 나누기
- 연두 면은 #00D959, 연두 글자 · 상태 선은 #007A35
- 주 버튼 글자는 검정
- Noto Sans KR 하나, 자간 -2%, 위 8개 스타일만
- 화면 좌우 20px, Primary 버튼은 화면당 1개
- 개인정보 안내는 S-02 입력칸 바로 아래 · S-03 버튼 아래에 원문 그대로
- 카드 그림은 원본 비율(500 × 836) 그대로, 정방향

### 하지 말 것

- 흰 글자를 연두(#00D959) 위에 쓰기
- 연두 #00D959로 글자 쓰기, #00DE00을 스와이프 안내 외에 쓰기
- `text/tertiary`로 꼭 읽어야 하는 안내(오락용 · 개인정보 · 오류) 쓰기
- 버튼 · 입력칸 · 결과 카드에 그림자 넣기
- 카드 그림을 자르거나 늘리기, 역방향으로 보여 주기
- 저장 이미지 · 공유 글에 생년월일 · 전공 원문 넣기
- 레퍼런스(uibowl)의 그림 · 캐릭터 · 브랜드 요소 쓰기

## 11. 코드 시작점

### 11-1. `app/globals.css` (Tailwind v4)

```css
@import "tailwindcss";

:root {
  /* shadcn 기본 변수 */
  --background: #f3f3f5;
  --foreground: #000000;
  --card: #ffffff;
  --card-foreground: #000000;
  --popover: #ffffff;
  --popover-foreground: #000000;
  --primary: #00d959;
  --primary-foreground: #000000;
  --secondary: #ffffff;
  --secondary-foreground: #000000;
  --muted: #f6f6f8;
  --muted-foreground: #4d4d4e;
  --accent: #e6faef;
  --accent-foreground: #007a35;
  --destructive: #e5484d;
  --border: #dcdcdd;
  --input: #dcdcdd;
  --ring: #007a35;

  /* 타로 추가 변수 */
  --text-tertiary: #979f9b;
  --accent-strong: #007a35;
  --accent-illust: #00de00;
  --disabled: #d7d7d7;
  --danger-text: #c62828;
  --inverse: #232427;
  --tarot-star: #1dbf5a;
}

@theme inline {
  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --color-card: var(--card);
  --color-card-foreground: var(--card-foreground);
  --color-popover: var(--popover);
  --color-popover-foreground: var(--popover-foreground);
  --color-primary: var(--primary);
  --color-primary-foreground: var(--primary-foreground);
  --color-secondary: var(--secondary);
  --color-secondary-foreground: var(--secondary-foreground);
  --color-muted: var(--muted);
  --color-muted-foreground: var(--muted-foreground);
  --color-accent: var(--accent);
  --color-accent-foreground: var(--accent-foreground);
  --color-destructive: var(--destructive);
  --color-border: var(--border);
  --color-input: var(--input);
  --color-ring: var(--ring);
  --color-text-tertiary: var(--text-tertiary);
  --color-accent-strong: var(--accent-strong);
  --color-accent-illust: var(--accent-illust);
  --color-disabled: var(--disabled);
  --color-danger-text: var(--danger-text);
  --color-inverse: var(--inverse);
  --color-tarot-star: var(--tarot-star);

  --font-sans: var(--font-noto-sans-kr), "Apple SD Gothic Neo", "Malgun Gothic", sans-serif;

  --radius-input: 12px;
  --radius-button-m: 14px;
  --radius-button-l: 16px;
  --radius-sheet: 20px;
  --radius-chip: 22px;
  --radius-result: 24px;
  --radius-tarot: 10px;
}

@theme {
  --shadow-xs: 0 0 #0000;
  --shadow-tarot: 0 6px 16px rgba(0, 0, 0, 0.12);
  --shadow-tarot-picked: 0 10px 28px rgba(0, 217, 89, 0.35);
}

@utility type-display { font-size: 28px; line-height: 38px; font-weight: 700; letter-spacing: -0.02em; }
@utility type-title { font-size: 22px; line-height: 32px; font-weight: 700; letter-spacing: -0.02em; }
@utility type-headline { font-size: 18px; line-height: 26px; font-weight: 700; letter-spacing: -0.02em; }
@utility type-body { font-size: 16px; line-height: 26px; font-weight: 400; letter-spacing: -0.02em; word-break: keep-all; }
@utility type-body-bold { font-size: 16px; line-height: 24px; font-weight: 700; letter-spacing: -0.02em; }
@utility type-label { font-size: 15px; line-height: 22px; font-weight: 500; letter-spacing: -0.02em; }
@utility type-caption { font-size: 13px; line-height: 19px; font-weight: 400; letter-spacing: -0.02em; word-break: keep-all; }
@utility type-caption-bold { font-size: 13px; line-height: 19px; font-weight: 700; letter-spacing: -0.02em; }

@layer base {
  * { @apply border-border outline-ring/50; }
  body { @apply bg-background text-foreground font-sans antialiased; }
}
```

### 11-2. 컴포넌트 variant 고칠 곳

| 파일 | 고칠 것 |
|---|---|
| `components/ui/button.tsx` | size `lg`: `h-14 w-full rounded-button-l type-body-bold`, `default`: `h-12 rounded-button-m type-label`. variant `outline`: `bg-card border-border text-foreground`. 비활성: `disabled:bg-disabled disabled:text-white disabled:opacity-100` |
| `components/ui/input.tsx` | `h-13 rounded-input px-4 bg-card type-body placeholder:text-text-tertiary focus-visible:border-2 focus-visible:border-accent-strong aria-invalid:border-destructive` |
| `components/ui/toggle-group.tsx` · `toggle.tsx` | `h-11 w-[105px] rounded-chip type-label text-muted-foreground data-[state=on]:bg-accent data-[state=on]:border-primary data-[state=on]:text-accent-strong data-[state=on]:font-bold` |
| `components/ui/card.tsx` | `rounded-result shadow-none px-6 py-7 gap-4` |
| `components/ui/alert.tsx` | 기본: `bg-muted border-0 rounded-input px-4 py-3.5 type-caption text-muted-foreground` |

## 12. 카드 그림 (Major Arcana 22장)

| 번호 | 이름 | 번호 | 이름 |
|---|---|---|---|
| 0 | The Fool (바보) | 11 | Justice (정의) |
| I | The Magician (마법사) | XII | The Hanged Man (매달린 사람) |
| II | The High Priestess (여사제) | XIII | Death (죽음) |
| III | The Empress (여황제) | XIV | Temperance (절제) |
| IV | The Emperor (황제) | XV | The Devil (악마) |
| V | The Hierophant (교황) | XVI | The Tower (탑) |
| VI | The Lovers (연인) | XVII | The Star (별) |
| VII | The Chariot (전차) | XVIII | The Moon (달) |
| VIII | Strength (힘) | XIX | The Sun (태양) |
| IX | The Hermit (은둔자) | XX | Judgement (심판) |
| X | Wheel of Fortune (운명의 수레바퀴) | XXI | The World (세계) |

- 그림: **Rider-Waite-Smith(1909)** 스캔, 500 × 836 JPEG 22장(디자인 팩 `images/`).
- 파일 이름은 `public/cards/00-the-fool.jpg` ~ `21-the-world.jpg`로 맞춥니다.

## 13. 정해지지 않은 것 (Known Gaps)

- **카드 그림 출처 [검토]** — 원화(1909)는 저작권이 끝난 것으로 알려져 있지만, 스캔 파일 출처("78 Tarot Cards 파일")의 사용 조건을 아직 확인하지 않았습니다. 확인 전까지 저장소(공개)에는 그림 파일을 올리지 않습니다.
- **주제 칩 아이콘** — 이모지를 대신할 SVG 아이콘 6개가 팩에 없습니다.
- **누름 · 포커스 상태** — 버튼 누름 · 포커스, 칩 포커스는 팩에 없어서 6-3의 [보완] 값을 임시로 씁니다.
- **다크 모드** — 팩에 없습니다. MVP 범위 밖.
- **개인정보 동의 체크 필요 여부** — PRD 미정 그대로.
- **이름 포함 안내** — PRD 리스크 대응("공유 · 저장 전에 이름이 들어간다는 것을 화면에서 보이게")에 해당하는 문구 · 위치가 팩에 없습니다.

## 14. Figma

- 디자인 파일: https://www.figma.com/design/bqKaOLNkHhLZxoYWZlBvRs — `화면 v2` · `컴포넌트 v2` 페이지가 이 가이드 기준입니다. `v1 … (보관)` 페이지는 이전 흑백 버전입니다.
