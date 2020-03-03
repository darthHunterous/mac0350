# 4.3.1 - Entidades e Atributos

* **Entidade**: algo do mundo real, com existência física ou conceitual
  * **Atributos**: propriedades que descrevem a entidade
    * Cada atributo tem um **valor**
    * Podem ser divididos em subpartes
    * **Atributos composto**: por outros mais básicos
      * Exemplo: Endereço
        * Endereço da rua
          * Nome
          * Número
          * Apartamento
        * Cidade
        * Estado
        * CEP
    * **Atributos simples/atômicos**: não divisíveis
* **Atributo Univalorado**: único valor
  * Exemplo: data de nascimento
* **Atributo Multivalorado**: conjunto de valores
  * Exemplo: telefone residencial (pode haver vários)
* **Atributo derivado**: não precisam ser armazenados, podem ser obtidos através de consulta pelo relacionamento entre dois atributos
  * Exemplos:
    * Idade de uma pessoa a partir da data atual e de nascimento
    * Número de empregados de um departamento a partir do número de empregados relacionados com o departamento
* **Atributo null**: sem valor para tal atributo, por não ser aplicável ou por ser desconhecido
  * Não aplicável: *Apartamento* para alguém que não more em um
  * Desconhecido: usuário não respondeu determinada informação