-- DDL

-- Create a new table
CREATE TABLE if not exists product (
	-- add id column that is primary key and auto increments
	id int primary key AUTO_INCREMENT not null,
    -- add name column of size 100 and which cannot be null
    name varchar(100) not null,
    -- add description column with default value 'Product'
    description varchar(1000) default 'Product'
);

-- Insert data into product table
INSERT INTO product (name, description)
values ('Ram', 'Description');
INSERT INTO product (name, description)
values ('Ram1', 'Description1');

-- Compact syntax for multiple inserts
INSERT INTO product (name, description)
values ('Ram3', 'Description'), ('Ram4', 'Description4');

-- Renamte table name to new_product
ALTER TABLE product RENAME TO new_product;

-- Rename table name back to product
ALTER TABLE NEW_product RENAME TO product;

-- Add new column
ALTER TABLE product 
ADD COLUMN status varchar(100) not null;

-- Create a new table product_rate with foreign key
CREATE TABLE product_rate (
	id int AUTO_INCREMENT PRIMARY KEY,
    product_id INT,
    rate decimal(10,2) not null,
    FOREIGN KEY (product_id) REFERENCES product(id)
);

-- Drop table
DROP TABLE product_rate;

-- Create a new table product_rate with foreign key (Naming the constraint)
CREATE TABLE product_rate (
	id int AUTO_INCREMENT PRIMARY KEY,
    product_id INT,
    rate decimal(10,2) not null,
    CONSTRAINT fk_product_id FOREIGN KEY (product_id) REFERENCES product(id)
);

-- Remove foreign key constraint
ALTER TABLE product_rate
DROP constraint fk_product_id;

-- Add foreign key constraint using ALTER syntax
ALTER TABLE product_rate
ADD constraint fk_product_id FOREIGN KEY (product_id) REFERENCES product(id)

-- Cannot remove column product_id because it is foreign key
-- Should drop foreign key first
ALTER TABLE product_rate 
DROP column product_id;
