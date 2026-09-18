# Data Dictionary

## Purpose

This document defines the tables and fields used in the Riftbound new-player
conversion and retention analysis.

All records will be synthetically generated for this portfolio project.

## Table 1: Players

### Table purpose

The players table contains one record for every fictional person who enters
the new-player funnel.

### Table grain

One row represents one player.

### Primary key

`player_id`

A primary key uniquely identifies each record. No two players can have the
same player ID.

### Fields

| Field | Data type | Description | Example |
|---|---|---|---|
| player_id | Text | Unique player identifier | P00001 |
| signup_date | Date | Date the player entered the funnel | 2026-01-15 |
| acquisition_channel | Text | How the player first discovered or entered Riftbound | Local game store |
| region | Text | Player's geographic region | Southeast |
| motivation | Text | Primary reason for becoming interested | Social |
| distance_to_store_miles | Decimal | Distance to the closest participating game store | 8.5 |
| demo_watched | Boolean | Whether the player watched a product demonstration | True |
| welcome_email_opened | Boolean | Whether the player opened the welcome email | True |

### Acquisition-channel values

- Local game store
- Friend referral
- Creator content
- Riot social media
- Convention

### Motivation values

- Competitive play
- Collecting
- Social play
- League of Legends fan
