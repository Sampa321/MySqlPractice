-- Create a table and store value 
CREATE TABLE test1 (num FLOAT);
INSERT INTO test1 VALUES (1234567891234567);
SELECT * FROM test1;    
output : 123457


-- Decimal
CREATE TABLE test2 (num DECIMAL(5,4)); //5 -> total number(precedence), 4 ->total number after point
INSERT INTO test2 VALUES(1.230000);
SELECT * FROM test2;    //1.2300

CREATE TABLE test3 (num DECIMAL(4,4));
INSERT INTO test3 VALUES(1.230000);   //error
INSERT INTO test3 VALUES(0.230000); 
SELECT * FROM test3;    //0.2300

CREATE TABLE test3 (num DECIMAL(5,4));
INSERT INTO test3 VALUES(1.23678);    
SELECT * FROM test3;    //1.2368

CREATE TABLE test3 (num DECIMAL);  // I don't give any value then automatically store precedence of 10 
INSERT INTO test3 VALUES(12345678901);  // error
INSERT INTO test3 VALUES(1.1234567); 
SELECT * FROM test3;    //1.1234567

==============================================Data types===================================================================

CREATE TABLE product_details(
    product_id INT AUTO_INCREMENT PRIMARY KEY,                                                                  -- unique identifier for each product
    product_code CHAR(10),                                                                                      -- Fixed-length of product code
    product_name VARCHAR(100),					                                                                -- Product Name
    short_description TINYTEXT,					                                                                -- A brief description of the product
    detailed_description TEXT,					                                                                -- Detailed product description
    additional_info MEDIUMTEXT,                                                                                 -- Additional product into like usage or warranty details
    full_manual LONGTEXT,						                                                                -- Full product manual or documentation
    size ENUM('Small', 'Medium', 'Large'),		                                                                -- Size option for the product
    available_colors SET('Red', 'Green', 'Blue', 'Black', 'White')                                               -- Available color options
);

CREATE TABLE EventSchedule(
    event_id INT AUTO_INCREMENT PRIMARY KEY,                                             
    event_data DATE,                                                                     -- To store the date of the event (e.g., '2025-01-23)
    event_datetime DATETIME,                                                             -- To store the exact date and time of the event (e.g.,'2025-01-23 12:00:00')
    event_timestamp TIMESTAMP,                                                           -- To store the exact date and time in UTC (e.g.,'2025-01-23 12:00:00')
    event_time TIME,                                                                     -- To store the time of the event (e.g., '12:00:00')
    event_year YEAR                                                                      -- To store the year of the event (e.g., '2025')
);

INSERT INTO eventSchedule (event_data, event_datetime, event_timestamp, event_time, event_year) VALUES
('2025-02-23', '2025-02-23 11:23:43', '2025-02-23 11:23:43', '11:23:43', 2025),
('2015-05-23', '2015-05-23 10:23:43', '2015-05-23 10:23:43', '10:23:43', 2015),
('2020-02-20', '2020-02-20 11:13:13', '2020-02-20 11:13:13', '11:13:13', '2020' );

SELECT * FROM EventSchedule;


-- Binary Data Types
CREATE TABLE user_files(
    user_id INT AUTO_INCREMENT PRIMARY KEY,                                                                     -- USER ID(Numeric)
    security_key BINARY(32),				                                                                    -- Fixed-length of binary data (e.g., SHA-256 hash)
    session_token VARBINARY(64),				                                                                --  Variable-length binary (e.g., encoded session token)
    profile_picture TINYBLOB,					                                                                -- Small binary objects (e.g., profile pictures)
    document MEDIUMBLOB,						                                                                -- Medium-binary files (e.g., PDF or Word files)
    large_media LONGBLOB						                                                                -- Large binary data (e.g., videos or high resolution)
)
