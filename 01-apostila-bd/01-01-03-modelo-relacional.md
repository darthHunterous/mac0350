# 1.1.3 - Modelo Relacional

* Surge de **necessidades**:

  * Aumentar independência dos dados nos SGBDs
  * Armazenamento e recuperação de dados baseados em álgebra relacional
  * Processamento dedicado (ad hoc)

* Estrutura fundamental: **relação** (tabela)

  * Relação composta por **atributos(()) (campos)
  * Cada instância do **esquema** (linha) é uma **tupla** (registro)

* **Restrições**: integridade referencial, chaves e integridade de junções de relações

  * Evitam:
    * Repetição de informação
    * Incapacidade de representação de informação
    * Perda de informação

* **Exemplo**: tabelas para modelo relacional de conta corrente do cliente

  * ```
    Código Cliente | Nome  | Rua | Cidade
    01             | Pedro | A   | São Paulo
    02             | Maria | B   | Jundiaí
    ----------------------------------------
    
    Número da Conta | Saldo
    20121           | 1200
    21582           | 1320
    21352           | 652
    -----------------------
    
    Código Cliente | Número da Conta
    1              | 20121
    2              | 21582
    3              | 21352
    --------------------------------
    ```