## Function that takes a variable and an array as arguments and returns a table

The function takes a variable and an array as arguments and returns all columns of the table for records matching the values from the array.

<pre>
CREATE OR REPLACE FUNCTION function_name(
    IN _variable varchar(255),
	IN _array character varying[]
	)
RETURNS SETOF table.name 

LANGUAGE plpgsql AS $$

BEGIN
    RETURN 
        QUERY 
          SELECT 
               *
          FROM 
              table.name
          where 
			  "actor_name" = "_variable" AND ("genre" = ANY (_array))
              ORDER BY "createdAt" ASC;

END;
$$
</pre>

Calling the function

<pre>
SELECT * from function_name('Elizabeth Taylor',array['comedy','drama','romance'])
</pre>
