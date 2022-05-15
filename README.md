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
