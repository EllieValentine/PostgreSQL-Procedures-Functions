## Function that updates a record

The function updates a record matching the given criteria.

<pre>
CREATE OR REPLACE FUNCTION function_name(
	IN argument1 character varying,
	IN argument2 character varying,
	IN argument3 character varying
	)
RETURNS boolean 
LANGUAGE plpgsql AS $$

DECLARE
    _tupdate bigint;
BEGIN
	_tupdate := ROUND(extract(epoch from now())::bigint;
	
	UPDATE table.name SET
		field3 = argument3,
		updated_at = "_tupdate"
		where field1 = argument1 AND field2 = argument2;
		
    RETURN FOUND;
END;
$$
</pre>

Calling the function

<pre>
SELECT * from function_name ('argument1','argument2','argument3')
</pre>
