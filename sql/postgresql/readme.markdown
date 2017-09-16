## statements

- `IN` and `any` are the same [stackoverflow.com/postgresql-in-vs-any](https://stackoverflow.com/questions/30263671/postgresql-in-vs-any "stackoverflow")

## <a name="commits"></a> commits and rollbacks

postgresql is auto-rolling-back on commits' fails. It means we can't make our own custom rolling-back strategy on the back-end (for the good ?). See my answer on this post for how to extend exception handling on rollbacks : [How can I tell PostgreSQL not to abort the whole transaction when a single constraint has failed?](https://stackoverflow.com/questions/9436122/how-can-i-tell-postgresql-not-to-abort-the-whole-transaction-when-a-single-const/46229608#46229608).  
Rollback means changing the data back to its original state, even the one changed from triggered procedures.

## functions

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

## sqlstate

When postgresql throws an exception it also sends a sqlstate back to the process that invoked the transaction. That means you can use that code to handle proper actions to specific exceptions. You can also make your own codes (for example, in user-defined triggers) :

```plpgsql
raise exception 'exception message' using errcode='12345';
```
*(note : the errcode needs to be 5bits long.)*

An example of how to use the code on a back-end program : 

## save and recovery

### pg_dump

```
$ pg_dump -h <host> -F<format> -n <schema> <databasename> > <dumpfile>
```

### pg_restore

```
$ pg_restore -d <databasename> <dumpfile>
```
**-d <databasename>** : the databasename needs to point an existing database. We can use `$ createdb <databasename>` to create one.

**<dumpfile>** refers to a file generated from pg_dump (it can be a custom-file, a tar, or a plain generated file).