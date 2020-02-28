# 1.1.1 - Modelo Hierárquico

* Possível por conta dos discos de armazenamento endereçáveis: permite a exploração da estrutura do endereçamento físico para a representação hierárquica de informações

* Os nós são registros (coleção de campos/atributos)

* Cada atributo contém uma informação

* Registro que precede outro é o registro-pai e os outros são registros-filhos

* **Ligação** é associar dois registros

* **Relacionamento** registro-pai e registro-filho tem cardinalidade `1:N`

  * Um pai pode ter vários filhos
  * Um filho só tem um pai

* Um registro pode ser associado a vários registros diferentes, mas requer ser **replicado**

  * **Desvantagem replicação**: pode ocorrer inconsistência de dados ao atualizar e há desperdício de espaço

* **Exemplo de modelo hierárquico** - Conta Corrente

  * Modelo

    * Nome | Rua | Cidade
      * Número da Conta | Saldo

  * Exemplo

    * [raiz]

      * Maria | Rua 01 | São Paulo

        * 20121 | R$ 550,00
        * 20578 | R$ 2000,00

      * Pedro | Rua 03 | Jundiaí

        