# SQL - Reflection
Learning about databases and SQL seems simple yet complicated. The whole GUI for SQL Studio isnt my favorite, I ran into some issues installing and getting everything just ready to work. The UI is pretty archaeic compared to the IDE's we have been working with. I also learned during this process that my computer nativley comes with sqlite3, so that was cool. I learned how helpful this can ben on the macro level with large quantities of data.I still need to get used to it though, while troubleshooting I saw that VSCode can manipulate DB files so maybe I will play around with taht at some point. 

CREATE DATABASE Bookstore;

USE Bookstore; CREATE TABLE Books ( BookID INTEGER, Title TEXT, Author TEXT, PublicationYear INTEGER, Price REAL );

INSERT INTO Books (Title, Author, PublicationYear, Price) VALUES
('1',	'The Foot Book', 'Dr. Seuss', 1968, 10.99),
('2',	'Hop on Pop',	'Dr. Seuss', 1968,	10.99),
('3',	'Fox in Socks',	'Dr. Seuss	1965,	10.99),
('4',	'ABC', 'Dr. Seuss',	1960,	10.99),
('5', 'Cat and the Hat',	'Dr.  Seuss',	1957,	10.99),
('6',	'The Lorax',	'Dr. Seuss',	1971,	10.99),
('7', 'Green Eggs and Ham',	'Dr. Seuss', 1960,	10.99),
('8',	'If I Ran the Zoo',	'Dr. Seuss',	1950,	10.99),
('9',	'The Grinch',	'Dr. Seuss',	1957,	10.99),
('10', 'Oh the Places You'll Go',	'Dr. Seuss', 1990,	10.99);



SELECT * FROM Books;
SELECT * FROM Books WHERE PublicationYear > 2000;
SELECT * FROM Books WHERE Author = 'Dr. Seuss';
UPDATE Books SET Price = 10.99 WHERE Title = 'The Lorax';
DELETE FROM Books WHERE BookID = 4;




----------------------------------------------------------------------
SQL Query Practice and Database Modification


INSERT INTO Books (BookID, Title, Author, PublicationYear, Price) 
VALUES 
(9, 'One fish, two fish, red fish, blue fish', 'Dr. Seuss',1960, 10.99),
(10, 'The Sneetches', 'Dr. Seuss', 1952, 10.99),
(11, 'The Butter Battle Book', 'Dr. Seuss', 1984, 10.99),
(12, 'Daisy Head Mayzie', 'Dr. Seuss', 1994, 10.99),
(13, 'Sleep Book', 'Dr. Seuss', 1962, 10.99);

Retreving books costing 20$ or more

SELECT *
FROM Books
WHERE Price >= 20;

Retrieving books with publication years between 1980-2020

SELECT 
FROM Books
WHERE PublicationYear > 1980 AND PublicationYear < 2020;

Counting books by each author

SELECT Author, COUNT() AS NumberOfBooks
FROM Books
GROUP BY Author;

Avg price of all books in table

SELECT AVG(Price) AS AveragePrice
FROM Books;


Update price of books published before 1990 by 10%

UPDATE Books
SET Price = Price * 0.9
WHERE PublicationYear < 1990;

SELECT * FROM Books;

Delete books published more than 50 years ago

DELETE FROM Books
WHERE PublicationYear < CURRENT_DATE - 50;

SELECT * FROM Books;

Relflection - Ater lecture today I realiezed that I wanted to ues MySQL rather than SQL studio, just based on the GUi. I had to go back and watch the lecture from today to follow along and learn to use mysql, and i'll probably touch up a bit on it sometime during the long weekend. But so far so good, that commands are simple and do what they say, even more explicitly than other languages, I think. 
