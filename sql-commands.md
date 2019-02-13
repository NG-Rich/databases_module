1. List the commands for adding, updating, and deleting data.

INSERT INTO, UPDATE, and DELETE FROM.

2. Explain the structure for each type of command.

The structure for adding data would be `INSERT INTO table VALUE (value);`. You have the option for a grouped expression if you plan to add multiple rows of data in a single statement (INSERT INTO table(column_names) VALUES (values)). Depending on how you structured your column values, you simply state the table you wish to add the data to and structure your values to it's corresponding datatypes.

For updating data, it's structured as `UPDATE table SET column_name WHERE value`. With this command you specify the table you wish to update, then you chose what you wish to update and command where to look to find the cell to make the change. Using the update command would mean you would want to be specific in how you wish to update certain data, as you wouldn't want to accidentally update more than your desired cell(s).

Finally, the command to delete data is structured as `DELETE FROM table WHERE column_name<=>value`. I placed `<=>` operators there because you have options as to which operator you'd like to use in specify what data to remove. It's irreversible when you decide you want to delete something so it's best to be careful when using this command. You're also able to use multiple WHERE clauses if you want to be specific in what set of data you wish to remove. `DELETE FROM table WHERE column_name>value AND column_name<value` <- an example

3. What are some of the data types that can be used in tables? Give a real-world example of each type.

Some datatypes that can be used in tables would be `timestamp and timestamptz`. A real-world example for `timestamp` could be data showing the time and date (without time zone) upon a user registering on a website. `timestamptz` could be data that shows the date, time, and time zone in which a user registered on a website.

4. Decide how to create a new table to hold a list of people invited to a wedding dinner. The table needs to have first and last names, whether they sent in their RSVP, the number of guests they are bringing, and the number of meals (1 for adults and 1/2 for children).

• Which data type would you use to store each of the following pieces of information?
  • First and last name.
    `text` data type
  • Whether they sent in their RSVP.
    `bool` data type
  • Number of guests.
    `int` data type
  • Number of meals.
    `float` data type
• Write a command that creates the table to track the wedding dinner.
`CREATE TABLE dinner (
      name text,
      rsvp bool,
      guests int,
      meals float
  );
`
• Write a command that adds a column to track whether the guest sent a thank you card.
`ALTER TABLE dinner ADD COLUMN card bool;`
• You have decided to move the data about the meals to another table, so write a command to remove the column storing the number meals from the wedding table.
`ALTER TABLE dinner DROP COLUMN meals;`
• The guests will need a place to sit at the reception, so write a command that adds a column for table number.
`ALTER TABLE dinner ADD COLUMN table int;`
• The wedding is over and we do not need to keep this information, so write a command that deletes the table numbers from the database.
`DELETE FROM dinner WHERE table > 0;`

5. Write a command to create a new table to hold the books in a library with the columns ISBN, title, author, genre, publishing date, number of copies, and available copies.

`CREATE TABLE library (
    isbn varchar,
    title varchar,
    author varchar,
    genre text,
    published date,
    copies smallint,
    available smallint
  );
`

• Find three books and add their information to the table.
`INSERT INTO library VALUES
('978-1401256821', 'The Multiversity Deluxe Edition', 'Grant Morrison', 'Superhero', '2015-10-21', 3, 2),
('978-0785834205', 'The Complete Fiction of H. P. Lovecraft', 'H. P. Lovecraft', 'Horror', '2016-07-01', 2, 2),
('978-1594632983', 'A Neurosurgeon''s Quest to Discover the Mysteries of the Brain and the Secrets of the Heart', 'James R. Doty, M.D.', 'Autobiography', '2016-02-02', 1, 0);
`
• Someone has just checked out one of the books. Change the number of available copies to 1 fewer.
`UPDATE library SET available = 1 WHERE isbn = '978-1401256821';`
• Now one of the books has been added to the banned books list. Remove it from the table.
`DELETE FROM library WHERE isbn = '978-0785834205';`

6. Write a command to make a new table to hold spacecrafts. Information should include id, name, year launched, country of origin, a brief description of the mission, orbiting body, if it is currently operating, and its approximate miles from Earth. In addition to the table creation, provide commands that perform the following operations:
`CREATE TABLE spacecrafts (
    satcat int,
    name varchar,
    launched int,
    origin text,
    description text,
    orbit varchar,
    operating bool,
    distance varchar
  );
`

• Add three non-Earth-orbiting satellites to the table.
`INSERT INTO spacecrafts VALUES
(28391, 'MESSENGER', 2004, 'United States', 'First spacecraft to orbit Mercury', 'Mercury', 'no', '48 million miles'),
(7915, 'Venera 9', 1975, 'Russia', 'First spacecraft to orbit Venus', 'Venus', 'no', '162 million miles'),
(5261, 'Mariner 9', 1971, 'United States', 'First spacecraft to orbit another planet', 'Mars', 'no', '5,751 miles'),
(26734, '2001 Mars Odyssey', 2001, 'United States', 'Longest surviving spacecraft in orbit another planet other than Earth', 'Mars', 'yes', '2,400 miles');
`
• Remove one of the satellites from the table since it has just crashed into the planet.
`DELETE FROM spacecrafts WHERE satcat = 28391;`
• Edit another satellite because it is no longer operating and change the value to reflect that.
`UPDATE spacecrafts SET operating = 'no' WHERE satcat = 26734;`

7. Write a command to create a new table to hold the emails in your inbox. This table should include an id, the subject line, the sender, any additional recipients, the body of the email, the timestamp, whether or not you have read the email, and the id of the email chain it's in. Also provide commands that perform the following operations:
`CREATE TABLE inbox (
    id int,
    unread bool,
    subject varchar,
    sender varchar,
    cc varchar,
    body text,
    sent timestamp,
    chain_id varchar
  );
`

• Add three new emails to the inbox.
`INSERT INTO inbox VALUES
(00003, 'yes', 'Welcome to Bloc!', 'success@bloc.io', '', 'Welcome my good friend! You''re on your first step..', '2018-07-17 02:10:06', '00003A'),
(00002, 'no', 'Your Amazon.com order of..', 'shipment-tracking@amazon.com', '', 'Your order of "Top Cats Daily!" has been shipped!', '2018-07-16 10:14:00', '00002A'),
(00001, 'no', 'JJ''s Wedding Invite', 'datdapper007@gmail.com', 'lonebroso@sfsu.edu, ttatman0102@yahoo.com', 'You''ve been cordially invited..', '2018-06-06 04:20:00', '00001A');
`
• You deleted one of the emails, so write a command to remove the row from the inbox table.
`DELETE FROM inbox WHERE id = 00002;`
• You started reading an email but just heard a crash in another room. Mark the email as unread before investigating the crash, so you can come back and read it later.
`UPDATE inbox SET unread = 'yes' WHERE id = 00001 AND sender = 'datdapper007@gmail.com';`
