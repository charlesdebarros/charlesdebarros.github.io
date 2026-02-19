---
title: "De Volta ao Básico - SQL 02 – Entendendo Como os Dados São Estruturados"
date: 2026-02-24 10:00
author: "Charles De Barros"
header:
  background-color: "#003f72"
  caption: "Structured Query Language é a base dos dados relacionais"
  caption_url: https://unsplash.com/
category: ["Back to Basics", "SQL"]
tags:
  - sql
  - sql basics
  - database tables
  - data types
  - relational databases
series: "SQL do Zero ao Pro"
series_part: 2
image: https://res.cloudinary.com/charlesdebarros/image/upload/v1753179253/22112368_6537887_uaprve.svg
description: "Aprenda como bancos de dados relacionais armazenam dados usando tabelas, linhas, colunas e tipos de dados. Fundamentos de SQL explicados de forma visual e prática."
---

# Tabelas, Linhas, Colunas e Tipos de Dados

Antes de escrever consultas SQL poderosas, você precisa entender **como os dados realmente são armazenados**.

Este artigo explica:
- O que realmente são tabelas, linhas e colunas  
- Por que esquemas e tipos de dados são importantes  
- Como desenvolvedores e analistas pensam de forma diferente sobre a estrutura dos dados  

Esta é a **Parte 02 da série SQL do Zero ao Pro**.

---

## Índice

