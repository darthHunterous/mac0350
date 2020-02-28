# 1.2.3 - Resumo de Arquiteturas de SGBD

* **Plataforma centralizada**: computador com grande capacidade de processamento, hospeda o SGBD
  * **Vantagem**: permite vários usuários manipulando grande volume de dados
  * **Desvantagem**: alto custo
* **Computador Pessoal**: stand-alone, funcionam como hospedeiro e também terminal de acesso do SGBD
  * **Vantagem**: simplicidade
* **Cliente-servidor**:
  * **Cliente**: fornece interface de usuário (processamento entrada e saída)
  * **Servidor**: consulta o banco e retorna resultados ao cliente
  * **Requisitos**: tratamento de transações, confirmações (commits), desfazer (rollback), linguagem para consulta e gatilhos (triggers)
  * **Vantagem**: divisão de processamento, menor tráfego de dados na rede
* **BD distribuído (N camadas)**: informação em vários servidores
  * Cada servidor atua como no modelo cliente-servidor
  * Existência de vários aplicativos consultando a rede por dados mas sem conhecimento de qual servidor específico contém os dados