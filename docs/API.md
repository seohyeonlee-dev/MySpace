# API Documentation
<br>

## Base URLs
- Core: http://localhost:3001
- MusicSpace: http://localhost:3000
<br>

---

## Core: /api/bookings

### POST /api/bookings
예약 생성

Request body:
```
{
  "spaceType": "music_studio",
  "spaceId": 1,
  "bookingDate": "2025-12-15",
  "startTime": "14:00",
  "endTime": "15:00",
  "userName": "홍길동",
  "userPhone": "010-0000-0000",
  "userEmail": "test@example.com"
}
```

Response 201:
```
{
  "id": 10,
  "spaceType": "music_studio",
  ...
}
```

### GET /api/bookings
쿼리 파라미터:
- spaceType
- spaceId
- date