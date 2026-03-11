# Discogs Music Database

Relational database built from the Discogs public data dump using PostgreSQL. Models 27+ tables across artists, releases, labels, and genres — including full schema design, ETL data import, and analytical SQL queries.

## Tech Stack
- PostgreSQL 18
- pgAdmin 4

## Schema Overview
Tables include: `artist`, `artist_alias`, `artist_url`, `artist_image`, `artist_namevariation`, `group_member`, `release`, `label`, `genre`, and more.

## Getting Started
1. Download the Discogs data dump from [data.discogs.com](https://data.discogs.com/)
2. Create a PostgreSQL database called `discogs`
3. Run `discogs_schema.sql` to create the table structure
4. Import the Discogs data into the schema

## Sample Queries
**Artists with the most group memberships:**
```sql
SELECT a.name, COUNT(*) as group_count
FROM group_member gm
JOIN artist a ON a.id = gm.member_artist_id
GROUP BY a.name
ORDER BY group_count DESC
LIMIT 10;
```

## Data Source
Data sourced from the [Discogs monthly data dump](https://data.discogs.com/).
