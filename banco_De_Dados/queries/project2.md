### 1 - Qual o número de clientes únicos do estado de Minas Gerais?
```
SELECT COUNT(DISTINCT c.customer_id)
FROM customer c 
WHERE customer_state = 'MG';
```
___
### 2 - Qual a quantidade de cidades únicas dos vendedores do estado de Santa Catarina?
```
SELECT COUNT(DISTINCT s.seller_city)
FROM sellers s 
WHERE seller_state = 'SC';
```
___
### 3 - Qual a quantidade de cidades únicas de todos os vendedores da base?
```
SELECT COUNT(DISTINCT s.seller_city)
FROM sellers s;
```
___
### 4 - Qual o número total de pedidos únicos acima de R$ 3.500
```
SELECT COUNT(DISTINCT oi.order_id)
FROM order_items oi
WHERE price > 3500;
```
___
### 5 - Qual o valor médio do preço de todos os pedidos?
```
SELECT ROUND(AVG(oi.price), 2)
FROM order_items oi;
```
___
### 6 - Qual o maior valor de preço entre todos os pedidos?
```
SELECT MAX(oi.price)
FROM order_items oi;
```
___
### 7 - Qual o menor valor de preço entre todos os pedidos?
```
SELECT MIN(oi.price)
FROM order_items oi;
```
___
### 8 - Qual a quantidade de produtos distintos vendidos abaixo do preço de R$ 100.00?
```
SELECT COUNT(DISTINCT(oi.product_id))
FROM order_items oi 
WHERE oi.price < 100;
```
___
### 9 - Qual a quantidade de vendedores distintos que receberam algum pedido antes do dia 23 de setembro de 2016?
```
SELECT COUNT(DISTINCT(oi.seller_id))
FROM order_items oi 
WHERE shipping_limit_date < '2016-09-23 00:00:00';
```
___
### 10 - Quais os tipos de pagamentos existentes?
```
SELECT DISTINCT(op.payment_type)
FROM order_payments op;
```
___
### 11 - Qual o maior número de parcelas realizado?
```
SELECT MAX(op.payment_installments)
FROM order_payments op;
```
___
### 12 - Qual o menor número de parcelas realizado?
```
SELECT MIN(op.payment_installments)
FROM order_payments op;
```
___
### 13 - Qual a média do valor pago no cartão de crédito?
```
SELECT ROUND(AVG(op.payment_value), 2)
FROM order_payments op 
WHERE op.payment_type = 'credit_card';
```
___
### 14 - Quantos tipos de status para um pedido existem?
```
SELECT COUNT(DISTINCT(o.order_status))
FROM orders o;
```
___
### 15 - Quais os tipos de status para um pedido?
```
SELECT DISTINCT(o.order_status)
FROM orders o;
```
___
### 16 - Quantos clientes distintos fizeram um pedido?
```
SELECT COUNT(DISTINCT(o.customer_id))
FROM orders o;
```
___
### 17 - Quantos produtos estão cadastrados na empresa?
```
SELECT COUNT(DISTINCT(p.product_id))
FROM products p;
```
___
### 18 - Qual a quantidade máxima de fotos de um produto?
```
SELECT MAX(p.product_photos_qty)
FROM products p;
```
___
### 19 - Qual  o maior valor do peso entre todos os produtos?
```
SELECT MAX(p.product_weight_g)
FROM products p;
```
___
### 20 - Qual a altura média dos produtos?
```
SELECT ROUND(AVG(p.product_height_cm), 2)
FROM products p;
```
___

<img src="https://media.giphy.com/media/xT77XZrTKOxycjaYvK/giphy.gif?cid=790b7611lqe4ipkvaiz1rfni84u5vbe4qv6c1xdkhzfkl840&ep=v1_gifs_search&rid=giphy.gif&ct=g" alt="cat eith glasses" width="280" height="200" style="display: block; margin: auto;">