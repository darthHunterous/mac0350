# 4.3.5 - Projeto da Base de Dados da Companhia usando Modelo Entidade Relacionamento

* Relação **GERENCIA** entre entidades **EMPREGADO** e **DEPARTAMENTO**
  * `1:1`
  * Participação parcial de EMPREGADO
  * Participação total de DEPARTAMENTO
  * Atributo `DataInicio` associado ao relacionamento
* Relação **TRABALHA-PARA** entre **DEPARTAMENTO** e **EMPREGADO**
  * `1:N`
  * Participação total de ambos
* Relação **CONTROLA** entre **DEPARTAMENTO** e **PROJETO**
  * `1:N`
  * Participação total de PROJETO
  * Participação parcial de DEPARTAMENTO
* Relação **SUPERVISIONA** entre **EMPREGADO (papel de supervisor)** e **EMPREGADO (papel de supervisionado)**
  * `1:N` [por que não seria 1:1? Seria pela estrutura hierárquica? O supervisor no topo seria responsável por até N, enquanto que o último supervisor, logo antes do único não-supervisor seria responsável por apenas 1]
  * Participação parcial pois nem todos funcionários tem um supervisor e nem todo funcionário é supervisor
* Relação **TRABALHA-EM** entre **EMPREGADO** e **PROJETO**
  * `M:N`
  * Relação com o atributo `horas`
  * Ambos com participação total
* Relação **DEPENDENTE-DE** entre **DEPENDENTE** e **EMPREGADO**
  * `1:N`
  * Relacionamento de identificação para a entidade fraca DEPENDENTE
  * Participação parcial de EMPREGADO
  * Participação total de DEPENDENTE

