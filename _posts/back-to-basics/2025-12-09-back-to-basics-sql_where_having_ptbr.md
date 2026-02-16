---
title: "Back to Basics - SQL 06"
subheadline: "WHERE e HAVING"
date: 2025-12-09 09:00
author: "Charles De Barros"
header: 
    background-color: "#003f72"
    caption: This is a caption for the header image with link
    caption_url: https://unsplash.com/
category: ['Back to Basics', 'SQL']
tags: ["Back to Basics", "SQL"]
image: https://res.cloudinary.com/charlesdebarros/image/upload/v1765302753/sql_where_and_having_difference_1024px_xfumxw.png
---

# Filtragem SQL com WHERE e HAVING
*(Com diagramas, ilustrações e desafios adicionais)*

## Índice
1. [Visão Geral](#visão-geral)
2. [Entendendo WHERE](#entendendo-where)  
3. [O que é Agregação?](#o-que-é-agregação)
4. [HAVING filtra grupos agregados](#having-filtra-grupos-agregados)
5. [WHERE vs HAVING](#where-vs-having)
6.  [Quando Usar Cada Uma](#quando-usar-cada-uma)
7. [Desafios Práticos](#desafios-práticos)  

---

## Visão Geral
Este artigo explora como o SQL filtra dados usando **WHERE** e **HAVING**, como funciona a agregação, e quando usar cada cláusula. Inclui diagramas, exemplos e desafios práticos.

---

## Entendendo WHERE

### O que WHERE faz?
A cláusula **WHERE** filtra linhas individuais *antes* de qualquer agrupamento ou agregação.

#### Diagrama: WHERE no fluxo da consulta
```

Linhas brutas da tabela
|
v
\+-----------+
|  WHERE    |  \<-- filtra antes do agrupamento
\+-----------+
|
v
(Linhas filtradas)

````

#### Exemplo
```sql
SELECT product_name, price
FROM products
WHERE price > 300;
````

-----

## O que é Agregação?

Agregação combina várias linhas em valores resumidos (SUM, COUNT, AVG etc.).

### Diagrama: Fluxo de agregação

```
Linhas filtradas
      |
      v
 +-------------+
 |  GROUP BY   |
 +-------------+
      |
      v
Resultados agregados
```

-----

## HAVING filtra grupos agregados

WHERE não pode filtrar valores agregados — por isso existe o **HAVING**.

### Diagrama: HAVING no fluxo da consulta

```
Linhas brutas
   |
   v
 +--------+
 | WHERE  |
 +--------+
   |
   v
Linhas filtradas
   |
   v
 +-----------+
 | GROUP BY  |
 +-----------+
   |
   v
Linhas agregadas
   |
   v
 +--------+
 | HAVING |  <-- filtra DEPOIS da agregação
 +--------+
```

#### Exemplo

```sql
SELECT customer_id, SUM(amount) AS total_spent
FROM sales
GROUP BY customer_id
HAVING SUM(amount) > 150;
```

-----

## WHERE vs HAVING

### Ilustração: O que cada cláusula filtra

```
 +------------------------------------+
 |            WHERE                   |
 |------------------------------------|
 | Filtra linhas individuais          |
 | Não usa agregações                 |
 | Executa antes do GROUP BY          |
 +------------------------------------+

 +------------------------------------+
 |            HAVING                  |
 |------------------------------------|
 | Filtra dados agregados             |
 | Usa COUNT, SUM etc                 |
 | Executa após o GROUP BY            |
 +------------------------------------+
```

-----

## Quando Usar Cada Uma

| Situação | WHERE | HAVING |
|----------|--------|---------|
| Filtrar linhas por valores brutos | ✔ | ❌ |
| Filtrar grupos por valores agregados | ❌ | ✔ |
| Excluir linhas desnecessárias cedo | ✔ | ❌ |
| Usar COUNT(), SUM(), AVG() | ❌ | ✔ |

-----

## Desafios Práticos

### Desafio 1

**Tabela:** `orders(customer_id, order_amount, status)`  
**Tarefa:** Mostrar clientes que:

1.  Apenas pedidos com status = 'Completed'
2.  Tenham mais de 3 pedidos concluídos
3.  Tenham gasto total acima de R$ 500

#### Solução

```sql
SELECT customer_id,
       COUNT(*) AS num_orders,
       SUM(order_amount) AS total_spent
FROM orders
WHERE status = 'Completed'
GROUP BY customer_id
HAVING COUNT(*) > 3
   AND SUM(order_amount) > 500;
```

-----

### Desafio 2

**Tabela:** `products(category, price)`  
**Tarefa:** Listar categorias cuja **média** de preços esteja entre R$ 200 e R$ 500.

#### Solução

```sql
SELECT category, AVG(price) AS avg_price
FROM products
GROUP BY category
HAVING AVG(price) BETWEEN 200 AND 500;
```

-----

### Desafio 3

**Tabela:** `sales(store, amount, date)`  
**Tarefa:** Exibir lojas que tiveram pelo menos **10 vendas acima de R$ 50** durante janeiro.

#### Solução

```sql
SELECT store,
       COUNT(*) AS count_sales
FROM sales
WHERE amount > 50
  AND date BETWEEN '2025-01-01' AND '2025-01-31'
GROUP BY store
HAVING COUNT(*) >= 10;
```
