### 1- Gere uma tabela com o id do cliente, a cidade e o estado onde ele vive.
````
SELECT customer_id, customer_city, customer_state 
FROM customer;
````
___
### 2- Gere uma tabela com o id do cliente e a cidade, somente dos clientes que vivem em Santa Catarina.
```
SELECT customer_id, customer_city
FROM customer c
WHERE c.customer_state = 'SC';
```
___
### 3- Gere uma tabela com o id do cliente e o estado, somente dos clientes que vivem em Florianópolis.
```
SELECT customer_id, customer_state
FROM customer c 
WHERE c.customer_city = 'florianopolis';
```
___
### 4- Gere uma tabela com o estado, latitude e longitude do estado de São Paulo
```
SELECT g.geolocation_state, g.geolocation_lat, g.geolocation_lng
FROM geolocation g
WHERE g.geolocation_state = 'SP';
```
___
### 5- Gere uma tabela com o id do produto, a data limite de envio e o preço, somente para produtos acima de 6300
```
SELECT oi.product_id, oi.shipping_limit_date, oi.price 
FROM order_items oi
WHERE oi.price > 6300;
```
___
### 6- Gere uma tabela com o id do pedido, o tipo de pagamento e o número de parcelas, somente para produtos com parcelas menores que 1.
```
SELECT op.order_id, op.payment_type, op.payment_installments 
FROM order_payments op 
WHERE op.payment_installments < 1;
```
___
### 7- Gere uma tabela com o id do pedido, id do cliente, o status do pedido e a data de aprovação , somente para compras aprovadas até dia 05 de Outubro de 2016
```
SELECT o.order_id, o.customer_id, o.order_status, o.order_approved_at
FROM orders o
WHERE o.order_approved_at < '2016-10-05';
```
___

<img src="https://media.giphy.com/media/twdrxCrIXkFhadahQE/giphy.gif?cid=ecf05e47gczh3iiypdf4038lsj2chaae4soitqv64iyeh6sk&ep=v1_gifs_search&rid=giphy.gif&ct=g" alt="mind blowing" width="280" height="200" style="display: block; margin: auto;">