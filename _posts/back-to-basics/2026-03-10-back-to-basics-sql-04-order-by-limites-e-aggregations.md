---
title: "Back to Basics – SQL 04 – ORDER BY, LIMIT e Agregações"
date: 2026-03-10 10:00
author: "Charles De Barros"
header:
 background-color: "#003f72"
 caption: "Structured Query Language é a base dos dados relacionais"
 caption_url: https://unsplash.com/
published: true
category: ["Back to Basics", "SQL"]
tags:
 - sql
 - order by
 - limit
 - aggregate functions
 - group by
series: "SQL do Zero ao Pro"
series_part: 4
image: https://res.cloudinary.com/charlesdebarros/image/upload/v1753179253/22112368_6537887_uaprve.svg
description: "Aprenda como ordenar resultados, limitar linhas e resumir dados usando ORDER BY, LIMIT e funções de agregação como COUNT, SUM e AVG."
---

# SQL 04 – ORDER BY, LIMIT e Agregações
## Transformando Dados Brutos em Respostas Úteis

Até agora, você aprendeu como **recuperar e filtrar dados**. 
Agora é hora de tornar esses dados **úteis**.

Neste artigo, você aprenderá a:
- Ordenar os resultados das consultas
- Limitar a quantidade de linhas retornadas
- Resumir grandes conjuntos de dados usando funções de agregação

Esta é a **Parte 04 da série SQL do Zero ao Pro**.

---

## Sumário

