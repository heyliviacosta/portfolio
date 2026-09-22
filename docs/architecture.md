# Arquitetura

## Stack

- **GitHub** — versionamento.
- **VS Code** — ambiente principal de desenvolvimento.
- **Supabase** — camada de dados, compartilhada entre todos os produtos do ecossistema, conectada ao repositório via integração nativa com o GitHub (branch de produção: `main`).
- **Vercel** — publicação das aplicações.

A tecnologia de frontend de cada produto será definida individualmente, no momento em que sua construção for iniciada.

## Dados

Todos os produtos usam exclusivamente dados sintéticos/fictícios. Nenhum dado real, código proprietário ou infraestrutura de terceiros é utilizado.

O schema e as migrations do Supabase vivem em `supabase/`, na raiz do repositório, e são compartilhados entre produtos — nenhum produto implementa schema/migrations própria. A forma como os schemas/tabelas serão organizados entre produtos ainda não foi definida; essa decisão fica em aberto até que exista necessidade concreta de modelar dados.

## Organização do repositório

Cada produto vive isolado em `products/<nome>/`, com seu próprio código e documentação. Não há pacotes compartilhados entre produtos neste momento — serão introduzidos apenas quando houver necessidade concreta de reuso.

## Branching

- `main` — versão estável.
- `develop` — integração/desenvolvimento.
- `feature/*` — desenvolvimento das entregas.
