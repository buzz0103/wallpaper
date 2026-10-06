# DESIGN.md — 월간 배너(월페이퍼) 디자인 규칙

월간 배너 자동 생성기(`index.html`)가 따르는 디자인 기준입니다.
값을 바꿀 때는 이 문서와 `index.html`을 함께 수정하세요.

## 1. 캔버스

| 항목 | 값 |
| --- | --- |
| 캔버스 크기 | **1440 × 900 px** |
| 사이트 노출 | `width: 80vw` (브라우저 크기에 따라 변동, 기본값 80vw) |
| 최대 너비 | `max-width: 1440px` |
| 모서리 | `border-radius: 80px` |
| 배경 이미지 | `src/assets/{YYYY}/{YYYYMM}.jpg` — 캔버스 비율로 cover 채움 |

## 2. 서체

한글과 영문/숫자를 서로 다른 폰트로 쓰고, **굵기 숫자를 맞춰서** 한 번에 같은 굵기가 적용됩니다.

| 용도 | 폰트 | Light | Medium | Bold |
| --- | --- | --- | --- | --- |
| 한글 | Elice DX Neolli OTF (`src/fonts/`) | 200 | 600 | 700 |
| 영문 · 숫자 | Montserrat (Google Fonts) | ExtraLight 200 | SemiBold 600 | Bold 700 |

```css
font-family: 'Montserrat', 'Elice DX Neolli OTF', sans-serif;
```

Montserrat에는 한글 글리프가 없어서, 한글은 자동으로 Elice DX Neolli로 대체됩니다.

### 굵기 선택 (UI)

- 가늘게 (Light) = 200
- 보통 (Medium) = 600
- 굵게 (Bold) = 700

## 3. 로고

- 파일: `src/assets/Brand_logo.svg` (120 × 33, 가로세로 비율 유지)
- 기본 크기: 가로 160px (슬라이더로 40~600px)
- 기본 위치: 좌측 상단 (x 150, y 90), 캔버스에서 드래그로 이동
- 배경 이미지에 로고가 이미 있으면 "로고 표시"를 꺼서 중복을 피합니다.

## 4. 레이어 기본값

| 레이어 | 위치 (x, y) | 크기 | 굵기 | 정렬 |
| --- | --- | --- | --- | --- |
| 연도 | 1200, 132 | 120px | Bold | 가운데 |
| 월 | 1200, 246 | 80px | Bold | 가운데 |
| 목차 | 300, 500 | 20px | — | 왼쪽 |
| 배너 문구 | 720, 780 | 48px | Bold | 가운데 |

그림자는 기본 꺼짐입니다.

## 5. 목차

- 항목 최대 **14개**, 순서대로 번호가 붙습니다.
- 번호: Montserrat SemiBold(600) / 내용: Elice DX Neolli Medium(600), 영문·숫자는 Montserrat.
- **번호와 내용은 같은 크기**이고, 크기 값을 키우면 함께 커집니다.
- 번호 칸은 고정 너비라서 한 자리/두 자리 번호도 내용 시작 위치가 같습니다.
- 인라인 서식
  - `**강조**` → Bold(700), 강조 색상
  - `!주석!` → 15px, 기본 `#767676`, 글자 끝에 붙여서 표시
- 배경 박스: 색상 · 투명도(0~100%) · 패딩(0~100px) · 모서리(0~100px)

## 6. 하단 배너

- 원본 2560 × 260 → **1/2 크기**(1280 × 130)로 하단 중앙에 배치
- `border-radius: 24px`, 하단 여백 30px
- 표시/숨김 선택 가능, 드래그로 위치 이동

## 7. 색상 (도구 UI)

| 토큰 | 값 | 용도 |
| --- | --- | --- |
| `--red` | `#CC2030` | 포인트, 선택 표시 |
| `--ink` | `#1c1c1e` | 본문 텍스트 |
| `--paper` | `#f6f5f3` | 작업 영역 배경 |
| `--line` | `#e4e2df` | 구분선 |
| `--muted` | `#8a8781` | 보조 텍스트 |

## 8. 저장 규칙

- PNG / JPG: 선택 테두리 없이 1440 × 900으로 저장
- 사이트용 PHP 세트: `wallpaper_{yy}{mm}.jpg`, `wallpaper_bg_{yy}{mm}.jpg`(블러 배경), `wallpaper_{yy}{mm}.php`

## 9. 파일 구조

```
index.html
DESIGN.md
src/
  assets/
    Brand_logo.svg
    {YYYY}/{YYYYMM}.jpg
  fonts/
    EliceDXNeolliOTF-Light.woff2   (200)
    EliceDXNeolliOTF-Medium.woff2  (600)
    EliceDXNeolliOTF-Bold.woff2    (700)
```
