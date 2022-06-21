## Simple delete function

The function takes a variable and an array as arguments and deletes all records matching the variable and the values from the array at the same time.

<pre>
CREATE OR REPLACE FUNCTION function_name(
    IN _variable varchar(255),
	IN _array character varying[]
	)
RETURNS Boolean

LANGUAGE plpgsql AS $$

BEGIN
	delete 
		from public.tags
		WHERE
		 "uid" = _uid AND ("id" = ANY (_tagsid));
  RETURN FOUND;

END;
$$
</pre>

Calling the function

<pre>
SELECT * from function_name('variable',array['id1','id2','id3'...,,'idn'])
</pre>

Example. Delete classes for a student who decided to drop

<pre>
SELECT * from function_name('Student Name',array['class1','class2','class3'])
</pre>
