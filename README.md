# command_SQL
Command SQL

DROP DATABASE MYSTOR; --// Удаление БД 

CREATE DATABASE MYSTOR; --// Создание БД

CREATE TABLE MYSTOR_TABLE; --// Создание таблици MYSTOR_TABLE

USE MYSTOR_TABLE -----// Команда выбирает нужную базу из нескольких(it doesn't work in phpmyadmin!!!)

CREATE TABLE article (
id int(8) NOT NULL  AUTO_INCREMENT,
name CHAR(255),
price FLOAT(8,2)  NOT NULL,
description VARCHAR(255),
PRIMARY KEY (id)
);

CREATE TABLE orders(
id int(8) NOT NULL  AUTO_INCREMENT,
id_article int(8),
users_name CHAR(50),
users_lastname CHAR(50),
users_phone int(50) NOT NULL,
date_orders DATE,
PRIMARY KEY (id),
FOREIGN KEY (id_article)
REFERENCES article(id)
);

Warning: #1681 Integer display width is deprecated and will be removed in a future release.

--------// ALTER  TABLE orders ADD FOREIGN KEY (id_article) REFERENCES article (id);

ALTER  TABLE orders MODIFY users_phone CHAR(13);

INSERT INTO article (price, name, description) VALUE (1000, 'Tovar_1', 'njvdkjvndjkvndjvndjvnjdfk vdfnvndjnvjdfv vdfndjvnkjdf'); 
INSERT INTO article (price, name, description) VALUE (1001, 'Tovar_8', 'njvdkjvndjkvndjvndjvnjdfk vdfnvndjnvjdfv vdfndjvnkjdf'); 
INSERT INTO article (price, name, description) VALUE (1002, 'Tovar_2', 'njvdkjvndjkvndjvndjvnjdfk vdfnvndjnvjdfv vdfndjvnkjdf'); 
INSERT INTO article (price, name, description) VALUE (1003, 'Tovar_3', 'njvdkjvndjkvndjvndjvnjdfk vdfnvndjnvjdfv vdfndjvnkjdf'); 
INSERT INTO article (price, name, description) VALUE (1004, 'Tovar_4', 'njvdkjvndjkvndjvndjvnjdfk vdfnvndjnvjdfv vdfndjvnkjdf'); 
INSERT INTO article (price, name, description) VALUE (1005, 'Tovar_5', 'njvdkjvndjkvndjvndjvnjdfk vdfnvndjnvjdfv vdfndjvnkjdf'); 
INSERT INTO article (price, name, description) VALUE (1006, 'Tovar_6', 'njvdkjvndjkvndjvndjvnjdfk vdfnvndjnvjdfv vdfndjvnkjdf'); 
INSERT INTO article (price, name, description) VALUE (1007, 'Tovar_7', 'njvdkjvndjkvndjvndjvnjdfk vdfnvndjnvjdfv vdfndjvnkjdf'); 
INSERT INTO article (price, name, description) VALUE (2007, 'qwerty', 'njvdkjvndjkvndjvndjvnjdfk vdfnvndjnvjdfv vdfndjvnkjdf'); 

INSERT INTO orders (id_article, users_name, users_lastname, users_phone, date_orders) VALUE ('2', 'user_1', 'user_last_1', '+380938888878', '1934-01-06'); 
INSERT INTO orders (id_article, users_name, users_lastname, users_phone, date_orders) VALUE ('2', 'user_2', 'user_last_2', '+380688888889', '1234-02-06'); 
INSERT INTO orders (id_article, users_name, users_lastname, users_phone, date_orders) VALUE ('3', 'user_3', 'user_last_3', '+380988888855', '1234-06-16'); 
INSERT INTO orders (id_article, users_name, users_lastname, users_phone, date_orders) VALUE ('4', 'user_4', 'user_last_4', '+380638888810', '1834-12-06');
INSERT INTO orders (id_article, users_name, users_lastname, users_phone, date_orders) VALUE ('5', 'user_5', 'user_last_5', '+380678888888', '1234-03-26');
INSERT INTO orders (id_article, users_name, users_lastname, users_phone, date_orders) VALUE ('5', 'user_6', 'user_last_6', '+380688888823', '1234-06-06');
INSERT INTO orders (id_article, users_name, users_lastname, users_phone, date_orders) VALUE ('7', 'user_7', 'user_last_7', '+380688888811', '2234-12-11');
INSERT INTO orders (id_article, users_name, users_lastname, users_phone, date_orders) VALUE ('9', 'user_6', 'user_last_6', '+380688888823', '1234-06-06');
INSERT INTO orders (id_article, users_name, users_lastname, users_phone, date_orders) VALUE (1, 'user_7', 'user_last_7', '+380688888811', '2234-12-11');

INSERT INTO orders (id_article, users_name, users_lastname,users_phone, date_orders) VALUE (8,'Vasia', 'gwerty', '+380688522323', '2022-08-22');
INSERT INTO orders (users_name, users_lastname,users_phone, date_orders) VALUE ('Marysia', 'gwerty', '+380688524423', '2022-08-12');

DELETE FROM orders WHERE id=1; 

SELECT * FROM `orders` WHERE users_name LIKE 'us%';

SELECT users_name,users_lastname FROM `orders`WHERE users_name LIKE 'us%';

SELECT users_name,users_lastname FROM `orders`WHERE users_name LIKE 'us%' LIMIT 2;

SELECT * FROM `article` ORDER BY price ASC;

SELECT * FROM `article` ORDER BY price DESC LIMIT 4;

SELECT COUNT(*) FROM  `article`;

SELECT COUNT(*),id_article FROM `orders` GROUP BY id_article
SELECT id_article,COUNT(*) AS k_vo_zakazov FROM `orders` GROUP BY id_article
SELECT id_article,COUNT(*) AS k_vo_zakazov FROM `orders` GROUP BY id_article HAVING COUNT(*) >= 2;

SELECT name,MIN(price) FROM article GROUP BY name HAVING MIN(price) >= 1004;
SELECT name,MIN(price) FROM article GROUP BY name HAVING MIN(price) >= 1004 ORDER BY price DESC;
SELECT name,MIN(price) AS priceMin FROM article GROUP BY name HAVING MIN(price) >= 1004 ORDER BY priceMin DESC

SELECT * FROM `article` WHERE id IN ( SELECT id_article FROM orders);

SELECT * FROM `article` 
JOIN `orders`
ON article.id = orders.id_article
