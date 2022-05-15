# PatikaDev-SQL
## <p id = 'Ödev 1' > Ödev 1 </p> 


#### Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

~~~Sql
Select title , description from film;
~~~


film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

~~~Sql
select * from film where length > 60 and lenght <75;

~~~

film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

~~~Sql
select * from film where rental_rate = 0.99 and replacement_cost = 12.99 or replacement_cost = 28.99;

~~~

customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

~~~Sql
select last_name from customer where first_name = 'Mary';
~~~


film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız

~~~Sql
select * from film where not(rental_rate = 4.99 OR rental_rate = 2.99) AND NOT length > 50;
~~~


## <p id = 'Ödev 2' > Ödev 2 </p> 

film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

~~~Sql
select * from film where replacement_cost BETWEEN 12.99 AND 16.99
~~~

actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

~~~Sql
select first_name , last_name from actor where first_name in ('Penelope','Nick','Ed');
~~~

film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

~~~Sql
select * from film where rental_rate in (0.99 , 2.99 , 4.99) and replacement_cost in (12.99 , 15.99 , 28.99);
~~~

## <p id = 'Ödev 3' > Ödev 3 </p> 

country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

~~~Sql
select country from country where country LIKE 'A%a';
~~~

country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

~~~Sql
select country from country where country like '%n' and   LENGTH(country) > 6;
~~~

film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız

~~~Sql
select title from film WHERE title ILIKE '%t%t%t%t%';
~~~

film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

~~~Sql
select * from film WHERE title LIKE 'C%' AND LENGTH(TITLE) > 90 AND rental_rate =2.99;
~~~

## <p id = 'Ödev 4' > Ödev 4 </p> 

film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

~~~Sql
select DISTINCT replacement_cost from film;
~~~

film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

~~~Sql
select count( DISTINCT (replacement_cost) )from film;
~~~

film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

~~~Sql
select Count(title) from film where title like 'T%' and rating = 'G';
~~~

country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

~~~Sql
select COUNT(country) from country where LENGTH(COUNTRY) = 5;
~~~

city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

~~~Sql
SELECT CITY FROM CITY WHERE CITY LIKE '%R' OR CITY LIKE '%r'
~~~

## <p id = 'Ödev 5' > Ödev 5 </p> 

film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız

~~~Sql
SELECT title, length FROM FILM WHERE TITLE LIKE '%n' order by length desc limit 5;
~~~

film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

~~~Sql
SELECT title, length FROM FILM WHERE TITLE LIKE '%n' order by length offset 5 limit 5;
~~~

customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

~~~Sql
SELECT last_name from customer where store_id = 1 order by last_name desc limit 4;
~~~

## <p id = 'Ödev 6' > Ödev 6 </p> 

film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

~~~Sql
SELECT AVG(rental_rate) from film;
~~~

film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

~~~Sql
SELECT count(title) from  film where title like 'C%';
~~~

film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır

~~~Sql
SELECT max(lenght) FROM FILM WHERE rental_rate = 0.99 ;
~~~

film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

~~~Sql
SELECT COUNT( DISTINCT replacement_cost )FROM film WHERE length > 150;
~~~


## <p id = 'Ödev 7' > Ödev 7 </p> 

film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

~~~Sql
SELECT rating from film group by rating;
~~~

film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

~~~Sql
SELECT replacement_cost , Count(replacement_cost) from film group by replacement_cost having Count(replacement_cost) > 50;
~~~

customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

~~~Sql
SELECT store_id , count(store_id) from customer group by store_id;
~~~

city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

~~~Sql
SELECT country_id,COUNT(*) FROM city GROUP BY country_id ORDER BY COUNT(*) DESC LIMIT 1;
~~~

## <p id = 'Ödev 8' > Ödev 8 </p> 

test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

~~~Sql
 CREATE TABLE employee (
  id INTEGER PRIMARY KEY,
  name VARCHAR(50) NOT NULL,
  email VARCHAR(100),
  birthday DATE
);
~~~

Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

