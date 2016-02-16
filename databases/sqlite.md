# SQLite

## `results_as_hash`

*From: [RubyDoc](http://www.rubydoc.info/github/luislavena/sqlite3-ruby/SQLite3%2FDatabase%3Aresults_as_hash)*
> A boolean that indicates whether rows in result sets should be returned as hashes or not. By default, rows are returned as arrays.

```ruby
@db = SQLite3::Database.new <path_to_db>

@db.results_as_hash = true
```
