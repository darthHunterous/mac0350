# 1.2.2 - Arquiteturas

* **Primeiras arquiteturas**: SGBD centralizado no mainframes, terminais de acesso possuíam apenas capacidade de visualização
* Aumento do poder de processamento de computadores pessoais fez com que SGBDs explorassem o poder de processamento do lado do usuário, levando à **arquitetura cliente-servidor**
  * **Vantagens**
    * Facilidade de implementação por separar as funcionalidades por servidores
    * Uso inteligente de um servidor pois tarefas simples são delegadas às máquinas clientes (mais baratas)
    * Usuário pode optar pela interface gráfica de sua preferência ao invés de usar a do servidor
* **Arquitetura cliente-servidor em SGBDs**:
  * Consultas e funcionalidade transacional permanecem no servidor (servidor de consulta ou transação)
  * Servidor SQL (back-end machine) e cliente é a front-end machine
  * Divisão lógica entre cliente e servidor através da linguagem padrão de SQL