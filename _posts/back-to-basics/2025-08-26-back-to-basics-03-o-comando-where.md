---
title: "Back to Basics - SQL 03"
subheadline: "O commando de restrição WHERE"
date: 2025-08-26 09:00
author: "Charles De Barros"
header: 
    background-color: "#003f72"
    caption: This is a caption for the header image with link
    caption_url: https://unsplash.com/
category: ['Back to Basics', 'SQL']
tags: ["Back to Basics", "SQL"]
image: #
---

![Selecting a Vinyl](https://res.cloudinary.com/charlesdebarros/image/upload/v1756452631/Where_bruno-wolff-l5-za_iUUdA-unsplash_jbanly.jpg)
<em>Foto cortesia de <a href="https://unsplash.com/@mrbrunowolff?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Bruno Wolff</a> no <a href="https://unsplash.com/photos/brown-and-gray-road-street-signs-at-daytime-l5-za_iUUdA?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a></em>
      
# Dominando o comando de restrição <span class="sql-statement-headline">WHERE</span>: Do Básico ao Avançado

A Linguagem de Consulta Estruturada (SQL) é a base do trabalho com bancos de dados relacionais. Entre suas muitas instruções, uma se destaca como essencial para filtragem e precisão de dados: o comando de restrição **`WHERE`**. Seja você um iniciante escrevendo sua primeira consulta ou um analista de dados avançado otimizando queries para performance, dominar o comando de restrição `WHERE` é fundamental.

Este artigo irá guiá-lo através de:

- O que é o comando de restrição `WHERE`  
- Como ele funciona com exemplos do básico ao avançado  
- Dicas de como usá-lo de forma eficaz  
- Erros comuns a evitar  
- Conjuntos de dados de exemplo para praticar  

Ao final, você será capaz de filtrar, manipular e analisar dados com confiança usando `WHERE`.

---

## 1. O que é o comando de restrição SQL <span class="sql-statement-headline">WHERE</span>?

O comando de restrição `WHERE` no SQL é usado para filtrar registros em uma consulta. Em vez de recuperar todas as linhas de uma tabela, o `WHERE` ajuda a selecionar apenas aquelas que atendem a determinadas condições.  

Por exemplo:

```sql
SELECT * 
FROM employees 
WHERE department = 'Sales';
```

Essa consulta retorna apenas os funcionários que trabalham no departamento de Vendas.

Pense no `WHERE` como o **porteiro do filtro** — ele determina quais linhas passam para o resultado.

---

## 2. A Sintaxe Básica do <span class="sql-statement-headline">WHERE</span>

A sintaxe geral é:

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

- **`table_name`**: Nome da tabela a ser consultada.  
- **`condition`**: Uma expressão lógica que retorna verdadeiro ou falso.  

Se a condição for **verdadeira**, a linha é incluída. Se for **falsa**, é excluída.

---

## 3. Exemplos para Iniciantes

### Exemplo 1: Filtrando por uma condição simples
Suponha que você tenha a tabela `students`:

| student_id | name     | age | grade |
|------------|----------|-----|-------|
| 1          | Alice    | 20  | A     |
| 2          | Bob      | 19  | B     |
| 3          | Charlie  | 21  | C     |

Consulta:

```sql
SELECT * 
FROM students
WHERE grade = 'A';
```

Resultado:

| student_id | name  | age | grade |
|------------|-------|-----|-------|
| 1          | Alice | 20  | A     |

---

### Exemplo 2: Usando condições numéricas
```sql
SELECT * 
FROM students
WHERE age > 19;
```

Resultado:

| student_id | name     | age | grade |
|------------|----------|-----|-------|
| 1          | Alice    | 20  | A     |
| 3          | Charlie  | 21  | C     |

---

### Exemplo 3: Combinando condições com <span class="sql-statement-headline">AND/OR</span>
```sql
SELECT * 
FROM students
WHERE grade = 'A' OR age < 20;
```

Resultado:

| student_id | name | age | grade |
|------------|------|-----|-------|
| 1          | Alice | 20  | A     |
| 2          | Bob   | 19  | B     |

---

## 4. Exemplos Intermediários

### Exemplo 4: Usando <span class="sql-statement-headline">IN</span>
O operador `IN` permite verificar vários valores possíveis sem escrever múltiplos `OR`s.

```sql
SELECT *
FROM students
WHERE grade IN ('A', 'B');
```

---

### Exemplo 5: Usando <span class="sql-statement-headline">BETWEEN</span>
```sql
SELECT *
FROM students
WHERE age BETWEEN 19 AND 21;
```

---

### Exemplo 6: Correspondência de padrões com <span class="sql-statement-headline">LIKE</span>
Suponha que temos:

| product_id | product_name   |
|------------|----------------|
| 1          | Apple iPhone   |
| 2          | Samsung Galaxy |
| 3          | Apple iPad     |

Consulta:

```sql
SELECT *
FROM products
WHERE product_name LIKE 'Apple%';
```

Resultado:

| product_id | product_name |
|------------|--------------|
| 1          | Apple iPhone |
| 3          | Apple iPad   |

---

### Exemplo 7: Verificando valores <span class="sql-statement-headline">NULL</span>
```sql
SELECT *
FROM employees
WHERE manager_id IS NULL;
```

Essa consulta retorna os funcionários sem gerentes.

---

## 5. Exemplos Avançados

### Exemplo 8: Subconsultas dentro do <span class="sql-statement-headline">WHERE</span>
Você pode usar outra consulta dentro do comando de restrição `WHERE`.

```sql
SELECT name
FROM employees
WHERE department_id IN (
    SELECT department_id 
    FROM departments 
    WHERE location = 'London'
);
```

---

### Exemplo 9: Usando <span class="sql-statement-headline">EXISTS</span>
```sql
SELECT name
FROM customers c
WHERE EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.customer_id = c.customer_id
);
```

Isso retorna clientes que realizaram pelo menos um pedido.

---

### Exemplo 10: Operadores condicionais com funções
```sql
SELECT *
FROM orders
WHERE YEAR(order_date) = 2024;
```

---

### Exemplo 11: Condições complexas com <span class="sql-statement-headline">AND/OR</span>
```sql
SELECT *
FROM employees
WHERE (department = 'Sales' AND salary > 50000)
   OR (department = 'IT' AND hire_date > '2022-01-01');
```

---

### Exemplo 12: Filtrando com Joins
```sql
SELECT e.name, d.department_name
FROM employees e
JOIN departments d 
  ON e.department_id = d.department_id
WHERE d.department_name = 'Finance';
```

---

## 6. Dicas para Trabalhar com <span class="sql-statement-headline">WHERE</span>

### Dica 1: Use Aliases
Aliases deixam suas consultas mais limpas:

```sql
SELECT e.name, e.salary
FROM employees e
WHERE e.salary > 60000;
```

---

### Dica 2: Atenção à Sensibilidade a Maiúsculas/Minúsculas
Na maioria dos bancos (como MySQL), `WHERE name = 'Alice'` não diferencia maiúsculas de minúsculas. Já em outros (como PostgreSQL), diferencia. Use `ILIKE` (Postgres) para correspondência sem diferenciação de maiúsculas.

---

### Dica 3: Use Índices
Filtrar grandes conjuntos de dados é mais rápido se a coluna usada no filtro estiver indexada.  
Exemplo:

```sql
CREATE INDEX idx_salary ON employees(salary);
```

---

### Dica 4: Evite <span class="sql-statement-headline">SELECT *</span>
Recupere apenas as colunas necessárias:

```sql
SELECT name, grade
FROM students
WHERE grade = 'A';
```

---

### Dica 5: Combine Condições com Cuidado
Em vez de escrever lógica confusa:

```sql
WHERE department = 'Sales' OR department = 'Marketing'
```

Use:

```sql
WHERE department IN ('Sales', 'Marketing');
```

---

## 7. Erros Comuns a Evitar

### Erro 1: Esquecer aspas em strings
```sql
-- ERRADO
WHERE name = Alice;

-- CORRETO
WHERE name = 'Alice';
```

---

### Erro 2: Confundir <span class="sql-statement-headline">NULL</span> com string vazia
```sql
-- ERRADO
WHERE manager_id = NULL;

-- CORRETO
WHERE manager_id IS NULL;
```

---

### Erro 3: Usar <span class="sql-statement-headline">AND/OR</span> sem parênteses
```sql
-- ERRADO
WHERE grade = 'A' OR grade = 'B' AND age > 20;

-- CORRETO
WHERE (grade = 'A' OR grade = 'B') AND age > 20;
```

---

### Erro 4: Uso excessivo de funções no <span class="sql-statement-headline">WHERE</span>
Isso pode impedir o uso de índices:

```sql
-- LENTO
WHERE YEAR(order_date) = 2024;

-- MELHOR
WHERE order_date >= '2024-01-01' AND order_date < '2025-01-01';
```

---

### Erro 5: Usar <span class="sql-statement-headline">SELECT *</span> em produção
Sempre especifique as colunas para evitar sobrecarga desnecessária.

---

## 8. Conjuntos de Dados para Praticar

### Dataset 1: Students

| student_id | name     | age | grade |
|------------|----------|-----|-------|
| 1          | Alice    | 20  | A     |
| 2          | Bob      | 19  | B     |
| 3          | Charlie  | 21  | C     |
| 4          | Diana    | 22  | B     |
| 5          | Ethan    | 20  | A     |

---

### Dataset 2: Employees

| employee_id | name     | department | salary | hire_date   | manager_id |
|-------------|----------|------------|--------|-------------|------------|
| 1           | Alice    | Sales      | 60000  | 2020-03-15  | NULL       |
| 2           | Bob      | IT         | 75000  | 2021-07-10  | 1          |
| 3           | Charlie  | HR         | 50000  | 2019-06-01  | 1          |
| 4           | Diana    | IT         | 80000  | 2022-01-20  | 2          |
| 5           | Ethan    | Sales      | 55000  | 2023-05-05  | 1          |

---

### Dataset 3: Products

| product_id | product_name   | price | category   |
|------------|----------------|-------|------------|
| 1          | Apple iPhone   | 999   | Electronics|
| 2          | Samsung Galaxy | 899   | Electronics|
| 3          | Dell Laptop    | 1200  | Computers  |
| 4          | Nike Shoes     | 150   | Apparel    |
| 5          | Levi’s Jeans   | 80    | Apparel    |

---

### Dataset 4: Orders

| order_id | customer_id | order_date | amount |
|----------|-------------|------------|--------|
| 1        | 101         | 2023-01-05 | 500    |
| 2        | 102         | 2023-02-12 | 150    |
| 3        | 103         | 2024-03-20 | 1200   |
| 4        | 101         | 2024-05-15 | 300    |
| 5        | 104         | 2024-07-25 | 750    |

---

## 9. Conclusão

O comando de restrição `WHERE` pode parecer simples, mas é uma das **ferramentas mais poderosas do SQL**. Ela permite filtrar linhas com base em condições que variam de comparações simples a subconsultas complexas.

- Iniciantes podem começar filtrando com operadores básicos (`=`, `<`, `>`).  
- Usuários intermediários podem explorar `IN`, `BETWEEN`, `LIKE` e `IS NULL`.  
- Usuários avançados podem combinar `WHERE` com joins, subconsultas e estratégias de indexação para eficiência.  

Praticando com os datasets de exemplo e mantendo em mente as dicas e erros comuns, você dominará a filtragem em SQL.

---

✅ **Próximo passo para você:**  
Escolha um dos datasets acima, carregue no seu banco favorito (MySQL, PostgreSQL ou SQLite) e escreva consultas usando o comando de restrição `WHERE`. Comece pequeno e aumente a complexidade aos poucos.  

---