- [Ordenando Resultados com ORDER BY](#ordenando-resultados-com-order-by)
- [Limitando Linhas com LIMIT](#limitando-linhas-com-limit)
- [Por que as Agregações Importam](#por-que-as-agregações-importam)
- [Funções de Agregação Comuns](#funções-de-agregação-comuns)
- [GROUP BY Explicado](#group-by-explicado)
- [Filtrando Agregações com HAVING](#filtrando-agregações-com-having)
- [SQL para Desenvolvedores vs Analistas](#sql-for-developers-vs-analysts)
- [Exercícios Práticos](#exercícios-práticos)
- [Conclusão](#conclusion)

---

## Ordenando Resultados com ORDER BY

Por padrão, o SQL **não garante a ordem** dos dados.

Se a ordem for importante, você deve especificá-la explicitamente.

### Sintaxe Básica

```sql
SELECT *
FROM employees
ORDER BY last_name;
```

Isso ordena os resultados em ordem crescente por padrão.

---

**DESC vs ASC**

```sql
SELECT  *
FROM employees
ORDER BY hire_date DESC;
```

* ASC → ascendente/crescente (padrão)
* DESC → descendente/decrescente

---

## Ordenando por Múltiplas Colunas

```sql
SELECT *
FROM employees
ORDER BY department ASC, hire_date DESC;
```

**O que isso faz:**

* Agrupa os funcionários por departamento
* Mostra as contratações mais recentes primeiro dentro de cada departamento

---

## Limitando Linhas com LIMIT

A cláusula LIMIT restringe quantas linhas são retornadas.

**Exemplo**

```sql
SELECT *
FROM products
LIMIT 10;
```

Retorna apenas as primeiras 10 linhas.

---

## ORDER BY + LIMIT (Muito Comum)

```sql
SELECT *
FROM products
ORDER BY price DESC
LIMIT 5;
```

**Em português claro:** 
“Mostre-me os 5 produtos mais caros.”

---

## Por que as Agregações Importam

A maioria das perguntas do mundo real são **perguntas de resumo**, não perguntas de nível de linha.

**Exemplos:**

* Quantos usuários nós temos?
* Qual é o valor médio do pedido?
* Qual foi a receita total no mês passado?

É aqui que entram as **funções de agregação**.

---

## Funções de Agregação Comuns

**COUNT – Contar Linhas**

```sql
SELECT COUNT(*)
FROM users;
```

Conta o total de linhas.

---

**SUM – Somar Valores**

```sql
SELECT SUM(total_amount)
FROM orders;
```

Soma valores numéricos.

---

**AVG – Valor Médio**

```sql
SELECT AVG(price)
FROM products;
```

Calcula a média aritmética.

---

**MIN e MAX**

```sql
SELECT MIN(price), MAX(price)
FROM products;
```

Encontra os valores _mínimo (menor)_ e _máximo (maior)_.

---

**GROUP BY Explicado**

> O GROUP BY permite que você agregue por categoria.

**Exemplo: Contar Usuários por País**

```sql
SELECT country, COUNT(*) AS user_count
FROM users
GROUP BY country;
```

O que acontece:

* As linhas são agrupadas por país
* O COUNT é aplicado a cada grupo
* Uma linha por país é retornada

---

**Modelo Mental para o GROUP BY**

> O GROUP BY "achata" ou colapsa muitas linhas em poucas linhas de resumo.

---

**Filtrando Agregações com HAVING**

Você não pode usar WHERE com resultados de agregações.

Use `HAVING` em vez disso.

**Exemplo:**

```sql
SELECT country, COUNT(*) AS user_count
FROM users
GROUP BY country
HAVING COUNT(*) > 100;
```

**Em português claro:** 
“Mostre apenas os países com mais de 100 usuários.”

---

**WHERE vs HAVING**

| Cláusula | Filtra |
| --- | --- |
| WHERE | Linhas antes do agrupamento |
| HAVING | Grupos após a agregação |
| SQL | para Desenvolvedores vs Analistas |

--- 

## SQL para Desenvolvedores vs Analistas
**SQL para Desenvolvedores**

Desenvolvedores usam esses recursos para:

* Criar rankings (leaderboards)
* Paginar resultados de APIs
* Otimizar consultas

**Padrões comuns:**

* ORDER BY com colunas indexadas
* LIMIT para paginação
* COUNT para monitoramento e verificações de saúde (health checks)

```sql
SELECT COUNT(*)
FROM orders
WHERE status = 'pending';
```

---

**SQL para Analistas de Dados**

Analistas usam agregações constantemente para:

* Acompanhar KPIs
* Criar dashboards
* Identificar tendências

**Padrões comuns:**

* GROUP BY + AVG
* Agregações baseadas em tempo
* HAVING para limites (thresholds)

```sql
SELECT department, AVG(salary)
FROM employees
GROUP BY department;
```

---

## Exercícios Práticos

**Exercício 1 – Ordenando Dados**  

Escreva uma consulta para:

* Selecionar todas as colunas
* Da tabela `employees`
* Ordenar por `hire_date` do mais novo para o mais antigo

--- 
**Exercício 2 – Limitando Resultados**  
Escreva uma consulta para:

* Selecionar todas as colunas
* Da tabela `products`
* Retornar apenas os 3 produtos mais baratos

**Exercício 3 – Agregação Básica**  

Escreva uma consulta para:

* Contar o número total de usuários
* Da tabela `users`

**Exercício 4 – GROUP BY**  

Escreva uma consulta para:

* Contar quantos funcionários trabalham em cada departamento

**Prática Bônus**

Tente combinar:

* WHERE
* GROUP BY
* HAVING
* ORDER BY
* LIMIT

Em uma única consulta.

--- 

## Conclusão

Com ORDER BY, LIMIT e agregações, o SQL deixa de ser sobre **linhas** e passa a ser sobre **respostas**.

Se você consegue:

* Ordenar dados intencionalmente
* Limitar conjuntos de resultados
* Resumir tabelas grandes

Você agora está fazendo SQL do mundo real.

No próximo artigo (**SQL 05**), mergulharemos em padrões de **GROUP BY**, **HAVING** em profundidade e pensamento analítico com SQL.

Boa consulta! 🚀


## Soluções dos exercícios do artigo – SQL 04

**Exercício 1 – Ordenando Dados (Resposta)**

```sql
SELECT *
FROM employees
ORDER BY hire_date DESC;
```

**Explicação**

* ORDER BY hire_date ordena pela data de contratação
* DESC garante que as contratações mais recentes apareçam primeiro

--- 

**Exercício 2 – Limitando Resultados (Resposta)**

```sql
SELECT *
FROM products
ORDER BY price ASC
LIMIT 3;
```

**Explicação**

* Os produtos são ordenados do mais barato para o mais caro
* LIMIT 3 retorna apenas as três primeiras linhas

---

**Exercício 3 – Agregação Básica (Resposta)**

```sql
SELECT COUNT(*)
FROM users;
```

**Explicação**

* COUNT(*) conta todas as linhas da tabela
* O resultado é um único número representando o total de usuários

---

**Exercício 4 – GROUP BY (Resposta)**

```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;
```

**Explicação**

* As linhas são agrupadas por departamento
* COUNT(*) é aplicado a cada grupo
* Uma linha por departamento é retornada

--- 

**Exercício Bônus – Consulta Combinada (Exemplo de Resposta)**

```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
WHERE active = true
GROUP BY department
HAVING COUNT(*) > 10
ORDER BY employee_count DESC
LIMIT 5;
```

**Explicação em Português Claro**

* Olhe apenas para funcionários ativos
* Agrupe-os por departamento
* Mantenha os departamentos com mais de 10 funcionários
* Ordene os departamentos pela contagem de funcionários (maior primeiro)
* Retorne apenas os 5 principais departamentos

**Principais Aprendizados**

* **ORDER BY** controla como os resultados são ordenados
* **LIMIT** controla quantas linhas são retornadas
* Funções de agregação resumem os dados
* **GROUP BY** transforma dados de nível de linha em insights
* **HAVING** filtra resultados agregados

Se você consegue ler e escrever consultas como estas, você está oficialmente ___pensando analiticamente em SQL___.

A seguir: **SQL 05 – Padrões de GROUP BY, Mergulho no HAVING e Pensamento Analítico** 🚀