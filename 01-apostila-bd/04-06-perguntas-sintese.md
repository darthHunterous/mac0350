# 4.6 - Exercícios de Síntese

### 01 - Discutir o papel de um modelo de dados de alto nível no processo de projeto da base de dados

* O modelo de dados de alto nível auxilia na compreensão da base de dados como um todo ao modelar as necessidades da base a partir de particularidades do mini-mundo

### 02 - Cite alguns casos onde o valor null pode ser aplicado

* No caso dos dependentes dos empregados, se este for utilizado como atributo e o empregado não possuir dependentes, pode-se usar null. Também em casos como número do apartamento e o usuário morando em uma casa ou até mesmo número de telefone e ele não possuindo um

### 03 - Defina entidade, atributo, valor de atributo, instância de relacionamento, atributo composto, atributo multivalorado, atributo derivado e atributo-chave

* Entidade: objeto representado na base de dados
* Atributo: propriedade que descreve uma característica do objeto
* Valor do atributo: valor armazenado na base de dados
* Instância do relacionamento: relacionamento entre duas instâncias de entidades armazenado na base de dados em um momento específico
* Atributo composto: atributo que pode ser dividido em subpartes, composto por outros atributos mais básicos
* Atributo multivalorado: atributo que pode receber um conjunto de valores ao invés de apenas um
* Atributo derivado: pode ser obtido através de consulta a outros atributos, não precisando ser armazenado
* Atributo-chave: atributo que dá um identificador único a cada instância de entidade

### 04 - O que é um tipo de entidade? Descreva as diferenças entre entidade e tipo de entidade

* Tipo de entidade é um conjunto de entidades que possuem os mesmo atributos definidos. A diferença é que tipo de entidade se refere de uma maneira mais generalizada enquanto que entidade é usado para se referir a instâncias desse objeto

### 05 - O que é tipo de relacionamento? Descreva as diferenças entre instância e tipo de relacionamento

* É uma associação entre tipos de entidades. O tipo de relacionamento se refere à associação generalizada, entre tipos de entidades, enquanto que a instância de um tipo de relacionamento se refere à associação entre instâncias de entidades específicas

### 06 - Quando é necessário utilizar nome de papéis na descrição de tipos de relacionamentos?

* Especialmente quando o relacionamento se dá entre instância do mesmo tipo de entidade, de forma a distinguir qual a função que cada uma exerce

### 07 - Descreva as duas alternativas para especificar as restrições estruturais sobre tipos de relacionamentos. Quais são as vantagens e desvantagens de cada uma?

* Pode-se usar a notação de restrição de participação total e existencial. A vantagem é que esta é mais simplificada e pode ser identificada pelo tracejado que une entidades e relacionamentos no DER, enquanto que a restrição estrutural no DER aumenta um pouco a carga visual, mas tem como vantagem poder indicar limites específicos nas quantidades de associação de cada instância, de acordo com as restrições do mini-mundo

### 08 - Sobre quais condições pode um atributo de um tipo de relacionamento binário ser promovido a um atributo de um dos tipos de entidades participantes? 

* Em um relacionamento `1:N`, o atributo deve ser colocado da entidade do lado `N` do relacionamento

### 09 - Sobre quais condições um tipo de relacionamento pode se tornar um atributo de um tipo de entidade?

* No caso de um tipo de entidade fraca, pode-se transformar o relacionamento de identificação em um atributo da entidade proprietária, desfazendo-se o uso de uma entidade fraca. Isso ocorre quando a entidade fraca não possui muito atributos ou não participa de outros relacionamentos de maneira independente sem ser com seu proprietário

### 10 - Qual o significado de um tipo de relacionamento recursivo? Dê alguns exemplos disso

* Quando um tipo de entidade se relaciona com o mesmo tipo de entidade. Exemplos são funcionários gerenciando funcionários ou itens que compõem outros itens

### 11 - Quando o conceito de entidade-fraca é útil na modelagem de dados? Defina os termos: tipo de entidade proprietário, tipo de relacionamento de identificação e chave-parcial. 

* O conceito de entidade fraca é útil quando essa entidade dependente possui muitos atributos ou também participa de outros relacionamentos de maneira independente.
* Tipo de entidade proprietário: tipo de entidade responsável por identificar um tipo de entidade fraca
* Tipo de relacionamento de identificação: tipo de relacionamento com o qual o tipo de entidade fraca possui dependência existencial referente à necessidade de identificação
* Chave-parcial: atributo de um tipo de entidade fraca que é capaz de identificar de maneira única uma instância de entidade fraca dentre todas as outras de um tipo de entidade proprietário

### 12 - Um tipo de relacionamento de identificação pode ter grau maior que dois?

* Sim, pode haver um relacionamento de identificação ternário. Um exemplo seria um candidato que realiza uma entrevista de emprego para uma companhia. Nesse caso o tipo de entidade fraca entrevista pode ser identificada por meio dos tipo de entidade candidato e companhia

### 13 - Discuta as condições em que um tipo de relacionamento ternário pode ser representado por um número de tipos de relacionamentos binários

* Não há uma equivalência direta entre um tipo de relacionamento ternário e vários binários, mas no caso em que representemos o ternário por meio de três tipos de relacionamentos binários tal equivalência pode ser válida se tivermos uma restrição 1:1 em ao menos um dos relacionamentos binários



