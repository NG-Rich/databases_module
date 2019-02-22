1. How do you find related data held in two separate data tables?

You used the JOIN clause to find related data in separate data tables.

2. Explain, in your own words, the difference between an INNER JOIN, LEFT OUTER JOIN, and RIGHT OUTER JOIN. Give a real-world example for each.

• INNER JOIN is the default when you just use the JOIN clause. It only displays results that matches the condition. A list of those who filled up their tank of gas and purchased a carwash.

• LEFT OUTER JOIN displays results of the two tables that matches the condition as well as data from the first/left table. An example could be a list of students and the same homeroom teacher to the right.

• RIGHT OUTER JOIN displays results of the two tables that matches the condition as well as data from the second/right table. An example would be a list of library card holders and their information joined by a table of books and those that are checked out.

3. Define primary key and foreign key. Give a real-world example for each.

• Primary key is a unique identifier in a table and it's referred to by the foreign key and it exists once throughout the table. An example would be a movie title and a list of theaters that show the movie.

• Foreign key is a field of data that refers to a primary key that identifies the relation between the two tables. An example would be a list of theaters that have the same movie title showing.

4. Define aliasing.

Abbreviating table names to simplify creating statements. It's helpful when you have a multitude of table names you want to compare/display and it makes it easier on your end.

5. Change this query so that you are using aliasing:

`SELECT professor.name, compensation.salary,
compensation.vacation_days FROM professor JOIN
compensation ON professor.id =
compensation.professor_id;
`

`SELECT p.name, c.salary, c.vacation_days FROM professor AS p JOIN compensation AS c ON p.id = c.professor_id;
`

6. Why would you use a NATURAL JOIN? Give a real-world example.

We would want to use NATURAL JOIN if we wish to display columns of the same name between two tables. We'd opt to use this over USING if we wish to not create a list of the shared columns.

7. Using this Employee schema and data, write queries to find the following information:

• List all employees and all shifts.
`SELECT e.name, s.date, s.start_time, s.end_time FROM employees AS e JOIN scheduled_shifts ON e.id = scheduled_shifts.employee_id JOIN shifts AS s ON s.id = scheduled_shifts.shift_id;
`

8. Using this Adoption schema and data, please write queries to retrieve the following information and include the results:

• Create a list of all volunteers. If the volunteer is fostering a dog, include each dog as well.
`SELECT v.first_name, v.last_name, d.name FROM volunteers AS v LEFT OUTER JOIN dogs AS d ON v.foster_dog_id = d.id;

first_name  last_name   name
Rubeus	    Hagrid	    Munchkin
Marjorie	  Dursley	    Marmaduke
Sirius	    Black	      null
Remus	      Lupin	      null
Albus	      Dumbledore  null
`
• The cat's name, adopter's name, and adopted date for each cat adopted within the past month to be displayed as part of the "Happy Tail" social media promotion which posts recent successful adoptions.
`SELECT c.name, a.first_name, a.last_name, cat_adoptions.date FROM adopters AS a JOIN cat_adoptions ON a.id = cat_adoptions.adopter_id JOIN cats AS c ON c.id = cat_adoptions.cat_id WHERE cat_adoptions.date > CURRENT_DATE - INTERVAL '30 Days';

name	   first_name	 last_name	date
Mushi	   Arabella	   Figg	      2019-01-31
Victoire Argus	     Filch	    2019-02-05
`

• Create a list of adopters who have not yet chosen a dog to adopt.
`SELECT a.first_name, a.last_name FROM adopters AS a JOIN dog_adoptions ON a.id != dog_adoptions.adopter_id;

| first_name | last_name |
| ---------- | --------- |
| Hermione   | Granger   |
| Arabella   | Figg      |
`

• Lists of all cats and all dogs who have not been adopted.
`SELECT cats.name FROM cats LEFT JOIN cat_adoptions ON cats.id = cat_adoptions.cat_id WHERE cat_adoptions.cat_id IS NULL;

| name     |
| -------- |
| Seashell |
| Nala     |

SELECT dogs.name FROM dogs JOIN dog_adoptions ON dogs.id != dog_adoptions.dog_id;

| name      |
| --------- |
| Boujee    |
| Munchkin  |
| Marley    |
| Lassie    |
| Marmaduke |
`

• The name of the person who adopted Rosco.
`SELECT a.first_name, a.last_name FROM adopters AS a JOIN dog_adoptions ON a.id = dog_adoptions.adopter_id;

| first_name | last_name |
| ---------- | --------- |
| Argus      | Filch     |
`

9. Using this Library schema and data, write queries applying the following scenarios and include the results:

• To determine if the library should buy more copies of a given book, please provide the names and position, in order, of all of the patrons with a hold (request for a book with all copies checked out) on "Advanced Potion-Making".
`SELECT p.name, h.rank FROM patrons AS p JOIN holds AS h ON p.id = h.patron_id WHERE h.isbn = '9136884926';

| name           | rank |
| -------------- | ---- |
| Terry Boot     | 1    |
| Cedric Diggory | 2    |

I noticed that Terry placed a hold on the book, but he also checked it out a day before. So I didn't know if that was on purpose and you wanted me to make the query accordingly, but I made the statement as asked directly. I can definitely change it if it's not entirely accurate.
`

• List all of the library patrons. If they have one or more books checked out, list the books with the patrons.
`SELECT p.name, b.title FROM transactions AS t LEFT JOIN books AS b ON t.isbn = b.isbn AND t.checked_in_date IS NULL JOIN patrons AS p ON p.id = t.patron_id;

| name             | title                                   |
| ---------------- | --------------------------------------- |
| Hermione Granger |                                         |
| Cho Chang        |                                         |
| Terry Boot       |                                         |
| Padma Patil      |                                         |
| Terry Boot       | Advanced Potion-Making                  |
| Hermione Granger |                                         |
| Cedric Diggory   | Fantastic Beasts and Where to Find Them |
`
