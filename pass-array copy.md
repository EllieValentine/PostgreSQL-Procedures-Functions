## Function that takes an array as an argument and returns a table

The function takes an array as an argument and returns all columns of the table for records matching the values from the array.

<pre>
CREATE OR REPLACE FUNCTION function_name(
    IN _id character varying[])
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
              ("id" = ANY (_id))
              ORDER BY "createdAt" ASC;

END;
$$
</pre>

Calling the function

<pre>
SELECT * from function_name(array['id1','id2','id3'...,,'idn'])
</pre>
