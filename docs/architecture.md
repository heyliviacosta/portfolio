# Arquitetura

## Stack

- **GitHub** — versionamento.
- **VS Code** — ambiente principal de desenvolvimento.
- **Supabase** — camada de dados.
- **Vercel** — publicação das aplicações.

A tecnologia de frontend de cada produto será definida individualmente, no momento em que sua construção for iniciada.

## Dados

Todos os produtos usam exclusivamente dados sintéticos/fictícios. Nenhum dado real, código proprietário ou infraestrutura de terceiros é utilizado.

## Organização do repositório

Cada produto vive isolado em `products/<nome>/`, com seu próprio código, dados e documentação. Não há pacotes compartilhados entre produtos neste momento — serão introduzidos apenas quando houver necessidade concreta de reuso.

## Branching

- `main` — versão estável.
- `develop` — integração/desenvolvimento.
- `feature/*` — desenvolvimento das entregas.
