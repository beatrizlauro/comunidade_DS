### 1 - Qual o número de clientes únicos do estado de São Paulo?
```
SELECT 
	COUNT(DISTINCT(c.customer_id)) AS numero_clientes_SP
FROM customer c 
WHERE c.customer_state = 'SP';
```
___
### 2 - Qual o número total de pedidos únicos feitos no dia 08 de Outubro de 2016.
```
SELECT 
	COUNT(DISTINCT(o.order_id)) as qtd_pedidos
FROM orders o 
WHERE DATE(o.order_purchase_timestamp) = '2016-10-08'; 
```
___
### 3 - Qual o número total de pedidos únicos feitos a partir do dia 08 de Outubro de 2016.
```
SELECT 
	COUNT(DISTINCT(o.order_id)) AS qtd_pedidos
FROM orders o 
WHERE DATE(o.order_purchase_timestamp) > '2016-10-08';
```
___
### 4 - Qual o número total de pedidos únicos feitos com a data limite de envio, a partir do dia 08 de Outubro de 2016 incluso.
```
SELECT 
	COUNT(DISTINCT(oi.order_id)) qtd_pedidos
FROM order_items oi 
WHERE DATE(oi.shipping_limit_date) >= '2016-10-08';
```
___
### 5 - Qual é o número total de pedidos únicos e o valor médio do frete para pedidos com valor abaixo de R$ 1.100?
```
SELECT
	COUNT(DISTINCT(oi.order_id)) AS qtd_pedidos_unicos,
	ROUND(AVG(oi.freight_value), 2) AS media_frete
FROM order_items oi 
WHERE oi.price <1100;
```
___
### 6 - Qual é o número total de pedidos únicos, a data mínima e máxima de limite de envio, e os valores máximo, mínimo e médio do frete para pedidos com valor abaixo de R$ 1.100, agrupados por cada vendedor?
```
SELECT 
	oi.seller_id,
	COUNT(DISTINCT(oi.order_id)) AS qtd_pedidos_unicos,
	DATE(MAX(oi.shipping_limit_date)) AS data_max_envio,
	DATE(MIN(oi.shipping_limit_date)) AS data_min_envio,
	MAX(oi.freight_value) AS max_frete,
	MIN(oi.freight_value) AS min_frete,
	AVG(oi.freight_value) AS media_frete
FROM order_items oi 
WHERE oi.price < 1100
GROUP BY oi.seller_id;
```
___

<img src="https://media.giphy.com/media/5Zesu5VPNGJlm/giphy.gif?cid=790b7611hx551rcmlsmjqtardhs3172okp4ljirw391z49iu&ep=v1_gifs_search&rid=giphy.gif&ct=g" alt="i'm trying my best" width="280" height="200" style="display: block; margin: auto;">