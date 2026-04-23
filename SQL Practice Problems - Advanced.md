SQL Practice Problems - Advanced  



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



* Find students whose final grade is above the overall average



Select \*

from students

where final\_grade > (

select avg(final\_grade)

from students

);



* Find students with attendance below the average of their gender



Select \*

from students as s1

where attendance\_pct < (

select  avg(attendance\_pct)

from students as s2

Where s2.gender = s1.gender

);



&nbsp;- Correlated subquery: s2.gender = s1.gender ensures we compare within the same gender.



* Rank students by final grade (highest to lowest)



Select \*,

rank() over (order by final\_grade desc)

from students;



* Rank students within each gender



Select \*,

rank() over (Partition by gender order by final\_grade desc)

from students;



&nbsp;- PARTITION BY creates separate ranking sequences for male and female students.



* Show each student’s final grade and the average grade of their gender



Select \*,

Avg(final\_grade) over (partition by gender)

from students;



&nbsp;- AVG() OVER (PARTITION BY ...) calculates the average without collapsing rows.



* For each attendance bucket:

&nbsp;-<70

&nbsp;-70–85

&nbsp;- >85

find number of students and average grade



&nbsp;SELECT 

&nbsp;   CASE 

&nbsp;       WHEN attendance\_pct < 70 THEN '<70'

&nbsp;       WHEN attendance\_pct BETWEEN 70 AND 85 THEN '70-85'

&nbsp;       ELSE '>85'

&nbsp;   END AS attendance\_bucket,

&nbsp;   COUNT(\*) AS num\_students,

&nbsp;   AVG(final\_grade) AS avg\_final\_grade

FROM students

GROUP BY attendance\_bucket;

