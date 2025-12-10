# Database Schema
<br>

## Databases
- myspace_core
- musicspace
- (future) icespace, thisspace
<br>

## Core: myspace_core
### users
- id (PK)
- email (UNIQUE)
- password_hash
- ...

### bookings
- user_id → users.id (FK)
- space_type (music_studio / ice_rink / ...)
- space_id (각 서비스의 공간 PK)
- ...
<br>

## MusicSpace: musicspace
### studios
- id (PK)
- name
- location
- price_per_hour
- ...

### studio_instruments
- studio_id → studios.id

### studio_amenities
- studio_id → studios.id