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

## Table 2: Purchases

### Table purpose

The purchases table records every fictional product purchase made by a player.

### Table grain

One row represents one purchase transaction.

### Primary key

`purchase_id`

### Foreign key

`player_id`

The `player_id` field connects each purchase to one record in the players
table.

### Fields

| Field | Data type | Description | Example |
|---|---|---|---|
| purchase_id | Text | Unique purchase identifier | O000001 |
| player_id | Text | Player who made the purchase | P00001 |
| purchase_date | Date | Date of the transaction | 2026-01-22 |
| product_type | Text | Type of Riftbound product purchased | Champion Deck |
| amount_usd | Decimal | Modeled transaction amount in US dollars | 19.99 |
| purchase_channel | Text | Where the purchase occurred | Local game store |

### Product-type values

- Champion Deck
- Proving Grounds
- Booster Pack
- Booster Bundle

### Purchase-channel values

- Local game store
- Online retailer
- Mass retailer
- Convention
