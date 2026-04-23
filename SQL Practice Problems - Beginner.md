SQL Practice Problems - Beginner 



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





* Select all columns for all students.



Select \* 

From Students;



* Select only name, final\_grade, and attendance\_pct.



Select name, final\_grade, attendance\_pct

From Students;



* Find students with final\_grade > 85



Select \*

From Students

where final\_grade > 85;



* Find students with attendance\_pct < 70



Select \*

From Students

where attendance\_pct < 70;



* Find students who took online classes



Select \*

from students

where online\_classes\_taken =True;



* List students ordered by final\_grade (highest first)



Select \*

from students 

order by final\_grade desc;



* List students ordered by study\_hours\_per\_week (lowest first)



Select \*

from students

order by study\_hours\_per\_week asc;



* Show the top 5 students by final grade



Select \*

from students

order by final\_grade desc

limit 5;



* Show the bottom 10 students by attendance



Select \*

from students

order by attendance\_pct asc

limit 10;

