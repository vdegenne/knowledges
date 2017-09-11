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