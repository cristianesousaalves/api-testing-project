# Manual de Execucao - Testes de API Open Library

## Pre-requisitos

- Node.js (v18+)
- Newman instalado globalmente
- Postman (opcional, para execucao visual)

## Instalacao

```bash
npm install -g newman newman-reporter-htmlextra
```

## Executar pelo terminal (Newman)

```bash
newman run collections/OpenLibrary_API_Tests.postman_collection.json \
  -e environments/openlibrary.postman_environment.json \
  -r cli,htmlextra \
  --reporter-htmlextra-export evidencias/relatorio.html
```

## Executar pelo Postman

1. Abra o Postman;
2. Importe a colecao: `collections/OpenLibrary_API_Tests.postman_collection.json`;
3. Importe o environment: `environments/openlibrary.postman_environment.json`;
4. Selecione o environment "Open Library" no canto superior direito;
5. Clique na colecao > Run > Start run.

## Gerar relatorio JSON

```bash
newman run collections/OpenLibrary_API_Tests.postman_collection.json \
  -e environments/openlibrary.postman_environment.json \
  -r json \
  --reporter-json-export evidencias/relatorio.json
```

## Estrutura do Projeto

```
api-testing-project/
+-- .github/workflows/api-tests.yml
+-- collections/OpenLibrary_API_Tests.postman_collection.json
+-- environments/openlibrary.postman_environment.json
+-- docs/
|   +-- APRESENTACAO.md
|   +-- MANUAL.md
|   +-- casos-de-teste.md
+-- evidencias/
|   +-- relatorio.html
|   +-- relatorio.json
+-- .gitignore
+-- README.md
+-- package.json
```
