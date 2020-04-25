# 5.1 - Conceitos do Modelo Relacional

* Modelo relacional representa os dados como coleção de relações
* Cada relação é uma tabela
* Linhas representam coleção de valores relacionados (representam entidade ou instância de relacionamento)

### Terminologia do modelo relacional

* **Tupla**: linha
* **Atributo**: coluna
* **Relação**: tabela
* **Domínio**: especifica o tipo dos valores de uma coluna

### Relação esquema R

* `R(A1, A2, ..., An)`
* Conjunto de atributos `R={A1, A2, ..., An}`
* `D` **domínio** de `Ai`
  * `dom(Ai)`
* **Grau da relação**: número de atributos
* **Exemplo**
  * `ESTUDANTE(Nome, NSS, Telefone, Endereço, TelComercial, Anos, MPA)`
    * `dom(NSS) = Número do seguro social`
    * `dom(MPA) = Média dos pontos acumulados`
* **Instância de relação**
  * `r(R)`
  * Conjunto de tuplas `r={t1,t2,...,tm}`
  * Cada tupla é uma lista de `n` valores
    * `t=<v1,v2,...,vn>`
  * Cada valor é elemento de `dom(Ai)` ou `NULL`
* **Intenção da relação**: esquema R
* **Extensão da relação**: instância `r(R)`