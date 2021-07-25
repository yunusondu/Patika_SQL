# PatikaDev-PostgreSQL

<a href='#Ödev 1'>Ödev 1</a><br>
<a href='#Ödev 2'>Ödev 2</a><br>
<a href='#Ödev 3'>Ödev 3</a><br>
<a href='#Ödev 4'>Ödev 4</a><br>
<a href='#Ödev 5'>Ödev 5</a><br>
<a href='#Ödev 6'>Ödev 6</a><br>
<a href='#Ödev 7'>Ödev 7</a><br>
<a href='#Ödev 8'>Ödev 8</a><br>
<a href='#Ödev 9'>Ödev 9</a><br>
<a href='#Ödev 10'>Ödev 10</a><br>
<a href='#Ödev 11'>Ödev 11</a><br>
<a href='#Ödev 12'>Ödev 12</a><br>
<a href='#psql'>PSQL ve Uygulama </a><br>
<a href='#Notlar'>Notlar </a><br>
 
 
 
## <p id = 'Ödev 1' > Ödev 1 </p> 
#### Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
~~~sql
SELECT title,description FROM film;
~~~
#### Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
~~~sql
SELECT * FROM film WHERE length > 60 and length < 75;
~~~
#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
~~~sql
SELECT * FROm film WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99
~~~
#### Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
~~~sql
SELECT last_name FROM customer where first_name = 'Mary';
Cevap : Smith
~~~
#### Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
~~~sql
SELECT * FROM film WHERE  length < 50 AND  NOT rental_RATE = 2.99 OR NOT rental_rate = 4.99
~~~
## <p id = 'Ödev 2' > Ödev 2 </p> 
#### Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
~~~sql
SELECT * FROM film WHERE BETWEEN 12.99 AND 16.99
~~~
#### Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
~~~sql
SELECT first_name,last_name FROM Actor WHERE first_name IN('Penelope','Nick','Ed');
~~~
#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.(IN operatörünü kullanınız.)
~~~sql
SELECT * FROM film WHERE rental_rate IN(0.99,2,99,4,99) AND replacement_cost IN(12.99,15.99,28.99);
~~~
## <p id = 'Ödev 3' > Ödev 3 </p> 
#### Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT country From Country WHERE country like 'A%a';
~~~
#### Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT country From Country WHERE LENGTH(country) > 6 AND country like '%n';
~~~
#### Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren
~~~sql
SELECT title FROM film WHERE title ILIKE '%t%t%t%t%';
~~~
#### Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
~~~sql
SELECT * From film Where title LIKE 'C%' AND length > 90 AND rental_rate = 2.99 ; 
~~~

## <p id = 'Ödev 4' > Ödev 4 </p> 
#### Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
~~~sql
SELECT DISTINCT replacement_cost FROM film; 
~~~
#### Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
~~~sql
SELECT COUNT( DISTINCT replacement_cost ) FROM film; 
~~~
#### Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
~~~sql
SELECT COUNT(*) FROM film WHERE title = 'T%' AND rating = 'G';
~~~
#### Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
~~~sql
SELECT COUNT(*) FROM film WHERE LENGTH(country) = 5;
~~~
#### City tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
~~~sql
SELECT COUNT(*) FROM City WHERE ILIKE city = '%R';
~~~


## <p id = 'Ödev 5' > Ödev 5 </p> 
#### Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
~~~sql
SELECT title,length FROM film WHERE title LIKE '%n' ORDER BY length DESC LIMIT 5 ;
~~~
#### Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
~~~sql
SELECT title FROM film WHERE title LIKE '%n' ORDER BY length OFFSET 5 LIMIT 5;
~~~
#### Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
~~~sql
SELECT last_name FROM customer WHERE store_id = 1 ORDER BY last_name DESC LIMIT 4;
~~~

## <p id = 'Ödev 6' > Ödev 6 </p> 
#### Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
~~~sql
SELECT AVG(rental_rate) FROM film;
~~~
#### Film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
~~~sql
SELECT COUNT(*) FROM film WHERE title LIKE 'C%';
~~~
#### Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
~~~sql
SELECT MAX(length) FROM film WHERE rental_rate = 0.99;
~~~
#### Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
~~~sql
SELECT COUNT( DISTINCT replacement_cost )FROM film WHERE length > 150;
~~~
## <p id = 'Ödev 7' > Ödev 7 </p> 
#### Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
~~~sql
SELECT rating FROM film GROUP BY rating;
~~~
#### Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
~~~sql
SELECT replacement_cost,COUNT(*) FROM film GROUP BY replacement_cost HAVING COUNT(*) > 50;
~~~
#### Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
~~~sql
SELECT store_id,COUNT(*) FROM customer GROUP BY store_id;
~~~
#### City tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
~~~sql
SELECT country_id,COUNT(*) FROM city GROUP BY country_id ORDER BY COUNT(*) DESC LIMIT 1;
~~~
## <p id = 'Ödev 8' > Ödev 8 </p>
#### Test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
~~~sql
 CREATE TABLE employee (
  id SERIAL PRIMARY KEY,
  name VARCHAR(50) NOT NULL,
  email VARCHAR(100),
  birthday DATE
); 
~~~
#### Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
~~~sql

