---
title: "De Volta ao Básico - SQL 03 – Consultas SELECT e Filtragem de Dados"
date: 2026-03-03 10:00
author: "Charles De Barros"
header:
  background-color: "#003f72"
  caption: "Structured Query Language é a base dos dados relacionais"
  caption_url: https://unsplash.com/
category: ["Back to Basics", "SQL"]
tags:
  - sql
  - select statement
  - where clause
  - filtering data
  - database queries
series: "SQL do Zero ao Pro"
series_part: 3
image: https://res.cloudinary.com/charlesdebarros/image/upload/v1753179253/22112368_6537887_uaprve.svg
description: "Aprenda a consultar dados usando SELECT, WHERE, operadores de comparação e condições lógicas. Habilidades essenciais de SQL para desenvolvedores e analistas."
---

# Consultas SELECT & filtragem de dados - fazendo as perguntas certas aos seus dados

O comando **SELECT** é, sem dúvida, o comando SQL mais utilizado.  
Se o SQL fosse um idioma, o **SELECT** seria a frase que você mais escreveria.

Neste artigo, você aprenderá como:
- Recuperar dados de tabelas
- Filtrar linhas usando condições
- Combinar múltiplos filtros
- Pensar como o banco de dados ao consultar dados

Esta é a **Parte 03 da série SQL do Zero ao Pro**.

---

## Sumário

