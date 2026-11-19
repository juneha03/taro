---
name: 오늘의 타로
theme: light
base: shadcn/ui (base) · style nova · Next.js App Router · Tailwind v4
colors:
  background: "#fafafa"
  card: "#ffffff"
  foreground: "#171717"
  body: "#4d4d4d"
  muted-foreground: "#666666"
  placeholder: "#a8a8a8"
  disabled: "#c9c9c9"
  border: "#ebebeb"
  primary: "#171717"
  primary-foreground: "#ffffff"
  primary-active: "#2e2e2e"
  mystic: "#5b3fa6"
  mystic-soft: "#f1edfa"
  destructive: "#c62828"
  tarot-back: "#171717"
typography:
  sans: "Pretendard Variable (한글 · 본문 · 제목)"
  mono: "Geist Mono (영문 라벨 · 로마 숫자 · 날짜 숫자)"
rounded:
  sm: 4px
  md: 6px
  lg: 6px
  xl: 6px
  card-art: 8px
  pill: 9999px
spacing: 4px grid
components: [Button, Field, Input, ToggleGroup, Alert, Card, Badge, Separator, Dialog, Toast, Spinner]
---

# 오늘의 타로 — 디자인 가이드

> 흰 종이 위에 인쇄한 타로 카드 한 장

이 문서는 레퍼런스 디자인 가이드(흑백 · 얇은 선 · 활자 중심)를 **타로카드 모바일 웹서비스**에 맞게 바꾼 것입니다. 기획 문서 [TARO_01_PRD](TARO_01_PRD.md) · [TARO_02_기능명세서](TARO_02_기능명세서.md) · [TARO_03_유저플로우](TARO_03_유저플로우.md) · [TARO_04_와이어프레임](TARO_04_와이어프레임.md)을 기준으로 합니다. 구현은 Next.js + Tailwind v4 + shadcn/ui를 전제로 합니다.

## 1. 디자인 방향

