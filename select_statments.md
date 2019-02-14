1. Write out a generic SELECT statement.
`SELECT column_name FROM table_name WHERE column_name LIKE 'The%';`

2. Create a fun way to remember the order of operations in a SELECT statement, such as a mnemonic.
`SELECT FROM your mind WHERE the answers lie, the order of operations is LIKE this statement gone by.`

3. Given this dogs table, write queries to select the following pieces of data:

`Intake teams typically guess the breed of shelter dogs, so the breed column may have multiple words (for example, "Labrador Collie mix").`

• Display the name, gender, and age of all dogs that are part Labrador.
`SELECT name, gender, age FROM dogs WHERE breed LIKE 'labrador%';`
• Display the ids of all dogs that are under 1 year old.
`SELECT id FROM dogs WHERE age < 1;`
• Display the name and age of all dogs that are female and over 35lbs.
`SELECT name, age FROM dogs WHERE gender = 'F' AND weight > 35;`
• Display all of the information about all dogs that are not Shepherd mixes.
`SELECT * FROM dogs WHERE breed NOT LIKE '%shepherd%';`
• Display the id, age, weight, and breed of all dogs that are either over 60lbs or Great Danes.
`SELECT id, age, weight, breed FROM dogs WHERE weight > 60 OR breed LIKE '%great dane%';`

4. Given this cats table, what records are returned from these queries?

• SELECT name, adoption_date FROM cats;
The name and adoption date columns in the cats table are returned.

• SELECT name, age FROM cats;
The name and age columns from the cats table are returned.

5. From the cats table, write queries to select the following pieces of data.
• Display all the information about all of the available cats.
`SELECT * FROM cats WHERE adoption_date IS NULL;`
• Display the name and sex of all cats who are 7 years old.
`SELECT name, gender FROM cats WHERE age = 7;`
• Find all of the names of the cats, so you don’t choose duplicate names for new cats.
`SELECT name FROM cats;`

6. List each comparison operator and explain when you would use it. Include a real world example for each.

  • The < operator would be used when we wish to return results that have values less than the expression we are comparing it to. Display money that is less than a certain amount. `SELECT * FROM bank WHERE amount < 1000;`

  • The > operator would be used when we wish to return results that have values greater than the expression we are comparing it to. Display money that is greater than a certain amount. `SELECT * FROM bank WHERE amount > 1000;`

  • The <= operator would be used when we want to return results that have values less than or equals to the expression we are comparing it to. Displaying weight that may be less than or equals to a certain value. `SELECT * FROM boxers WHERE weightclass <= 200;`

  • The >= operator is used when we want results that have values greater than or equals to the expression we are comparing it to. Displaying weight that may be greater than or equals to a certain value. `SELECT * FROM boxers WHERE weightclass >= 200;`

  • The = operator would be used when we want to compare the expression to match the exact value(s). If we want to display a string that may match the exact text. `SELECT * FROM library WHERE author = 'D. Darwin';`

  • The <>/!= operator is used when we want to compare values that aren't equal to the expression. Displaying data that isn't equals to the exact string. `SELECT * FROM library WHERE author != 'D. Darwin';`

7. From the cats table, what data is returned from these queries?

• SELECT name FROM cats WHERE gender = ‘F’;
  Displays name of cats that are female
• SELECT name FROM cats WHERE age <> 3;
  Displays name of cats where their age is less than or greater than 3
• SELECT ID FROM cats WHERE name != ‘Mushi’ AND gender = ‘M’;
  Displays the id of cats whose names aren't Mushi and gender being male
