# 7.2 - Exemplos de consultas na Álgebra Relacional

### Encontrar nome e endereço dos empregados que trabalham para o departamento de Pesquisa

* ```
  DEPARTAMENTO_PESQUISA <-- Sigma[DNOME = 'Pesquisa'](DEPARTAMENTO)
  EMPREGADOS_DEPARTAMENTO_PESQUISA <-- Join[DNUMERO = NDEP](DEPARTAMENTO_PESQUISA, EMPREGADO)
  RESULTADO <-- Pi[PNOME, SNOME, ENDERECO](EMPREGADOS_DEPARTAMENTO_PESQUISA)
  ```

### Listar número do projeto, número do departamento e sobrenome, endereço e nascimento do gerente desse departamento para todo projeto em Stafford

* ```
  PROJETOS_STAFFORD <-- Sigma[PLOCALIZACAO = 'Stafford'](PROJETO)
  DEPARTAMENTOS_PROJETOS_STAFFORD <-- Join[DNUM = DNUMERO](PROJETOS_STAFFORD, DEPARTAMENTO)
  GERENTES_DEPARTAMENTOS_STAFFORD <-- Join[SSNGER = NSS](DEPARTAMENTOS_PROJETOS_STAFFORD, EMPREGADO)
  RESULT <-- Pi[PNUMERO, DNUM, SNOME, ENDERECO, DATANASC](GERENTES_DEPARTAMENTOS_STAFFORD)
  ```

### Nomes dos empregados que trabalham em todos projetos do departamento 5

* ```
  PROJETOS_DEP5(NUMERO_PROJETO) <-- Pi[PNUMERO](Sigma[DNUM = 5])(PROJETO)
  EMPREGADOS_PROJETOS(CPF, NUMERO_PROJETO) <-- Pi[NSSEMP, PNRO](TRABALHA_EM)
  CPF_EMPREGADOS_TODOS_PROJETOS_DEP5 <-- Division(EMPREGADOS_PROJETOS, PROJETOS_DEP5)
  RESULT <-- Pi[SNOME, PNOME](CPF_EMPREGADOS_TODOS_PROJETOS_DEP5 * EMPREGADO)
  ```

### Lista de números de projeto onde um empregado de sobrenome Smith trabalha ou é gerente de tal departamento

* ```
  RESULT = Pi[NSSEMP, PNRO, DNUM](Join[PNRO = PNUMERO](TRABALHA_EM, PROJETO))
  RESULT = Join[DNUM = DNUMERO](RESULT, Pi[DNUMERO, NSSGER](DEPARTAMENTO))
  RESULT = Join[NSSEMP = NSS](RESULT, Pi[NSS, SNOME](EMPREGADO))
  RESULT = Join[NSSGER = NSS](RESULT, Pi[NSS, SNOME](EMPREGADO))
  FINAL_RESULT = Pi[PNRO](Sigma[SNOME = 'Smith'](RESULT))
  ```

* Forma da apostila

  * ```
    SMITH(NSSEMP) = Pi[NSS](Sigma[SNOME = 'Smith'](EMPREGADO))
    PROJETOS_SMITH_TRABALHA = Pi[PNRO](TRABALHA_EM * SMITH)
    GERENTES = Pi[SNOME, DNUMERO](Join[NSS = NSSGER](EMPREGADO, DEPARTAMENTO))
    GERENTES_SMITH = Sigma[SNOME = 'Smith'](GERENTES)
    DEPARTAMENTOS_GERENCIADOS_SMITH(DNUM) = Pi[DNUMERO](GERENTES_SMITH)
    PROJETOS_GERENCIADOS_SMITH(PNRO) = Pi[PNUMERO](DEPARTAMENTOS_GERENCIADOS_SMITH * PROJETO)
    RESULT = Union(PROJETOS_SMITH_TRABALHA, PROJETOS_GERENCIADOS_SMITH)
    ```

### Listar nome de empregados com mais de um dependente

* ```
  T1(NSS, NUMERO_DEPENDENTES) = Function[NSSEMP, COUNT NOMEDEPENDENTE](DEPENDENTE)
  T2 = Sigma[NUMERO_DEPENDENTES >= 2](T1)
  RESULT = Pi[SNOME, PNOME](T2 * EMPREGADO)
  ```

### Listar nome de empregados sem dependentes

* ```
  TODOS_EMPREGADOS = Pi[NSS](EMPREGADO)
  EMPREGADOS_COM_DEPENDENTES(NSS) = Pi[NSSEMP](DEPENDENTE)
  EMPREGADOS_SEM_DEPENDENTES = TODOS_EMPREGADOS - EMPREGADOS_COM_DEPENDENTES
  RESULT = Pi[SNOME, PNOME](EMPREGADOS_SEM_DEPENDENTES * EMPREGADO)
  ```

### Listar nome dos gerentes com dependentes

* ```
  GERENTES(NSS) = Pi[NSSGER](DEPARTAMENTO)
  EMPREGADOS_COM_DEPENDENTES(NSS) = Pi[NSSEMP](DEPENDENTE)
  GERENTES_COM_DEPENDENTES = Intersecao(GERENTES, EMPREGADOS_COM_DEPENDENTES)
  RESULT = Pi[SNOME, PNOME](GERENTES_COM_DEPENDENTES * EMPREGADO)
  ```

