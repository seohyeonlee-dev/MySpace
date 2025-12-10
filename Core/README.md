# Core - Shared Library
<br>

## Overview
Core는 MySpace 프로젝트의 공통 도메인 로직을 모아둔 공유 라이브러리입니다.
- 공통 DB 스키마 (users, bookings, payments)
- 공통 API (/api/bookings, /api/auth, /api/users)
- 공통 타입 및 유효성 검사
- 공통 프론트엔드 컴포넌트 (예약 폼 등)
<br>

## Structure
Core/
├── backend/         # Next.js + Prisma API
└── frontend/        # Expo 기반 공유 컴포넌트
<br>

## Backend Usage
```
cd Core/backend
npm install
npm run dev
```

다른 서비스에서:
```
cd MusicSpace/backend
npm install ../Core/backend      # 초기에는 로컬 참조
# 또는 npm install @myspace/core # 패키지로 배포 후
```
<br>

## Frontend Usage
```
import { BookingForm } from '@myspace/core/frontend';
// 또는 상대경로 import로 시작해도 OK
```