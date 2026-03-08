# Space Hub

**공간 예약 플랫폼** — 스터디룸, 회의실, 세미나실을 한 곳에서 검색하고 예약·결제까지 할 수 있는 풀스택 웹 서비스입니다.

[![Next.js](https://img.shields.io/badge/Next.js-16-black?style=for-the-badge&logo=next.js&logoColor=white)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com/)

---

## 목차

- [주요 기능](#-주요-기능)
- [기술 스택](#-기술-스택)
- [프로젝트 구조](#-프로젝트-구조)
- [시작하기](#-시작하기)
- [환경 변수](#-환경-변수)
- [주요 라우트](#-주요-라우트)
- [기여](#-기여)

---

## ✨ 주요 기능

### 이용자

| 기능 | 설명 |
|------|------|
| **회원가입·로그인** | 이메일/비밀번호 인증, Supabase Auth 연동, 비밀번호 강도 검사 |
| **공간 탐색** | 카테고리별 필터, 이미지 갤러리, 상세 정보 조회 |
| **예약** | 날짜·시간대 선택, 실시간 예약 가능 시간 반영 (React Day Picker) |
| **결제** | PortOne V2 연동, 카드 결제 및 서버 검증, 취소·환불 지원 |
| **마이페이지** | 내 예약 목록 조회, 예약 취소 |

### 관리자

| 기능 | 설명 |
|------|------|
| **대시보드** | 오늘/이번 달 매출·예약 수, 주간 매출·예약 상태 차트 |
| **통계 분석** | 일별/월별 매출, 카테고리별·시간대별·요일별 차트, TOP 상품 (Recharts) |
| **예약 관리** | 캘린더·테이블 뷰, 상태 변경, 상세 모달 (React Big Calendar) |
| **결제 관리** | 결제 목록, 상세 모달, 환불 처리 |
| **상품 관리** | 공간 CRUD, 이미지 업로드 (Supabase Storage) |
| **알림** | 결제 완료 시 알림 생성, 읽음/읽지않음 처리 |

### 인프라·보안

- **Row Level Security (RLS)** — Supabase RLS로 테이블 단위 접근 제어
- **미들웨어 인증** — Next.js 미들웨어로 사용자·관리자 경로 보호
- **Server Actions** — 데이터 변경은 Next.js Server Actions로 처리 (API 라우트 최소화)
- **결제 검증** — 클라이언트 금액이 아닌 서버에서 PortOne API로 재검증

---

## 🛠 기술 스택

| 구분 | 기술 |
|------|------|
| **프레임워크** | Next.js 16 (App Router) |
| **언어** | TypeScript 5 (strict) |
| **스타일** | Tailwind CSS v4 |
| **UI** | Radix UI, shadcn/ui (New York), Lucide React |
| **백엔드·DB** | Supabase (PostgreSQL, Auth, Storage) |
| **결제** | PortOne V2 (포트원) |
| **차트** | Recharts 3 |
| **캘린더** | React Big Calendar, React Day Picker |
| **캐러셀** | Embla Carousel |
| **검증** | Zod 4 |
| **토스트** | Sonner |

---

## 📁 프로젝트 구조

```
src/
├── app/                    # Next.js App Router
│   ├── layout.tsx          # 루트 레이아웃 (메타데이터, 폰트)
│   ├── page.tsx            # 메인(홈) 페이지
│   ├── globals.css
│   ├── login/, signup/     # 인증 페이지
│   ├── mypage/             # 마이페이지
│   ├── products/           # 공간 목록·상세
│   ├── admin/              # 관리자 (대시보드, 예약·결제·상품·알림·통계)
│   ├── auth/callback/      # OAuth 콜백
│   └── actions/            # Server Actions (auth, 예약, 결제, 상품, 알림 등)
├── components/
│   ├── layout/             # Header, Footer, RootLayoutWrapper
│   ├── auth/                # LoginForm, SignupForm
│   ├── products/            # ProductList, ProductCard, ReservationForm 등
│   ├── mypage/              # MyPageContent, ReservationCard
│   ├── admin/               # 대시보드·예약·결제·상품·알림·통계용 컴포넌트
│   └── ui/                  # shadcn/ui 공통 컴포넌트
├── lib/
│   ├── supabase/            # client, server, middleware용 Supabase 클라이언트
│   ├── auth.ts
│   ├── api/                 # products, reservations, payments API 래퍼
│   ├── payment/             # PortOne 클라이언트
│   └── utils/
├── types/                   # database, product, payment, supabase 타입
├── data/                    # 정적/샘플 데이터 (선택)
└── ...
```

---

## 🚀 시작하기

### 필요 환경

- [Node.js](https://nodejs.org/) **v18.17 이상**
- [npm](https://www.npmjs.com/) 또는 [yarn](https://yarnpkg.com/)
- [Supabase](https://supabase.com/) 프로젝트
- [PortOne](https://admin.portone.io/) 계정 (결제 연동 시)

### 설치 및 실행

**1. 저장소 클론**

```bash
git clone https://github.com/GDandTOP/ResurveHub.git
cd ResurveHub
```

**2. 의존성 설치**

```bash
npm install
```

**3. 환경 변수 설정**

프로젝트 루트에 `.env.local` 파일을 만들고, `.env.local.example`을 참고해 필요한 값을 채웁니다. (자세한 항목은 [환경 변수](#-환경-변수) 참고)

**4. 개발 서버 실행**

```bash
npm run dev
```

브라우저에서 [http://localhost:3000](http://localhost:3000) 으로 접속합니다.

**5. 프로덕션 빌드 및 실행 (선택)**

```bash
npm run build
npm run start
```

---

## 🔐 환경 변수

| 변수명 | 설명 | 비고 |
|--------|------|------|
| `NEXT_PUBLIC_SUPABASE_URL` | Supabase 프로젝트 URL | Project Settings → API |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Supabase Anonymous Key (클라이언트용) | 동일 |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase Service Role Key (서버 전용) | **절대 노출 금지** |
| `NEXT_PUBLIC_APP_URL` | 앱 기준 URL (예: `http://localhost:3000`) | OAuth·콜백 등에 사용 |
| `NEXT_PUBLIC_PORTONE_STORE_ID` | PortOne 상점 ID | 포트원 관리자콘솔 |
| `NEXT_PUBLIC_PORTONE_CHANNEL_KEY` | PortOne 채널 키 | 동일 |
| `PORTONE_V2_API_SECRET` | PortOne V2 API Secret (서버 전용) | **절대 노출 금지** |
| `NEXT_PUBLIC_PAYMENT_ENV` | 결제 환경 (`development` / `production`) | 선택 |

자세한 설명과 예시는 `.env.local.example` 파일을 참고하세요.

---

## 🗺 주요 라우트

| 경로 | 설명 | 접근 |
|------|------|------|
| `/` | 메인(홈) | 전체 |
| `/products` | 공간 목록 | 전체 |
| `/products/[id]` | 공간 상세·예약 | 전체 |
| `/login`, `/signup` | 로그인·회원가입 | 비로그인 |
| `/mypage` | 내 예약 | 로그인 사용자 |
| `/admin` | 관리자 홈 | 관리자 |
| `/admin/dashboard` | 대시보드 | 관리자 |
| `/admin/reservations` | 예약 관리 | 관리자 |
| `/admin/payments` | 결제 관리 | 관리자 |
| `/admin/products` | 상품 관리 | 관리자 |
| `/admin/analytics` | 통계 분석 | 관리자 |
| `/admin/notifications` | 알림 | 관리자 |
| `/about`, `/company`, `/faq`, `/support` 등 | 소개·고객지원 | 전체 |

---

## 📜 사용 스크립트

| 명령어 | 설명 |
|--------|------|
| `npm run dev` | 개발 서버 실행 (기본 포트 3000) |
| `npm run build` | 프로덕션 빌드 |
| `npm run start` | 프로덕션 서버 실행 |
| `npm run lint` | ESLint 실행 |

---

## 🤝 기여

1. 저장소를 포크한 뒤 브랜치를 생성합니다.
2. 변경 사항을 커밋하고 원격 브랜치에 푸시합니다.
3. 원본 저장소에 Pull Request를 생성합니다.

---

## 📄 라이선스

이 프로젝트는 MIT 라이선스로 제공됩니다. 자세한 내용은 [LICENSE](./LICENSE) 파일을 참고하세요.
