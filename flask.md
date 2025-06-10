# Running app

```console
$ flask --app <app name> run
```

OR

```console
$ export FLASK_APP=<app name>
$ flask run
```

OR

```console
$ python <app>.py
```

# Tips and Tools

## Random Text Generator (secrets module)

```python
>>> import secrets
>>> secrets.token_hex(<byte>)
```

## Use Virtual Environment

```console
$ python -m venv venv
```

# SQLAlchemy

## `db.Relationship()`

### `lazy` Parameter

Lazy parameter determines how the related objects get loaded when querying
through relationships.

- `lazy='select'` (or `True`) (default)\
  It emits a `SELECT` statement
- `lazy=dynamic`

## `db.create_all()`

It is the command that creates database tables based on the models or classes
defined in your application.<br>

When your run your application and call `db.create_all()` _for the first time_,
it will create the necessary tables. Subsequent runs _won't_ recreate the tables
if they already exist.

- Model Definitions
- Database initialization
- Table creation

## `extract()`

## Python REPL Examples (GymLog)

```python
>>> from app import app, db
>>> app.app_context().push()
>>> db.create_all()
>>> from app import GymClass, Attendance
>>>
```

# flask-migrate

## How to add `flask-migrate` to an existing project?

1. At root directory, init the package
   ```console
   $ flask db init
   ```

   This command **creates** the database.

2. Run the initial migration
   ```console
   $ flask db migrate -m "Initial migration"
   ```

   This command **detects** differences between the current **database** and
   **models** defined in your files, and **generates** migration script if there
   are any.

   a. If database has already been created - for example, by `db.create_all()` -
   the command won't detect any changes, thus generating nothing\
   `INFO  [alembic.env] No changes in schema detected.`

   Workaround: compare models to an empty database
   ```console
   $ export DATABASE_URL=sqlite:///
   ```
   This command creates an empty database in memory.

3. Run the upgrade. This command applies changes in the migration script to the
   database.
   ```console
   $ flask db upgrade
   ```

   a. If the database already exists and matches the current models, you can
   stamp the current database.
   ```console
   $ flask db stamp head
   ```

   This command adds the alembic metadata to the database to indicate that the
   database is updated to the latest provision. Basically, stamp this database
   with the HEAD revision.

## How to migrate future changes?

A new column has been added to the table --

1. Generate migration script
   ```console
   $ flask db migrate
   ```
2. Apply migration
   ```console
   $ flask db upgrade
   ```