| 레퍼런스에서 가져온 것 | 타로 서비스에 맞게 바꾼 것 |
|---|---|
| 거의 흰 종이 배경(#fafafa), 거의 검은 글자(#171717) | 그대로. 카드 그림이 화면의 유일한 "그림"이 되도록 나머지는 흑백 |
| 장식 색 없음 | **보라 한 가지(Mystic #5b3fa6)만** 허용. 선택된 주제 · 별자리 · 카드 테두리 강조에만 씀 |
| 그림자 대신 얇은 선(hairline) | 그대로. 카드 · 입력칸 · 보조 버튼 모두 1px 선 |
| 6px 모서리 | 그대로. 타로 카드 그림만 8px |
| ▲ 삼각형 브랜드 마크 | **✦ 별 마크**로 바꿈. 서비스 이름 · 로딩 · 공유 글 머리에 씀 |
| 터미널 글꼴(Geist Mono)로 영문 대문자 라벨 | 로마 숫자(XIX) · 영문 라벨(TODAY'S TAROT) · 날짜 숫자에만. **한글 라벨에는 쓰지 않음** |
| 데스크톱 1280px, 64px 큰 제목 | **모바일 우선.** 최대 너비 440px, 제목 최대 32px |
| 마케팅 페이지(로고 띠, 3단 그리드) | 쓰지 않음. 화면 3개(S-01~S-03)가 세로 한 줄로 흐름 |

한 줄 원칙: **조용한 흑백 화면에서 카드 한 장만 빛나게.** 꾸밈보다 읽기 · 안심(개인정보 안내) · 공유가 먼저입니다.

## 2. 색

### 2-1. 색 토큰

| 이름 | 값 | shadcn 변수 | 쓰는 곳 |
|---|---|---|---|
| Paper | `#fafafa` | `--background` | 페이지 배경 |
| Card White | `#ffffff` | `--card` · `--popover` | 결과 카드, 입력칸, 대화상자 |
| Ink | `#171717` | `--foreground` · `--primary` | 제목, 주 버튼 배경, 카드 뒷면 |
| Body | `#4d4d4d` | `--body` (추가) | 해석 본문, 설명 글 |
| Stone | `#666666` | `--muted-foreground` | 안내문, 도움말, 오락용 안내 |
| Smoke | `#a8a8a8` | `--placeholder` (추가) | 입력칸 예시 글자 |
| Ash | `#c9c9c9` | `--disabled` (추가) | 비활성 버튼 글자 |
| Hairline | `#ebebeb` | `--border` · `--input` | 모든 1px 선 |
| Wash | `#f4f4f4` | `--muted` · `--secondary` · `--accent` | 보조 버튼 눌림, 안내 상자 배경 |
| Mystic | `#5b3fa6` | `--mystic` (추가) · `--ring` | 선택된 주제, 별자리 배지 글자, 포커스 링 |
| Mystic Soft | `#f1edfa` | `--mystic-soft` (추가) | 선택된 주제 배경, 별자리 배지 배경 |
| Error | `#c62828` | `--destructive` | 생년월일 오류 문구 · 입력칸 테두리 |

### 2-2. 색 규칙

- 글자 색은 **Ink → Body → Stone** 3단계만 씁니다. 회색을 새로 만들지 않습니다.
- 보라(Mystic)는 **"지금 고른 것"** 표시에만 씁니다. 버튼 배경, 큰 면, 제목 글자에는 쓰지 않습니다.
- 빨강(Error)은 입력 오류에만 씁니다. 해석 내용(건강 · 재물 등)에 경고 색을 쓰지 않습니다. 해석은 겁주지 않습니다(PRD 원칙 4).
- 그라디언트는 쓰지 않습니다. 레퍼런스의 무지개 그라디언트는 가져오지 않았습니다.
- 대비: Ink/Paper 17.2:1, Body/White 8.5:1, Stone/White 5.7:1, Stone/Wash 5.2:1, Mystic/White 7.8:1, Mystic/Mystic Soft 6.7:1. 모두 WCAG AA(4.5:1) 이상입니다.

## 3. 글씨

### 3-1. 글꼴

| 글꼴 | 변수 | 쓰는 곳 | 대체 글꼴 |
|---|---|---|---|
| **Pretendard Variable** | `--font-sans` | 한글 · 모든 제목 · 본문 · 버튼 | system-ui, Apple SD Gothic Neo, Malgun Gothic |
| **Geist Mono** | `--font-mono` | 로마 숫자(XIX), 영문 대문자 라벨, 날짜 숫자, 서비스 영문 표기 | ui-monospace, Consolas |

- 레퍼런스의 Geist Sans는 한글 글자가 없어서 Pretendard로 바꿨습니다(무료 · SIL OFL). Next.js에서는 `next/font/local`로 불러옵니다.
- Geist Mono는 `next/font/google` 또는 `geist` 패키지로 불러옵니다.
- 한글은 대문자가 없으므로 **한글 라벨에 Mono · 대문자 · 넓은 자간을 쓰지 않습니다.**

### 3-2. 글씨 크기

| 역할 | 크기 / 줄 높이 | 굵기 | 자간 | Tailwind 유틸리티 | 예 |
|---|---|---|---|---|---|
| display | 32px / 1.2 | 600 | -0.02em | `type-display` | 오늘의 타로 (S-01) |
| title | 22px / 1.3 | 600 | -0.01em | `type-title` | 나에 대해 알려 주세요 (S-02) |
| card-name | 20px / 1.3 | 600 | -0.01em | `type-card-name` | 태양 |
| body-lg | 17px / 1.6 | 400 | 0 | `type-reading` | 해석 3줄 |
| body | 15px / 1.5 | 400 | 0 | `type-body` | 설명 글, 버튼 |
| label | 14px / 1.4 | 500 | 0 | `type-label` | 입력칸 이름, 주제 칩 |
| caption | 13px / 1.5 | 400 | 0 | `type-caption` | 개인정보 안내, 오락용 안내 |
| eyebrow (Mono) | 11px / 1.5 | 500 | 0.08em, 대문자 | `type-eyebrow` | TODAY'S TAROT, XIX |

- 레퍼런스의 400~450 가는 제목은 한글에서 흐리게 보여서 **제목은 600**으로 올렸습니다. 700 이상은 쓰지 않습니다.
- 한글은 줄 높이 1.0이면 글자가 겹치므로 **제목도 최소 1.2**를 씁니다.
- 해석 3줄(`type-reading`)은 17px로, 화면에서 가장 편하게 읽히는 크기로 둡니다. 한 줄 최대 약 30자, 3줄 · 90자 이내(PRD 원칙 3).
- 한글 줄바꿈은 `word-break: keep-all`로 단어 중간에서 끊지 않습니다.

## 4. 간격 · 배치

### 4-1. 간격 단위 (4px 그리드)

| 토큰 | 값 | Tailwind | 쓰는 곳 |
|---|---|---|---|
| 1 | 4px | `gap-1` | 아이콘과 글자 |
| 2 | 8px | `gap-2` | 주제 칩 사이, 배지 안쪽 |
| 3 | 12px | `gap-3` | 버튼 2개 사이, 라벨과 입력칸 |
| 4 | 16px | `gap-4` · `px-4` | 화면 좌우 여백, 카드 안쪽 여백 |
| 5 | 20px | `gap-5` | 입력칸 묶음 사이 |
| 6 | 24px | `gap-6` | 화면 안 큰 묶음 사이 |
| 8 | 32px | `gap-8` | 제목과 본문 묶음 사이 |
| 10 | 40px | `pt-10` | 화면 맨 위 여백 |

### 4-2. 화면 틀

- **모바일 우선.** 기준 화면 360~430px. 내용 최대 너비 `max-w-[440px] mx-auto`. 데스크톱에서도 가운데 한 줄로 보여 줍니다.
- 좌우 여백 16px(`px-4`), 위 40px, 아래는 `pb-[max(24px,env(safe-area-inset-bottom))]`.
- 세로 흐름은 `flex flex-col gap-*`로만 만듭니다. `space-y-*`는 쓰지 않습니다(shadcn 규칙).
- 상단 바는 없습니다. S-02만 왼쪽 위에 뒤로 가기(←) 아이콘 버튼을 둡니다.
- 주 버튼은 화면 아래쪽에 둡니다. 입력이 길어지면 `sticky bottom-0`으로 [카드 한 장 뽑기]를 붙입니다.
- 가로 스크롤이 생기면 안 됩니다(360px에서 확인).

## 5. 모양 · 깊이

### 5-1. 모서리

| 대상 | 값 | Tailwind 클래스 (shadcn nova) |
|---|---|---|
| 작은 표시 | 4px | `rounded-sm` |
| 메뉴 항목 | 6px | `rounded-md` |
| 버튼 · 입력칸 · 주제 칩 | 6px | `rounded-lg` (값을 6px로 고정) |
| 결과 카드 · 대화상자 | 6px | `rounded-xl` (값을 6px로 고정) |
| 알림(toast) | 6px | `rounded-2xl` (값을 6px로 고정) |
| 타로 카드 그림 | 8px | `rounded-card-art` (추가) |
| 배지(별자리 · 주제) | 9999px | `rounded-4xl` |

- 버튼 · 카드에는 6px보다 큰 모서리를 쓰지 않습니다. 둥근 알약 모양은 배지에만 씁니다.

### 5-2. 깊이

- **그림자 대신 얇은 선.** 결과 카드 테두리는 레퍼런스의 겹선 기법을 씁니다: `0 0 0 1px rgba(0,0,0,0.08), 0 0 0 2px #fafafa`
- 보조 버튼 · 입력칸: `0 0 0 1px #ebebeb`
- 그림자(drop shadow)는 **타로 카드 그림 하나에만** 허용합니다: `0 8px 24px rgba(23,23,23,0.12)`. 화면에서 카드만 떠 보이게 하려는 예외입니다.

| 층 | 이름 | 값 | 쓰는 곳 |
|---|---|---|---|
| 0 | Paper | `#fafafa` | 페이지 |
| 1 | Card White | `#ffffff` + 겹선 | 결과 카드, 입력칸 |
| 2 | Ink | `#171717` | 카드 뒷면, 주 버튼 |

## 6. 컴포넌트

shadcn 규칙을 따릅니다: **이미 있는 컴포넌트와 variant를 먼저 쓰고**, `className`은 배치에만 씁니다. 색 · 글씨를 `className`으로 덮어쓰지 않습니다.

### 6-1. 컴포넌트 고르기

| 필요한 것 | shadcn 컴포넌트 | 화면 · 기능 |
|---|---|---|
| 주 버튼 · 보조 버튼 | `Button` | 모든 화면 |
| 이름 · 생년월일 · 전공 입력 | `FieldGroup` + `Field` + `FieldLabel` + `Input` + `FieldDescription` | S-02 · F-2 |
| 주제 6개 중 하나 | `ToggleGroup` (single) + `ToggleGroupItem` | S-02 · F-2 |
| 개인정보 안내 | `Alert` | S-02 · S-03 · 원칙 1 |
| 결과 카드 | `Card` + `CardHeader` + `CardTitle` + `CardContent` + `CardFooter` | S-03 · F-4 |
| 별자리 · 주제 표시 | `Badge` | S-03 |
| 구분선 | `Separator` | S-03 |
| "길게 눌러 저장/복사" 대체 화면 | `Dialog` (+ `DialogTitle`) | F-5 · F-6 실패 시 |
| 저장 · 복사 완료 알림 | `toast` (base) / `sonner` (radix) | F-5 · F-6 |
| 이미지 만드는 중 | `Spinner` + `Button disabled` | F-5 |

### 6-2. 버튼

| variant | 모양 | 높이 · 여백 | 쓰는 곳 |
|---|---|---|---|
| `default` (주) | Ink 배경 · 흰 글자 · 6px | **48px** · 좌우 20px · 전체 너비 | [타로 시작] [카드 한 장 뽑기] [이미지 저장] |
| `outline` (보조) | 투명 배경 · Body 글자 · 1px Hairline | 48px · 좌우 20px | [결과 공유] [다시 뽑기] |
| `ghost` (낮음) | 배경 · 선 없음 · Stone 글자 | 44px | [처음으로] |
| `icon` | 투명 · 44×44px 터치 영역 | `size-11` | ← 뒤로 가기 |

- 손가락 터치를 위해 **모든 버튼은 최소 44px 높이**입니다. 레퍼런스의 32~36px 버튼보다 키웠습니다.
- 한 화면에 `default` 버튼은 **한 줄에 하나**만 둡니다. S-03은 [이미지 저장](default) + [결과 공유](outline)을 한 줄 2칸, [다시 뽑기](outline) + [처음으로](ghost)를 그 아래 한 줄에 둡니다.
- 상태:
  - 누름: 배경 `--primary-active` (#2e2e2e), `active:translate-y-px`
  - 비활성: 배경 `#ebebeb` · 글자 `#c9c9c9` · `disabled` 속성. [카드 한 장 뽑기]는 이름 · 생년월일 · 주제가 다 차기 전까지 비활성(F-2).
  - 포커스: `ring-2 ring-ring ring-offset-2` (Mystic 보라)
  - 처리 중: `<Button disabled><Spinner data-icon="inline-start" />이미지 만드는 중</Button>`. `isLoading` 같은 속성은 없습니다.
- 아이콘은 `data-icon="inline-start"`로 넣고 크기 클래스를 붙이지 않습니다.

### 6-3. 입력 (S-02)

```tsx
<FieldGroup>
  <Field>
    <FieldLabel htmlFor="name">이름 (닉네임 OK)</FieldLabel>
    <Input id="name" maxLength={10} autoComplete="off" placeholder="지민" />
  </Field>
  <Field data-invalid={birthError || undefined}>
    <FieldLabel htmlFor="birth">생년월일</FieldLabel>
    <Input id="birth" inputMode="numeric" autoComplete="off"
      placeholder="2004.08.03" aria-invalid={birthError || undefined} />
    {birthError && <FieldDescription>날짜를 다시 확인해 주세요</FieldDescription>}
  </Field>
  <Field>
    <FieldLabel htmlFor="major">전공 (선택)</FieldLabel>
    <Input id="major" autoComplete="off" placeholder="경영학과" />
  </Field>
</FieldGroup>
```

- 입력칸 높이 48px, 흰 배경, 1px Hairline, 6px 모서리, 글자 16px(아이폰 확대 방지).
- 생년월일은 숫자만 받고 `YYYY.MM.DD`로 점을 자동으로 넣습니다. 숫자는 Geist Mono로 보여 줍니다(`font-mono tabular-nums`).
- 오류는 `Field`에 `data-invalid`, `Input`에 `aria-invalid`로 표시합니다. 빨간 테두리 + 아래 문구 "날짜를 다시 확인해 주세요".
- **개인정보 보호:** 모든 입력칸에 `autoComplete="off"`. `<form>`은 서버로 보내지 않고(`onSubmit`에서 `preventDefault`), 값은 React 상태에만 둡니다. localStorage · 쿠키 · 주소창(URL)에 넣지 않습니다(기능명세서 "데이터와 개인정보").

### 6-4. 주제 선택 (S-02)

```tsx
<ToggleGroup type="single" value={topic} onValueChange={setTopic}
  className="grid grid-cols-3 gap-2">
  <ToggleGroupItem value="career">💼 커리어</ToggleGroupItem>
  <ToggleGroupItem value="money">💰 재물</ToggleGroupItem>
  <ToggleGroupItem value="love">💕 연애</ToggleGroupItem>
  <ToggleGroupItem value="health">🌿 건강</ToggleGroupItem>
  <ToggleGroupItem value="study">📚 학업</ToggleGroupItem>
  <ToggleGroupItem value="general">✨ 종합</ToggleGroupItem>
</ToggleGroup>
```

- 3칸 × 2줄, 칸 높이 48px, 간격 8px.
- 기본: 흰 배경 + 1px Hairline + Body 글자.
- 선택: Mystic Soft 배경 + 1px Mystic 선 + Mystic 글자(`data-[state=on]` 변형으로 컴포넌트 variant에 넣음).
- 반복문으로 `Button`을 만들어 직접 선택 상태를 관리하지 않습니다(shadcn 규칙: 2~7개 선택지는 `ToggleGroup`).

### 6-5. 개인정보 안내 (S-02 · S-03)

```tsx
<Alert>
  <LockIcon />
  <AlertDescription>
    입력한 이름 · 생년월일 · 전공은 해석을 만드는 데만 쓰고, 서버로 보내거나 저장하지 않아요.
    창을 닫거나 [처음으로]를 누르면 바로 지워져요.
  </AlertDescription>
</Alert>
```

- Wash(#f4f4f4) 배경, 선 없음, 13px Stone 글자, 6px 모서리, 안쪽 여백 12px.
- S-02는 **입력칸 바로 아래**, S-03은 버튼 아래에 둡니다(PRD 리스크 대응).
- 문구는 기능명세서 원문 그대로 씁니다. 줄이지 않습니다.

### 6-6. 타로 카드 그림

- 비율 **2:3**(예: 너비 200px × 높이 300px), 모서리 8px, 유일한 그림자 허용.
- 뒷면: Ink(#171717) 바탕 + 가운데 흰 ✦ 별 마크 + 1px 안쪽 흰 선(inset 8px).
- 앞면: 카드 그림 + 아래에 로마 숫자(Mono eyebrow) · 카드 이름(`type-card-name`).
- 정방향만 씁니다(MVP).
- 그림은 직접 만들었거나 사용 허가가 분명한 것만 씁니다(PRD 리스크 · 미정). 확정 전에는 흑백 선 그림 자리 표시(placeholder)를 씁니다.

### 6-7. 뒤집기 효과 (F-3)

| 항목 | 값 |
|---|---|
| 시간 | **600ms** (기능명세서: 1초 이내) |
| 움직임 | Y축 180° 회전, `ease-[cubic-bezier(0.2,0.8,0.2,1)]` |
| 구현 | `perspective-[1000px]` + `transform-3d` + `backface-hidden` 앞 · 뒷면 2장 |
| 움직임 줄이기 설정 | `motion-reduce:` 일 때 회전 없이 200ms 서서히 나타나기 |

- 뒤집는 동안 버튼은 비활성입니다. 한 번에 한 장만 뽑습니다.
- 반짝임 · 파티클 같은 효과는 넣지 않습니다.

### 6-8. 결과 카드 (S-03 · F-4)

```tsx
<Card id="result-card">
  <CardHeader>
    <p className="type-eyebrow">TODAY'S TAROT</p>
    <CardTitle>{name}님의 타로</CardTitle>
    <div className="flex gap-2">
      <Badge variant="secondary">{topicLabel}</Badge>
      <Badge variant="mystic">{zodiacSymbol} {zodiacName}</Badge>
    </div>
  </CardHeader>
  <CardContent className="flex flex-col items-center gap-4">
    <TarotCard card={card} />
    <Separator />
    <p className="type-reading">{line1}<br />{line2}{line3 && <><br />{line3}</>}</p>
  </CardContent>
  <CardFooter>
    <p className="type-caption">※ 오락용 타로 해석입니다</p>
  </CardFooter>
</Card>
```

- 흰 배경 + 겹선 테두리, 6px 모서리, 안쪽 여백 20px.
- 순서: 이름 · 주제 → 카드 그림 → 카드 이름 · 별자리 → 해석 3줄 → 오락용 안내(와이어프레임 S-03).
- 해석이 2줄(전공 없음)이어도 카드 높이가 크게 흔들리지 않게 `min-h`를 둡니다.
- **생년월일 · 전공 원문은 카드에 넣지 않습니다.** 별자리 이름과 전공 계열 문장만 보입니다(PRD 원칙 2).
- `Badge`에 `mystic` variant를 추가합니다: Mystic Soft 배경 + Mystic 글자.

### 6-9. 알림 · 대체 화면 (F-5 · F-6)

| 상황 | 컴포넌트 | 문구 |
|---|---|---|
| 이미지 저장 성공 | toast (2초) | 이미지를 저장했어요 |
| 자동 복사 성공 | toast (3초) | 결과를 복사했어요. 원하는 앱에 붙여 넣어 주세요 |
| 이미지 저장 안 됨 | `Dialog` + 이미지 | 이미지를 길게 눌러 저장해 주세요 |
| 복사 실패 | `Dialog` + 글 상자 | 아래 글을 길게 눌러 복사해 주세요 |
| 생년월일 오류 | `FieldDescription` | 날짜를 다시 확인해 주세요 |

- toast는 화면 아래 가운데, Ink 배경 + 흰 글자, 6px 모서리.
- `Dialog`에는 반드시 `DialogTitle`을 넣습니다(보이지 않게 하려면 `sr-only`).
- 공유 · 저장 버튼 근처에 "결과 이미지 · 공유 글에 이름이 들어가요. 닉네임을 써도 돼요"를 caption으로 보여 줍니다(PRD 리스크).

## 7. 화면별 구성

### S-01 시작 (F-1)

- 위에서부터: eyebrow `TODAY'S TAROT` → 제목 "오늘의 타로"(`type-display`) → 카드 뒷면(2:3, 너비 160px) → 설명 2줄(Body) → [타로 시작](default, 전체 너비) → caption "※ 오락용 타로 · 정보는 저장 안 해요".
- 화면 높이 안에 모두 들어오게 세로 가운데 정렬합니다.

### S-02 내 정보 · 주제 (F-2)

- ← 뒤로 가기 → 제목 "나에 대해 알려 주세요" → 입력 3개 → "어떤 주제가 궁금한가요?"(`type-label`) → 주제 칩 3×2 → 개인정보 `Alert` → [카드 한 장 뽑기](default, 아래 고정).

### S-03 맞춤 해석 결과 (F-4~F-7)

- 결과 카드 → 이름 안내 caption → [이미지 저장][결과 공유] → [다시 뽑기][처음으로] → 개인정보 `Alert`.
- [처음으로]는 모든 상태를 지우고 S-01로 갑니다. 다시 S-02에 오면 입력칸이 비어 있어야 합니다(F-7).

## 8. 저장 이미지 (1080 × 1350, F-5)

화면의 결과 카드를 그대로 이미지로 만듭니다. 화면 크기와 상관없이 아래 크기로 고정합니다.

| 요소 | 위치 · 크기 |
|---|---|
| 배경 | Paper #fafafa, 안쪽 여백 72px |
| 카드 틀 | 흰 배경 + 2px Hairline, 모서리 12px |
| 머리 | eyebrow `TODAY'S TAROT` 28px Mono · "{이름}님의 타로 · {주제}" 48px 600 |
| 카드 그림 | 가운데, 440 × 660px, 모서리 16px |
| 카드 이름 · 별자리 | 44px 600 · 별자리 배지 32px |
| 해석 | 38px / 1.6, Body 색, 최대 3줄 |
| 오락용 안내 | 26px Stone "※ 오락용 타로 해석입니다" |
| 바닥 | "✦ 오늘의 타로" 26px · 서비스 주소(시작 링크) |

- 넣지 않는 것: 생년월일, 전공 원문, 날짜 · 시각.
- 만드는 방법: 숨겨진 1080×1350 DOM을 그려 `html-to-image`(`toPng`)로 PNG로 만듭니다. 폰트가 다 불러와진 뒤(`document.fonts.ready`) 그립니다. 서버로 보내지 않고 기기 안에서 만듭니다.

## 9. 공유 글 (F-6)

```
✦ {이름}님의 타로 · {주제}
{카드 이름} · {별자리}
{해석 3줄}
※ 오락용 타로 해석입니다
나도 한 장 뽑기 → {시작 링크}
```

- 와이어프레임의 🔮 대신 서비스 마크 ✦를 머리에 씁니다(둘 중 하나로 통일. 미정이면 🔮 유지 가능).
- 시작 링크에는 이름 · 결과를 넣지 않습니다(`?name=` 같은 주소 금지, PRD 원칙 5).

## 10. 쓰는 말 (문구 규칙)

- 해요체로 짧게. "~할 때예요", "~돌아볼 때예요".
- 단정 금지: ✕ "돈을 벌게 됩니다" → ○ "지출 우선순위를 돌아볼 때예요". 건강 · 재물은 특히 조심합니다.
- 이름 호칭은 "{이름}님".
- 버튼은 동작으로: [타로 시작] [카드 한 장 뽑기] [이미지 저장] [결과 공유] [다시 뽑기] [처음으로]. 기획 문서의 이름을 바꾸지 않습니다.

## 11. 접근성

- 터치 영역 최소 44×44px.
- 포커스 링은 숨기지 않습니다(Mystic 2px).
- 카드 그림에 `alt="{카드 이름} 카드"`.
- 뒤집기 후 해석 영역에 `aria-live="polite"`로 결과를 읽어 줍니다.
- 색만으로 상태를 알리지 않습니다: 선택된 주제는 색 + 선 굵기, 오류는 색 + 문구.

## 12. 해야 할 것 · 하지 말 것

### 해야 할 것

- 글자는 Ink · Body · Stone 3단계만 쓰기
- 보라(Mystic)는 선택 상태 · 별자리 · 포커스에만 쓰기
- 버튼 · 카드 · 입력칸 모서리는 6px, 배지만 알약 모양
- 깊이는 1px 얇은 선으로, 그림자는 타로 카드 그림에만
- 버튼 · 입력칸 높이 48px(최소 44px)
- 한글 제목은 600 굵기, 줄 높이 1.2 이상, `keep-all` 줄바꿈
- 개인정보 안내는 S-02 · S-03 두 곳에 원문 그대로
- shadcn 컴포넌트와 variant 먼저, `className`은 배치에만
- 세로 간격은 `flex flex-col gap-*`
- 색은 의미 토큰(`bg-primary`, `text-muted-foreground`)으로

### 하지 말 것

- 보라 외의 장식 색, 그라디언트, 별 · 반짝이 배경 넣기
- 해석 내용에 빨강 · 경고 아이콘 쓰기
- 한글에 Mono · 대문자 · 넓은 자간 쓰기
- 700 이상 굵은 제목, 6px보다 큰 버튼 · 카드 모서리
- 입력값을 localStorage · 쿠키 · URL에 넣기, `autoComplete` 켜 두기
- 결과 이미지 · 공유 글에 생년월일 · 전공 원문 넣기
- `space-y-*`, `bg-blue-500` 같은 원색 클래스, `dark:` 직접 덮어쓰기
- `Button`을 반복해 주제 선택 만들기(→ `ToggleGroup`)
- 레퍼런스 브랜드의 이름 · ▲ 마크 · 로고 쓰기

## 13. 코드 시작점

### 13-1. shadcn 프로젝트 만들기

nova 스타일을 고릅니다: 6px 모서리, 얇은 선 위주, 촘촘한 컨트롤이 이 가이드와 가장 가깝습니다. 버튼 · 입력 높이는 48px로 따로 키웁니다.

```bash
npx shadcn@latest init --base base --preset nova --template next --name taro-app --no-monorepo -y
npx shadcn@latest add button field input toggle-group alert card badge separator dialog toast spinner
```

### 13-2. `app/globals.css` (Tailwind v4)

```css
@import "tailwindcss";

:root {
  /* shadcn 기본 변수 */
  --background: #fafafa;
  --foreground: #171717;
  --card: #ffffff;
  --card-foreground: #171717;
  --popover: #ffffff;
  --popover-foreground: #171717;
  --primary: #171717;
  --primary-foreground: #ffffff;
  --secondary: #f4f4f4;
  --secondary-foreground: #171717;
  --muted: #f4f4f4;
  --muted-foreground: #666666;
  --accent: #f4f4f4;
  --accent-foreground: #171717;
  --destructive: #c62828;
  --border: #ebebeb;
  --input: #ebebeb;
  --ring: #5b3fa6;
  --radius: 6px;

  /* 타로 서비스 추가 변수 */
  --body: #4d4d4d;
  --placeholder: #a8a8a8;
  --disabled: #c9c9c9;
  --primary-active: #2e2e2e;
  --mystic: #5b3fa6;
  --mystic-soft: #f1edfa;
  --tarot-back: #171717;
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

  --color-body: var(--body);
  --color-placeholder: var(--placeholder);
  --color-disabled: var(--disabled);
  --color-primary-active: var(--primary-active);
  --color-mystic: var(--mystic);
  --color-mystic-soft: var(--mystic-soft);
  --color-tarot-back: var(--tarot-back);

  --font-sans: var(--font-pretendard), system-ui, "Apple SD Gothic Neo", "Malgun Gothic", sans-serif;
  --font-mono: var(--font-geist-mono), ui-monospace, Consolas, monospace;

  /* 모서리: nova 컴포넌트 클래스에 고정 */
  --radius-sm: 4px;
  --radius-md: 6px;
  --radius-lg: 6px;
  --radius-xl: 6px;
  --radius-2xl: 6px;
  --radius-3xl: 6px;
  --radius-4xl: 9999px;
  --radius-card-art: 8px;
}

@theme {
  /* 얇은 선만 쓰는 깊이 */
  --shadow-xs: 0 0 #0000;
  --shadow-hairline: 0 0 0 1px #ebebeb;
  --shadow-card: 0 0 0 1px rgba(0, 0, 0, 0.08), 0 0 0 2px #fafafa;
  --shadow-tarot: 0 8px 24px rgba(23, 23, 23, 0.12);
}

@utility type-display { font-size: 32px; line-height: 1.2; font-weight: 600; letter-spacing: -0.02em; word-break: keep-all; }
@utility type-title { font-size: 22px; line-height: 1.3; font-weight: 600; letter-spacing: -0.01em; word-break: keep-all; }
@utility type-card-name { font-size: 20px; line-height: 1.3; font-weight: 600; letter-spacing: -0.01em; }
@utility type-reading { font-size: 17px; line-height: 1.6; font-weight: 400; color: var(--body); word-break: keep-all; }
@utility type-body { font-size: 15px; line-height: 1.5; font-weight: 400; color: var(--body); word-break: keep-all; }
@utility type-label { font-size: 14px; line-height: 1.4; font-weight: 500; }
@utility type-caption { font-size: 13px; line-height: 1.5; font-weight: 400; color: var(--muted-foreground); word-break: keep-all; }
@utility type-eyebrow { font-family: var(--font-mono); font-size: 11px; line-height: 1.5; font-weight: 500; letter-spacing: 0.08em; text-transform: uppercase; }

@layer base {
  * { @apply border-border outline-ring/50; }
  body { @apply bg-background text-foreground font-sans antialiased; }
  input::placeholder { color: var(--placeholder); }
}
```

### 13-3. 컴포넌트 variant 고칠 곳

| 파일 | 고칠 것 |
|---|---|
| `components/ui/button.tsx` | `size.default`를 `h-12 px-5`, `size.icon`을 `size-11`로. `default` variant에 `active:bg-primary-active`. 비활성은 `disabled:bg-border disabled:text-disabled` |
| `components/ui/input.tsx` | `h-12 bg-card text-base shadow-hairline` |
| `components/ui/toggle-group.tsx` · `toggle.tsx` | `h-12`, `data-[state=on]:bg-mystic-soft data-[state=on]:text-mystic data-[state=on]:border-mystic` |
| `components/ui/badge.tsx` | `mystic` variant 추가: `bg-mystic-soft text-mystic` |
| `components/ui/card.tsx` | `shadow-card`, 선(`border`) 대신 겹선 그림자 |
| `components/ui/alert.tsx` | 기본 variant를 `bg-muted border-0 text-muted-foreground type-caption` |

버튼과 입력칸 높이는 **함께** 바꿉니다(둘 다 48px).

## 14. 정해지지 않은 것 (Known Gaps)

- **카드 그림 출처** — 직접 제작 또는 사용 허가 확인 전까지 흑백 자리 표시 그림 사용(PRD 미정).
- **공유 글 머리 기호** — 🔮(와이어프레임) 또는 ✦(이 가이드) 중 하나로 통일 필요.
- **어두운 화면(다크 모드)** — MVP 범위 밖. 색은 모두 의미 토큰으로 정해 두어 나중에 `.dark` 블록만 추가하면 됩니다.
- **주제 축소 여부** — 주제가 3개로 줄면 주제 칩을 3칸 × 1줄로 바꿉니다.
- **개인정보 동의 체크** — 필요하다고 정해지면 `Field` + `Checkbox`를 개인정보 `Alert` 아래에 추가합니다.
