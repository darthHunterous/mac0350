# 3.2 - Arquitetura e Independência de Dados

* Arquitetura mais difundida: Three Schema
  * Separa a aplicação de usuário da base de dados
  * Esquemas em três níveis
    1. **Nível interno**: **esquema interno** para a estrutura do armazenamento físico da base de dados
    2. **Nível conceitual**: **esquema conceitual** para descrever a estrutura da base de dados
       * Omite a estrutura física do armazenamento e foca na descrição de entidades, tipos de dados, relacionamentos e restrições
    3. **Nível externo (visão)**: **esquemas externos (visões de usuários)** que descreve a visão da base de dados a partir de um grupo de usuários
       * Visão descreve a parte da base que interessa a um grupo de interesse e esconde o resto

### Independência de dados

* Alterar o esquema de um nível sem precisar alterar o do nível superior
* **Independência lógica**: alterar o esquema conceitual sem alterar os esquemas externos ou aplicações
  * Expandir ou reduzir a base de dados com mais ou menos tipos de registros
* **Independência física**: alterar esquema interno sem alterar o esquema conceitual
  * Necessário para reorganizar arquivos físicos para melhorar o desempenho em recuperação ou modificação de dados