# Especificação do produto — Prisma

## Contexto

Uma empresa SaaS B2B de gestão empresarial vende também por meio de uma rede de parceiros comerciais, principalmente consultorias e empresas de tecnologia.

## Problema

À medida que a rede cresce, torna-se necessário entender quais parceiros geram valor, com que frequência produzem e quais fatores explicam sua performance.

## Objetivo do Prisma

Integrar informações comerciais e financeiras e transformá-las em uma visão confiável da performance da rede de parceiros.

## Perguntas que a V1 deve responder

- Quem são os parceiros.
- Quanto cada parceiro gerou de receita.
- Quantos negócios fechou.
- Qual seu ticket médio.
- Com que frequência produz.
- Qual seu Score e Faixa ABCD.
- Qual sua posição em relação aos demais.
- Por que recebeu determinada classificação.
- Quais parceiros ainda não possuem histórico suficiente.
- Quais problemas de dados impedem uma avaliação confiável.

## Escopo da V1

- Parceiros independentes.
- Negócios.
- Empresas clientes.
- Receita.
- Performance mensal.
- Score.
- Faixa ABCD.
- Ranking.
- Consistência de Produção.
- Qualidade dos dados.

## Fora do escopo da V1

- Hierarquias de unidades/escritórios ou estruturas equivalentes às Casas. Será tratado como evolução futura.

## Princípios

- Score e suas regras devem ser transparentes e versionados.
- Consistência de Produção compõe o Score de Performance, com peso de 15% na V1, medida na V1 pela proporção entre meses com produção e meses observáveis.
- Mês corrente não participa da avaliação.
- Parceiros novos devem receber tratamento específico.
- Problemas de qualidade devem ser identificáveis e explicáveis.
