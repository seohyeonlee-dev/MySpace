# Architecture
<br>

## High-level Overview
- Core: 공통 도메인 (예약, 사용자, 결제)
- MusicSpace: 음악 연습실 도메인
- IceSpace, ThisSpace: 확장 예정
<br>

## Repository Layout
MySpace/
├── Core/
├── MusicSpace/
├── IceSpace/
└── ThisSpace/
<br>

## Request Flow (MusicSpace 예약)
1. 사용자가 MusicSpace 앱에서 예약 버튼 클릭
2. MusicSpace/frontend → MusicSpace/backend (/api/studios/...)
3. 예약 확정 시 Core/backend (/api/bookings) 호출
4. Core/backend → myspace_core DB에 예약 레코드 생성