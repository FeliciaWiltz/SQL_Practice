SQL Practice Problems - Challenging 



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





**Risk detection**



* Create a query that flags students as "High Risk" if:



&nbsp;- attendance < 70



&nbsp;- AND study\_hours\_per\_week < 10



&nbsp;- AND final\_grade < 70



SELECT \*,

&nbsp;      CASE

&nbsp;          WHEN attendance\_pct < 70 

&nbsp;               AND study\_hours\_per\_week < 10 

&nbsp;               AND final\_grade < 70

&nbsp;          THEN 'High Risk'

&nbsp;          ELSE 'Not High Risk'

&nbsp;      END AS risk\_status

FROM students;





**“What-if” analysis**



* Increase final grades by 5 points for students with:



&nbsp;- attendance > 90



&nbsp;- parental\_support = 'High'



&nbsp;- Cap grades at 100



UPDATE students

SET final\_grade = LEAST(final\_grade + 5, 100)

WHERE attendance\_pct > 90

&nbsp; AND parental\_support = 'High';



or 



SELECT \*,

&nbsp;      LEAST(final\_grade + 5, 100) AS adjusted\_final\_grade

FROM students

WHERE attendance\_pct > 90

&nbsp; AND parental\_support = 'High';



&nbsp;- LEAST(final\_grade + 5, 100) ensures the grade does not exceed 100.





**Data quality report**



* Write a query that returns:



&nbsp;- Total rows



&nbsp;- Rows with missing critical fields



&nbsp;- Rows with invalid grades



&nbsp;- Rows with invalid attendance



SELECT

&nbsp;   COUNT(\*) AS total\_rows,

&nbsp;   SUM(CASE WHEN final\_grade IS NULL OR attendance\_pct IS NULL THEN 1 ELSE 0 END) AS missing\_critical\_fields,

&nbsp;   SUM(CASE WHEN final\_grade < 0 OR final\_grade > 100 THEN 1 ELSE 0 END) AS invalid\_grades,

&nbsp;   SUM(CASE WHEN attendance\_pct < 0 OR attendance\_pct > 100 THEN 1 ELSE 0 END) AS invalid\_attendance

FROM students;



&nbsp;- SUM(CASE WHEN ... THEN 1 ELSE 0 END) is a standard pattern to count conditions in one row.





