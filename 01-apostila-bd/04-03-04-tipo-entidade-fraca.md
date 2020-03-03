# 4.3.4 - Tipo de entidade fraca

* **Tipos de entidades fracas**: sem atributos-chaves, pode ser que não seja possível distinguir entidades por conta de combinação de valores idênticas nos atributos
* Entidades fracas são identificadas pela associação a outro tipo de entidade (**proprietário da identificação**) através de um **relacionamento de identificação**
* Pela necessidade de identificação, a entidade fraca tem dependência existencial (restrição de participação total) com o relacionamento de identificação
* Exemplo da entidade DEPENDENTE relacionado a EMPREGADO em `1:N`
* **Chave-parcial**: atributos que podem identificar de maneira única uma entidade fraca dentre as entidades fraca relacionadas à uma entidade proprietária
  * No exemplo, o nome de um dependente serviria pois se assume que não haverá nomes idênticos dentre os dependentes de um empregado
* Tipo de entidade fraca pode ser representada como atributo composto e multivalorado
  * Substituir o tipo de entidade fraca DEPENDENTE por um atributo multilvalorado e composto de EMPREGADO, chamado dependente
  * **Critério** para definir uma entidade fraca: quanto tem muitos atributos ou participa de maneira independente de seu proprietários em outros relacionamentos além do de identificação