insert into employee (id, name, email, birthday) values (1, 'Enriqueta', 'ereadwing0@answers.com', '1979-11-10');
insert into employee (id, name, email, birthday) values (2, 'Milo', 'mlaytham1@salon.com', '2021-01-13');
insert into employee (id, name, email, birthday) values (3, 'Corine', 'ctolhurst2@house.gov', '1963-04-25');
insert into employee (id, name, email, birthday) values (4, 'Sasha', 'sjoriot3@ucoz.com', '1978-02-04');
insert into employee (id, name, email, birthday) values (5, 'Kerry', 'klarenson4@etsy.com', '1950-02-10');
insert into employee (id, name, email, birthday) values (6, 'Orion', 'ozavattiero5@dion.ne.jp', '1992-09-14');
insert into employee (id, name, email, birthday) values (7, 'Garland', 'gjahan6@barnesandnoble.com', '1928-03-25');
insert into employee (id, name, email, birthday) values (8, 'Saloma', 'sovendon7@vk.com', '2010-08-13');
insert into employee (id, name, email, birthday) values (9, 'Irv', 'idrews8@slashdot.org', '1917-05-02');
insert into employee (id, name, email, birthday) values (10, 'Zilvia', 'zplitz9@google.com.au', '1911-10-07');
insert into employee (id, name, email, birthday) values (11, 'Donovan', 'dmardena@google.com.au', '2012-10-01');
insert into employee (id, name, email, birthday) values (12, 'Karil', 'ksiretb@ucoz.com', '1976-09-03');
insert into employee (id, name, email, birthday) values (13, 'Letta', 'lbeltznerc@ftc.gov', '1997-09-24');
insert into employee (id, name, email, birthday) values (14, 'Florence', 'flamdind@abc.net.au', '1982-09-21');
insert into employee (id, name, email, birthday) values (15, 'Anita', 'achekee@uol.com.br', '2012-05-31');
insert into employee (id, name, email, birthday) values (16, 'Antonina', 'adowsef@imageshack.us', '1904-07-23');
insert into employee (id, name, email, birthday) values (17, 'Genia', 'gvlasovg@house.gov', '1961-03-22');
insert into employee (id, name, email, birthday) values (18, 'Ester', 'ecruxh@php.net', '1946-05-24');
insert into employee (id, name, email, birthday) values (19, 'Leeanne', 'lschapiroi@webmd.com', '1925-04-05');
insert into employee (id, name, email, birthday) values (20, 'Fern', 'fdorricottj@csmonitor.com', '1919-05-03');
insert into employee (id, name, email, birthday) values (21, 'Cordelie', 'cstalleyk@aol.com', '1936-07-28');
insert into employee (id, name, email, birthday) values (22, 'Baron', 'bmantrupl@va.gov', '1949-04-25');
insert into employee (id, name, email, birthday) values (23, 'Adore', 'amassenm@java.com', '1933-09-20');
insert into employee (id, name, email, birthday) values (24, 'Westley', 'wyeelesn@jimdo.com', '1984-07-18');
insert into employee (id, name, email, birthday) values (25, 'Oralee', 'ofilimoreo@indiegogo.com', '1993-01-31');
insert into employee (id, name, email, birthday) values (26, 'Penrod', 'pclatworthyp@g.co', '2000-01-16');
insert into employee (id, name, email, birthday) values (27, 'Hurley', 'hjaumeq@blogtalkradio.com', '1953-04-07');
insert into employee (id, name, email, birthday) values (28, 'Alfredo', 'adavittir@shutterfly.com', '1915-11-09');
insert into employee (id, name, email, birthday) values (29, 'Jarvis', 'jlunos@google.nl', '1953-04-12');
insert into employee (id, name, email, birthday) values (30, 'Amalle', 'arolset@howstuffworks.com', '1922-09-14');
insert into employee (id, name, email, birthday) values (31, 'Kele', 'ksweetenhamu@addtoany.com', '1993-01-31');
insert into employee (id, name, email, birthday) values (32, 'Ermin', 'eoldeyv@newsvine.com', '2007-12-15');
insert into employee (id, name, email, birthday) values (33, 'Zitella', 'zbarbrookw@hp.com', '1948-02-01');
insert into employee (id, name, email, birthday) values (34, 'Davon', 'dvesquex@ameblo.jp', '1916-04-04');
insert into employee (id, name, email, birthday) values (35, 'Gray', 'geffnerty@microsoft.com', '1937-07-04');
insert into employee (id, name, email, birthday) values (36, 'Maridel', 'mommundsenz@ask.com', '1999-09-17');
insert into employee (id, name, email, birthday) values (37, 'Anya', 'adight10@addthis.com', '1981-02-14');
insert into employee (id, name, email, birthday) values (38, 'Rolland', 'rnore11@yandex.ru', '1956-03-13');
insert into employee (id, name, email, birthday) values (39, 'Merrill', 'mkingswood12@hhs.gov', '2019-04-21');
insert into employee (id, name, email, birthday) values (40, 'Ammamaria', 'atregien13@state.tx.us', '1961-12-08');
insert into employee (id, name, email, birthday) values (41, 'Baily', 'bcarlucci14@hugedomains.com', '1961-07-06');
insert into employee (id, name, email, birthday) values (42, 'Koral', 'klewins15@army.mil', '1957-05-07');
insert into employee (id, name, email, birthday) values (43, 'Rowan', 'rcancutt16@tripod.com', '1908-03-12');
insert into employee (id, name, email, birthday) values (44, 'Gordie', 'gisenor17@mac.com', '1958-01-07');
insert into employee (id, name, email, birthday) values (45, 'Sophey', 'smatcham18@imgur.com', '1974-02-27');
insert into employee (id, name, email, birthday) values (46, 'Alida', 'apoultney19@networkadvertising.org', '1939-11-07');
insert into employee (id, name, email, birthday) values (47, 'Edin', 'epickrell1a@squidoo.com', '1907-11-29');
insert into employee (id, name, email, birthday) values (48, 'Aaron', 'amountney1b@bandcamp.com', '1934-08-01');
insert into employee (id, name, email, birthday) values (49, 'Murdock', 'mmoff1c@buzzfeed.com', '1919-05-17');
insert into employee (id, name, email, birthday) values (50, 'Theresina', 'thellier1d@stumbleupon.com', '1928-11-27');
~~~

#### Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
~~~sql
UPDATE Employee SET name = 'Barbaros' WHERE id = 1;
UPDATE Employee SET email = 'rtb.barbaros@gmail.com' WHERE name = 'Barbaros';
UPDATE Employee SET birthday = '2021/05/29' WHERE email = '123@gmail.com';
UPDATE Employee SET birthday = '2021/05/29',name = 'Revaha' WHERE email = '123@gmail.com';
UPDATE Employee SET name = 'Barbaros',birthday = '2021/05/29' WHERE id = 1;
~~~
#### Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
~~~sql
DELETE FROM Employee WHERE name = 'Revaha';
DELETE FROM Employee WHERE email = 'rtb.barbaros@gmail.com';
DELETE FROM Employee WHERE birthday = '2021/05/29';
DELETE FROM Employee WHERE name = 'Tayyip';
DELETE FROM Employee WHERE id = '1';
~~~
## <p id = 'Ödev 9' > Ödev 9 </p> 
#### City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT city,country FROM city ci JOIN country co ON (co.country_id = ci.country_id );
~~~
#### Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT first_name,last_name,payment_id FROM customer c JOIN payment p ON ( p.customer_id = c.customer_id);
~~~
#### Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
~~~sql
SELECT first_name,last_name,rental_id FROM customer c JOIN rental r ON( c.customer_id = r.customer_id );
~~~
##  <p id = 'Ödev 10' > Ödev 10 </p> 
#### City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
~~~sql
SELECT city,country FROM city ci LEFT JOIN country co ON ( ci.country_id = co.country_id );
~~~
#### Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
~~~sql
SELECT first_name,last_name,payment_id FROM customer c RIGHT JOIN payment p ON ( p.customer_id = c.customer_id);
~~~
#### Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.
~~~sql
SELECT first_name,last_name,rental_id FROM customer c FULL JOIN rental r ON( c.customer_id = r.customer_id );
~~~

