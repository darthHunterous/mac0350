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