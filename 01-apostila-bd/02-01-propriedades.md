# 2.1 - Propriedades

* **Base de dados**: coleção de dados logicamente relacionados
  * Projetada e instanciada (preenchida) com dados para um propósito específico
  * Representa aspecto do mundo real (mini-mundo)
  * Alteração no mini-mundo provoca mudança na base de dados
  * Possui fonte para os dados, interação com o mundo real e audiência interessada no conteúdo
* **SGBD - Sistema Gerenciador de Banco de Dados**: sistema de software que facilita **definir**, **construir** e **manipular** base de dados
  * **Definir**: especificar tipos de dados a serem armazenados
  * **Construir**: armazenar dados em um meio controlado pelo SGBD
  * **Manipular**: consultar, modificar a base para equiparar mudanças no mini-mundo e gerar relatórios
* **Sistema de base de dados**: base de dados + software de gerenciamento
  * **Interação com usuário**:
    * Usuário -> sistema de base de dados
    * Sistema de base de dados (consultas/programas de aplicação) -> SGBD
    * SGBD (software que processa consultas -> software de acesso à base) -> base de dados