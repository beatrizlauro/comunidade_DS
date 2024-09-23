### 1 - Qual o número de clientes únicos nos estado de Minas Gerais ou Rio de Janeiro?
```
SELECT 
	c.customer_state,
	COUNT(DISTINCT c.customer_id) AS clientes_MG_RJ
FROM customer c 
WHERE c.customer_state IN ('MG', 'RJ')
GROUP BY c.customer_state;
```
___
### 2 - Qual a quantidade de cidades únicas dos vendedores no estado de São Paulo ou Rio de Janeiro com a latitude maior que -24.54 e longitude menor que -45.63?
```
SELECT
	g.geolocation_state,
	COUNT(DISTINCT(g.geolocation_city)) AS cidades
FROM geolocation g 
WHERE 
	g.geolocation_state in ('SP', 'RJ') 
	AND g.geolocation_lat > -24.54 
	AND g.geolocation_lng < -45.63
GROUP BY g.geolocation_state;
```
___
### 3 - Qual o número total de pedidos únicos, o número total de produtos e o preço médio dos pedidos com o preço de frete maior que R$ 20 e a data limite de envio entre os dias 1 e 31 de Outubro de 2016? 
#### OBS: Use o comando DATE( ) para converter de timestamp (data com hora) para apenas data!
```
SELECT 
	COUNT(DISTINCT(oi.order_id)) AS pedidos_unicos,
	COUNT(oi.product_id) AS total_produtos,
	ROUND(AVG(oi.price), 2) AS preco_medio
FROM order_items oi
WHERE 
	oi.freight_value > 20 
	AND DATE(oi.shipping_limit_date) BETWEEN '2016-10-01' AND '2016-10-31';
```
___
### 4 - Mostre a quantidade total dos pedidos e o valor total do pagamento, para pagamentos entre 1 e 5 prestações ou um valor de pagamento acima de R$ 5000. Agrupe por quantidade de prestações.
```
SELECT 
	op.payment_installments AS quantidade_parcelas,
	COUNT(op.order_id) AS quantidade_pedidos,
	SUM(op.payment_value) AS total_pagamento
FROM order_payments op 
WHERE 
	op.payment_installments BETWEEN 1 AND 5 
	OR op.payment_value > 5000
GROUP BY op.payment_installments;
```
___
### 5 - Qual a quantidade de pedidos com o status em processamento ou cancelada acontecem com a data estimada de entrega maior que 01 de Janeiro de 2017 ou menor que 23 de Novembro de 2016?
```
SELECT 
	o.order_status,
	COUNT(o.order_id) AS quantidade_pedidos
FROM orders o 
WHERE 
	o.order_status in ('canceled', 'processing') 
	AND (DATE(o.order_estimated_delivery_date) > '2017-01-01' OR DATE(o.order_estimated_delivery_date) < '2016-11-23')
GROUP BY o.order_status ;
```
___
### 6 - Quantos produtos estão cadastrados nas categorias: perfumaria, brinquedos, esporte lazer, cama mesa e banho e móveis de escritório que possuem mais de 5 fotos, um peso maior que 5 g, um altura maior que 10 cm, uma largura maior que 20 cm?
```
SELECT 
	p.product_category_name,
	COUNT(DISTINCT p.product_id) AS quantidade_items
FROM products p 
WHERE 
	p.product_category_name in ('perfumaria', 'brinquedos', 'esporte_lazer', 'cama_mesa_banho', 'moveis_escritorio')
	AND p.product_photos_qty > 5 
	AND p.product_height_cm > 10 
	AND p.product_width_cm > 20
GROUP BY p.product_category_name;
```
___

<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExM3pwMjJoamliN243Z3l3czZkcWt3aTZjaHV1cWI1Z3lhN21vY3U3cCZlcD12MV9naWZzX3NlYXJjaCZjdD1n/CTX0ivSQbI78A/giphy.gif" alt="technology" width="280" height="200" style="display: block; margin: auto;">