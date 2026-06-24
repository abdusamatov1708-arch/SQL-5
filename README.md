# SQL-5
SELECT COUNT(*)                    AS jami_buyurtmalar,
       COUNT(DISTINCT customer_id) AS mijozlar_soni
FROM orders;
SELECT SUM(amount) AS jami_savdo,
       AVG(amount) AS ortacha_chekka,
       MIN(amount) AS eng_arzon_buyurtma,
       MAX(amount) AS eng_qimmat_buyurtma
FROM orders;
SELECT ROUND(AVG(amount), 2) AS yaxlatilgan_orta_savdo
FROM orders;
SELECT UPPER(customer_name)                                         AS katta_harflarda,
       LENGTH(customer_name)                                        AS ism_uzunligi,
       customer_name || ' - barcha buyurtmalar summasi: ' || amount AS xabar_matni
FROM orders;
SELECT NOW()                          AS hozirgi_vaqt,
       CURRENT_DATE                   AS bugungi_sana,
       EXTRACT(YEAR FROM order_date)  AS buyurtma_yili,
       EXTRACT(MONTH FROM order_date) AS buyurtma_oyi
FROM orders;
SELECT CEIL(4.1)  AS tepaga, -- Natija: 5
       FLOOR(4.9) AS pastga, -- Natija: 4
       MOD(10, 3) AS qoldiq  -- Natija: 1 (chunki 10 ni 3 ga bo'lsa 1 qoldiq qoladi)
FROM orders;
-- BU KO'D XATOLIK BERADI!
SELECT customer_id, AVG(amount)
FROM orders
WHERE AVG(amount) > 500
GROUP BY customer_id;
SELECT customer_id, AVG(amount) AS ortacha_summa
FROM orders
GROUP BY customer_id
HAVING AVG(amount) > 500;
