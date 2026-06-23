 -- 23/06/2026

Create database bookStore;
USE bookStore;
CREATE TABLE book (
 book_id int PRIMARY KEY,
 title VARCHAR(100),
 AUTHOR varchar(40),
 price decimal(10,2),
 publication_date date,
 catagory varchar(30),
 in_store int
 );
 
 INSERT INTO book (`book_id`,`title`,`AUTHOR`,`price`,`publication_date`,`catagory`,`in_store`) values
 (4, 'The MYsql Guide', 'John Smith', 25.78, '2023-02-23','Technology', 50),
 (5, 'Data Science Guide', 'John roy', 90.78, '2023-06-23','Technology', 40),
 (6, 'Python Guide', 'Lisa anderson', 35.38, '2025-02-20','Technology', 20);
 
 INSERT INTO book (`book_id`,`title`,`AUTHOR`,`price`,`publication_date`,`catagory`,`in_store`) values
 (17, 'Java', 'John Smith', 400.89, '2021-02-20','Mystery', 55);
 
 INSERT INTO book (`book_id`,`title`,`AUTHOR`,`price`,`publication_date`,`catagory`,`in_store`) values
 (12, 'DSA', null, 300.89, '2023-10-30','Mystery', 45);
 
SELECT * FROM book;
SELECT * FROM book where catagory = 'technology';
SELECT title,price from book where price >=30;
SELECT TITLE, publication_date from book where publication_date < '2023-03-23';
SELECT * FROM book where catagory = 'technology' and price >40;
SELECT * FROM book where (catagory = 'technology' or catagory = 'Mystery')  and price >40;
SELECT * FROM book where catagory != 'technology';
 -- or
SELECT * FROM book where not catagory = 'technology';

-- Finding null values
SELECT * FROM book where AUthor is null;   -- SELECT * FROM book where AUthor = null;  -> wrong because that is undefined
 
SELECT * FROM book where AUthor is not null;     -- SELECT * FROM book where not AUthor = null;  -> wrong because that is undefined



-- pattern Matching
SELECT * FROM book where title like '%sql%';
SELECT * FROM book where title like 'Data%';  -- check 1st word
SELECT * FROM book where title like '%Guide'; -- check last word
SELECT * FROM book where title like binary '%sql%'; -- check case-sensitive
SELECT * FROM book where author like '_ohn%';
SELECT * FROM book where price between 20 and 30;
SELECT * FROM book where catagory in('Technology','Mystery');
SELECT * FROM book where price >= (select avg(price) from book);  -- which price more than the avg price
SELECT * FROM book where catagory in(SELECT catagory FROM book where in_store >10);

 -- Find all books published in 2023 that cost less than the average book price.
select * FROM book where year(publication_date) = 2023 and price < (Select avg(price) from book);
 
 
 -- List all techology books with "sql" in the title that have more than 50 copies in stock.
SELECT * FROM book where title like '%sql%' and catagory = 'Technology' and in_store >=50;
 
 
-- Find books that are either in the Technology catagory with price > $30 or in the Mystery catagory with price  < $20.
select * FROM book where (catagory = 'Technology' and price > 30) or (catagory = 'Mystery' and price < 30);

-- List all books where the author's name contains either 'son' or 'th' and were published after March 2023.
select * FROM book where (author like '%son%' or author like '%th%') and publication_date >= '2023-01-04';