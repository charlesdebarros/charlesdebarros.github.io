---
title: "Back to Basics - SQL 01 – Um Guia Prático Para Inciantes"
date: 2026-02-17 09:00
author: "Charles De Barros"
header:
  background-color: "#003f72"
  caption: "A Linguagem de Consulta Estruturada (SQL) é a base dos dados relacionais"
  caption_url: https://unsplash.com/
category: ["Back to Basics", "SQL"]
tags:
  - sql
  - sql basics
  - relational databases
  - data analysis
  - backend development
series: "SQL from Zero to Pro"
series_part: 1
image: https://res.cloudinary.com/charlesdebarros/image/upload/v1753179253/22112368_6537887_uaprve.svg
description: "Aprenda o que é SQL, como funciona e como desenvolvedores e analistas o utilizam na prática. Parte 1 de uma série completa para iniciantes em SQL."
---

# Introdução ao SQL: O que é SQL e como ele funciona

> SQL (Structured Query Language - Linguagem de Consulta Estruturada) é a linguagem padrão usada para interagir com bancos de dados relacionais.

Se você trabalha com **dados, aplicativos, análise ou sistemas de backend**, o SQL é uma habilidade fundamental.

Este artigo é a **Parte 01 de uma série de 10 partes sobre SQL**, projetada para:
- **Desenvolvedores** construindo aplicações
- **Analistas** consultando e interpretando dados
- **Iniciantes** que desejam clareza sem jargões técnicos excessivos

---

## Índice

