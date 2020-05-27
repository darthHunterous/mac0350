# 07 - Linguagens Formais de Consulta

## 7.1 - Álgebra Relacional

* Operações para manipular relações
* Dois grupos:
  * Operações sobre teoria de conjuntos: union, intersection, difference, cartesian product
  * Operações para base de dados relacionais: select, project, join

### 7.1.1 - Operações SELECT e PROJECT

* **7.1.1.1 - Operador SELECT**
  * Seleciona conjunto de tuplas (linhas) sob **condição de seleção**
  * **&sigma;<sub>SALARIO > 3000 </sub>(EMPREGADO)**
  * **&sigma;<sub><condição de seleção> </sub>(<nome da relação>)**
  * Condição de seleção composta:
    * **&sigma;<sub>(NDEP = 4 AND SALARIO > 2500) OR (NDEP = 5 AND SALARIO > 3000) </sub>(EMPREGADO)**
  * Unário, aplicado apenas uma relação
  * **Comutativo**:
    * **&sigma;<sub>\<cond1\> </sub>(&sigma;<sub>\<cond2\></sub>(R)) = &sigma;<sub>\<cond2\> </sub>(&sigma;<sub>\<cond1\></sub>(R))**
    * **&sigma;<sub>\<cond1\> </sub>(&sigma;<sub>\<cond2\></sub>(R))** equivalente a:
      * **&sigma;<sub>\<cond1\> AND \<cond2\></sub>(R)**
* **7.1.1.2 - Operador PROJECT**
  * Seleciona colunas (atributos) da tabela de relação e ignora outras
  * **&pi;<sub>\<lista de atributos\></sub>(\<nome da relação\>)**
  * **&pi;<sub>SNOME, PNOME, SALARIO</sub>(EMPREGADO)**
  * Grau da relação resultante é a quantidade de atributos na lista passada
  * **Eliminação da duplicidade**: em duplas idênticas que resultem do operador, remove informação caso não seja passada um atributo chave na lista
  * Não é comutativa:
    * **&pi;<sub>\<lista1\></sub>(&pi;<sub>\<lista2\></sub>(R)) = &pi;<sub>\<lista1\></sub>(R)**
      * Se lista2 contém os atributos em lista1, do contrário retorna nulo

### 7.1.2 - Sequência de Operações

* Única expressão algébrica ou várias relações intermediárias
* **&pi;<sub>PNOME, SNOME, SALARIO</sub>(&sigma;<sub>NDEP = 5</sub>(EMPREGADO))**
* Sequência:
  * **DEP5_EMPS <-- &sigma;<sub>NDEP = 5</sub>(EMPREGADO)**
  * **RESULT <-- &pi;<sub>PNOME, SNOME, SALARIO</sub>(DEP5_EMPS)**

### 7.1.3 - Renomeando atributos

* Listar os nomes a serem reatribuídos entre parênteses:
  * **DEP5_EMPS <-- &sigma;<sub>NDEP = 5</sub>(EMPREGADO)**
  * **RESULT(PRIMEIRO_NOE, SOBRENOME, SALARIO) <-- &pi;<sub>PNOME, SNOME, SALARIO</sub>(DEP5_EMPS)**

### 7.1.4 - Operações da Teoria de Conjuntos

* Exemplo com UNION

  * **DEP5_EMPS <-- &sigma;<sub>NDEP = 5</sub>(EMPREGADO)**
  * **RESULT1 <-- &pi;<sub>NSS</sub>(DEP5_EMPS)**
	* **RESULT2(NSS) <-- &pi;<sub>NSSSUPER</sub>(DEP5_EMPS)**
	* **RESULT <-- RESULT1 &cup; RESULT2**
* Número do seguro social de todos empregados do departamento 5 ou que supervisionam alguém de lá
* UNION, INTERSECTION, DIFFERENCE
  * Binárias, requerem duas relações
  * As duas relações devem ter o mesmo **tipo de duplas**
    * **União compatível**: duas relações com mesmo número de atributos e que cada par de atributos correspondente tenha o mesmo domínio
  * UNION: todas tuplas nas duas relações, eliminando duplicatas
  * INTERSECTION: todas tuplas comuns a ambas relações
  * DIFFERENCE: todas tuplas na primeira relação que não estejam na segunda
  * UNION e INTERSECTION são comutativas e associativas
  * DIFFERENCE não é comutativa
* CARTESIAN PRODUT: &chi;
  * Não precisa ser união compatível
  * Relação 1 com `n` atributos e 2 com `m` atributos resulta numa relação com `n + m` atributos
  * Relação 1 com `x` tuplas e 2 com `y` tuplas resulta numa relação com `x * y` tuplas
  * Exemplo: recuperar uma lista dos dependentes dos empregados mulheres
    * **EMP_FEM <-- &sigma;<sub>SEXO = 'F'</sub>(EMPREGADO)**
    * **EMP_NOMES <-- &pi;<sub>PNOME, SNOME, NSS</sub>(EMP_FEM)**
    * **EMP_DEP <-- EMP_NOMES &chi; DEPENDENTE**
    * **DEP_ATUAL <-- &sigma;<sub>NSS = NSSEMP</sub>(EMP_DEP)**
    * **RESULT <-- &pi;<sub>PNOME, SNOME, NOMEDEPENDENTE</sub>(DEP_ATUAL)**
  * Operação JOIN especifica um CARTESIAN PRODUCT seguido por um SELECT

### 7.1.5 - Operação JOIN

