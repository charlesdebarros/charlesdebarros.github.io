---
title: "ORDER BY e GROUP BY"
subheadline: "Back to Basics - SQL 05"
date: 2025-09-02 09:00
author: "Charles De Barros"
header: 
    background-color: "#003f72"
    caption: This is a caption for the header image with link
    caption_url: https://unsplash.com/
category: ['Back to Basics', 'SQL']
tags: ["back to basics", "sql"]
image: #
---


![Ordering Chaos](https://res.cloudinary.com/charlesdebarros/image/upload/v1758016165/brett-jordan-M3cxjDNiLlQ-unsplash_misrtr.jpg)
<em>>Foto cortesia de  <a href="https://unsplash.com/@brett_jordan?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Brett Jordan</a> on <a href="https://unsplash.com/photos/brown-wooden-letter-blocks-on-white-surface-M3cxjDNiLlQ?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a></em>
      

# <span class="sql-statement-headline">ORDER BY</span> vs <span class="sql-statement-headline">GROUP BY</span> no SQL: Um Guia Completo com Exemplos

## Índice
1. [Introdução](#introdução)  
2. [O que é ORDER BY?](#o-que-é-order-by)  
   - [Sintaxe Básica](#sintaxe-básica-order-by)  
   - [Exemplo para Iniciantes](#exemplo-para-iniciantes-order-by)  
   - [Exemplo Intermediário](#exemplo-intermediário-order-by)  
   - [Exemplo Avançado](#exemplo-avançado-order-by)  
3. [O que é GROUP BY?](#o-que-é-group-by)  
   - [Sintaxe Básica](#sintaxe-básica-group-by)  
   - [Exemplo para Iniciantes](#exemplo-para-iniciantes-group-by)  
   - [Exemplo Intermediário](#exemplo-intermediário-group-by)  
   - [Exemplo Avançado](#exemplo-avançado-group-by)  
4. [ORDER BY vs GROUP BY: Diferenças Principais](#order-by-vs-group-by-diferenças-principais)  
5. [Erros Comuns e Como Evitá-los](#erros-comuns-e-como-evitá-los)  
6. [Dicas para Usar ORDER BY e GROUP BY com Eficiência](#dicas-para-usar-order-by-e-group-by-com-eficiência)  
7. [Tabela de Prática e Consultas](#tabela-de-prática-e-consultas)  
8. [Conclusão](#conclusão)  

---

## Introdução
Ao trabalhar com SQL, duas cláusulas frequentemente causam confusão para iniciantes e até mesmo usuários intermediários: **ORDER BY** e **GROUP BY**. À primeira vista, podem parecer semelhantes — ambas organizam resultados de consultas de alguma forma. No entanto, elas têm finalidades muito diferentes.  

Neste artigo, vamos explicar o que cada cláusula faz, apresentar exemplos do nível iniciante ao avançado, destacar erros comuns, compartilhar dicas práticas e fornecer uma tabela de prática para fortalecer suas habilidades em SQL.

---

## O que é ORDER BY?
A cláusula **ORDER BY** é usada para **ordenar** os resultados de uma consulta. Ela não altera os dados em si — apenas organiza as linhas em uma ordem especificada.

### Sintaxe Básica (ORDER BY)
```sql
SELECT coluna1, coluna2
FROM nome_tabela
ORDER BY coluna1 [ASC|DESC];
```

- `ASC` = Ordem ascendente (padrão).  
- `DESC` = Ordem descendente.  

---

### Exemplo para Iniciantes (ORDER BY)
```sql
SELECT nome, idade
FROM funcionarios
ORDER BY idade ASC;
```
**Explicação:** Recupera todos os nomes e idades dos funcionários, ordenados do mais jovem para o mais velho.

---

### Exemplo Intermediário (ORDER BY)
```sql
SELECT nome, departamento, salario
FROM funcionarios
ORDER BY departamento ASC, salario DESC;
```
**Explicação:** Ordena primeiro os departamentos em ordem alfabética. Dentro de cada departamento, ordena os salários do maior para o menor.

---

### Exemplo Avançado (ORDER BY)
```sql
SELECT nome, salario,
       RANK() OVER (ORDER BY salario DESC) AS ranking_salario
FROM funcionarios;
```
**Explicação:** Usa uma **função de janela** com `ORDER BY` para ranquear os funcionários de acordo com o salário, do maior para o menor.

---

## O que é GROUP BY?
A cláusula **GROUP BY** é usada para **agrupar dados** que compartilham um valor em comum. Ela é geralmente usada em conjunto com funções de agregação como `SUM()`, `COUNT()`, `AVG()`, `MAX()` e `MIN()`.

### Sintaxe Básica (GROUP BY)
```sql
SELECT coluna1, função_agregada(coluna2)
FROM nome_tabela
GROUP BY coluna1;
```

---

### Exemplo para Iniciantes (GROUP BY)
```sql
SELECT departamento, COUNT(*) AS total_funcionarios
FROM funcionarios
GROUP BY departamento;
```
**Explicação:** Conta quantos funcionários existem em cada departamento.

---

### Exemplo Intermediário (GROUP BY)
```sql
SELECT departamento, AVG(salario) AS media_salarial
FROM funcionarios
GROUP BY departamento
ORDER BY media_salarial DESC;
```
**Explicação:** Agrupa os funcionários por departamento, calcula a média salarial e depois ordena os departamentos da maior para a menor média.

---

### Exemplo Avançado (GROUP BY)
```sql
SELECT departamento, cargo, SUM(salario) AS total_salarios
FROM funcionarios
GROUP BY departamento, cargo
HAVING SUM(salario) > 50000
ORDER BY total_salarios DESC;
```
**Explicação:** Agrupa por departamento e cargo, calcula o total de salários por grupo, filtra os grupos com soma maior que 50.000 usando `HAVING`, e ordena pelo total de salários.

---

## ORDER BY vs GROUP BY: Diferenças Principais

| Característica        | ORDER BY                                   | GROUP BY                                    |
|-----------------------|--------------------------------------------|---------------------------------------------|
| Finalidade            | Ordena linhas em uma ordem específica      | Agrupa linhas em linhas resumidas           |
| Funciona com          | Qualquer coluna (selecionada ou não)       | Colunas no SELECT que não são agregadas     |
| Funções de agregação  | Não são necessárias                        | Normalmente usadas (COUNT, SUM, AVG, etc.)  |
| Número de linhas      | Mesmo número de linhas da consulta original| Menos linhas (resumidas)                    |
| Exemplo de uso        | Ordenar funcionários por salário           | Contar funcionários por departamento        |

---

## Erros Comuns e Como Evitá-los

1. **Usar GROUP BY sem agregações**  
   ```sql
   SELECT departamento, nome
   FROM funcionarios
   GROUP BY departamento;
   ```
   ❌ Erro: `nome` não está nem agrupado nem agregado.  

   ✅ Correção:
   ```sql
   SELECT departamento, COUNT(nome)
   FROM funcionarios
   GROUP BY departamento;
   ```

2. **Esquecer o ORDER BY após o GROUP BY**  
   O GROUP BY não garante ordem na saída. Sempre use `ORDER BY` se quiser resultados em ordem específica.

   ✅ Exemplo:
   ```sql
   SELECT departamento, AVG(salario) AS media_salarial
   FROM funcionarios
   GROUP BY departamento
   ORDER BY media_salarial DESC;
   ```

3. **Confundir ORDER BY com GROUP BY**  
   - `ORDER BY` ordena linhas.  
   - `GROUP BY` agrupa linhas.  

   ✅ Dica: Se você precisa de **resumos**, use `GROUP BY`. Se precisa de **ordenação**, use `ORDER BY`.

4. **Usar alias de coluna incorretamente no GROUP BY**  
   Alguns bancos de dados não permitem alias no `GROUP BY`. Use sempre os nomes reais das colunas.  

   ✅ Exemplo:
   ```sql
   SELECT departamento AS depto, COUNT(*)
   FROM funcionarios
   GROUP BY departamento;
   ```

---

## Dicas para Usar ORDER BY e GROUP BY com Eficiência

- Sempre use **GROUP BY** junto a funções de agregação.  
- Use **ORDER BY** para melhorar a legibilidade — especialmente em relatórios.  
- Combine-os de forma eficiente:  
  ```sql
  SELECT departamento, COUNT(*) AS total
  FROM funcionarios
  GROUP BY departamento
  ORDER BY total DESC;
  ```
- Use **HAVING** com GROUP BY para filtrar resultados agregados (não WHERE).  
- Cuidado com performance — ordenar grandes volumes (`ORDER BY`) ou agrupar muitas colunas (`GROUP BY`) pode ser lento. Utilize índices quando possível.  
- Evite usar posição de coluna em `ORDER BY` (como `ORDER BY 2`) em código de produção. Prefira sempre os nomes das colunas para clareza.

---

## Tabela de Prática e Consultas

Vamos usar uma tabela simples chamada **funcionarios**:

| id | nome    | departamento | cargo       | idade | salario |
|----|---------|--------------|-------------|-------|---------|
| 1  | Alice   | TI           | Desenvolvedor | 25  | 50000   |
| 2  | Bob     | TI           | Desenvolvedor | 30  | 60000   |
| 3  | Carlos  | RH           | Recrutador    | 28  | 45000   |
| 4  | Diana   | RH           | Gerente       | 40  | 70000   |
| 5  | Eduardo | Vendas       | Executivo     | 35  | 65000   |

### Consultas para praticar:
1. Liste os funcionários pelo salário, do maior para o menor.  
   ```sql
   SELECT nome, salario
   FROM funcionarios
   ORDER BY salario DESC;
   ```

2. Conte quantos funcionários existem em cada departamento.  
   ```sql
   SELECT departamento, COUNT(*) AS total_funcionarios
   FROM funcionarios
   GROUP BY departamento;
   ```

3. Encontre o departamento com a maior média salarial.  
   ```sql
   SELECT departamento, AVG(salario) AS media_salarial
   FROM funcionarios
   GROUP BY departamento
   ORDER BY media_salarial DESC
   LIMIT 1;
   ```

4. Mostre o total de salários por cargo, mas apenas se for acima de 100.000.  
   ```sql
   SELECT cargo, SUM(salario) AS total_salarios
   FROM funcionarios
   GROUP BY cargo
   HAVING SUM(salario) > 100000;
   ```

---

## Conclusão
Entender a diferença entre **ORDER BY** e **GROUP BY** é essencial para dominar SQL.  
- **ORDER BY** ajuda a controlar a ordem dos resultados.  
- **GROUP BY** permite resumir e agregar dados.  

Quando usados corretamente, tornam-se ferramentas poderosas para análise de dados. Evite os erros comuns, pratique com as consultas acima e você rapidamente ganhará confiança no uso de ambas as cláusulas.  
