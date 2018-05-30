# Postgresql

## Installation (fait sur Fedora 26)
Toutes les [instructions et détails](https://fedoraproject.org/wiki/PostgreSQL).

- on installe les paquets
```bash
sudo dnf install postgresql-server postgresql-contrib
```
- on initialise l'environnement
```bash
sudo postgresql-setup --initdb --unit postgresql
# sudo initdb -E UTF8
```
- on active le daemon
```bash
sudo systemctl start postgresql
sudo systemctl enable postgresql # pour le démarrer à chaque boot
```
---
- on change le mot de passe par défaut de postgres
```bash
sudo -u postgres psql

postgres=# alter user postgres password 'newPassword';
```
- on crée un nouvel utilisateur
```bash
postgres=# CREATE USER john WITH PASSWORD 'helloworld';
postgres=# CREATE DATABASE johndb OWNER john;
```
- on modifie `/var/lib/pgsql/data/pg_hba.conf` pour se connecter en `md5` ou en `peer`.
- Si on se connecte en `peer`, on doit aussi modifier le mot de passe de l'utilisateur Unix `postgres` automatiquement créer dans les étapes précédentes.
```bash
sudo passwd postgres
```

### Upgrade
```bash
sudo postgresql-setup upgrade # si postgresql est déjà installé et qu'on souhaite juste faire une mise à jour
```

## statements

- `IN` and `any` are the same [stackoverflow.com/postgresql-in-vs-any](https://stackoverflow.com/questions/30263671/postgresql-in-vs-any "stackoverflow")

## <a name="commits"></a> commits and rollbacks

postgresql is auto-rolling-back on commits' fails. It means we can't make our own custom rolling-back strategy on the back-end (for the good ?). See my answer on this post for how to extend exception handling on rollbacks : [How can I tell PostgreSQL not to abort the whole transaction when a single constraint has failed?](https://stackoverflow.com/questions/9436122/how-can-i-tell-postgresql-not-to-abort-the-whole-transaction-when-a-single-const/46229608#46229608).  
Rollback means changing the data back to its original state, even the one changed from triggered procedures.

## Functions

### examples

**language sql**

```sql
CREATE OR REPLACE FUNCTION schema.myfunction(IN search text)
  RETURNS TABLE(id integer) AS
$BODY$
select id
from schema.table
where name ilike '%'||search||'%'
   or description ilike '%'||search||'%';
$BODY$
  LANGUAGE sql VOLATILE
  COST 100
  ROWS 1000;
```

## triggers
### examples
```sql
create function schema.add_after_insert ()
  returns trigger as $$
begin
if (TG_OP = 'DELETE') then
  ...
  return old;
end if;

insert into schema.t2 values (...);
return null; -- a trigger needs a return statement, use "null" in an AFTER trigger if nothing is to be returned or else "NEW" or "OLD"

end; $$
  language plpgsql;

create trigger tafter after insert or update or delete on schema.t1
  for each row
  [when (pg_trigger_depth() = 0)] -- we can use that if triggers trigger others triggers, and need to prevent a recursive loop (see note #2).
  execute procedure test.add_after_insert();
```
 
*note : the data changed from triggers will also get rolled-back on commits' fails. See [commits and rollbacks](#commits)*  
*note #2 : [origin](https://stackoverflow.com/a/14262289/773595)*

We can use useful constant inside the trigger procedure :

- **TG_OP** : the operation that triggered the procedure ('DELETE', 'UPDATE', 'INSERT', ...)
- **TG_TABLE_NAME** : the table name that triggered the procedure.
- **user** : the current connected user (e.g. 'postgres').

## sqlstate

When postgresql throws an exception it also sends a sqlstate back to the process that invoked the transaction. That means you can use that code to handle proper actions to specific exceptions. You can also make your own codes (for example, in user-defined triggers) :

```plpgsql
raise exception 'exception message' using errcode='12345';
```
*(note : the errcode needs to be 5bits long.)*

An example of how to use the code on a back-end program : 


## case structure

### example
```sql
SELECT a,
       CASE WHEN a=1 THEN 'one'
            WHEN a=2 THEN 'two'
            ELSE 'other'
       END
    FROM test;
```
*(from [postgresql.org/docs](https://www.postgresql.org/docs/7.4/static/functions-conditional.html))*

## Save & Recovery (`pg_dump` & `pg_restore`)

```bash
pg_dump -Fc database > database.backup
# Will save all objects of the "database" in database.backup (custom)
# We can then use :
pg_restore -Fc -d database database.backup
# To recreate all objects in the "database"
pg_restore -Fc -c -d database database.backup
# To clean all the existing objects first before recreating them again
# OR
pg_restore -Fc -C -d anotherDatabase -c database.backup
# This will recreate the "database" saved in the "database.backup" and use
# the database "anotherDatabase" to issue the DROP and CREATE command.
# If the database specified by -d is the same as the one saved in the "database.backup"
# the command will fail.
### All commands above are ok if the user invoking the command is owner of
### all the objects in the database.

### If some objects are owned by another administrator (e.g. postgres)
### We can use :
pg_restore -Fc -U postgres -d database database.backup
# To recreate all objects in the database

### Other useful options
pg_dump -a --inserts database > database.sql
# Will just save the data and will use INSERT instead of COPY (plain)

pg_dump --section=pre-data --section=post-data database > database.sql
# Saving pre-data and post-data section (plain)
```
