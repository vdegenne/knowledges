## statements

- `IN` and `any` are the same [stackoverflow.com/postgresql-in-vs-any](https://stackoverflow.com/questions/30263671/postgresql-in-vs-any "stackoverflow")

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