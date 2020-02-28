# 1.1.2 - Modelo em Rede

* Elimina conceito de hierarquia

* Permite um mesmo registro em várias associações

* Organizado em grafo com um tipo de associação (**set**) que define `1:N` entre registros proprietário e membro

  * Com dois relacionamentos `1:N` entre registros A e D e também C e D, é possível construir um relacionamento `M:N` entre A e D

* Normas da CODASYL para esse modelo: **concorrência** e **segurança**

  * **Segurança**: permitir o bloqueio de parte do banco de dados para prevenir acessos simultâneos

* Modelo em rede permite o acesso a qualquer nó sem passar pela raiz (ao contrário do hierárquico)

* **Exemplo**:

  * Modelo

    * `Nome | Rua | Cidade` -> `Número da Conta | Saldo`

  * ```
    Maria | Rua 01 | São Paulo -> 20578 | R$ 2000,00
    
    Pedro | Rua 03 | Jundiaí -> 20552 | R$ 2500,00
                             -> 21784 | R$ 300,00
                             
    José | Rua 05 | Barueri -> 22458 | R$ 1250,00
    ```

* Tanto o modelo hierárquico quanto em rede são orientados a registros: qualquer **acesso** (inserir, consultar, alterar ou remover) são feitos um registro de cada vez