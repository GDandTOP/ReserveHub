## 포트폴리오 제목

공간 예약 플랫폼(Space Hub) — Next.js·Supabase·PortOne 기반 스터디룸/회의실 예약·결제 풀스택 개발

---

## 프로젝트 상세

1. 포트폴리오 소개 :
스터디룸, 회의실, 세미나실을 한 곳에서 검색하고 예약·결제까지 할 수 있는 공간 예약 플랫폼 웹 서비스입니다. Next.js 16 App Router와 Supabase(PostgreSQL, Auth, Storage)를 백엔드로 사용하고, PortOne V2로 결제를 연동하였습니다. 이용자용 공간 탐색·예약·결제·마이페이지와 관리자용 대시보드·예약/결제/상품 관리·통계·알림까지 풀스택으로 구현하였습니다.
2. 작업 범위 :

- Full-Stack 개발 (Next.js Frontend + Supabase Backend 전담)
- 회원 인증 및 회원/관리자 권한 분리 (미들웨어·RLS)
- 공간(상품) CRUD, 예약·결제·취소·환불 플로우 개발
- 관리자 대시보드, 통계(Recharts), 예약 캘린더(React Big Calendar), 알림 시스템 구축
- PortOne V2 연동 및 서버 측 결제 검증·환불 처리

1. 주요 업무 :

- Supabase Auth 기반 이메일/비밀번호 회원가입·로그인 및 OAuth 콜백 처리
- Supabase RLS(Row Level Security)로 테이블 단위 접근 제어, 관리자/일반 사용자 경로 분리
- Next.js Server Actions로 예약 생성·수정·취소, 결제 검증·환불, 상품 CRUD, 알림 생성 처리
- PortOne V2 API 연동: 클라이언트 결제 요청 후 서버에서 금액·상태 재검증 및 DB 반영
- React Day Picker로 예약 가능 시간대 선택, React Big Calendar로 관리자 예약 캘린더·테이블 뷰
- Recharts로 일별/월별 매출, 카테고리·요일·시간대별 통계, TOP 상품 차트 구현
- Supabase Storage를 활용한 공간 이미지 업로드 및 관리자 상품 등록/수정
- 결제 완료 시 알림 생성, 읽음/읽지않음 처리 및 관리자 알림 목록 UI

1. 주안점 :

- RLS와 Next.js 미들웨어로 인증되지 않은 사용자의 관리자·마이페이지 접근 차단
- 결제 금액·상태를 서버에서 PortOne API로 재검증하여 위변조 방지
- Server Actions 중심 설계로 API 라우트 최소화, 타입 안전한 데이터 변경
- 공간 목록·상세·예약 가능 시간 조회를 서버/클라이언트 API 래퍼로 분리하여 유지보수성 확보

---

## 프로젝트 배경

1. 문제점

- 스터디룸·회의실·세미나실 등 공간 예약이 업체별로 나뉘어 있어 한 곳에서 비교·예약·결제하기 어려움
- 예약 가능 시간 확인, 결제·취소·환불을 하나의 플로우로 처리하는 서비스에 대한 수요 존재
- 관리자가 예약·매출·상품을 한 대시보드에서 관리할 수 있는 솔루션 필요

1. 프로젝트 목표

- Next.js와 Supabase를 활용해 이용자용 예약·결제와 관리자용 운영 기능을 갖춘 단일 풀스택 웹 서비스 구축
- 실시간 예약 가능 시간 반영, PortOne 연동 결제·환불, RLS 기반 보안으로 신뢰할 수 있는 예약 플랫폼 제공
- 대시보드·통계·캘린더로 관리자 업무 효율화

1. 주안점

- 사용자 경험: 카테고리 필터, 이미지 갤러리, 날짜·시간 선택 UX, 결제 후 마이페이지에서 예약 확인
- 보안: RLS·미들웨어로 경로별 접근 제어, 결제는 서버 검증 필수
- 확장성: App Router·Server Actions·lib/api 구조로 기능 추가 및 유지보수 용이

---

## 프로젝트 성과

