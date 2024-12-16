# sqlite-template

## Installing sqlite
Developers should have sqlite installed in their local machine.

* For Mac users, you can install sqlite via homebrew:

```bash
brew install sqlite3
```

* For Linux users:

```bash
sudo apt update
sudo apt install sqlite3
```

## Usage
This template repository consists one file:

1. `init.sql`:  contains sql statements for create database objects (tables and indexes) and seeding the database objects with sample rows.

Please follow the below instructions to initialize a database.

Run the following command to initialize a sqlite database from the initialization script:

```bash
sqlite3 {your_db_name}.db < init.sql
```

To use the database run the following to enter into the sqlite console:

```bash
sqlite3 {your_db_name}.db
```

Our initialized tables contain foreign keys, and foreign key constraints are disabled in sqlite by default. To enable them, run the following:
```
> PRAGMA FOREIGN_KEYS = ON;
```

Confirm the change by ensuring the output to the below command is `1`:
```
> PRAGMA FOREIGN_KEYS;
```

Within the console you can also run the following and confirm the tables from the initialization script were created:

```
> .tables
```

## Schemas

Below are the schemas for the tables used in this exercise

### Organizations Table

| name | datatype | nullable | indexed |
| ----- | ----- | ----- | ----- |
| organization_id (PK) | integer | N | Y |
| name (unique constraint) | varchar(100) | N | Y |
| url | varchar(50) | Y | N |
| email | varchar(50) | Y | N |


### Locations Table
| name | datatype | nullable | indexed |
| ----- | ----- | ----- | ----- |
| location_id (PK) | integer | N | Y |
| organization_id (FK) | integer | N | Y |
| street_address | varchar(100) | N | N |
| street_address_2 | varchar(100) | Y | N |
| city | varchar(100) | N | N |
| province | varchar(100) | N | N |
| country | varchar(50) | N | Y |
| country_code | varchar(3) | N | Y |
| postal_code | varchar(20) | N | N |