~~~Sql
insert into employee (id, name, email, Birthday) values (1, 'Amberly', 'alowres0@springer.com', '2021-08-21');
insert into employee (id, name, email, Birthday) values (2, 'Beckie', 'bionn1@homestead.com', '2021-09-17');
insert into employee (id, name, email, Birthday) values (3, 'Alena', 'aoheaney2@trellian.com', '2022-04-21');
insert into employee (id, name, email, Birthday) values (4, 'Diena', 'dmcfaul3@google.ca', '2022-03-27');
insert into employee (id, name, email, Birthday) values (5, 'Kathye', 'kstockoe4@biglobe.ne.jp', '2022-01-16');
insert into employee (id, name, email, Birthday) values (6, 'Giacomo', 'gbrimicombe5@nytimes.com', '2022-04-03');
insert into employee (id, name, email, Birthday) values (7, 'Stacie', 'stroup6@vkontakte.ru', '2022-04-11');
insert into employee (id, name, email, Birthday) values (8, 'Emma', 'elatter7@vistaprint.com', '2021-09-04');
insert into employee (id, name, email, Birthday) values (9, 'Gerrie', 'gdanforth8@jigsy.com', '2022-02-08');
insert into employee (id, name, email, Birthday) values (10, 'Mureil', 'mprosh9@intel.com', '2022-05-10');
insert into employee (id, name, email, Birthday) values (11, 'Adrien', 'aheatera@cbslocal.com', '2021-06-11');
insert into employee (id, name, email, Birthday) values (12, 'Marabel', null, '2021-06-29');
insert into employee (id, name, email, Birthday) values (13, 'Kiri', 'kpetcheyc@wiley.com', '2022-05-14');
insert into employee (id, name, email, Birthday) values (14, 'Putnam', 'pbroggettid@is.gd', '2021-11-02');
insert into employee (id, name, email, Birthday) values (15, 'Lutero', 'lsagee@apache.org', '2021-10-09');
insert into employee (id, name, email, Birthday) values (16, 'Baxie', 'batwoolf@arstechnica.com', '2021-08-25');
insert into employee (id, name, email, Birthday) values (17, 'Angelika', 'aslorag@about.com', '2022-04-23');
insert into employee (id, name, email, Birthday) values (18, 'Codie', 'cscaddingh@ted.com', '2021-11-10');
insert into employee (id, name, email, Birthday) values (19, 'Tulley', 'thedderlyi@alexa.com', '2022-02-10');
insert into employee (id, name, email, Birthday) values (20, 'Raleigh', 'rnicholasj@diigo.com', '2021-05-26');
insert into employee (id, name, email, Birthday) values (21, 'Bette', 'bwoodallk@washingtonpost.com', '2022-05-04');
insert into employee (id, name, email, Birthday) values (22, 'Colin', 'cvedeneevl@purevolume.com', '2021-10-13');
insert into employee (id, name, email, Birthday) values (23, 'Isador', 'ihallardm@sitemeter.com', '2021-10-15');
insert into employee (id, name, email, Birthday) values (24, 'Lorelei', 'lmcmurtyn@xinhuanet.com', '2021-05-24');
insert into employee (id, name, email, Birthday) values (25, 'Shaun', 'smatissoffo@gmpg.org', '2022-02-04');
insert into employee (id, name, email, Birthday) values (26, 'Orly', 'omillgatep@digg.com', '2021-09-20');
insert into employee (id, name, email, Birthday) values (27, 'Nancey', null, '2022-02-08');
insert into employee (id, name, email, Birthday) values (28, 'Cicely', 'creesonr@live.com', '2021-05-22');
insert into employee (id, name, email, Birthday) values (29, 'Annetta', 'akuhnwalds@cnbc.com', '2021-10-13');
insert into employee (id, name, email, Birthday) values (30, 'Moses', 'mschruurt@wordpress.com', '2022-05-04');
insert into employee (id, name, email, Birthday) values (31, 'Tove', 'tallderidgeu@theglobeandmail.com', '2021-10-07');
insert into employee (id, name, email, Birthday) values (32, 'Daryl', null, '2022-02-04');
insert into employee (id, name, email, Birthday) values (33, 'Shayne', 'smcluckiew@berkeley.edu', '2021-09-18');
insert into employee (id, name, email, Birthday) values (34, 'Ilaire', 'icolerickx@amazon.co.uk', '2021-09-17');
insert into employee (id, name, email, Birthday) values (35, 'Lydon', 'lcoodey@ezinearticles.com', '2022-05-02');
insert into employee (id, name, email, Birthday) values (36, 'Kerk', 'kfaggez@squarespace.com', '2021-11-22');
insert into employee (id, name, email, Birthday) values (37, 'Garrot', null, '2022-02-28');
insert into employee (id, name, email, Birthday) values (38, 'Haleigh', 'hlowcock11@opensource.org', '2022-02-14');
insert into employee (id, name, email, Birthday) values (39, 'Jerrome', 'jpendre12@amazonaws.com', '2021-06-05');
insert into employee (id, name, email, Birthday) values (40, 'Reinwald', 'rgerritsma13@slate.com', '2021-07-25');
insert into employee (id, name, email, Birthday) values (41, 'Melvin', null, '2021-09-21');
insert into employee (id, name, email, Birthday) values (42, 'Eimile', 'estovold15@gov.uk', '2022-01-17');
insert into employee (id, name, email, Birthday) values (43, 'Codie', null, '2022-02-08');
insert into employee (id, name, email, Birthday) values (44, 'Ariela', 'abeddis17@github.com', '2022-01-21');
insert into employee (id, name, email, Birthday) values (45, 'Andeee', 'alandy18@abc.net.au', '2022-04-24');
insert into employee (id, name, email, Birthday) values (46, 'Lilli', 'lgrout19@hc360.com', '2021-12-22');
insert into employee (id, name, email, Birthday) values (47, 'Trumann', 'tcrowdson1a@jalbum.net', '2021-10-24');
insert into employee (id, name, email, Birthday) values (48, 'Claude', 'cpetru1b@techcrunch.com', '2021-09-19');
insert into employee (id, name, email, Birthday) values (49, 'Barbabas', 'bgilbeart1c@xrea.com', '2021-08-29');
insert into employee (id, name, email, Birthday) values (50, 'Michele', 'mchiechio1d@odnoklassniki.ru', '2021-11-06');

