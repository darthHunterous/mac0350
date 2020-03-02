# 4.2 - Exemplo

* Processo para projetar a base de dados para uma **COMPANHIA** usando MER
* Armazena dados de:
  * Empregados
  * Departamentos
  * Projetos
* Após obter e analisar requisitos, projetistas produziram uma descrição do mini-mundo
  * Companhia organizada em departamentos
    * Nome
    * Número
    * Empregado que gerencia o departamento
      * Data de início de gerência
    * Uma ou mais localizações
  * Departamento controla vários projetos
    * Nome
    * Número
    * Localização
  * Empregado
    * Nome
    * Número seguridade social
    * Endereço
    * Salário
    * Sexo
    * Data de nascimento
    * Associado a um departamento
    * Pode trabalhar em vários projetos (podendo ser de departamentos diferentes)
      * Número de horas trabalhadas em cada projeto pelo empregado
      * Supervisor direto do projeto
    * Dependentes do empregado
      * Nome
      * Sexo
      * Data de nascimento
      * Relacionamento com empregado