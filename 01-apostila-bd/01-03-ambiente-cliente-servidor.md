# 1.3 - Ambiente de Implementação Cliente Servidor

* Em um ambienete de desenvolvimento de aplicativos há um gap semântico entre os paradigmas de interfaces e de armazenamento de informações: importância de estruturas como **Case** e **Cursores**
* **Case**: converte solicitações na interface para linguagem que seja processada pelos servidores de dados
* A resposta para uma consulta dada pelo servidor é uma tabela com zero ou mais tuplas. Retornando múltiplas tuplas faz-se necessário um **Cursor** para processar
* **Cursor**: similar a ponteiro de arquivo, aponta para uma tupla retornada na consulta
  * Controlado em SQL por 3 comandos: **OPEN**, **FETCH**, **CLOSE**
  * **OPEN**: inicializa o cursor, executa a consulta e aponta o cursor para a posição anterior à primeira tupla
  * **FETCH**: ao executar a primeira vez retornar a primeira tupla e aponta o cursor para ela
    * Execuções seguintes apontarão para a próxima tupla, retornando ela
  * **CLOSE**: desbloqueia o cursor após a última linha