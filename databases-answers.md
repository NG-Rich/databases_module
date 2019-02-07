1. What data types do each of these values represent?

  1) "A Clockwork Orange"
  2) 42
  3) 09/02/1945
  4) 98.7
  5) $15.99

Number 1 represents a text data type (tinytext). Number 2, 4, and 5 represent numeric data types (tinyint, decimal, and money, respectively). Number 3 represents a date and time data type (date).

2. Explain when a database would be used. Explain when a text file would be used.

We would generally want to use a database when we want to handle small to large amounts of data with the ease of being able to manipulate it with relative ease. A text file would be used when we want to manipulate code, such as arrays or blocks of code.

3. Describe one difference between SQL and other programming languages.

The one difference between SQL and other programming languages is how you work with it. SQL is declarative, rather than other languages where it's procedural. We're more worried about what we want to find out rather than how we want the program to find it out for us.

4. In your own words, explain how the pieces of a database system fit together at a high level.

I'm not entirely sure what this question means, but I can attempt to answer it as best as I'm understand it. Pieces of a database system fit together at a high level because it can provide an abundance of information for specific categories that can be accessed and managed easily. For example, if you wanted to find a specific set of users in a member list that signed up during a specific date, you can do that. However, if you wanted to find that information as well as display their emails then that's possible as well. It can all be done with relative ease since you have all that information in a database system.

5. Explain the meaning of table, row, column, and value.

A table is the database that is separated into rows and columns.
Rows are what each individual's data is displayed as a whole, with columns separating the information into their specific categories.
Columns are the specific categories in which they list all the information that pertain said category (Columns all contain text but have different meanings).
Value would be the piece of information that describe the column/row or in each cell.

6. List three data types that can be used in a table.

text, date, time

7. Given this payments table, provide an English description of the following queries and include their results:

`    SELECT date, amount
     FROM payments;

     SELECT amount
     FROM payments
     WHERE amount > 500;

     SELECT *
     FROM payments
     WHERE payee = 'Mega Foods';
`

The first query asks to return data from the date and amount (to the fourth decimal) column in the payments table.

`   2016-05-01	1500.0000
    2016-05-10	37.0000
    2016-05-15	124.9300
    2016-05-23	54.7200
`

The second query asks to return data from the amount column where the value is greater than 500 from the payments table.

`   1500.0000
`

The final query returns all the data (date, payee, amount, memo) where the payee is to 'Mega Foods' from the payments table.

`   2016-05-15	Mega Foods	124.9300	Groceries
`

8. Given this users table, write SQL queries using the following criteria and include the output:

• The email and sign-up date for the user named DeAndre Data.
• The user ID for the user with email 'aleesia.algorithm@uw.edu'.
• All the columns for the user ID equal to 4.

`   SELECT email, signup
    FROM users
    WHERE name = 'DeAndre Data';

    SELECT userid
    FROM users
    WHERE email = 'aleesia.algorithm@uw.edu';

    SELECT *
    FROM users
    WHERE userid = 4;
`

`   datad@comcast.net	2008-01-20

    1

    4	Brandy Boolean	bboolean@nasa.gov	1999-10-15
`
