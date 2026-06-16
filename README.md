# API Testing Project - ReqRes

Projeto pratico de **Testes de API** utilizando Postman, Newman e GitHub Actions.

## Sobre o Projeto

Este repositorio contem uma suite completa de testes automatizados para a API publica [ReqRes](https://reqres.in), cobrindo:

- Happy Path (fluxos positivos)
- Edge Cases (casos de borda)
- Negative Tests (testes negativos)

## Estrutura do Repositorio

```
api-testing-project/
+-- README.md
+-- collections/
|   +-- ReqRes_API_Tests.postman_collection.json
+-- environments/
|   +-- dev.postman_environment.json
+-- test-data/
|   +-- users.csv
+-- evidences/
|   +-- screenshots/
|   +-- reports/
+-- newman-reports/
|   +-- .gitkeep
+-- docs/
|   +-- apresentacao-lider.md
+-- .github/
    +-- workflows/
        +-- api-tests.yml
```

## Como Executar

### Pre-requisitos

- Node.js (v16+)
- Newman instalado globalmente
- Newman HTMLExtra Reporter

### Instalacao

```bash
npm install -g newman newman-reporter-htmlextra
```

### Executar testes via CLI

```bash
newman run collections/ReqRes_API_Tests.postman_collection.json -e environments/dev.postman_environment.json -r htmlextra --reporter-htmlextra-export newman-reports/report.html
```

### Executar com dados externos (data-driven)

```bash
newman run collections/ReqRes_API_Tests.postman_collection.json -e environments/dev.postman_environment.json -d test-data/users.csv -r htmlextra --reporter-htmlextra-export newman-reports/report-data-driven.html
```

## Metricas de Cobertura

| Categoria       | Cenarios | Status |
|-----------------|----------|--------|
| Happy Path      | 8        | OK     |
| Edge Cases      | 4        | OK     |
| Negative Tests  | 5        | OK     |
| **Total**       | **17**   | OK     |

## Tecnologias Utilizadas

- **Postman** - Criacao e execucao de testes
- **Newman** - Execucao via CLI
- **Newman HTMLExtra** - Relatorios visuais
- **GitHub Actions** - CI/CD automatizado
- **ReqRes API** - API publica de testes

## Modulos de Estudo

1. Fundamentos - REST, HTTP, Status Codes, Autenticacao
2. Postman na Pratica - Collections, Environments, Tests
3. Projeto Pratico - Cenarios reais com ReqRes
4. Versionamento e CI - GitHub + Actions + Newman
5. Evidencias e Apresentacao - Relatorios e documentacao

## Autor

Projeto desenvolvido como estudo pratico de API Testing.

## Licenca

MIT