- [O que o SELECT faz?](#o-que-o-select-faz)
- [Selecionando Colunas](#selecionando-colunas)
- [Filtrando Linhas com WHERE](#filtrando-linhas-com-where)
- [Operadores de Comparação](#operadores-de-comparação)
- [Operadores Lógicos](#operadores-lógicos)
- [Filtrando Texto e Datas](#filtrando-texto-e-datas)
- [SQL para Desenvolvedores vs Analistas](#sql-for-developers-vs-analysts)
- [Exercícios Práticos](#exercícios-práticos)
- [Conclusão](#conclusão)

---

## O que o SELECT faz?

O comando `SELECT` recupera dados de uma ou mais tabelas.

### Estrutura básica

```sql
SELECT nome_da_coluna
FROM nome_da_tabela;
```

**Examplo**
```sql
SELECT name
FROM customers;
```

**O que isto significa:**  
* Procure na tabela customers (clientes)
* Retorne os valores da coluna name (nome)
* Inclua todas as linhas

### Selecionando colunas

**Selecionando todas as colunas**
```sql
SELECT * 
FROM employees;
```

> ⚠️ ___`SELECT *`___ é útil para aprendizado, mas deve ser evitado em consultas de produção.

**Selecionando colunas específicas SQL**

```sql
SELECT first_name, last_name
FROM employees; 
```
 
**Benefícios:**

* Consultas mais rápidas
* Intenção clara
* Menos dados desnecessários

### Filtrando linhas com WHERE

A cláusula `WHERE` filtra linhas com base em uma condição.

**Exemplo básico**

```sql 
SELECT *
FROM employees
WHERE department = 'HR';
```

Em português claro:

* Procure em employees (funcionários)
* Mantenha apenas as linhas onde o department (departamento) seja 'HR' (RH)

### Operadores de Comparação

O SQL utiliza operadores de comparação para filtrar valores.

|Operador|Significado|Exemplo|
|---|---|---|
| = | Igual a | department = 'HR' |
| != ou <> | Diferente de | status != 'inactive' |
|> | Maior que | salary > 50000 |
|< | Menor que | age < 30 |
|>= | Maior ou igual | price >= 100 |
|<= | Menor ou igual | score <= 60 |

Exemplo

```sql
SELECT name, price
FROM products
WHERE price > 100;
```

### Operadores lógicos

Os operadores lógicos permitem combinar condições.

#### AND (E)

```sql
SELECT  *
FROM employees
WHERE department = 'Sales'
AND salary > 60000;
```

Ambas as condições devem ser verdadeiras.
#### OR (OU)

```sql
SELECT  *
FROM employees
WHERE department = 'HR'
OR department = 'Finance';
```
Qualquer uma das condições pode ser verdadeira.

#### NOT (NÃO)

```sql
SELECT  *
FROM users
WHERE NOT active = true;
```
Nega uma condição.

### Filtrando texto e datas

**Filtrando texto**

Valores de texto devem estar entre aspas simples.

```sql
SELECT  *
FROM customers
WHERE country = 'UK';
```
Comparações de texto podem ser **case-sensitive** (diferenciar maiúsculas de minúsculas) dependendo da colação (collation) do banco de dados.

**Filtrando datas**

```sql
SELECT  *
FROM orders
WHERE order_date >= '2025-01-01';
```

Utilizar tipos de data adequados permite:
* Ordenação
* Filtragem por intervalos
* Cálculos de data

### SQL para Desenvolvedores vs Analistas

**SQL para Desenvolvedores**

Desenvolvedores focam em:
* Filtros precisos
* Performance
* Uso de índices

**Padrões comuns:**

* Filtragem por chaves primárias
* Uso de cláusulas WHERE em JOINs
* Consultas defensivas (evitando linhas inesperadas)

```sql
SELECT  *
FROM users
WHERE id = 42;
```

**SQL para Analistas de Dados**

Analistas focam em:
* Explorar conjuntos de dados
* Encontrar tendências
* Refinar resultados

**Padrões comuns:**

* Múltiplos filtros
* Consultas amplas refinadas passo a passo
* Consultas exploratórias temporárias

```sql
SELECT  *
FROM sales
WHERE region = 'EU'
AND sale_date >= '2025-01-01';
```

## Exercícios práticos

**Exercício 1 – Leia a Consulta**

Explique o que esta consulta faz em português claro:

```sql
SELECT  email
FROM users
WHERE active = true;
```

**Exercício 2 – Escreva uma consulta filtrada**

Escreva uma consulta para:
* Selecionar name e price
* Da tabela products
* Onde o preço seja menor que 50

**Exercício 3 – Combine condições**

Escreva uma consulta que:
* Selecione todas as colunas
* Da tabela employees
* Onde o departamento seja Engineering
* E a data de contratação seja após 2024-01-01

Prática bônus
Experimente com:
* `>` versus `>=`
* Combinar AND e OR
* Filtrar texto vs valores numéricos

## Conclusão

As cláusulas `SELECT` e `WHERE` formam a **base das consultas SQL**.

Se você consegue:
* Selecionar colunas específicas
* Filtrar linhas com precisão
* Combinar condições logicamente

Você já possui as habilidades necessárias para consultar bancos de dados do mundo real.

No próximo artigo (**SQL 04**), exploraremos a **ordenação de resultados**, **limitação de linhas** e **agregação de dados**, que é onde o SQL começa a responder a perguntas de nível de negócio.

Boa consulta! 🚀

## Soluções dos exercícios do artigo - SQL 03

**Exercício 1 – Leia a consulta (resposta)**

```sql
SELECT  email
FROM users
WHERE active = true;
```

**Explicação em português claro**

* Procure na tabela users
* Mantenha apenas os usuários cujo status active seja true
* Retorne apenas a coluna email

Esta consulta retorna os endereços de e-mail de todos os usuários ativos.

**Exercício 2 – Escreva uma consulta filtrada (resposta)**

```sql
SELECT  name, price
FROM products
WHERE price < 50;
```

**O que esta consulta faz:**

* Recupera nomes e preços de produtos
* Exclui produtos com preço igual ou superior a 50 

**Exercício 3 – Combine condições (resposta)**

```sql
SELECT  *
FROM employees
WHERE department = 'Engineering'
AND hire_date > '2024-01-01';
```

**Explicação em português claro**

* Procure na tabela employees
* Mantenha apenas funcionários no departamento de Engenharia
* Inclua apenas aqueles contratados após 1º de janeiro de 2024

**Prática Bônus – Exemplos de exploração**

Abaixo estão alguns exemplos de consultas que você pode testar enquanto experimenta.

**Usando `Maior Que` vs `Maior ou Igual A`**

```sql
SELECT  *
FROM products
WHERE price >= 100;
```
Retorna produtos com preço 100 ou mais, incluindo exatamente 100.

**Combinando `AND` e `OR`**

```sql
SELECT  *
FROM employees
WHERE department = 'HR'
OR department = 'Finance'
AND active = true;
```

> ⚠️ Importante: O `AND` é avaliado antes do `OR`.

Para tornar a lógica explícita:

```sql
SELECT  *
FROM employees
WHERE (department = 'HR' OR department = 'Finance')
AND active = true;
```

**Filtrando texto vs valores numéricos**
```sql
-- Comparação de texto
SELECT *
FROM customers
WHERE country = 'UK';
```

```sql
-- Comparação numérica
SELECT *
FROM orders
WHERE total_amount > 500;
```

Valores de texto usam aspas, valores numéricos não.

## Principais aprendizados

* SELECT escolhe as colunas
* FROM escolhe a tabela
* WHERE filtra as linhas
* Operadores lógicos e de comparação permitem refinar os resultados com precisão

Se você consegue ler e escrever essas consultas com confiança, você está oficialmente fazendo consultas como um usuário de SQL — e não apenas memorizando a sintaxe.

Próximo passo: **SQL 04 – ORDER BY, LIMIT e Agregações** 🚀
