SQL Practice Problems - Cleaning 



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





* Find students with NULL final grades



Select \*

from students

where final\_grade is null;



* Count how many students are missing attendance\_pct



Select count(\*)

from students

where attendance\_pct is null;



* Replace NULL study\_hours\_per\_week with the overall average (use an UPDATE statement)



Update students

set study\_hours\_per\_week = (

select avg(study\_hours\_per\_week)

from students

where study\_hours\_per\_week is not null

&nbsp;)

where study\_hours\_per\_week is null;



* Find students with: attendance < 0 or > 100 and final\_grade < 0 or > 100



SELECT \*

FROM students

WHERE attendance\_pct < 0 OR attendance\_pct > 100;



and 



SELECT \*

FROM students

WHERE final\_grade < 0 OR final\_grade > 100;



* Convert parental\_support to UPPERCASE in the output
* 

SELECT UPPER(parental\_support) AS parental\_support\_upper, \*

FROM students;



* Create a column that labels students as:
* "High Performer" if final\_grade ≥ 85
* "Average Performer" if 70–84
* "At Risk" if < 70
* (Hint: CASE WHEN)



SELECT \*,

&nbsp;      CASE

&nbsp;          WHEN final\_grade >= 85 THEN 'High Performer'

&nbsp;          WHEN final\_grade BETWEEN 70 AND 84 THEN 'Average Performer'

&nbsp;          ELSE 'At Risk'

&nbsp;      END AS performance\_label

FROM students;







