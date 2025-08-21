## 💡 Example Usage

### Quickstart
```bash
# 1. Initialise local workspace (~/.federate)
federate init
```

```bash
# Query data with a plan
./federate query --plan examples/dedupe.yaml --root-dataset author_books 
```

## Example Plan

```yaml
storage:
  type: sqlite

# DATASOURCES: Define where and how to access data (connections)
datasources:
  # PostgreSQL connection for books data  
  - name: books_db
    type: POSTGRES
    connection:
      host: localhost
      port: 5432
      database: books
      username: user
      password: password
      ssl_mode: disable
    desc: "Books PostgreSQL database"
  
  - name: authors_db
    type: POSTGRES
    connection:
      host: localhost
      port: 5432
      database: authors
      username: user
      password: password
      ssl_mode: disable
    desc: "Authors PostgreSQL database"

  # Special datasource for JOIN operations (federated queries)
  - name: federated
    type: JOIN
    connection: {}
    desc: "Federated datasource for JOIN operations"

# DATASETS: Define how to process and translate data (plugins)
datasets:
  # Extract books from PostgreSQL using SQL plugin
  - name: books
    datasource_name: books_db
    type: SQL
    query: "SELECT name as title, author, review FROM books"
    config:
      timeout: 30
  
  - name: authors
    datasource_name: authors_db
    type: SQL
    query: "SELECT id, slug, name, bio FROM authors"
    dedupe_key:
     - id
     - slug
    config:
      timeout: 30

  # JOIN operation using the federated datasource
  - name: author_books
    datasource_name: federated
    type: SQL
    query: |
      SELECT a.name, b.title as title, b.review FROM authors a JOIN books b ON a.slug = b.author
    config:
      timeout: 60
    children:
      - dataset_name: authors
      - dataset_name: books
```

