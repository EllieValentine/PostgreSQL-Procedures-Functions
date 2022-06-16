## Function that returns a table

The function returns all columns of the table for records matching the given criteria.

<pre>
CREATE OR REPLACE FUNCTION function_name(
    argument integer)
RETURNS SETOF table.name 

LANGUAGE plpgsql AS $$

BEGIN
    RETURN 
        QUERY 
          SELECT 
              *
          FROM 
              table.name 
          WHERE 
              condition1 = false 
              AND (condition2 = false 
              AND condition3 = true 
              AND condition4 < argument)
              ORDER BY "createdAt" ASC;

END;
$$
</pre>

Calling the function

<pre>
SELECT * from function_name ('argument')
</pre>
