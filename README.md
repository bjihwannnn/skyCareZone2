# 🌤️ SkyCareZone — 에어컨 청소 · 클리닝 · 방역 전문 서비스

> **깨끗함과 따뜻함을 중심으로.**  
> 빠르고 안정적인 정적 웹사이트를 목표로 **Astro + Tailwind CSS** 기반으로 제작.

<br><br><br>

## 🚀 기술 스택

| 구분 | 기술 |
|------|------|
| **Framework** | [Astro](https://astro.build/)
| **Styling** | [Tailwind CSS](https://tailwindcss.com/)
| **Language** | HTML, CSS, JavaScript |
| **Font** | [Noto Sans KR](https://fonts.google.com/specimen/Noto+Sans+KR)

<br><br><br>

## 🧱 프로젝트 구조

```

src/
├─ layouts/
│  └─ BaseLayout.astro        # 공통 레이아웃 (헤더, 푸터, SEO/OG 메타 포함)
│
├─ components/
│  ├─ HeroSection.astro       # 페이지 상단 히어로 섹션
│  ├─ ProcedureSection.astro  # 절차 안내 카드 섹션
│  ├─ NoticeListSection.astro # 유의사항 리스트
│  ├─ GallerySection.astro    # 작업사진 갤러리
│  └─ CTASection.astro        # 하단 문의(Call To Action)
│
├─ pages/
│  ├─ index.astro             # 메인 홈 페이지
│  ├─ AirConditioner.astro    # 에어컨 청소 서비스 페이지
│  ├─ Cleaning.astro          # 클리닝 서비스 페이지
│  └─ Disinfection.astro      # 방역 서비스 페이지
│
└─ styles/
└─ global.css              # Tailwind + SkyCareZone 커스텀 스타일

```

<br><br><br>

## 🎨 주요 디자인 컨셉

- **SkyCare 팔레트**
  - Light: `#E6F4F9`
  - Blue: `#3B82F6`
  - DarkBlue: `#1E3A8A`
  - Orange: `#F97316`
  - Warm: `#FDE68A`

<br><br><br>

## 🧾 빌드 체크리스트 요약

| 항목                            | 상태 |
| ----------------------------- | -- |
| Tailwind 정상 동작                | ✅  |
| SkyCare 커스텀 색상 적용             | ✅  |
| HeroSection 배경 정상 렌더링         | ✅  |
| Gallery lazy-load / alt 속성 적용 | ✅  |
| SEO/OG 메타 반영                  | ✅  |
| key 누락 경고 없음                  | ✅  |
| favicon 표시 확인                 | ✅  |

<br><br><br>

### 🧡 Branding Slogan

> **“깨끗함과 따뜻함을 한 번에 — SkyCareZone.”**
