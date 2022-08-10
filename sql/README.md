# **SQL**

- [Query Example](#query-example)
- [sqlc setting](#sqlc-setting)

## ***query example***

```sql
-- Filter by condition
WITH filtered_user AS (SELECT * FROM users WHERE gender = $1),
-- 
total_count AS (SELECT COUNT(1) AS total_count FROM filtered_user),
-- Paginated
paginated_user AS (
SELECT *
FROM filtered_user
ORDER BY (
    CASE
    WHEN COALESCE($4, '') = 'male' THEN created_at
    ELSE THEN updated_at END
) DESC
OFFSET $2 :: int
LIMIT $3 :: int
)
-- Start Query
SELECT user.*, (SELECT total_count FROM total_count) AS total_count
FROM user
INNER JOIN paginated_user USING(id)
ORDER BY (
    CASE
    WHEN COALESCE($4, '') = 'male' THEN created_at
    ELSE THEN updated_at END
) DESC;
```

## ***sqlc setting***

```sh
$ cat sqlc.yaml 
version: 1
packages:
  - path: "db"
    name: "db"
    engine: "postgresql"
    schema: "schema.sql"
    queries: "query.sql"

$ sqlc generate

$ tree
.
├── cmd
│   └── main.go
├── db
│   ├── db.go
│   ├── models.go
│   └── query.sql.go
├── go.mod
├── go.sum
├── query.sql
├── schema.sql
└── sqlc.yaml

```