* Combina tuplas de duas relações em uma única
* Exemplo: nome dos gerentes de cada departamento
  * **DEPT_GER <-- DEPARTAMENTO [X]<sub>NSSGER = NSS</sub> EMPREGADO**
  * **RESULT <-- &pi;<sub>DNOME, SNOME, PNOME</sub> (DEPT_GER)**
* Mesmo exemplo com produto cartesiano e select
  * **EMP_DEP <-- EMP_NOMES &chi; DEPENDENTE**
  * **DEP_ATUAL <-- &sigma;<sub>NSS = NSSEMP</sub> (EMP_DEP)**
* Forma geral do JOIN:
  * **R [X] <sub>\<condição join\></sub> S**
* **THETA JOIN**: JOIN com condição especificada
* **EQUIJOIN**: quando é usado apenas `=` como comparação
* **NATURAL JOIN**: equijoin seguido da remoção de atributos duplicados
  * **PROJ_DEPT <-- PROJETO \* <sub>DNUM = DNUMERO</sub> DEPARTAMENTO**
  * Mantém-se apenas o primeiro atributo de união (DNUM)
  * Pode-se destacar a comparação por sempre significa um `=` no NATURAL JOIN:
    * **Q <-- R \* <sub>(\<lista1\>),(\<lista2\>)</sub> S**
  * Se os atributos tiverem o mesmo nome em ambas relações pode-se omitira as condições:
    * **DEPT_LOCS <-- DEPARTAMENTO \* LOCAIS_DEPTO**

### 7.1.7 - Operação DIVISION

* Temos R com:

  * ```
    R = [{a1, b1}, {a2, b1}, {a3, b1}, {a4, b1},
         {a1, b2}, {a3, b2},
         {a2, b3}, {a3, b3}, {a4, b3},
         {a1, b4}, {a2, b4}, {a3, b4}]
       
    S = {a1, a2, a3}
    
    Divisão
    T = R / S
    
    Resultado:
    T = {b1, b4}
    ```

* Outra forma de expressar **T <-- R &div; S**:

  * **T1 <-- &pi;<sub>Y</sub>(R)**
  * **T2 <-- &pi;<sub>Y</sub>((S &chi; T1) - R)**
  * **T <-- T1 - T2**
  
* Exemplo: recuperar o nome dos empregados que trabalham em todos projetos que John Smith trabalha

  * Primeiro: lista de números dos projetos que John trabalha, colocada em **SMITH_PNOS**
    * **SMITH <-- &sigma;<sub>PNOME = 'John' and SNOME = 'Smith'</sub>(EMPREGADO)**
    * **SMITH_PNOS <-- &pi;<sub>PNRO</sub>(TRABALHA_EM \* <sub>NSSEMP = NSS</sub> SMITH)**
  * Segundo: listar o número do seguro social de cada empregado junto com o número do projeto em que trabalha:
    * **NSS_PNRO <-- &pi;<sub>PNRO, NSSEMP</sub>(TRABALHA_EM)**
  * Terceiro: aplicar division
    * **NSS_DESEJADO(NSS) <-- NSS_PNRO &div; SMITH_PNOS**
    * **RESULT <-- &pi;<sub>PNOME, SNOME</sub>(NSS_DESEJADO \* EMPREGADO)**

### 7.1.8 - Operações relacionais adicionais

* Abaixo, consultas adicionais que não podem ser expressas em álgebra relacional mas são implementadas por SGBDs

### 7.1.9 - Funções de agregação

* **Funções agregadas**: SUM, AVERAGE, MAXIMUM, MINIMUM, COUNT
  * Aplicadas sobre todas tuplas de uma relação
* Operação FUNCTION:
  * **<sub>\<atributos de agrupamento\></sub> F <sub>\<lista de funções\></sub> (\<nome da relação\>)**
  * Exemplo: recuperar para cada departamento o número de empregados e a média salarial:
    * **R(DNO, NRO_EMPS, MEDIA) <-- <sub>NDEP</sub> F <sub>COUNT NSS, AVERAGE SALARIO</sub>(EMPREGADO)**
  * O atributo de agrupamento não precisa ser especificado e, assim a função será aplicada a todos os valores de tupla da relação especificada, resultando em uma única dupla

### 7.1.10 - Operações de fechamento recursivo (clausura recursiva)

* Exemplo: todos os níveis de supervisão por um funcionário chamado James Borg (incluindo todos que este supervisiona e todos supervisionados por aqueles supervisionados por James, em diante)
  * Supervisionados por James:
    * **BORG_NSS <-- &pi;<sub>NSS</sub>(&sigma;<sub>PNOME = 'James' AND SNOME = 'Borg'</sub>(EMPREGADO))**
    * **SUPERVISAO(SNN1, SNN2) <-- &pi;<sub>NSS, NSSSUPER</sub>(EMPREGADO)**
    * **RESULT1 <-- &pi;<sub>SNN1</sub>(SUPERVISAO [X]<sub>SNN2 = NSS</sub>BORG_NSS)**
  * Recuperar todos supervisionados por James indiretamente no nível dois:
    * **RESULT2 <-- &pi;<sub>SNN1</sub>(SUPERVISAO [X]<sub>SNN2 = NSS</sub>RESULT1)**
  * Obter todos supervisionados por James direta e indiretamente no nível dois:
    * **RESULT3 <-- (RESULT1 &cup; RESULT2)**
* Porém, não é possível recuperar todos supervisionados por James em todos os níveis sem conhecer de antemão o número máximo de níveis dessa recursão