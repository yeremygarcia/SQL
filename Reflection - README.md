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




------------------------------------------------------------------------
SQL Mastery and Complex Queries

Additional Table Creation

CREATE TABLE Bookstore.Sales (
    SaleID INT,
    BookID INT,
    SaleDate DATE,
    Quantity INT,
    TotalPrice FLOAT
);

Data Insertion


Inserting sales records with matching BookIDs
INSERT INTO Bookstore.Sales (SaleID, BookID, SaleDate, Quantity, TotalPrice)
VALUES (1, Book1, '2023-06-01', 2, 10.99);

INSERT INTO Bookstore.Sales (SaleID, BookID, SaleDate, Quantity, TotalPrice)
VALUES (2, Book2, '2023-06-02', 1, 10.99);

INSERT INTO Bookstore.Sales (SaleID, BookID, SaleDate, Quantity, TotalPrice)
VALUES (3, Book3, '2023-06-03', 3, 10.99);

INSERT INTO Bookstore.Sales (SaleID, BookID, SaleDate, Quantity, TotalPrice)
VALUES (4, Book4, '2023-06-04', 1, 10.99);

INSERT INTO Bookstore.Sales (SaleID, BookID, SaleDate, Quantity, TotalPrice)
VALUES (5, Book5, '2023-06-05', 2, 10.99);

INSERT INTO Bookstore.Sales (SaleID, BookID, SaleDate, Quantity, TotalPrice)
VALUES (6, Book6, '2023-06-06', 1, 10.99);

INSERT INTO Bookstore.Sales (SaleID, BookID, SaleDate, Quantity, TotalPrice)
VALUES (7, Book7, '2023-06-07', 2, 10.99);

INSERT INTO Bookstore.Sales (SaleID, BookID, SaleDate, Quantity, TotalPrice)
VALUES (8, Book8, '2023-06-08', 1, 10.99);

INSERT INTO Bookstore.Sales (SaleID, BookID, SaleDate, Quantity, TotalPrice)
VALUES (9, Book9, '2023-06-09', 1, 10.99);

INSERT INTO Bookstore.Sales (SaleID, BookID, SaleDate, Quantity, TotalPrice)
VALUES (10, Book10, '2023-06-10', 3, 10.99);


Complex Query Practice

SELECT *
FROM Bookstore.Books
WHERE BookID IN (SELECT DISTINCT BookID FROM Bookstore.Sales);

SELECT b.BookID, b.Title, SUM(s.TotalPrice) AS TotalSales
FROM Bookstore.Books b
JOIN Bookstore.Sales s ON b.BookID = s.BookID
GROUP BY b.BookID, b.Title;

SELECT *
FROM Bookstore.Books
WHERE BookID NOT IN (SELECT DISTINCT BookID FROM Bookstore.Sales);

SELECT b.BookID, b.Title, SUM(s.TotalPrice) AS TotalSales
FROM Bookstore.Books b
JOIN Bookstore.Sales s ON b.BookID = s.BookID
GROUP BY b.BookID, b.Title
ORDER BY TotalSales DESC
LIMIT 1;

SELECT a.AuthorID, a.AuthorName, SUM(s.TotalPrice) AS TotalSales
FROM Bookstore.Authors a
JOIN Bookstore.Books b ON a.AuthorID = b.AuthorID
JOIN Bookstore.Sales s ON b.BookID = s.BookID
GROUP BY a.AuthorID, a.AuthorName;


Database Modification

UPDATE Bookstore.Sales
SET Quantity = 5
WHERE SaleID = 1;

DELETE FROM Bookstore.Sales
WHERE SaleID = 2;

UPDATE Bookstore.Books
SET Price = Price * 0.9
WHERE BookID = 1001;

Reflection: For this assingment I figured out why sql lite was being difficult and was able to get a working server for workbench do push all of this data through. Not as difficult as day 1 for sure. The GUI is pretty intuiituive, I also watched a tutorial on doing it all in the command line, so maybe I will try that tomorrow, believ it or not it actually seems simpler.


------------------------------------------------------------------------
SQL QUERIES:

1: SUBQUERY PRACTICE

AVG: SELECT AVG(Price) AS AveragePrice FROM Books; (10.99)

SELECT * 
FROM Books
WHERE Price > (SELECT AVG(Price) FROM Books);

Find the 'BookID' of the book(s) with the highest 'TotalPrice' in the 'Sales' table.

SELECT BookID
FROM Sales
WHERE TotalPrice = (SELECT MAX(TotalPrice) FROM Sales);

2: AGGREGATION PRACTICE

Find the total number of books sold.

SELECT SUM(Quantity) 
FROM Sales;

Calculate the total revenue from book sales.

SELECT SUM(TotalPrice)
FROM Sales;

Find the average, minimum, and maximum book price.

SELECT 
AVG(Price),
MIN(Price),
MAX(Price)
FROM Books;

Group by 'Author' and count the number of books per author.

SELECT Author, COUNT(*)
FROM Books
GROUP BY Author;

3: JOIN PRACTICE

Using an INNER JOIN, retrieve all records of books and their corresponding sales.

SELECT *
FROM Books
INNER JOIN Sales
ON Books.BookID = Sales.BookID;

Using a LEFT JOIN, retrieve all books, and display sales records where available.

SELECT *
FROM Books
LEFT JOIN Sales
ON Books.BookID = Sales.BookID;

Using a RIGHT JOIN, retrieve all sales, and display book information where available.

SELECT *
FROM Sales
RIGHT JOIN Books
ON Sales.BookID = Books.BookID;



