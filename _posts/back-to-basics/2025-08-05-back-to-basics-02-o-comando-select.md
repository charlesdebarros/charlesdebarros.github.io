---
title: "Back to Basics - SQL 02"
subheadline: "O Comando SELECT"
date: 2025-08-05 09:00
author: "Charles De Barros"
header: 
    background-color: "#003f72"
    caption: This is a caption for the header image with link
    caption_url: https://unsplash.com/
category: ['Back to Basics', 'SQL', 'Portuguese']
tags: ["Back to Basics", "SQL", "portuguese"]
image: #
---

![Selecting a Vinyl](https://res.cloudinary.com/charlesdebarros/image/upload/v1754387663/mitchel-lensink-KmGMMxVv0_Q-unsplash_nufyrb.jpg)
<em>Foto cortesia de <a href="https://unsplash.com/@lensinkmitchel?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Mitchel Lensink</a> on <a href="https://unsplash.com/photos/person-holding-roo-panes-painting-KmGMMxVv0_Q?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a></em>

# Entendendo o comando <span class="sql-statement-headline">SELECT</span> do SQL: Um Guia Abrangente

SQL (Structured Query Language) é a base para gerenciar e consultar dados em bancos de dados relacionais. Entre seus muitos comandos, a comando `SELECT` é a mais essencial e frequentemente utilizada. Seja você um analista de dados, desenvolvedor, administrador de banco de dados ou alguém que está começando sua jornada com bancos de dados, dominar o `SELECT` é fundamental para trabalhar eficazmente com dados.

Neste artigo, vamos explorar tudo o que você precisa saber sobre a comando `SELECT` — desde sua sintaxe e usos principais até exemplos práticos que você pode aplicar em cenários do mundo real.

## O que é a comando <span class="sql-statement">SELECT</span> no SQL?

A comando `SELECT` é usada no SQL para **recuperar dados de uma tabela do banco de dados**. Ela permite consultar uma ou mais tabelas e extrair dados específicos conforme suas necessidades.

Seja para buscar tabelas inteiras ou apenas certas colunas, filtrar dados com condições ou agrupar e ordenar resultados, a comando `SELECT` é sua porta de entrada para trabalhar com dados armazenados em bancos de dados relacionais.

### Por que o <span class="sql-statement">SELECT</span> é importante?

- Permite a **recuperação de dados**.
- Permite extrair apenas as **informações relevantes**.
- É a base para construir **consultas mais complexas**, como aquelas que usam `JOIN`, `GROUP BY` ou `WHERE`.
- Dá suporte à **agregação de dados**, análises e relatórios.

## Sintaxe Básica do <span class="sql-statement">SELECT</span>

A sintaxe básica de uma comando `SELECT` é:

```sql
SELECT column1, column2, ...
FROM table_name;
````

Vamos analisar isso:

* `SELECT` informa ao SQL quais dados você deseja recuperar.
* `column1, column2, ...` são os nomes das colunas que você deseja retornar.
* `FROM table_name` especifica a tabela onde estão os dados.

### Exemplo:

```sql
SELECT first_name, last_name
FROM employees;
```

Isso recupera as colunas `first_name` e `last_name` da tabela `employees`.

## Exemplo 1: <span class="sql-statement sql-statement-border">SELECT *</span> – Selecionando Todas as Colunas

O asterisco `*` é um caractere curinga no SQL. Quando usado com `SELECT`, ele recupera **todas as colunas** da tabela especificada.

### Sintaxe:

```sql
SELECT * FROM table_name;
```

### Exemplo:

```sql
SELECT * FROM customers;
```

Esta comando retorna **todas as colunas** de **todas as linhas** na tabela `customers`.

> **Nota de Boa Prática:** Embora `SELECT *` seja conveniente para consultas rápidas ou exploração de dados, não é recomendado para consultas em produção. Selecionar todas as colunas pode causar problemas de desempenho e retornar dados desnecessários. É melhor especificar apenas as colunas necessárias.

## Exemplo 2: <span class="sql-statement sql-statement-border">SELECT</span> Colunas Específicas

Em vez de usar `*`, você pode (e deve) especificar as colunas exatas que deseja recuperar.

### Sintaxe:

```sql
SELECT column1, column2
FROM table_name;
```

### Exemplo:

```sql
SELECT customer_id, customer_name
FROM customers;
```

Isso retorna apenas as colunas `customer_id` e `customer_name` da tabela `customers`.

> Isso melhora o desempenho e torna suas consultas mais claras e fáceis de manter.

## Exemplo 3: Usando Apelidos (Aliases) para Colunas no <span class="sql-statement sql-statement-border">SELECT</span>

Às vezes, os nomes das colunas são longos, pouco claros ou precisam ser mais amigáveis no resultado da consulta. É aí que entram os **apelidos**. Você pode renomear uma coluna na saída usando a palavra-chave `AS`.

### Sintaxe:

```sql
SELECT column_name AS alias_name
FROM table_name;
```

### Exemplo:

```sql
SELECT first_name AS "First Name", last_name AS "Last Name"
FROM employees;
```

Isso retornará as colunas com os cabeçalhos `First Name` e `Last Name` em vez de `first_name` e `last_name`.

Você também pode usar apelidos sem o `AS`:

```sql
SELECT first_name "First Name", last_name "Last Name"
FROM employees;
```

> Apelidos são úteis para melhorar a legibilidade, especialmente ao exibir resultados de consultas em relatórios ou visualizações.

## Exemplo 4: <span class="sql-statement sql-statement-border">SELECT COUNT(*)</span> – Contando Linhas

A função `COUNT(*)` é uma função agregada que retorna o **número de linhas** em uma tabela, incluindo aquelas com valores `NULL`.

### Sintaxe:

```sql
SELECT COUNT(*) FROM table_name;
```

### Exemplo:

```sql
SELECT COUNT(*) FROM orders;
```

Isso retorna o número total de registros na tabela `orders`.

Você também pode contar linhas com condições específicas usando `WHERE`:

```sql
SELECT COUNT(*) FROM orders
WHERE order_status = 'Shipped';
```

> `COUNT(*)` é amplamente usado em painéis, resumos e métricas de desempenho.

## Exemplo 5: <span class="sql-statement sql-statement-border">SELECT DISTINCT</span> – Removendo Duplicatas

No SQL, a palavra-chave `DISTINCT` garante que os resultados retornados contenham **apenas valores únicos**, removendo quaisquer duplicatas.

### Sintaxe:

```sql
SELECT DISTINCT column1
FROM table_name;
```

### Exemplo:

```sql
SELECT DISTINCT country
FROM customers;
```

Isso retornará uma lista de **países únicos** da tabela `customers`, com cada país aparecendo apenas uma vez.

Você também pode usar `DISTINCT` com múltiplas colunas:

```sql
SELECT DISTINCT city, state
FROM customers;
```

Neste caso, o SQL considera cada combinação única de `city` e `state`.

> Use `DISTINCT` com cautela em conjuntos de dados grandes, pois pode impactar o desempenho.

## Dicas Adicionais para Usar o <span class="sql-statement">SELECT</span>

### 1. **Filtrando Resultados com <span class="sql-statement">WHERE</span>**

```sql
SELECT first_name, department
FROM employees
WHERE department = 'Sales';
```

### 2. **Ordenando Resultados**

```sql
SELECT customer_name, country
FROM customers
ORDER BY country ASC;
```

### 3. **Limitando o Número de Linhas**

No MySQL e PostgreSQL:

```sql
SELECT * FROM products
LIMIT 10;
```

No SQL Server:

```sql
SELECT TOP 10 * FROM products;
```

## Erros Comuns a Evitar

| Erro            | Por que é um problema?           | Melhor abordagem              |
| --------------- | -------------------------------- | ----------------------------- |
| Usar `SELECT *` | Retorna dados desnecessários     | Selecione colunas específicas |
| Sem `WHERE`     | Pode sobrecarregar os resultados | Filtre os dados relevantes    |
| Sem aliases     | Reduz a legibilidade             | Use `AS` para nomear colunas  |


### Tabela resumo de exemplos do SELECT

| Uso                    | Exemplo em SQL                           |
| ------------------------------ | ---------------------------------------- |
| Selecionar todas as colunas    | `SELECT * FROM users;`                   |
| Selecionar colunas específicas | `SELECT name, email FROM users;`         |
| Usar aliases                   | `SELECT name AS "Full Name" FROM users;` |
| Contar total de linhas         | `SELECT COUNT(*) FROM orders;`           |
| Selecionar valores únicos      | `SELECT DISTINCT city FROM customers;`   |




### Cenário do Mundo Real

Vamos supor que você trabalha em uma empresa de e-commerce. Você quer preparar um relatório rápido que mostre:

* Quantos pedidos foram realizados
* A lista única de países de onde vêm os clientes
* Os nomes e e-mails dos clientes formatados de forma clara

**Consultas:**

```sql
-- Total number of orders
SELECT COUNT(*) AS total_orders
FROM orders;

-- Unique list of customer countries
SELECT DISTINCT country
FROM customers;

-- Customer names with formatted output
SELECT first_name AS "First Name", last_name AS "Last Name", email AS "Email Address"
FROM customers;
```

---

### Conclusão

A comando `SELECT` é o comando SQL mais vital e amplamente utilizado por um motivo — ela capacita os usuários a extrair e manipular dados de maneiras infinitas. Seja para puxar tabelas completas com `SELECT *`, isolar dados específicos ou tornar os resultados mais legíveis com aliases, entender como usar o `SELECT` de forma eficaz é o primeiro passo para se tornar proficiente em SQL.

À medida que você constrói consultas mais complexas, lembre-se de:

* Começar de forma simples
* Selecionar apenas os dados necessários
* Usar funções como `COUNT()` e `DISTINCT` para resumir e esclarecer
* Testar e otimizar suas consultas para melhor desempenho

Ao dominar a comando `SELECT`, você desbloqueia a capacidade de consultar e transformar dados de qualquer banco de dados relacional — fazendo seus dados trabalharem com mais inteligência, não com mais esforço.