- [O que é SQL?](#o-que-é-sql)
- [Como o SQL funciona](#como-o-sql-funciona)
- [Bancos de Dados Relacionais vs. Não-Relacionais](#bancos-de-dados-relacionais-vs-não-relacionais)
- [SQL vs. RDBMS](#sql-vs-rdbms)
- [O SQL diferencia maiúsculas de minúsculas?](#o-sql-diferencia-maiúsculas-de-minúsculas)
- [Exemplos de Sintaxe Básica de SQL](#exemplos-de-sintaxe-básica-de-sql)
- [SQL para Desenvolvedores vs. Analistas](#sql-for-developers-vs-analysts)
- [Exercícios Práticos](#exercícios-práticos)
- [Conclusão](#conclusão)
- [Soluções dos exercícios do artigo](#soluções-dos-exercícios-do-artigo)

---

## O que é SQL?

**SQL (Structured Query Language)** é uma linguagem de programação declarativa usada para **criar, ler, atualizar e excluir dados** armazenados em bancos de dados relacionais.

> 💡 **Definição de uma frase:** > SQL é uma linguagem que permite consultar e manipular dados estruturados armazenados em tabelas de bancos de dados relacionais.

### Modelo Mental: Como visualizar o SQL

- Um **banco de dados** → uma pasta  
- Uma **tabela** → uma planilha  
- Uma **linha** → um registro único  
- Uma **coluna** → um atributo/característica  
- **SQL** → a linguagem que você usa para fazer perguntas  

### Exemplo de consulta SQL

```sql
SELECT name
FROM customers
WHERE country = 'UK';
```

---

## SQL 01: Os Fundamentos

**O que isso significa em português simples:**
1. Procure na tabela customers (clientes)
2. Encontre as linhas onde o country (país) é 'UK'
3. Retorne apenas a coluna name (nome)

---

**Como o SQL funciona: O ciclo de vida da consulta**  
O SQL segue um processo passo a passo específico para entregar seus dados:

1. Você escreve uma consulta SQL.
2. O banco de dados a analisa e valida (verificando erros de sintaxe).
3. O planejador de consulta decide como executá-la (encontrando o caminho mais rápido).
4. Tabelas e índices são percorridos.
5. Um conjunto de resultados é retornado.

---

## SQL é declarativo

O SQL é uma linguagem **declarativa**, o que significa que você descreve **o que** você quer, não **como** obter.

```sql
SELECT * FROM products WHERE price > 100;
```

**O banco de dados decide:**
*Qual índice usar
*Como percorrer as linhas
*Como otimizar a performance

---

## Sublinguagens do SQL (Referência Rápida)

| Categoria | Propósito | Comandos |
|---|---|---|
| DQL | Consultar dados | SELECT |
| DDL | Definir estrutura| CREATE, ALTER, DROP |
| DML | Modificar dados | INSERT, UPDATE, DELETE |
| DCL | Controlar acesso | GRANT, REVOKE|

---

## Relacional (SQL) vs. Não-Relacional (NoSQL)

**Bancos de dados Relacionais (SQL)**
* Esquema fixo
* Tabelas com linhas e colunas
* Consistência forte (ACID)Excelente para dados estruturados
* Exemplos: MySQL, PostgreSQL, Oracle, SQL Server

**Bancos de dados Não-Relacionais (NoSQL)**
* Esquema flexível
* Dados em JSON, chave-valor ou grafos
* Escalável horizontalmente
* Projetado para alto volume ou dados não estruturados
* Exemplos: MongoDB, Redis, Cassandra, Neo4j

**Principais diferenças**

| Característica | SQL | (Relacional) NoSQL |
| --- | --- | --- |
| Esquema | Fixo | Flexível |
| Linguagem de Consulta | SQL | Específica do banco |
| Transações | Fortes | Frequentemente eventuais |
| Caso de Uso | Dados estruturado | Dados massivos ou não estruturados |

---

## SQL vs. RDBMS
* **SQL** = A Linguagem: Define a sintaxe e as regras para interagir com os dados.
* **RDBMS** = O Software: Sistemas de Gerenciamento de Banco de Dados Relacionais que executam o SQL e armazenam os dados (ex: MySQL, PostgreSQL, SQLite).

🧠 **Analogia**: SQL é como o idioma Inglês; MySQL ou PostgreSQL são como telefones que permitem que você o fale.

---

## O SQL diferencia maiúsculas de minúsculas?

| Item | Diferencia (Case-sensitive)?|
| === | === | === |
| Palavras-chave SQL | ❌ Não (_SELECT_ é o mesmo que _select_ )|
| Nomes de tabelas e colunas |⚠️ Depende do SO/Banco de Dados|
| Valores de texto (Strings) |⚠️ Depende das configurações de collation|

---

## Exemplos de sintaxe básica de SQL

**SELECT – Consultar dados**
```sql
SELECT * FROM employees;
SELECT first_name, last_name FROM employees;
SELECT * FROM employees WHERE department = 'HR';
```

**INSERT - Adicionar dados**
```sql
INSERT INTO employees (first_name, last_name)
VALUES ('Jane', 'Doe');
```

**UPDATE - Modificar dados**
UPDATE – Modificar dados
```sql
UPDATE employees
SET department = 'Marketing'
WHERE id = 101;
```

**DELETE – Remover dados**
```sql
DELETE FROM employees WHERE id = 101;
```

--- 

## SQL para Desenvolvedores vs. Analistas
**SQL para Desenvolvedores**

* Alimentar APIs e serviços de backend
* Garantir a integridade dos dados
* Otimizar performance e ajuste de índices
* Trabalhar com migrações e transações

**SQL para Analistas de Dados**

* Explorar conjuntos de dados
* Criar relatórios e dashboards
* Usar GROUP BY e Agregações
* Funções de janela (Window functions) para insights profundos

---

## Exercícios Práticos
**Exercício 1 – Identifique as partes**
Identifique o nome da tabela, as colunas selecionadas e a condição de filtro:

```sql
SELECT email FROM users WHERE active = true;
```

**Exercício 2 – Escreva sua primeira consulta**  
Escreva uma consulta para selecionar todas as colunas de uma tabela chamada products onde o preço (price) seja maior que 50.

**Exercício 3 – Pense como o SQL**
Explique em português simples o que esta consulta faz:

```sql
SELECT name FROM customers ORDER BY created_at DESC;
```

---

## Conclusão
O SQL está na intersecção do desenvolvimento de software, análise de dados e business intelligence. No próximo artigo (SQL 02), vamos detalhar tabelas, linhas, colunas e tipos de dados.

Bons estudos e ótimas consultas! 🚀

---

## Soluções dos exercícios do artigo
**Exercício 1 – Identifique as Partes**

Consulta:

```sql
SELECT email FROM users WHERE active = true;
```
* Nome da tabela: users
* Colunas selecionadas: email
* Condição de filtro: active = true (Isso garante que você obtenha apenas registros de usuários que estão marcados como ativos no momento).

---

**Exercício 2 – Escreva Sua Primeira Consulta**

Tarefa:

```text
Selecione todas as colunas de uma tabela chamada products onde o preço é maior que 50.
```
Solução:

```sql
SELECT * FROM products 
WHERE price > 50;
```

**Exercício 3 – Pense Como o SQL**

Consulta:

```sql
SELECT name FROM customers ORDER BY created_at DESC;
```

Explicação em Português Simples:

"Vá até a tabela de clientes (customers), pegue o nome (name) de cada cliente e liste-os começando pelo criado mais recentemente (mais novo) até o mais antigo."

---

### Bônus: Como o banco de dados "pensa" (A ordem de execução)
Embora escrevamos o SQL na ordem SELECT -> FROM -> WHERE, o banco de dados o executa em uma ordem diferente para ser eficiente:

* **FROM**: Onde estão os dados? (Encontra a tabela)
* **WHERE**: De quais linhas eu preciso? (Filtra os dados)
* **SELECT**: Quais colunas devo mostrar? (Escolhe os campos)
* **ORDER BY**: Como devo apresentá-los? (Ordena os resultados)