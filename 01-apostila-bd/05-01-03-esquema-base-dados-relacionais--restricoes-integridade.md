# 5.1.3 - Esquemas de bases de dados relacionais e Restrições de Integridade

* **Esquema da base de dados relacional S** :  conjunto de relações esquema `S={R1, R2, ..., Rm}` mais conjunto de restrições de integridade `RI`
* **Instância da base de dados relacional DB**: conjunto de instância de relações `DB={r1,r2,...,rm}`, onde `ri` é instância de `Ri` e satisfaz restrições de integridade

### Restrições de integridade

* **Restrições de chave**: especifica chaves candidatas, de valores únicos entre todas as tuplas
* **Integridade de entidade**: nenhum valor nulo em chaves primárias
* **Integridade referencial**: estabelece que uma tupla de uma relação que se refere a outra relação deve se referir a uma tupla existente naquela outra
  * **Chave estrangeira**
    * Atributos da chave estrangeira em `R1` têm mesmo domínio dos atributos da chave primária na outra relação `R2` (chave estrangeira **referencia** a relação `R2`)
    * Chave estrangeira na tupla `t1` tem valor que ocorre como chave primária de alguma tupla `t2` ou tem valor `null`
      * `t1[CE]=t2[CP]` -> `t1` referencia tupla `t2`
* Chave estrangeira pode referenciar a própria relação
  * Exemplo: um emprego pode ter como chave estrangeira o NSS de seu supervisor, que por sua vez é outro empregado
  * No diagrama, desenha-se um arco partindo da chave-estrangeira e chegando na relação referenciada
* **Restrição de integridade semântica**
  * Exemplos:
    * O salário de um empregado não pode ultrapassar o de seu supervisor
    * Número máximo de horas que um empregado pode trabalhar por semana é 56