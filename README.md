# patikadev_SQL

[Ödev 1](#ödev-1)  
[Ödev 2](#ödev-2)   
[Ödev 3](#ödev-3)       
[Ödev 4](#ödev-4)    
[Ödev 5](#ödev-5)     
[Ödev 6](#ödev-6)     
[Ödev 7](#ödev-7)     
[Ödev 8](#ödev-8) 
## Ödev 1
#### 1.film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
``` sql 
SELECT title, description FROM film;
```
#### 2.film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
``` sql 
SELECT * FROM film
WHERE length > 60 AND length < 75;
```
#### 3.film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
``` sql 
SELECT * FROM film
WHERE rental_rate=0.99 AND replacement_cost=12.99 OR replacement_cost= 28.99 ;
```
#### 4.customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
``` sql 
SELECT * FROM customer
WHERE first_name = 'Mary';
```
> Answer: Smith

#### 5.film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
``` sql 
SELECT * FROM film
WHERE NOT (length > 50)  AND NOT(rental_rate = 2.99 OR rental_rate = 4.99) ;
```
## Ödev 2
#### 1.film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
``` sql 
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```
#### 2.actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
``` sql 
SELECT first_name, last_name FROM actor
WHERE  first_name IN ('Penelope', 'Nick', 'Ed');
```
#### 3.film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.(IN operatörünü kullanınız.)
``` sql 
SELECT * FROM film
WHERE  rental_rate IN ( 0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);
```
## Ödev 3

#### 1.country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
``` sql 
SELECT * FROM country
WHERE country LIKE 'A%a';
```
#### 2.country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
``` sql 
SELECT * FROM country
WHERE country LIKE '%_____n';
```
#### 3.film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren
``` sql 
SELECT title FROM film
WHERE title ILIKE '%t%t%t%t%';
```
#### 4.film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
``` sql 
SELECT * FROM film
WHERE title LIKE 'C%' AND length >90 AND rental_rate = 2.99;
```
## Ödev 4

#### 1.film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
``` sql 
SELECT DISTINCT replacement_cost FROM film;
```
#### 2.film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
``` sql 
SELECT COUNT(DISTINCT replacement_cost) FROM film;
```
#### 3.film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
``` sql 
SELECT COUNT(*) FROM film
WHERE title LIKE 'T%' AND rating = 'G';
```
#### 4.country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
``` sql 
SELECT COUNT(*) FROM country
WHERE country LIKE '_____';
```
#### 5.city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
``` sql 
SELECT COUNT(*) FROM city
WHERE city ILIKE '%R';
```
## Ödev 5
#### 1.film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
``` sql 
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
```
#### 2.film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
``` sql 
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
OFFSET 5
LIMIT 5;
```
#### 3.customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
``` sql 
SELECT * FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
```
## Ödev 6
#### 1.film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
``` sql 
SELECT AVG(rental_rate) FROM film;
```
>Answer: 2.98000
#### 2.film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
``` sql 
SELECT Count(title) FROM film
WHERE title LIKE 'C%';
```
>Answer: 92
#### 3.film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

``` sql 
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99 ;
```
>Answer: 184
#### 4.film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

``` sql 
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150 ;
```
>Answer: 21

## Ödev 7
#### 1.film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
``` sql 
SELECT rating FROM film ;
```
#### 2.film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
``` sql 
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
```

#### 3.customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

``` sql 
SELECT store_id, COUNT(*) FROM CUSTOMER
GROUP BY store_id;

```
>Answer: store_id:1 = 326  store_id:2 = 273
#### 4.city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.

``` sql 
SELECT  country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
```
>Answer: country_id:44  count:60

## Ödev 8
#### 1.test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
``` sql 
CREATE TABLE employee (
	id INTEGER, name VARCHAR(50), birthday DATE, email VARCHAR(100));
```
#### 2.Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
``` sql 
insert into employee (id, name, birthday, email) values (1, 'Tina', '1963-03-09', 'trohan0@prnewswire.com');
insert into employee (id, name, birthday, email) values (2, 'Katerina', '1989-06-04', 'kerb1@google.com.br');
insert into employee (id, name, birthday, email) values (3, 'Benjie', '1980-10-08', 'bpettus2@goo.ne.jp');
insert into employee (id, name, birthday, email) values (4, 'Babbette', '1983-07-04', 'bszach3@forbes.com');
insert into employee (id, name, birthday, email) values (5, 'Carline', '1965-03-01', 'clegood4@storify.com');
insert into employee (id, name, birthday, email) values (6, 'Marc', '1975-05-25', 'mbycraft5@kickstarter.com');
insert into employee (id, name, birthday, email) values (7, 'Ollie', '1989-04-12', 'ocarlet6@squarespace.com');
insert into employee (id, name, birthday, email) values (8, 'Mae', '1991-03-02', 'mmatzke7@mail.ru');
insert into employee (id, name, birthday, email) values (9, 'Kippy', '1960-06-10', 'kmacalpine8@wsj.com');
insert into employee (id, name, birthday, email) values (10, 'Erskine', '1954-07-02', 'ebagehot9@marketwatch.com');
insert into employee (id, name, birthday, email) values (11, 'Kali', '1971-12-14', 'kivashnikova@amazon.com');
insert into employee (id, name, birthday, email) values (12, 'Peggie', '1971-10-14', 'pirnisb@t-online.de');
insert into employee (id, name, birthday, email) values (13, 'Melinde', '1957-07-28', 'mpiatekc@shareasale.com');
insert into employee (id, name, birthday, email) values (14, 'Delcine', '1965-08-21', 'detchinghamd@globo.com');
insert into employee (id, name, birthday, email) values (15, 'Brier', '1971-09-01', 'bfilochove@geocities.jp');
insert into employee (id, name, birthday, email) values (16, 'Sonia', '1974-04-30', 'soakwellf@livejournal.com');
insert into employee (id, name, birthday, email) values (17, 'Hector', '1959-08-24', 'hkitteringhamg@mozilla.com');
insert into employee (id, name, birthday, email) values (18, 'Janean', '1990-05-09', 'jroscamph@constantcontact.com');
insert into employee (id, name, birthday, email) values (19, 'Cherri', '1964-06-07', 'cpiddocki@tiny.cc');
insert into employee (id, name, birthday, email) values (20, 'Cori', '1990-04-17', 'cmeldonj@eepurl.com');
insert into employee (id, name, birthday, email) values (21, 'Allyn', '1995-01-10', 'amcettigenk@w3.org');
insert into employee (id, name, birthday, email) values (22, 'Hildy', '1987-11-27', 'hgrigollil@cbslocal.com');
insert into employee (id, name, birthday, email) values (23, 'Teodora', '1987-06-03', 'tspradberym@flickr.com');
insert into employee (id, name, birthday, email) values (24, 'Taffy', '1969-12-05', 'tdreweryn@spiegel.de');
insert into employee (id, name, birthday, email) values (25, 'Whittaker', '1980-02-11', 'wleatono@google.com.au');
insert into employee (id, name, birthday, email) values (26, 'Turner', '1997-05-12', 'tcattonnetp@zdnet.com');
insert into employee (id, name, birthday, email) values (27, 'Una', '1961-07-04', 'ugathq@virginia.edu');
insert into employee (id, name, birthday, email) values (28, 'Liuka', '1960-01-22', 'lkeirler@ucoz.ru');
insert into employee (id, name, birthday, email) values (29, 'Eddie', '1975-08-12', 'ewestmancoats@seesaa.net');
insert into employee (id, name, birthday, email) values (30, 'Candide', '1991-02-04', 'cboerdert@delicious.com');
insert into employee (id, name, birthday, email) values (31, 'Corney', '1977-10-14', 'cadamkiewiczu@noaa.gov');
insert into employee (id, name, birthday, email) values (32, 'Addy', '1950-08-13', 'aobreenv@marketwatch.com');
insert into employee (id, name, birthday, email) values (33, 'Wallie', '1990-09-16', 'wmckeeverw@trellian.com');
insert into employee (id, name, birthday, email) values (34, 'Felisha', '1997-12-24', 'fbunworthx@smugmug.com');
insert into employee (id, name, birthday, email) values (35, 'Krystle', '1996-02-18', 'kcookleyy@pbs.org');
insert into employee (id, name, birthday, email) values (36, 'Carlye', '1980-12-27', 'cmayheadz@macromedia.com');
insert into employee (id, name, birthday, email) values (37, 'Pearla', '1999-03-24', 'praubenheimers10@com.com');
insert into employee (id, name, birthday, email) values (38, 'Kane', '1961-08-28', 'khefforde11@yolasite.com');
insert into employee (id, name, birthday, email) values (39, 'Euell', '1991-05-08', 'eniblett12@prweb.com');
insert into employee (id, name, birthday, email) values (40, 'Gussie', '1998-11-28', 'gdiangelo13@google.com.au');
insert into employee (id, name, birthday, email) values (41, 'Karly', '1993-08-05', 'kindruch14@yellowpages.com');
insert into employee (id, name, birthday, email) values (42, 'Antonino', '1965-08-21', 'apiele15@walmart.com');
insert into employee (id, name, birthday, email) values (43, 'Cindie', '1950-08-06', 'cdarte16@fastcompany.com');
insert into employee (id, name, birthday, email) values (44, 'Johnathon', '1966-09-01', 'jsoitoux17@oaic.gov.au');
insert into employee (id, name, birthday, email) values (45, 'Nicholas', '1990-01-03', 'natlay18@freewebs.com');
insert into employee (id, name, birthday, email) values (46, 'Jeffry', '1968-01-31', 'jchimenti19@ifeng.com');
insert into employee (id, name, birthday, email) values (47, 'Aubrey', '1984-08-23', 'atempest1a@mozilla.com');
insert into employee (id, name, birthday, email) values (48, 'Cleo', '1995-07-30', 'cstapels1b@nasa.gov');
insert into employee (id, name, birthday, email) values (49, 'Veronica', '1969-09-27', 'vkilduff1c@histats.com');
insert into employee (id, name, birthday, email) values (50, 'Fredelia', '1983-10-20', 'fmetschke1d@blog.com');
```

#### 3.Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

``` sql 
UPDATE employee
SET name = 'burak'
WHERE email ='tcattonnetp@zdnet.com';

UPDATE employee
SET email = 'burak@hotmail.com'
WHERE name = 'burak';

UPDATE employee
SET birthday = '1997-02-20'
WHERE id = 42;

UPDATE employee
SET id = 100
WHERE name = 'Nicholas';

UPDATE employee
SET name = 'jeff'
WHERE name = 'burak';
```
#### 4.Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

``` sql 
DELETE FROM employee WHERE birthday = '"1960-01-22"';
DELETE FROM employee WHERE name = 'jeff';
DELETE FROM employee WHERE email = '"jchimenti19@ifeng.com"';
DELETE FROM employee WHERE id = '100';
DELETE FROM employee WHERE name = '"Mae"';
```


