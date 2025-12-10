# MySpace - 공간 예약 플랫폼 통합 프로젝트

![MySpace Logo](https://via.placeholder.com/500x200?text=MySpace+-+Space+Booking+Platform)

> **여러 공간을 한 플랫폼에서 예약하세요**  
> 음악 연습실(MusicSpace) · 아이스링크(IceSpace) · 다양한 공간(ThisSpace)

## 🎯 프로젝트 개요

**MySpace**는 다양한 공간 예약을 통합 관리하는 플랫폼입니다. 사용자는 하나의 앱/웹에서 음악 연습실, 아이스링크, 회의실, 스포츠 시설 등 여러 공간을 검색하고 예약할 수 있습니다.

### 플랫폼 구성

| 플랫폼 | 설명 | 상태 |
|--------|------|------|
| **MusicSpace** | 음악 연습실(피아노, 드럼, 보컬 등) 예약 서비스 | 🚀 개발 중 |
| **IceSpace** | 아이스링크, 스케이트장 예약 서비스 | 📋 계획 중 |
| **ThisSpace** | 범용 공간 예약 서비스 (회의실, 스튜디오 등) | 📋 계획 중 |

## 📁 저장소 구조

```
MySpace/
├── README.md                    # 메인 프로젝트 문서
├── .github/
│   └── workflows/               # CI/CD 설정
├── Core/                        # 🔑 공유 라이브러리 (별도 npm 패키지)
│   ├── backend/
│   │   ├── prisma/
│   │   │   ├── schema.prisma    # 공유 DB 스키마
│   │   │   └── migrations/
│   │   ├── lib/
│   │   │   ├── db.ts            # 데이터베이스 연결
│   │   │   ├── types.ts         # 공유 타입 정의
│   │   │   ├── auth.ts          # 인증 로직
│   │   │   └── validators.ts    # 유효성 검사
│   │   ├── api/
│   │   │   ├── bookings/        # 예약 API (모든 공간 공통)
│   │   │   ├── auth/            # 인증 API
│   │   │   └── users/           # 사용자 API
│   │   ├── package.json
│   │   └── tsconfig.json
│   ├── frontend/
│   │   ├── components/
│   │   │   ├── BookingForm.tsx      # 공유 예약 폼
│   │   │   ├── TimeSlotPicker.tsx   # 공유 시간대 선택
│   │   │   └── SpaceCard.tsx        # 공유 공간 카드
│   │   ├── hooks/
│   │   │   ├── useBooking.ts
│   │   │   └── useSpaces.ts
│   │   ├── lib/
│   │   │   ├── api.ts           # API 클라이언트
│   │   │   └── types.ts         # 공유 타입
│   │   ├── package.json
│   │   └── tsconfig.json
│   └── package.json
│
├── MusicSpace/                  # 음악 연습실 플랫폼
│   ├── backend/
│   │   ├── prisma/
│   │   │   └── schema.prisma    # MusicSpace 특화 스키마 확장
│   │   ├── lib/
│   │   │   ├── db.ts
│   │   │   └── musicTypes.ts    # 음악 특화 타입
│   │   ├── api/
│   │   │   ├── studios/         # 연습실 상세 API
│   │   │   └── instruments/     # 악기/시설 API
│   │   ├── app.ts
│   │   ├── package.json
│   │   └── .env.example
│   ├── frontend/
│   │   ├── app/
│   │   │   ├── (tabs)/
│   │   │   │   ├── index.tsx     # 메인 페이지
│   │   │   │   ├── search.tsx    # 검색 (Core 컴포넌트 활용)
│   │   │   │   └── map.tsx       # 지도
│   │   │   ├── studio-detail/
│   │   │   │   └── [id].tsx      # 연습실 상세 페이지 (MusicSpace 특화)
│   │   │   └── _layout.tsx
│   │   ├── components/
│   │   │   ├── StudioCard.tsx    # 연습실 카드 (Core SpaceCard 확장)
│   │   │   └── AmenityBadge.tsx  # 악기/시설 배지
│   │   ├── app.json
│   │   ├── package.json
│   │   └── .env.example
│   ├── docs/
│   │   └── SETUP.md             # MusicSpace 설정 가이드
│   └── package.json
│
├── IceSpace/                    # 아이스링크 예약 플랫폼 (향후)
│   ├── backend/
│   │   ├── prisma/
│   │   │   └── schema.prisma
│   │   └── api/
│   │       └── rinks/
│   ├── frontend/
│   │   ├── app/
│   │   │   ├── rink-detail/
│   │   │   └── _layout.tsx
│   │   └── components/
│   │       └── RinkCard.tsx
│   └── package.json
│
├── ThisSpace/                   # 범용 공간 예약 (향후)
│   ├── backend/
│   ├── frontend/
│   └── package.json
│
└── docs/
    ├── ARCHITECTURE.md          # 전체 아키텍처 설계
    ├── SETUP.md                 # 환경 설정 (통합)
    ├── DATABASE.md              # DB 스키마 (Core)
    ├── API.md                   # API 문서 (Core)
    └── DEPLOYMENT.md            # 배포 가이드
```

## 🚀 빠른 시작

### 사전 요구사항
- Node.js 18+ LTS
- PostgreSQL 14+
- Git
- npm 또는 yarn

### 로컬 개발 환경 설정

```bash
# 1. 저장소 클론
git clone https://github.com/seohyeonlee-dev/MySpace.git
cd MySpace

# 2. Core 라이브러리 설치 (모든 서비스의 공통 기반)
cd Core
npm install
npm run build

# 3. MusicSpace 백엔드 설정
cd ../MusicSpace/backend
npm install
cp .env.example .env.local
# DATABASE_URL 등 환경변수 설정
npm run db:setup

# 4. MusicSpace 프론트엔드 설정
cd ../frontend
npm install
npm start
```

## 📚 문서

- [**Core 라이브러리 가이드**](./Core/README.md) - 공유 코드 개발
- [**MusicSpace 설정**](./MusicSpace/docs/SETUP.md) - 음악 연습실 개발
- [**전체 아키텍처**](./docs/ARCHITECTURE.md) - 시스템 설계
- [**데이터베이스 스키마**](./docs/DATABASE.md) - DB 구조
- [**API 문서**](./docs/API.md) - REST API
- [**배포 가이드**](./docs/DEPLOYMENT.md) - Azure 배포

## 🏗️ 아키텍처

### 멀티 플랫폼 구조

```
┌─────────────────────────────────────────────┐
│  사용자 (웹/앱)                              │
└────────────────┬────────────────────────────┘
                 │
        ┌────────┴────────┐
        │                 │
  ┌─────▼─────┐     ┌─────▼──────┐
  │MusicSpace │     │IceSpace    │
  │(프론트)   │     │(프론트)    │
  └─────┬─────┘     └─────┬──────┘
        │                 │
        └────────┬────────┘
                 │
        ┌────────▼────────┐
        │ Core 라이브러리  │
        │ - 공유 API      │
        │ - 공유 컴포넌트  │
        │ - 공유 타입      │
        └────────┬────────┘
                 │
        ┌────────▼────────────────┐
        │ 백엔드 API              │
        │ /api/bookings  (공통)   │
        │ /api/studios   (특화)   │
        │ /api/rinks     (특화)   │
        └────────┬────────────────┘
                 │
        ┌────────▼─────────┐
        │ PostgreSQL DB    │
        │ (통합 데이터베이스)│
        └──────────────────┘
```

### 기술 스택

| 계층 | 기술 | 버전 |
|------|------|------|
| **프론트엔드** | React Native + Expo + TypeScript | 18+ |
| **백엔드** | Next.js + Node.js | 18 LTS |
| **ORM** | Prisma | 5.x |
| **데이터베이스** | PostgreSQL | 14+ |
| **인증** | NextAuth.js | 4.x |
| **배포** | Azure App Service + GitHub Actions | - |

## 🔄 Core 라이브러리 역할

**Core**는 모든 플랫폼이 공유하는 기능을 포함합니다:

### 백엔드 (Core/backend)
- ✅ **통합 데이터베이스 스키마** (Prisma)
- ✅ **공통 API 엔드포인트** (`/api/bookings`, `/api/users`, `/api/auth`)
- ✅ **타입 정의** (TypeScript 인터페이스)
- ✅ **유효성 검사 로직**
- ✅ **인증/인가 로직**

### 프론트엔드 (Core/frontend)
- ✅ **공유 컴포넌트** (BookingForm, TimeSlotPicker, SpaceCard)
- ✅ **공유 훅** (useBooking, useSpaces)
- ✅ **API 클라이언트** (axios 래퍼)
- ✅ **공유 타입/상수**

## 🔌 각 플랫폼의 역할

### MusicSpace (음악 연습실)
- 📋 스튜디오 특화 정보 (악기 종류, 음향 시설)
- 🎨 연습실 상세 페이지
- 🔍 악기/시설별 검색 필터
- 📱 음악 관련 UI/UX

### IceSpace (아이스링크)
- 📋 링크 특화 정보 (빙판 크기, 보드 서비스)
- 🎨 링크 상세 페이지
- 🔍 레벨별 클래스 검색
- 📱 스포츠 관련 UI/UX

## 🛠️ 개발 워크플로우

### 1단계: 공통 기능 개발 (Core)
```bash
cd Core/backend
# 새로운 API 엔드포인트 추가
# 예: /api/bookings/available-times

# Core 빌드 및 배포
npm run build
npm publish  # npm 레지스트리에 배포
```

### 2단계: 플랫폼별 기능 개발
```bash
cd MusicSpace/backend
# Core를 의존성으로 설치
npm install @myspace/core

# MusicSpace 특화 API 추가
# 예: /api/studios/[id]/instruments
```

### 3단계: 프론트엔드 개발
```bash
cd MusicSpace/frontend
# Core 컴포넌트 활용
import { BookingForm, SpaceCard } from '@myspace/core-ui';
```

## 📊 데이터베이스 설계

### 공통 테이블 (Core)
- `users` - 사용자 (모든 플랫폼)
- `bookings` - 예약 (모든 플랫폼)
- `bookings_line_items` - 예약 상세 항목
- `payments` - 결제 (모든 플랫폼)

### MusicSpace 특화 테이블
- `studios` - 연습실
- `studio_instruments` - 악기/시설
- `studio_amenities` - 편의시설

### IceSpace 특화 테이블 (향후)
- `rinks` - 아이스링크
- `ice_classes` - 클래스
- `rink_amenities` - 편의시설

## 🔐 환경 변수

### Core/backend/.env
```env
# 데이터베이스
DATABASE_URL=postgresql://user:pass@localhost:5432/myspace_core

# 인증
NEXTAUTH_SECRET=your_secret_here
NEXTAUTH_URL=http://localhost:3000
```

### MusicSpace/backend/.env
```env
# Core 서버
CORE_API_URL=http://localhost:3001

# 추가 설정
KAKAO_MAP_API_KEY=your_kakao_key
```

## 🚢 배포

### Azure 배포 구조

```
Azure Subscription
├── Resource Group: myspace-rg
│   ├── App Service: myspace-core-api
│   ├── App Service: musicspace-api
│   ├── App Service: musicspace-web
│   ├── PostgreSQL: myspace-db
│   └── Container Registry: myspace-acr
└── GitHub Actions (CI/CD)
```

배포 가이드는 [DEPLOYMENT.md](./docs/DEPLOYMENT.md)를 참조하세요.

## 📈 마일스톤

- [x] **Phase 1**: MusicSpace MVP (현재)
- [ ] **Phase 2**: IceSpace 개발 (2025년 Q2)
- [ ] **Phase 3**: ThisSpace 일반화 (2025년 Q3)
- [ ] **Phase 4**: 결제/정산 시스템 (2025년 Q4)
- [ ] **Phase 5**: 모바일 앱 스토어 배포 (2026년 Q1)

## 👥 팀 및 기여

- **프로젝트 리더**: 이서현
- **백엔드**: 보안, 시스템 설계
- **프론트엔드**: UI/UX, 반응형 디자인

기여 방법은 [CONTRIBUTING.md](./CONTRIBUTING.md)를 참조하세요.

## 📝 라이센스

MIT License - 자유롭게 사용, 수정, 배포 가능

## 🤝 지원

- 📧 이메일: seohyeonlee.dev@gmail.com
- 💬 이슈 트래킹: [GitHub Issues](https://github.com/seohyeonlee-dev/MySpace/issues)
- 📖 문서: [docs/](./docs/)

---

**Made with ❤️ by 이서현**  
*마지막 업데이트(README): 2025. 12. 10.*
