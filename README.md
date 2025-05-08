# Patika.devxKizBasinaSQL

# DVD Rental Veri Tabanı - Veri Analisti Ödevi

Bu proje, `dvdrental` örnek veri tabanı kullanarak farklı sorguların yazılmasını ve analiz edilmesini içerir. Aşağıda verilen SQL sorguları, veri tabanındaki film ve müşteri verilerini çeşitli filtrelerle incelemektedir.

## Sorgular

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