##  <p id = 'Ödev 11' > Ödev 11 </p> 
#### Actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
~~~sql
( SELECT first_name FROM actor )
UNION
( SELECT first_name FROM customer )
~~~
#### Actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
~~~sql
( SELECT first_name FROM actor )
INTERSECT
( SELECT first_name FROM customer )
~~~
#### Actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
~~~sql
( SELECT first_name FROM actor )
EXCEPT
( SELECT first_name FROM customer )
~~~
#### İlk 3 sorguyu tekrar eden veriler için de yapalım.
~~~sql
( SELECT first_name FROM actor )
UNION ALL
( SELECT first_name FROM customer )
~~~
~~~sql
( SELECT first_name FROM actor )
INTERSECT ALL
( SELECT first_name FROM customer )
~~~
~~~sql
( SELECT first_name FROM actor )
EXCEPT ALL
( SELECT first_name FROM customer )
~~~
## <p id = 'Ödev 12' > Ödev 12 </p>
#### Film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
~~~sql
SELECT COUNT(*)  FROM film WHERE length > ( SELECT AVG(length) FROM film);
~~~
#### Film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
~~~sql
SELECT COUNT(*) FROM film WHERE rental_rate = ( SELECT MAX(rental_rate) FROM film);
~~~
#### Film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
~~~sql
SELECT title
FROM film
WHERE film_id = any
( SELECT film_id
 FROM film
WHERE rental_rate = ( SELECT MIN(rental_rate ) FROM film )
 AND
 replacement_cost = ( SELECT MIN(replacement_cost) FROM film ) );
~~~
#### Payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
~~~sql
SELECT first_name,last_name
FROM customer c
JOIN payment p
ON ( p.customer_id = c.customer_id )
WHERE amount = ( SELECT MAX(amount) from payment );
~~~


# <p id = 'psql1' > PSQL ve Uygulama I </p> 
## PSQL
### PSQL, PostgreSQL ile birlikte gelen terminal tabanlı bir kullanıcı arayüzüdür. PSQL sayesinde komut satırında sorgular yazıp, sonuçlarını görebiliriz. Aşağıda temel PSQL komutlarının ilk bölümünü bulabilirsiniz.

#### PSQL ile PostgreSQL'e bağlanmak.
~~~
psql -U <kullanıcı_adı>
~~~
#### Kullanıcıya ait şifreyi girdikten sonra varsayılan veritabanı postgres'e bağlanıyor.
~~~
postgres=#
~~~
#### Bulunan veritabanlarını listelemek için:
~~~
\l veya \list
~~~
#### Bizim örneğimizde dvdrental veritabanına bağlanacağız.
~~~
\c dvdrental veya \connect dvdrental
~~~
#### Bağlanılan dvdrental veritabanında bulunan tabloları listelemek için:
~~~
\dt
~~~
#### Herhangi bir tablonun sütunlarını ve tablo detaylarını görmek için:
~~~sql
\dt <tablo_adı>
~~~
#### PSQL terminal ekranından çıkmak için:
~~~
\q
~~~
#### PSQL ile PostgreSQL'e host, port, kullanıcı adı ve veritabanı ismi ile bağlanmak için:
~~~sql
psql -h <host_name> -p <port_name> -U <kullanıcı_adı> <veritabanı_adı>
~~~
#### Yeni veritabanı oluşturmak için
~~~sql
CREATE DATABASE <veritabanı_adı>
~~~
#### Yeni tablo oluşturmak için
~~~sql
CREATE TABLE <tablo_adı> {
  <sütun_adı> VERİ TİPİ (KISITLAMA)
  <sütun_adı> VERİ TİPİ (KISITLAMA)
  ...}
 ~~~
#### Tablo detaylarını görmek için
~~~sql
\d+ <tablo_adı>
~~~
#### Bir tablodaki sütun ismini değiştirmek için
~~~sql
ALTER TABLE <tablo_adı> RENAME COLUMN <sütun_adı> TO <yeni_sütun_adı>
~~~
#### Bir sütuna UNIQUE kısıtlaması eklemek için
~~~sql
ALTER TABLE <tablo_adı> ADD CONSTRAINT <kısıtlama_adı> UNIQUE <sütun_adı>
~~~

#### Örnek Sorgu Senaryoları
#### Customer tablosunda bulunan first_name değeri ve last_name değeri 'A' karakteri ile başlayan verileri sıralayınız.
~~~sql
SELECT * 
FROM customer
WHERE first_name LIKE 'A%' AND last_name LIKE 'A%';
~~~
#### Film tablosunda bulunan ve uzunluğu 80 ile 120 arasında bulunan ve aynı zamanda rental_rate değeri 0.99 veya 2.99 olan verileri sıralayınız.
~~~sql
SELECT * 
FROM film
WHERE (length BETWEEN 80 AND 120) AND (rental_rate IN (0.99, 2.99));
~~~

# <p id = 'Notlar' > NOTLAR </p> 
~~~sql
 ~~ = LIKE ,  ~~* = ILIKE , !~~ = NOT LIKE ,  !~~* = NOT LIKE
~~~

