SQL Practice Problems - Joining tables 



Students Table - 



student\_id

name

gender

attendance\_pct

study\_hours\_per\_week

previous\_grade

final\_grade

parental\_support

extracurricular\_activities

online\_classes\_taken



activities table -



student\_id

activity\_name

hours\_per\_week





* Show student names with their activity names



Select students.name, activities.activity\_name

from students

join activites

on students.student\_id = activities.student\_id;



* Show students who do not have any activities



Select students.name

from students

left join activites

on students.student\_id = activities.student\_id;

where activities.student\_id is null ;



&nbsp;- left join and where statments are typically used for 'missing matches'



* Total extracurricular hours per student



Select students.name, coalesce(sum(activites.hours\_per\_week),0) 

from students

left join activites

on students.student\_id = activities.student\_id

group by students.name;



 - coalesce replace null with 0.

&nbsp; - left joing includes students with no activities



* Average final grade for students with vs without activities



SELECT 

&nbsp;   CASE WHEN a.student\_id IS NULL THEN 'No Activities' ELSE 'Has Activities' END AS activity\_status,

&nbsp;   AVG(s.final\_grade) AS avg\_final\_grade

FROM students s

LEFT JOIN activities a

ON s.student\_id = a.student\_id

GROUP BY activity\_status;



-Always use table aliases (s, a) — cleaner and easier with multiple joins.



\-Use LEFT JOIN if you want to include rows even when there’s no match.



\-Use INNER JOIN if you only care about rows that exist in both tables.



\-Always think about aggregations after joins — sum, avg, count can explode numbers if the join duplicates rows. (GROUP BY fixes this.)



