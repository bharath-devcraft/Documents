### **Access PostgreSQL via Terminal**
---

```markdown

## Switching to PostgreSQL User
- **Switch to the PostgreSQL user (default: postgres)**:  
  ```bash
  sudo su - postgres
  ```

## Accessing PostgreSQL
- **Start PostgreSQL session**:  
  ```bash
  psql
  ```

## Basic Database Commands
- **List all databases**:  
  ```bash
  \l
  ```
- **Connect to a specific database**:  
  ```bash
  \c <database_name>
  ```
- **List tables in the current database**:  
  ```bash
  \dt
  ```
- **List functions in the current database**:  
  ```bash
  \df
  ```
- **List triggers in the current database**:  
  ```bash
  \dy
  ```

## Viewing and Editing Functions and Triggers
- **View a specific function's definition**:  
  ```bash
  \sf <function_name>
  ```
- **Edit a specific function**:  
  ```bash
  \ef <function_name>
  ```
- **View a specific trigger's definition**:  
  ```bash
  \sy <trigger_name>
  ```
- **Edit a specific trigger**:  
  ```bash
  \ey <trigger_name>
  ```

## Extended View Mode
- **Enable expanded view for better readability**:  
  ```bash
  \x
  ```

## Viewing Schemas, Indexes, and More
- **List schemas in the database**:  
  ```bash
  \dn
  ```
- **List indexes in the database**:  
  ```bash
  \di
  ```

## Table Structure and Data
- **Describe a table's structure**:  
  ```bash
  \d <table_name>
  ```
- **Show the structure of a table with extended information**:  
  ```bash
  \d+ <table_name>
  ```
- **List all columns for a table**:  
  ```bash
  \c <table_name>
  ```
- **View data in a table**:  
  ```bash
  SELECT * FROM <table_name>;
  ```

## SQL Queries and Execution
- **Execute SQL queries**:  
  ```bash
  SELECT * FROM <table_name>;
  ```

## Exit and Quit PostgreSQL
- **Quit PostgreSQL session**:  
  ```bash
  \q
  ```

---

### Additional PostgreSQL Useful Commands:
- **View the current user**:  
  ```bash
  SELECT current_user;
  ```
- **Check connection information**:  
  ```bash
  \conninfo
  ```
- **List all roles (users)**:  
  ```bash
  \du
  ```
- **List all sequences**:  
  ```bash
  \ds
  ```

-------------------------------------------------------------------------------------------------------------------

### **Advanced PostgreSQL Commands**

#### Database Management
- **Backup a database**:
  Use the `pg_dump` command to backup the database:
  ```bash
  pg_dump <database_name> > <backup_file>.sql
  ```
- **Restore a database from backup**:
  Use the `psql` command to restore the database:
  ```bash
  psql <database_name> < <backup_file>.sql
  ```
  
#### User and Permission Management
- **Create a new database user**:
  ```sql
  CREATE ROLE <role_name> WITH LOGIN PASSWORD '<password>';
  ```
- **Grant privileges to a user**:
  ```sql
  GRANT ALL PRIVILEGES ON DATABASE <database_name> TO <role_name>;
  ```
- **List all roles and their attributes**:
  ```bash
  \du
  ```
- **Revoke privileges from a user**:
  ```sql
  REVOKE ALL PRIVILEGES ON DATABASE <database_name> FROM <role_name>;
  ```

#### Query Performance and Indexing
- **Analyze a query execution plan**:
  Use `EXPLAIN` or `EXPLAIN ANALYZE` to see the execution plan of a query:
  ```sql
  EXPLAIN ANALYZE SELECT * FROM <table_name>;
  ```
- **List all indexes**:
  ```bash
  \di
  ```
- **Create an index on a table**:
  ```sql
  CREATE INDEX <index_name> ON <table_name> (<column_name>);
  ```
- **Drop an index**:
  ```sql
  DROP INDEX <index_name>;
  ```
- **Vacuum a table** (removes dead rows and optimizes the database):
  ```sql
  VACUUM <table_name>;
  ```
- **Full vacuum for the entire database**:
  ```sql
  VACUUM FULL;
  ```

#### Transaction Management
- **Start a transaction**:
  ```sql
  BEGIN;
  ```
- **Commit a transaction**:
  ```sql
  COMMIT;
  ```
- **Rollback a transaction**:
  ```sql
  ROLLBACK;
  ```

#### Data Import/Export
- **Import data from a CSV file**:
  ```sql
  COPY <table_name> FROM '<file_path>' WITH (FORMAT csv, HEADER);
  ```
- **Export data to a CSV file**:
  ```sql
  COPY <table_name> TO '<file_path>' WITH (FORMAT csv, HEADER);
  ```

#### Advanced Queries
- **Find the size of a specific table**:
  ```sql
  SELECT pg_size_pretty(pg_total_relation_size('<table_name>'));
  ```
- **Find the size of the entire database**:
  ```sql
  SELECT pg_size_pretty(pg_database_size('<database_name>'));
  ```
- **Search for specific strings in your database**:
  Use `pg_catalog` to search for specific strings in the database:
  ```sql
  SELECT * FROM pg_catalog.pg_tables WHERE tablename LIKE '%<search_term>%';
  ```
  
#### Logs and Monitoring
- **View PostgreSQL logs**:
  Use `pg_log` or the system’s log files:
  ```bash
  sudo tail -f /var/log/postgresql/postgresql-<version>-main.log
  ```
- **Check current PostgreSQL settings**:
  ```sql
  SHOW ALL;
  ```

#### Database Clustering and Replication
- **List all replication slots**:
  ```sql
  SELECT * FROM pg_replication_slots;
  ```
- **Create a replication slot** (for logical replication):
  ```sql
  SELECT * FROM pg_create_logical_replication_slot('replication_slot_name', 'test_decoding');
  ```
- **Drop a replication slot**:
  ```sql
  SELECT pg_drop_replication_slot('replication_slot_name');
  ```

#### Advanced Configuration
- **View the database's configuration parameters**:
  ```sql
  SHOW <parameter_name>;
  ```
- **Set the configuration parameter for the current session**:
  ```sql
  SET <parameter_name> = <value>;
  ```
  
### Useful PostgreSQL System Views
- **List all connections to the database**:
  ```sql
  SELECT * FROM pg_stat_activity;
  ```
- **Find slow queries** (long-running queries):
  ```sql
  SELECT * FROM pg_stat_activity WHERE state = 'active' AND now() - query_start > interval '5 minutes';
  ```
- **Check for locked tables**:
  ```sql
  SELECT * FROM pg_locks WHERE granted = 'f';
  ```

### Miscellaneous
- **Enable or disable the query planner’s parallelism**:
  ```sql
  SET max_parallel_workers_per_gather = 0; -- Disable parallelism
  SET max_parallel_workers_per_gather = 4; -- Enable parallelism
  ```
- **Change the schema search path**:
  ```sql
  SET search_path TO <schema_name>;
  ```
  
