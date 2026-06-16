# Apresentacao para Lideranca - API Testing

## Objetivo do Estudo

Desenvolver competencia pratica em **Testes de API** para contribuir com a qualidade das entregas do time, automatizando validacoes que hoje dependem de testes manuais.

---

## O que foi Aprendido

### Modulo 1 - Fundamentos de APIs REST
- Comunicacao cliente-servidor via protocolo HTTP
- Metodos HTTP e seus propositos (GET, POST, PUT, PATCH, DELETE)
- Codigos de status e tratamento de erros (2xx, 4xx, 5xx)
- Autenticacao e seguranca (API Key, Bearer Token)
- Anatomia de uma requisicao: Headers, Body, Query/Path Params

### Modulo 2 - Postman como Ferramenta de Teste
- Organizacao profissional: Workspaces, Collections, Folders
- Variaveis (global, collection, environment) para reutilizacao
- Assertions automatizadas com pm.test() e pm.expect()
- Pre-request Scripts para setup dinamico
- Data-driven testing para multiplicar cenarios com dados externos

### Modulo 3 - Projeto Pratico
- API utilizada: ReqRes (https://reqres.in)
- 17 cenarios de teste organizados em 3 categorias
- Validacoes de: status code, response time, body schema, headers
- Encadeamento de requests com variaveis dinamicas

### Modulo 4 - Versionamento e CI/CD
- Colecao exportada e versionada no GitHub
- Pipeline automatizado com GitHub Actions + Newman
- Execucao agendada (daily) e em cada push/PR
- Relatorios HTML gerados automaticamente

### Modulo 5 - Evidencias e Documentacao
- Relatorios visuais com Newman HTMLExtra Reporter
- Screenshots organizados por cenario
- Documentacao completa no repositorio

---

## Demonstracao Pratica

### Fluxo Executado

```
1. Listar usuarios (GET /users)
   -> Validar: status 200, array de usuarios, campos obrigatorios

2. Buscar usuario especifico (GET /users/:id)
   -> Validar: dados corretos do usuario, correspondencia de ID

3. Criar usuario (POST /users)
   -> Validar: status 201, ID gerado, dados retornados

4. Atualizar usuario (PUT /users/:id)
   -> Validar: status 200, dados atualizados, timestamp

5. Atualizar parcial (PATCH /users/:id)
   -> Validar: apenas campo alterado atualizado

6. Deletar usuario (DELETE /users/:id)
   -> Validar: status 204, body vazio

7. Login com sucesso (POST /login)
   -> Validar: token retornado e armazenado

8. Login sem senha (POST /login) - NEGATIVO
   -> Validar: status 400, mensagem de erro adequada
```

---

## Metricas

| Metrica                  | Valor   |
|--------------------------|---------|
| Total de Testes          | 17      |
| Happy Path               | 8       |
| Edge Cases               | 4       |
| Negative Tests           | 5       |
| Taxa de Sucesso Esperada | 100%    |
| Assertions por Teste     | 2-5     |
| Total de Assertions      | ~45     |
| Tempo Medio de Execucao  | < 15s   |

---

## Beneficios para o Time

1. **Deteccao precoce de bugs** - Testes rodam a cada push
2. **Documentacao viva** - Colecao serve como spec da API
3. **Regressao automatizada** - Nenhum teste manual repetitivo
4. **Confianca em deploys** - Pipeline barra codigo quebrado
5. **Onboarding facilitado** - Novos membros entendem a API pelos testes

---

## Proximos Passos

| Acao                                | Prazo       | Prioridade |
|-------------------------------------|-------------|------------|
| Aplicar em APIs internas do time    | 2 semanas   | Alta       |
| Adicionar testes de contrato (schema)| 3 semanas   | Media      |
| Integrar com Jira (report automatico)| 1 mes       | Media      |
| Workshop para o time                | 1 mes       | Alta       |
| Explorar testes de performance      | 2 meses     | Baixa      |

---

## Repositorio

- **GitHub**: [api-testing-project](link-do-repositorio)
- **Estrutura**: Colecao + Environments + CI/CD + Relatorios
- **Como rodar**: `newman run collections/ReqRes_API_Tests.postman_collection.json -e environments/dev.postman_environment.json`

---

## Conclusao

O estudo demonstrou que e possivel implementar uma suite de testes de API robusta com ferramentas gratuitas (Postman + Newman + GitHub Actions), trazendo **automacao**, **confiabilidade** e **documentacao** para o processo de desenvolvimento.

A proposta e expandir essa pratica para as APIs do nosso produto, comecando pelos endpoints mais criticos.