- [O que é uma Tabela de Banco de Dados?](#o-que-é-uma-tabela-de-banco-de-dados)
- [Linhas: Registros em uma Tabela](#linhas-registros-em-uma-tabela)
- [Colunas: Atributos e Campos](#colunas-atributos-e-campos)
- [Esquemas e Estrutura de Tabelas](#esquemas-e-estrutura-de-tabelas)
- [Tipos de Dados SQL Comuns](#tipos-de-dados-sql-comuns)
- [Por que os Tipos de Dados Importam](#por-que-os-tipos-de-dados-importam)
- [SQL para Desenvolvedores vs Analistas](#sql-para-desenvolvedores-vs-analistas)
- [Exercícios Práticos](#exercícios-práticos)
- [Conclusão](#conclusão)
- [Soluções dos exercícios do artigo](#soluções-dos-exercícios-do-artigo)

---

## O que é uma Tabela de Banco de Dados?

Uma **tabela** é onde os bancos de dados relacionais armazenam dados.

Pense em uma tabela como uma **planilha**:
- As colunas definem **que tipo de dado** é armazenado
- As linhas armazenam **registros individuais**

### Exemplo: Tabela `customers`

| id | name | email | country |
|---|----|------|--------|
| 1 | Alice | alice@email.com | UK |
| 2 | Bob | bob@email.com | PT |

Cada tabela geralmente representa **um conceito do mundo real**, como:
- customers
- orders
- products
- employees

---

## Linhas: Registros em uma Tabela

Uma **linha** representa um **registro único**.

Na tabela `customers`:
- Uma linha = um cliente
- Cada linha contém valores para cada coluna

```text
(1, Alice, alice@email.com, UK)
(2, Bob, bob@email.com, PT)
```

---

## Chaves Primárias

A maioria das tabelas possui uma __chave primária__:

* Identifica de forma única cada linha
* Geralmente é uma coluna id

```sql
id INT PRIMARY KEY
```

🧠 Nenhuma duas linhas podem compartilhar o mesmo valor de chave primária.

---

## Colunas: Atributos e Campos

Uma coluna define um único atributo dos dados.

Exemplos:

* name
* email
* price
* created_at

Cada coluna possui:

* Um nome
* Um tipo de dado
* Restrições opcionais

```sql
name VARCHAR(100)
```

__Regras das Colunas__

* Todo valor em uma coluna deve seguir o mesmo tipo de dado
* As colunas descrevem que tipo de dado é permitido

---

## Esquemas e Estrutura de Tabelas

Um __esquema__ é um contêiner lógico para tabelas.

Pense nele como:

* Uma pasta dentro de um banco de dados
* Uma forma de organizar tabelas

```text
database
 └── public
     ├── users
     ├── orders
     └── products
```

__Por que Esquemas Importam__

Os esquemas ajudam com:

* Organização
* Permissões
* Evitar conflitos de nomes

---

## Tipos de Dados SQL Comuns

Os tipos de dados definem que tipo de valor uma coluna pode armazenar.

| __Tipos Numéricos__ | |
| === | === |
| Tipo | Exemplo |
| INT | 42 |
| DECIMAL | 99.99 |
| FLOAT | 3.14 |


| __Tipos de Texto__ | |
| === | === |
| Tipo | Exemplo |
| VARCHAR | 'Alice' |
| TEXT | Descrições longas |


| __Tipos de Data & Hora__ | |
| === | === |
| Tipo | Exemplo |
| DATE | 2025-07-21 |
| TIMESTAMP | 2025-07-21 10:00 |


| __Tipo Booleano__ | |
| === | === |
| Tipo | Exemplo |
| BOOLEAN | true / false |

--- 

## Por que os Tipos de Dados Importam

Escolher o tipo de dado correto afeta:

* Tamanho de armazenamento
* Performance
* Precisão dos dados

__Exemplo__
```sql
price VARCHAR(10)   ❌
price DECIMAL(10,2) ✅
```

__Benefícios dos Tipos de Dados Corretos__

* Previnem dados inválidos
* Aceleram consultas
* Permitem indexação
* Reduzem bugs

---

## SQL para Desenvolvedores vs Analistas
**SQL para Desenvolvedores**

__Desenvolvedores se preocupam com:__

* Integridade dos dados
* Restrições
* Performance

__Áreas de foco comuns:__

* Chaves primárias e estrangeiras
* Restrições NOT NULL e UNIQUE
* Tipos de dados amigáveis para índices
* Migrações de esquema

---

**SQL para Analistas de Dados**

__Analistas se preocupam com:__

* Consultas e agregações
* Legibilidade
* Significado de negócio

__Áreas de foco comuns:__

* Clareza na nomenclatura das colunas
* Consistência de data/hora
* Precisão numérica
* Tratamento de NULL

---

## Exercícios Práticos

**Exercício 1 – Identifique a Estrutura**

Dada a definição da tabela, identifique:

* Nome da tabela
* Colunas
* Tipos de dados

```sql
CREATE TABLE products (
  id INT PRIMARY KEY,
  name VARCHAR(100),
  price DECIMAL(10,2),
  in_stock BOOLEAN
);
```
---

**Exercício 2 – Projete uma Tabela**

Projete uma tabela chamada employees com:

* id
* first name
* last name
* email
* hire date

Escreva a instrução `CREATE TABLE`.

---

**Exercício 3 – Pense Como um Banco de Dados**

Por que `DATE` é uma escolha melhor do que `VARCHAR` para uma data de nascimento?

Escreva sua resposta em inglês simples.

**Prática Extra**

Crie uma tabela localmente usando SQLite ou um editor SQL online e tente:

* Adicionar colunas
* Inserir linhas
* Selecionar colunas específicas

---

## Conclusão

Tabelas, linhas, colunas e tipos de dados formam a __base de todo banco de dados relacional__.

Se você entende:

* Como as tabelas são estruturadas
* Por que os tipos de dados existem
* Então escrever consultas SQL se torna __dramaticamente mais fácil__.

No próximo artigo (__SQL 03__), vamos mergulhar em __consultas SELECT e filtragem de dados__, onde o SQL realmente começa a mostrar seu poder.

Boas consultas 🚀


## Soluções dos exercícios do artigo

**Exercício 1 – Identifique a Estrutura (Resposta)**

Dada a definição da tabela:

```sql
CREATE TABLE products (
  id INT PRIMARY KEY,
  name VARCHAR(100),
  price DECIMAL(10,2),
  in_stock BOOLEAN
);
```

__Nome da Tabela__

* products

__Colunas e Tipos de Dados__

| Nome da Coluna | Tipo de Dado | Descrição |
| === | === | === |
| id | INT | Identificador único de cada produto |
| name | VARCHAR(100) | Nome do produto |
| price | DECIMAL(10,2) | Preço do produto com duas casas decimais |
| in_stock | BOOLEAN | Indica se o produto está disponível |

__Chave Primária__

* `id` é a __chave primária__
* Ela identifica de forma única cada linha da tabela

---

**Exercício 2 – Projete uma Tabela (Resposta)**
__Recapitulação dos Requisitos__

Crie uma tabela chamada employees com:

* id
* first name
* last name
* email
* hire date

__Uma Possível Solução__

```sql
CREATE TABLE employees (
  id INT PRIMARY KEY,
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  email VARCHAR(255),
  hire_date DATE
);
```

__Por que Essas Escolhas?__

* `INT` para `id`: eficiente e comumente indexado
* `VARCHAR` para nomes e email: comprimento flexível
* `DATE` para data de contratação: permite consultas e ordenações baseadas em data

---

**Exercício 3 – Pense Como um Banco de Dados (Resposta)**
__Pergunta__

Por que `DATE` é uma escolha melhor do que `VARCHAR` para uma data de nascimento?

__Resposta (Em Linguagem Simples)__

Usar o tipo de dado `DATE` garante que:

* Apenas datas válidas possam ser armazenadas
* As datas possam ser ordenadas corretamente
* Cálculos com datas (idade, duração) sejam possíveis
* Indexação e filtragem sejam mais rápidas

Se as datas forem armazenadas como `VARCHAR`, o banco de dados:

* Não consegue compará-las ou ordená-las de forma confiável
* Não consegue realizar cálculos de data
* Não consegue garantir a validade das datas

---

A seguir: **SQL 03 – Consultas SELECT e Filtragem de Dados** 🚀
