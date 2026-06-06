SELECT VERSION();

--  create Database
CREATE DATABASE my_database;

-- Use the desired database
USE my_database;

-- create a table
CREATE TABLE products (
   product_id INT AUTO_INCREMENT PRIMARY KEY,
   product_name VARCHAR(100) NOT NULL,
   price DECIMAL(10,2) NOT NULL
);

-- Insert records
INSERT INTO products (product_name, price) VALUES ('Laptop', 999.99), ('Headphone', 49.99), ('Monitor', 199.90);

-- Select records
SELECT product_id, product_name, price FROM products ORDER BY price DESC;