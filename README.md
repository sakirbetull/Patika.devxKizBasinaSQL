# Patika.devxKizBasinaSQL

# DVD Rental Veri Tabanı - Veri Analisti Ödevi

Bu proje, `dvdrental` örnek veri tabanı kullanarak farklı sorguların yazılmasını ve analiz edilmesini içerir. Aşağıdaki senaryolar kapsamında, çeşitli filtreleme işlemleri yapılmıştır.

## Sorgular
## ÖDEV 1

1. **Film Tablosunda `title` ve `description` Sütunlarındaki Veriler**
   ```sql
   select title, description from film;
   ```

2. **Film Tablosunda length 60'dan Büyük ve 75'ten Küçük Olma Koşuluyla Verileri Sıralama**
   ```sql
   select * from film
   where length > 60 and length < 75;
   ```
3. **Film Tablosunda rental_rate 0.99 ve replacement_cost 12.99 veya 28.99 Olma Koşuluyla Verileri Sıralama**
   ```sql
   select * from film
   where rental_rate = 0.99 and (replacement_cost = 12.99 or replacement_cost = 28.99);
   ```
4. **Customer Tablosunda first_name 'Mary' Olan Müşterinin last_name'ini Sorgulama**
   ```sql
   select * from customer
   where first_name = 'Mary';
   ```
   
5. **Film Tablosundaki length 50'den Büyük Olmayan ve rental_rate 2.99 veya 4.99 Olmayan Verileri Sıralama**
   ```sql
   select * from film 
   where not (length > 50 and (rental_rate = 2.99 or rental_rate = 4.99));
   ```


<img width="1079" alt="Ekran görüntüsü 2025-05-08 213044" src="https://github.com/user-attachments/assets/55830f41-9b9a-4b30-a848-c5b440ad0499" />

## ÖDEV 2

1. **Replacement Cost Değeri 12.99 ile 16.99 Arasında Olan Filmler (BETWEEN - AND)**
   ```sql
   select * from film
   where replacement_cost between 12.99 and 16.98;
   ```

2️. **Actor Tablosunda First Name 'Penelope', 'Nick' veya 'Ed' Olanlar (IN Kullanımı)**
   ```sql
   select * from actor
   where first_name in ('Penelope', 'Nick', 'Ed');
   ```

3️. **Film Tablosunda Belirli rental_rate ve replacement_cost Olan Filmler (IN Kullanımı)**
   ```sql
   select * from film
   where rental_rate in (0.99, 2.99, 4.99) and replacement_cost in (12.99, 15.99, 28.99);
   ```

<img width="1079" alt="Ekran görüntüsü 2025-05-08 221647" src="https://github.com/user-attachments/assets/8320fea2-ba7f-4082-ac7a-ddfd1e5ae0f9" />


## ÖDEV 3


1. **'A' Harfi ile Başlayıp `'a'` Harfi ile Biten Ülke İsimleri**
   ```sql
   select * from country
   where country like 'A%a';
   ```
   
2. **En Az 6 Karakter Uzunluğunda ve 'n' Harfi ile Biten Ülkeler**
   ```sql
   select * from country
   where country like '%_____%n';
   ```

3. Film İsminde En Az 4 Tane 'T' Harfi Geçen Filmler
   ```sql
   select * from film
   where title ilike '%t%t%t%t%';
   ```

4. **'C' ile Başlayan, Uzunluğu 90'dan Büyük ve Kirası 2.99 Olan Filmler**
   ```sql
   select * from film
   where title ilike 'C%' AND length > 90 AND rental_rate = 2.99;
   ```
   
* column LIKE 'pattern' ifadesi, aslında column ~~ 'pattern'

* column ILIKE 'pattern' ifadesi, aslında column ~~* 'pattern'

  <img width="1075" alt="Ekran görüntüsü 2025-05-08 233031" src="https://github.com/user-attachments/assets/c9b7ae0d-e276-44b8-a0f7-456d3a410204" />

## ÖDEV 4

1️. **`replacement_cost` Sütunundaki Farklı Değerleri Listeleme**
   ```sql
   select distinct(replacement_cost) from film;
   ```

2️. **replacement_cost Sütununda Kaç Farklı Değer Olduğunu Hesaplama**
   ```sql
   select count(distinct replacement_cost) from film;
   ```

3️. **İsmi 'T' Harfiyle Başlayan ve Rating Değeri 'G' Olan Film Sayısı**
   ```sql
   select count(*) from film
   where title like 'T%' and rating = 'G';
   ```

4️. **Tam Olarak 5 Karakter Uzunluğunda Ülke İsimlerinin Sayısı**
   ```sql
   select count(*) from country
   where country like '_____';
   ```

5️. **Şehir İsimlerinden 'R' ya da 'r' Harfiyle Bitenlerin Sayısı**
   ```sql
   select count(*) from city 
   where city ilike '%r';
   ```


**PSQL**

**PSQL, PostgreSQL ile birlikte gelen terminal tabanlı bir kullanıcı arayüzüdür.**
**PSQL sayesinde komut satırında sorgular yazıp, sonuçlarını görebiliriz.**

## ÖDEV 5

1️. **Sonu 'n' Harfi ile Biten En Uzun 5 Film**
   ```sql
   select * from film
   where title like '%n'
   order by length desc
   limit 5;
   ```

2️. **Sonu 'n' Harfi ile Biten ve Uzunluk Bakımından 6. ila 10. Sıradaki Filmler**
   ```sql
   select * from film
   where title like '%n'
   order by length desc
   offset 5
   limit 5;
   ```

3️. **store_id = 1 Olan Müşterilerden last_name Sırasına Göre İlk 4 Kayıt**
   ```sql
   select * from customer
   where store_id = 1
   order by last_name desc
   limit 4;
   ```

<img width="1076" alt="Ekran görüntüsü 2025-05-10 155834" src="https://github.com/user-attachments/assets/246aa0c0-6f01-4bf0-84b2-14ff93eadd3e" />


# ÖDEV 6

1️. **Rental Rate Ortalaması**
   ```sql
   select avg(rental_rate) from film;
   ```

2️. **Baş Harfi 'C' Olan Film Sayısı**
   ```sql
   select count(*) from film
   where title like 'C%';
   ```

3️. **Kiralama Ücreti 0.99 Olan Filmler Arasındaki En Uzun Süre**
   ```sql
   select max(length) from film
   where rental_rate = 0.99;
   ```

4️. **150 Dakikadan Uzun Filmler Arasında Kaç Farklı replacement_cost Değeri Var?**
   ```sql
   select count(distinct replacement_cost) from film
   where length > 150;
   ```

# ÖDEV 7

1️. **Rating Değerlerine Göre Film Sayısı**
   ```sql
   select count(*), rating from film
   group by rating;
   ```

2️. **50'den Fazla Filme Sahip replacement_cost Değerleri**
   ```sql
   select count(*), replacement_cost from film
   group by replacement_cost
   having count(*) > 50
   order by 1;
   ```

3️. **store_id Bazlı Müşteri Sayıları**
   ```sql
   select store_id, count(customer_id) from customer
   group by store_id;
   ```

4️. **En Fazla Şehir Sayısına Sahip Ülke (country_id)**
   ```sql
   select country_id, count(city_id) as city_count
   from city
   group by country_id
   order by city_count desc
   limit 1;
   ```

