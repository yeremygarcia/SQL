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
