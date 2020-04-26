# 06 - Mapeamento MER -> Modelo de Dados Relacional

* Modelagem através de modelo de alto nível (Modelo Entidade Relacionamento - MER)
  * Esquema das visões com diagramas entidade relacionamento (DER)
* Depois da modelagem, mapeamento do diagrama para modelo de dados de implementação (hierárquico, rede ou relacional)

### Passo a passo do mapeamento

1. Cada entidade do DER, criar relação com os atributos simples dela
   * Transfomar atributos compostos em atributos simples
   * Um dos atributos chave da entidade deve ser usado como chave primária da relação
2. Criar uma relação para cada tipo de entidade fraca, com seus atributos
   * Usar nessa relação uma chave estrangeira que seja chave primária da relação que contém o tipo de entidade de identificação
   * Chave primária: combinação da chave primária do tipo de entidade de identificação e da chave parcial do tipo de entidade fraca
3. Criar relações para cada tipo de entidade que participa de um relacionamento binário `1:1` no DER
   * Uma das relações inclui como chave estrangeira a chave primária da outra
     * Incluir a chave estrangeira na relação com restrição de participação total (exemplo: incluir em departamento na relação "empregado gerencia departamento")
   * Atributos do tipo de relacionamento são incluídos na relação que recebe a chave estrangeira
4. Criar relações para cada tipo de entidade em um relacionamento binário `1:N`
   * A relação do lado `N` recebe a chave primária da relação `1` como chave estrangeira
   * Atributos do tipo de relacionamento ficam como atributos da relação do lado `N`
5. Criar apenas uma relação para representar um relacionamento `M:N`
   * Incluir como chaves estrangeiras as chaves primárias das duas relações. As chaves estrangeiras compõem a chave primária da nova relação
   * Atributos do tipo de relacionamento viram atributos da nova relação
6. Criar uma relação para cada atributo multivalorado, com um atributo correspondente a esse atributo original e a chave primária da relação que representa o detentor desse atributo originalmente (tipo de entidade ou relacionamento)
   * A chave primária da nova relação é a combinação do atributo multivalorado com a outra chave primária inserida
7. Criar uma nova relação para cada relacionamento `n-ario`, (`n > 2`)
   * Chave estrangeira da nova relação são as chaves primárias das relações dos tipos de entidade envolvidos
   * Atributos do relacionamento viram atributos da nova relação
   * Chave primária da nova relação é a combinação das chaves estrangeiras

### Relacionamentos no esquema relacional

* Representados por dois atributos diferentes, um para chave primária e outro para estrangeira
* Duas relações são relacionadas quando têm mesmo valor para os atributos A e B mencionados acima (primária e estrangeira)