~~~

Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

~~~Sql
UPDATE Employee SET name = 'Siar' WHERE id = 1;
UPDATE Employee SET email = 'siar_1995@hotmail.com' WHERE id = 1;
UPDATE Employee SET birthday = '2021-04-23' WHERE birthday = '2021-09-19';
UPDATE Employee SET email = 'patikadev@gmail.com' WHERE email = 'bgilbeart1c@xrea.com';
UPDATE Employee SET name = 'Ahmet' WHERE name = 'Andeee';
~~~

Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
~~~Sql
DELETE FROM Employee WHERE name = 'Siar';
DELETE FROM Employee WHERE email = 'smcluckiew@berkeley.edu';
DELETE FROM Employee WHERE birthday = '2022-04-24';
DELETE FROM Employee WHERE name = 'Claude';
DELETE FROM Employee WHERE id = '35';
~~~

## <p id = 'Ödev 9' > Ödev 9 </p> 

city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

~~~Sql
select c.city , co.country from city as c inner join country as co on co.country_id = c.country_id ;
~~~

customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

~~~Sql
SELECT c.first_name, c.last_name, p.payment_id FROM customer as c INNER JOIN payment as p ON ( p.customer_id = c.customer_id);
~~~

customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

~~~Sql
SELECT c.first_name, c.last_name, r.rental_id FROM customer as  c JOIN rental as  r ON( c.customer_id = r.customer_id );
~~~
