# MusicSpace SETUP
<br>

## Overview
MusicSpace는 음악 연습실(피아노, 드럼, 보컬 등)을 예약하는 서비스입니다.
이 문서는 개발 환경을 처음 세팅하는 사람을 기준으로 작성되었습니다.
<br>

## Prerequisites
- Node.js 18+
- PostgreSQL
- Core/backend가 이미 동작 중 (myspace_core DB)
<br>

## 1. Database
```
CREATE DATABASE musicspace;
\c musicspace

-- studios, studio_instruments, studio_amenities 테이블 생성 (여기 SQL 붙여넣기)
```
<br>

## 2. Backend Setup
```
cd MusicSpace/backend
npm install
cp .env.example .env.local  # 없으면 직접 생성
npm run dev                 # http://localhost:3000
```
<br>

## 3. Frontend Setup
```
cd MusicSpace/frontend
npm install
npm start                  # Expo 개발 서버