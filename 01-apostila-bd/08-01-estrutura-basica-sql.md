# 8.1 - Estrutura básica SQL

* Expressão em 3 cláusulas:
  * Select
  * From
  * Where
* **SELECT**: projeção da álgebra relacional
  * Relaciona atributos do resultado da consulta
  * DISTINCT para eliminar duplicidade
  * ALL mantém duplicidade (comportamento padrão)
  * Asterisco denota todos atributos
* **FROM**: produto cartesiano da álgebra relacional
* **WHERE**: predicado da álgebra relacional envolvendo atributos da relação em FROM
  * Operadores de comparação, conectores lógicos
* Exemplo:
  * `select A1, A2, ..., An from r1, r2, ..., rn where P`
  * Equivalente a:
    * `Pi[A1, A2, ..., An](Sigma[p](r1 X r2 X ... rm))` 

## 8.1.1 - Operação RENAME

* `nome_antigo as nome_novo`
* Pode aparecer em SELECT ou FROM

## 8.1.2 - Operações com Strings

* Coincidência de pares com operador LIKE
  * Caracteres especiais: `%` (qualquer string) e `_` (qualquer caracter)
  * Exemplos:
    * `____%`: qualquer string com ao menos 4 caracteres
    * `uni%`: qualquer string que comece com uni

## 8.1.3 - Ordenação e Apresentação de Tuplas

* ORDER BY
* Padrão: ordem ascendente
* Exemplos:
  * `ORDER BY <nome-do-campo> asc`
  * `ORDER BY <nome-do-campo> desc`

## 8.1.4 - Operações com Conjuntos

* Operações de união, interseção e diferença como: union, intersect e except

## 8.1.5 - Funções Agregadas

* Presentes em SQL:

  * Sum
  * avg
  * count
  * min
  * max

* Cláusula `group by` permite aplicar a função sobre um grupo de conjunto de tuplas

* Definir condições e aplicar a grupos com cláusula `having`

* Exemplos de cláusulas:

  * ```
    select A1, A2, ..., An
    from r1, r2, ..., rn
    where P
    group by A1
    having <funcao-agregada>
    ```

## 8.1.6 - Subconsultas aninhadas

* Expressão select from where dentro de outra consulta

* Membros de conjuntos

  * Verifica se uma tupla é membro de uma relação

  * ```
    select A1, A2, ..., An
    from r1, r2, ..., rn
    where P in (select A1, A2, ..., An
                from r1, r2, ..., rn
                where P)
    ```

* Comparações de conjunto:

  * Trocar o `in` acima por comparações como:
    * `> some`
    * `<= some`
    * `= some`
    * `> all`
    * `>= all`

* Verificar relação vazia

  * Trocar `in` por `exists`

## 8.1.7 - Visões

* Relação que não faz parte do modelo lógico mas visível ao usuário como relação virtual
* Após a visão ser computada as relações usadas para gerá-la podem mudar, ficando desatualizada
* O BD armazena sua definição e não o resultado, recomputando a cada consulta
* Criar:
  * `CREATE VIEW <nome-da-visao> AS <expressao-consulta>`
* Eliminar:
  * `DROP VIEW <nome-da-visao>`

## 8.1.8 - Inserção

* Adiciona uma tupla a uma relação

* ```
  INSERT INTO <relacao>
  VALUES <lista-valores-atributos>
  ```

## 8.1.9 - Atualização

* UPDATE modifica valores de uma ou mais tuplas

* ```
  UPDATE <relacao>
  SET <lista dos atributos a serem alterados>
  WHERE <condicao>
  ```

## 8.1.10 - Remoção

* Remove de relação `r` onde a condição `P` é válida

* ```
  DELETE FROM r
  WHERE p
  ```

## 8.1.11 - SQL DDL

### Data de nascimento e endereço do empregado 'John B. Smith'

* ```
  SELECT DATANASC, ENDERECO
  FROM EMPREGADO
  WHERE PNOME = 'John' AND MNOME = 'B' AND SNOME = 'Smith'
  ```

* Equivalente a:

  * `Pi[DATANASC, ENDERECO](Sigma[PNOME = 'John' AND MNOME = 'B' AND SNOME = 'Smith'](EMPREGADO))`

### Nome e endereço dos empregados que trabalham para o departamento Pesquisa

* ```
  SELECT PNOME, SNOME, ENDERECO
  FROM EMPREGADO, DEPARTAMENTO
  WHERE DNOME = 'Pesquisa' AND DNUMERO = NDEP
  ```

### Número do projeto, número do departamento responsável, sobrenome, endereço e data de nascimento do gerente para todo projeto em Stafford

* ```
  SELECT PNUMERO, DNUM, SNOME, ENDERECO, DATANASC
  FROM PROJETO, DEPARTAMENTO, EMPREGADO
  WHERE PLOCALIZACAO = 'Stafford' AND DNUM = DNUMERO AND NSSGER = NSS
  ```

### Nomes dos empregados que trabalham em todos os projetos do departamento 5

* ```
  SELECT PNOME, SNOME
  FROM EMPREGADO
  WHERE ((SELECT PNRO
          FROM TRABALHA_EM
          WHERE NSS = NSSEMP)
          CONTAINS
          (SELECT PNUMERO
           FROM PROJETO
           WHERE DNUM = 5)) 
  ```

* CONTAINS compara dois conjuntos e retorna TRUE se um conjunto contém todos os valores do outro, similar ao DIVISION da álgebra relacional

### Número de projetos onde um empregado de sobrenome Smith trabalha ou é gerente

* ```
  (SELECT PNUMERO
  FROM PROJETO, TRABALHA_EM, EMPREGADO
  WHERE SNOME = 'Smith' AND NSSEMP = NSS AND PNUMERO = PNRO)
  UNION
  (SELECT PNUMERO
  FROM PROJETO, EMPREGADO, DEPARTAMENTO
  WHERE SNOME = 'Smith' AND DNUM = DNUMERO AND NSSGER = NSS)
  ```

### Nome de empregados com mais de um dependente

* ```
  SELECT PNOME, SNOME
  FROM EMPREGADO
  WHERE (SELECT COUNT(*)
         FROM DEPENDENTE
         WHERE NSS = NSSEMP) >= 2
  ```

* `(*)` indica o número de tuplas

### Nome de empregados sem dependentes

* ```
  SELECT PNOME, SNOME
  FROM EMPREGADO
  WHERE NOT EXISTS (SELECT *
  									FROM DEPENDENTE
  									WHERE NSS = NSSEMP)
  ```

* `*` indica todos os atributos da tupla selecionada

### Nome dos gerentes com dependentes

* ```
  SELECT PNOME, SNOME
  FROM EMPREGADO
  WHERE EXISTS (SELECT *
                FROM DEPENDENTE
                WHERE NSS = NSSEMP)
        AND
        EXISTS (SELECT *
                FROM DEPARTAMENTO
                WHERE NSS = NSSGER)
  ```

