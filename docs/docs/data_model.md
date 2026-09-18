# Riftbound Player Retention Data Model

## Overview

The project uses five relational tables to model the fictional player journey
from signup through purchasing and organized-play participation.

```mermaid
erDiagram
    PLAYERS ||--o{ PURCHASES : makes
    PLAYERS ||--o{ ATTENDANCE : records
    STORES ||--o{ EVENTS : hosts
    EVENTS ||--o{ ATTENDANCE : includes

    PLAYERS {
        string player_id PK
        date signup_date
        string acquisition_channel
        string region
        string motivation
        decimal distance_to_store_miles
        boolean demo_watched
        boolean welcome_email_opened
    }

    PURCHASES {
        string purchase_id PK
        string player_id FK
        date purchase_date
        string product_type
        decimal amount_usd
        string purchase_channel
    }

    STORES {
        string store_id PK
        string store_name
        string city
        string state
        string region
        string store_type
        boolean carries_riftbound
        boolean hosts_events
        integer community_support_score
    }

    EVENTS {
        string event_id PK
        string store_id FK
        date event_date
        string event_type
        integer capacity
        integer registrations
        string event_status
        decimal entry_fee_usd
    }

    ATTENDANCE {
        string player_id PK, FK
        string event_id PK, FK
        date registration_date
        boolean registered
        boolean attended
        integer attendance_number
        time check_in_time
        integer final_placement
    }
```

## Relationships

### Players and purchases

One player may make zero, one, or multiple purchases. Each purchase belongs to
one player.

### Players and attendance

One player may have zero, one, or multiple attendance records. Each attendance
record belongs to one player.

### Stores and events

One store may host zero, one, or multiple events. Each event belongs to one
store.

### Events and attendance

One event may have multiple player attendance records. Each attendance record
belongs to one event.

## Analytical path

The tables support the following player journey:

1. Count new players in `players`.
2. Connect players to their first transaction in `purchases`.
3. Connect players to events through `attendance`.
4. retrieve event dates and formats from `events`.
5. retrieve store characteristics from `stores`.
6. calculate conversion and retention intervals.
