# 5.1.2 - Atributos chaves de relação

* **Subconjuntos de atributos** tal que nenhuma tupla tenha a mesma combinação de valores para tais atributos
  * Subconjunto denotado por `SC`
  * Para qualquer tupla `t1` e `t2` em `r` de `R`, vale: `t1[SC] != t2[SC]`
  * `SC` é **super chave** da relação esquema
  * Toda relação tem ao menos a super chave do conjunto de todos seus atributos
* **Chave** é uma super chave com a propriedade adicional de não se poder remover um atributo desta chave sem que ela deixa de ser uma super chave
  * Chave é uma super chave mínima
  * Na relação `ESTUDANTE`, conjunto `{NSS}` é super-chave pois dois estudantes não podem ter o mesmo `NSS` e também chave pois não se pode remover um atributo do conjunto
    * Qualquer conjunto que inclua `NSS` é superchave mas não é chave, pois a remoção de algum atributo que não seja `NSS` ainda fará desse conjunto uma superchave
* Relação esquema pode ter mais de uma chave, cada uma é uma **chave candidata**
  * Exemplo: NSS de estudante e código interno de estudantes na escola
  * Uma das chaves candidatas é a **chave primária**