# 7.3 - Questões de Revisão

1. União compatível é quando duas relações têm o mesmo número de atributos e com cada par de atributos correspondente com o mesmo domínio
2. Não entendi a questão
3. Vide 07-01-00: theta join, equijoin e natural join

### Questão 04

1. Nome dos empregados do departamento 5 que trabalham mais de 10 horas no projeto ProdutoX

   * ```
     NUMERO_PROJETO_PRODUTOX(PNRO) = Pi[PNUMERO](Sigma[PNOME = 'ProdutoX'](PROJETO))
     EMPREGADOS_10HORAS_PRODUTOX(NSS) = Pi[NSSEMP](Sigma[HORAS > 10.0](NUMERO_PROJETO_PRODUTOX * TRABALHA_EM))
     RESULT = Pi[SNOME, PNOME](EMPREGADOS_10HORAS_PRODUTOX * EMPREGADO)
     ```

2. Listar nome dos empregados que tenham dependente de mesmo nome

   * ```
     DEPENDENTES(NSS, NOMEDEPENDENTE) = Pi[NSSEMP, NOMEDEPENDENTE](DEPENDENTE)
     EMPREGADOS(NSS, NOME) = Pi[NSS, PNOME](EMPREGADO)
     RESULT = Pi[NOME](Sigma[NOME = NOMEDEPENDENTE](DEPENDENTES * EMPREGADOS))
     ```

3. Nome dos empregados supervisionados por Franklin Wong

   * ```
     NSS_FRANKLIN_WONG(NSSSUPER) = Pi[NSS](Sigma[PNOME = 'Franklin' AND SNOME = 'Wong'](EMPREGADO))
     SUPERVISIONADOS_WONG = Pi[PNOME, SNOME](EMPREGADO * NSS_FRANKLIN_WONG)
     ```