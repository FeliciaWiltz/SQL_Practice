SQL Practice Problems - Intermediate 



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





* Find the average final grade



Select avg(final\_grade)

from students;



* Find the minimum and maximum attendance



Select Max(attedance\_pct), Min(attendance\_pct)

from students;



* Count how many students are in the dataset



Select count(\*)

from students;



* Average final grade by gender



Select gender, avg(final\_grade)

from students

group by gender;



* Average attendance by parental\_support



Select parental\_support, avg(attendance\_pct)

from students

group by parental\_support;



* Count students by online\_classes\_taken



select online\_classes\_taken, count(\*)

from students

group by online\_classes\_taken; 



* Show only parental support groups with average final grade > 80



Select parental\_support, avg(final\_grade)

from students

group by parental\_support

having avg(final\_grade) > 80;



* Find genders with more than 20 students



select gender, count(\*)

from students

groupy by gender

having count(\*) > 20;





&nbsp;- SELECT \* is not allowed with GROUP BYEvery selected column must be:

in GROUP BY, or aggregated



\- In most SQL databases, you cannot use a SELECT alias (avg\_grade) inside HAVING.

