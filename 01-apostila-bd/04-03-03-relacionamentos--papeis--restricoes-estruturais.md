# 4.3.3 - Relacionamentos, Papéis e Restrições Estruturais

* **Tipo de Relacionamento**: R entre `n` tipos de entidades, conjunto de associações entre entidades desses tipos
  * Tipos E_1, E_2, ..., E_n de entidade **participam** do tipo de relacionamento R e entidades individuais (e_1, e_2, ..., e_n) participam na instância do relacionamento r_i = (e_1, e_2, ..., e_n)
* Exemplo do tipo de relacionamento **TRABALHA-PARA** entre tipos de entidades **EMPREGADO** e **DEPARTAMENTO**
  * r_1: e_1 -> d_1
  * r_2: e_2 -> d_2
  * r_3: e_3 -> d_1
  * r_4: e_4 -> d_2
  * r_5: e_5 -> d_3
  * r_6: e_6 -> d_1
  * r_7: e_7 -> d_3
* e_1, e_3, e_6 trabalham para d_1
* e_2, e_4 trabalham para d_2
* e_5, e_7 trabalham para d_3

### Grau do Tipo de Relacionamento

* Número dos tipos de entidades que participam do relacionamento
* **TRABALHA-PARA**: grau dois
* **Binário**: grau dois
* **Ternário**: grau três

### Exemplo de Ternário - Relacionamento FORNECE

* Instância `r_i` associa fornecedor `s` que fornece peça `p` a um projeto `j`
* Exemplo de **FORNECE**
  * `r1`: `s1`, `p1` -> `j1`
  * `r2`: `s1`, `p1` -> `j2`
  * `r3`: `s1`, `p2` -> `j3`
  * `r4`: `s2`, `p1` -> `j1`
  * `r5`: `s2`, `p1` -> `j3`
  * `r6`: `s2`, `p3` -> `j2`
  * `r7`: `s2`, `p3` -> `j3`

### Relacionamento Ternário vs. 3 binários

* O ternário geralmente representa mais informação
* 3 binários: **PODE-FORNECER**, **USA**, **FORNECE-ALGO**
  * **PODE-FORNECER**: fornecedor `s` pode fornecer peça `p`
  * **USA**:  projeto `j` usa peça `p`
  * **FORNECE-ALGO**: fornecedor `s` fornece peça para projeto `j`
* **Armadilha de conexão**: existência de três instâncias de relacionamentos `(s, p)`, `(j, p)` e `(s, j)` não implica que instância `(s, j, p)` exista no ternário **FORNECE**

### Relacionamento como atributo

* Tipo de relacionamento como atributo
* Exemplo do **TRABALHA-PARA**: atributo departamento no tipo de entidade *EMPREGADO* em que o valor é a entidade departamento em questão
* Pode ser departamento como atributo do tipo de entidade EMPREGADO ou empregado como atributo multivalorado do tipo de entidade DEPARTAMENTO

### Nome do papel

* Cada tipo de entidade tem um **papel** no relacionamento
* **Nome do papel**: indica o papel que uma entidade tem para cada instância do relacionamento
  * Exemplo: em **TRABALHA-PARA**, EMPREGADO tem papel de empregado ou trabalhador e DEPARTAMENTO tem papel departamento ou empregador

### Relacionamento recursivo

* Um mesmo tipo de entidade participa mais de uma vez em um dado tipo de relacionamento só que com papéis distintos
* Nome do papel distingue o significado da participação
* **Exemplo** de auto-relacionamento:
  * EMPREGADO e SUPERVISIONA
    * `r1`: `e1` -> `e2`
    * `r2`: `e2` -> `e3`
    * `r3`: `e3` -> `e4`
  * O tipo de entidade EMPREGADO participa duas vezes: no papel de supervisor e depois no papel de supervisionado

### Restrições sobre tipos de relacionamentos

* Restrições determinadas por situações do mini-mundo que os relacionamentos representam
* No exemplo do **TRABALHA-PARA**, se houver a regra de um empregado trabalhar apenas em um departamento, essa restrição deve constar no esquema
* **Tipos** de restrição de relacionamento
  * **Razão de cardinalidade**
  * **Participação**

### Razão de cardinalidade

* Quantidade de instâncias de relacionamento que a entidade pode participar
* No exemplo do **TRABALHA-PARA**, DEPARTAMENTO:EMPREGADO tem razão de cardinalidade `1:N`
  * Muitos empregados podem trabalhar para um departamento mas um empregado trabalha apenas em um
* Razões mais comuns: `1:1`, `1:N` e `M:N`
* **Exemplo de `1:1`:**
  * Relacionamento **GERENCIA** entre **DEPARTAMENTO** E **EMPREGADO**
  * EMPREGADO: (e1, e2, ..., e7)
  * DEPARTAMENTO: (d1, d2, d3)
  * GERENCIA:
    * r1: e3 -> d1
    * r2: e6 -> d2
    * r3: e5 -> d3
  * Um empregado pode gerenciar apenas um departamento e um departamento pode ter apenas um gerente
* **Exemplo de `M:N`**:
  * Relacionamento **TRABALHA-EM** entre **EMPREGADO** e **PROJETO**
  * EMPREGADO: (e1, e2, e3, e4)
  * PROJETO: (p1, p2, p3, p4)
  * TRABALHA-EM:
    * r1: e1 -> p1
    * r2: e2 -> p1
    * r3: e2 -> p4
    * r4: e3 -> p2
    * r5: e3 -> p3
    * r6: e3 -> p4
    * r7: e4 -> p3
  * Um empregado pode trabalhar em vários projetos, e vários empregados podem trabalhar em um projeto

### Restrição de participação

* Existência de uma entidade depende dela estar relacionada com outra por meio de um relacionamento
* Dois tipos:
  * **Restrição de participação total**
    * Exemplo: regra da empresa que todo empregado deve trabalhar para um departamento
      * Entidade empregado só pode existir se participar de uma instância de relacionamento **TRABALHA-PARA**
    * Também chamada de **dependência existencial**
  * **Restrição de participação parcial**
    * Exemplo: nem todo empregado precisa gerenciar um departamento
      * Algumas entidades do conjunto EMPREGADO podem estar relacionadas a um departamento via GERENCIA, mas não obrigatoriamente todas

### Restrição estrutural

* Associar um par (min, max) para cada participação de um tipo de entidade E em um tipo de relacionamento R
  * Cada entidade `e` em E deve participar ao menos `min` vezes e no máximo `max` vezes em instâncias de relacionamento R
* Se `min == 0`, restrição de participação parcial
* Se `min > 0`, restrição de participação total

### Atributos nos tipos de relacionamento

* Tipos de relacionamento podem ter atributos como tipos de entidade
* Exemplo: quantidade de horas semanais que um empregado trabalha em certo projeto
  * Atributo `horas` em cada instância do relacionamento **TRABALHA-EM**
* Em tipo de relacionamento `1:N`, o atributo de relacionamento só pode ser colocado no tipo de entidade do lado `N` do relacionamento
  * No relacionamento **TRABALHA-PARA**, um atributo `DataInicio` pode ser colocado como atributo de EMPREGADO pois cada entidade empregado participa de apenas uma instância de TRABALHA-PARA
* No caso `M:N`, o atributo deve ser especificado como atributo de relacionamento pois as entidades dos dois lados podem participar de inúmeras instâncias do relacionamento
  * Exemplo: `horas` no relacionamento **TRABALHA-EM** pois o número de horas que um empregado trabalhar um projeto depende da combinação empregado-projeto

















































































