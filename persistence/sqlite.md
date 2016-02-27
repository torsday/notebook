# SQLite

## Methods

### GROUP BY

## Ruby Config

### `results_as_hash`

*From: [RubyDoc](http://www.rubydoc.info/github/luislavena/sqlite3-ruby/SQLite3%2FDatabase%3Aresults_as_hash)*
> A boolean that indicates whether rows in result sets should be returned as hashes or not. By default, rows are returned as arrays.

```ruby
@db = SQLite3::Database.new <path_to_db>

@db.results_as_hash = true
```

## Examples

### Get all URLS updated in the past 10 days

```sqlite
SELECT * FROM Urls WHERE UpdatedAt >= date('now','-10 day');
```

### Update value for rows updated in past 10 days

```sqlite
UPDATE Urls
SET Downloaded = 0
WHERE UpdatedAt >= date('now','-10 day');
```

### Group, count, and sort

```sqlite
SELECT *, count(Url)
FROM Urls
GROUP BY HttpCode
ORDER BY count(Url) DESC;
```
