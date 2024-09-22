### 1 - Qual o número de clientes únicos de todos os estados?
```
SELECT 
	c.customer_state,	
	COUNT(DISTINCT(c.customer_id)) AS id_cliente
FROM customer c
GROUP BY c.customer_state;
```
___
### 2 - Qual o número de cidades únicas de todos os estados?
```
SELECT 
	c.customer_state,
	COUNT(DISTINCT(c.customer_city)) AS cidade_cliente 
FROM customer c 
GROUP BY c.customer_state;
```
___
### 3 - Qual o número de clientes únicos por estado e por cidade?
```
SELECT 
	c.customer_state,
	c.customer_city,
	COUNT(DISTINCT(c.customer_id)) AS cliente_por_cidade
FROM customer c 
GROUP BY c.customer_state, c.customer_city;
```
___
### 4 - Qual o número de clientes únicos por cidade e por estado?
```
SELECT 
	c.customer_city,
	c.customer_state,
	COUNT(DISTINCT(c.customer_id)) AS cliente_por_cidade
FROM customer c 
GROUP BY c.customer_city, c.customer_state;
```
___
### 5 - Qual o número total de pedidos únicos por cada vendedor?
```
SELECT 
	oi.seller_id,
	COUNT(DISTINCT(oi.order_id)) AS quantidade_pedidos
FROM order_items oi 
GROUP BY oi.seller_id;
```
___
### 6 - Qual o número total de pedidos únicos, a data mínima e máxima de  limite envio, o valor máximo, mínimo e médio do frete dos pedidos por cada vendedor?
```
SELECT 
	oi.seller_id,
	COUNT(DISTINCT(oi.order_id)) AS pedidos_unicos,
	MIN(oi.shipping_limit_date) AS data_minima_envio,
	MAX(oi.shipping_limit_date) AS data_maxima_envio,
	MAX(oi.freight_value) AS valor_maximo_frete,
	MIN(oi.freight_value) AS valor_minimo_frete,
	AVG(oi.freight_value) AS valor_medio_frete
FROM order_items oi 
GROUP BY oi.seller_id;
```
___
### 7 - Qual o valor médio, máximo e mínimo do preço de todos os pedidos de cada produto?
```
SELECT 
	oi.product_id,
	AVG(oi.price) AS preco_medio,
	MAX(oi.price) AS preco_maximo,
	MIN(oi.price) AS preco_minimo
FROM order_items oi 
GROUP BY oi.product_id;
```
___
### 8 - Qual a quantidade de vendedores distintos que receberam algum pedido e o preço médio das vendas?
```
SELECT 
	COUNT(DISTINCT(oi.seller_id)) AS quantidade_vendedores,
	ROUND(AVG(oi.price), 2) AS media_vendas
FROM order_items oi;
```
___
### 9 - Qual a quantidade de pedidos por tipo de pagamentos?
```
SELECT 
	op.payment_type,
	COUNT(order_id) AS quantidade_pedidos 
FROM order_payments op
GROUP BY op.payment_type ;
```
___
### 10 - Qual a quantidade de pedidos, a média do valor do pagamento e o número máximo de parcelas por tipo de pagamentos?
```
SELECT 
	op.payment_type,
	COUNT(op.order_id) AS quantidade_pedidos,
	AVG(op.payment_value) AS media_valor,
	MAX(op.payment_installments) AS maximo_parcelas
FROM order_payments op
GROUP BY op.payment_type;
```
___
### 11 - Qual a valor mínimo, máximo, médio e as soma total paga por cada tipo de pagamento e número de parcelas disponíveis?
```
SELECT 
	op.payment_type,
	op.payment_installments,
	MAX(op.payment_value) AS valor_maximo,
	MIN(op.payment_value) AS valor_minimo,
	AVG(op.payment_value) AS valor_medio,
	SUM(op.payment_value) AS valor_total
FROM order_payments op
GROUP BY op.payment_type, op.payment_installments;
```
___
### 12 - Qual a média de pedidos por cliente?
```
SELECT  
	o.customer_id,
	AVG(o.order_id) AS media_pedidos
FROM orders o 
GROUP BY o.customer_id;
```
___
### 13 - Qual a quantidade de pedidos por status?
```
SELECT 
	o.order_status,
	COUNT(o.order_id) AS quantidade_pedidos
FROM orders o 
GROUP BY o.order_status;
```
___
### 14 - Qual a quantidade de pedidos realizados por dia?
#### OBS: Use o comando DATE( ) para converter de timestamp (data com hora) para apenas data!
```
SELECT 
	DATE(o.order_approved_at) AS data,
	COUNT(o.order_id) AS quantidade_pedidos
FROM orders o 
GROUP BY DATE(o.order_approved_at);
```
___
### 15 - Quantos produtos estão cadastrados na empresa por categoria?
```
SELECT 
	p.product_category_name,
	COUNT( DISTINCT (p.product_id)) AS quantidade_produtos 
FROM products p 
GROUP BY p.product_category_name;
```
___

<img src="https://media.giphy.com/media/SVH9y2LQUVVCRcqD7o/giphy.gif?cid=790b7611acwu7obc0yrvo5er6ieraqaxonhi8vq2745znjmy&ep=v1_gifs_search&rid=giphy.gif&ct=g" alt="very cool" width="280" height="200" style="display: block; margin: auto;">