1. 성과명 : Next.js·Supabase·PortOne 단일 스택으로 공간 예약·결제·관리자 운영까지 풀사이클 구현
2. 설명 :
별도 백엔드 서버 없이 Next.js 16 App Router, Supabase(Auth, PostgreSQL, Storage), PortOne V2를 조합하여 회원 인증부터 공간 탐색·예약·결제·취소·환불, 마이페이지, 관리자 대시보드·예약/결제/상품 관리·통계·알림까지 서비스 전체 사이클을 완성하였습니다. RLS와 미들웨어로 권한을 분리하고, 결제는 서버에서 PortOne API로 재검증하여 안전하게 처리하였습니다. TypeScript strict와 Server Actions·lib 분리 설계로 코드 품질과 유지보수성을 확보하였습니다.

---

## 진행 단계

요구사항 정의 > Supabase·PortOne 설정 > 인증·RLS·미들웨어 구축 > 공간(상품) CRUD > 예약·결제 플로우 > 마이페이지·관리자 대시보드 > 통계·캘린더·알림 > 배포·QA

- 공간 예약 플랫폼 요구사항 정의 및 DB 스키마·RLS 정책 설계
- Supabase 프로젝트 생성, 환경 변수 설정, Auth·Storage·RLS 구성
- Next.js 미들웨어로 로그인/관리자 경로 보호, Server Actions 기반 인증 연동
- 공간(상품) 목록·상세·예약 가능 시간 API 및 ReservationForm(React Day Picker) 구현
- PortOne V2 클라이언트·서버 연동, 결제 검증·DB 반영·취소·환불 Server Actions 구현
- 마이페이지(내 예약 목록·취소), 관리자 대시보드(오늘/이번 달 매출·예약 수, 차트) 구현
- Recharts 통계(일별/월별 매출, 카테고리·요일·시간대별), React Big Calendar 예약 캘린더·테이블 뷰
- 결제 완료 알림 생성·읽음 처리, 관리자 상품 CRUD·이미지 업로드(Supabase Storage)
- 빌드·배포 및 최종 QA

---

## 핵심 기능

PortOne V2 결제 연동 및 서버 검증
클라이언트에서 PortOne SDK로 결제 요청 후, 서버 Action에서 PortOne V2 API를 호출해 결제 금액·상태를 재검증합니다. 검증 성공 시 payments·reservations 테이블에 반영하고, 취소·환불 시에도 동일 API로 상태를 갱신하여 DB와 결제사 데이터 정합성을 유지합니다.

Supabase RLS와 Next.js 미들웨어 기반 권한 분리
관리자 전용 테이블/행은 RLS로 서버 역할(service role) 또는 관리자 식별자로만 접근 가능하도록 제한하고, Next.js 미들웨어에서 /admin, /mypage 등 경로별로 로그인·관리자 여부를 검사하여 미인증 사용자는 로그인 페이지 또는 홈으로 리다이렉트합니다.

관리자 대시보드·통계·예약 캘린더
오늘/이번 달 매출·예약 수를 대시보드에 집계하고, Recharts로 일별/월별 매출, 카테고리·요일·시간대별 차트 및 TOP 상품 테이블을 구현하였습니다. React Big Calendar로 예약을 캘린더·테이블 뷰로 조회하고 상태 변경·상세 모달을 제공합니다.

---

## 기술 스택

- Frontend: Next.js 16 (App Router), React 19, TypeScript 5, Tailwind CSS v4, Radix UI, shadcn/ui (New York), Lucide React, class-variance-authority, tailwind-merge, Embla Carousel
- Backend/DB: Supabase (PostgreSQL, Auth, Storage), Supabase SSR·middleware 클라이언트
- 결제: PortOne V2 (포트원) — 브라우저 SDK + 서버 API 검증·환불
- 차트·캘린더: Recharts 3, React Big Calendar, React Day Picker
- 검증·기타: Zod 4, date-fns, Sonner (토스트)
- 배포: Vercel 또는 Node 서버 (next build / next start)
- 기타: Next.js Server Actions, RLS, Next.js Middleware

