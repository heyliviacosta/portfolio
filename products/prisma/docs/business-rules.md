# Metodologia funcional V1 — Prisma

## 1. Janela de avaliação

- Utilizar os últimos 12 meses completos móveis.
- O mês corrente nunca participa da avaliação.
- A janela representa a performance estrutural do parceiro.
- Tendência recente é uma dimensão futura e não compõe a V1.

## 2. Elegibilidade analítica

Existem quatro estados:

- **Elegível**: possui pelo menos 90 dias desde o cadastro, já possui produção e não apresenta problema crítico de qualidade que impeça a avaliação.
- **Novo**: possui menos de 90 dias desde o cadastro.
- **Sem produção**: possui pelo menos 90 dias desde o cadastro e nunca teve negócio ganho.
- **Dados inconsistentes**: possui problema crítico de qualidade que impede cálculo confiável.

Apenas parceiros Elegíveis participam de Score, Faixa ABCD e ranking.

## 3. Score de Performance

O Score possui quatro dimensões:

| Dimensão | Peso |
|---|---|
| Receita realizada | 45% |
| Negócios ganhos | 25% |
| Ticket médio contratado | 15% |
| Consistência de Produção | 15% |

Cada dimensão é normalizada para uma nota relativa por percentil da população elegível.

O Score final é a soma ponderada das quatro notas normalizadas.

Os indicadores absolutos devem permanecer disponíveis para interpretação. O percentil representa posição relativa e não substitui a métrica original.

## 4. Receita realizada

- A fonte conceitual da receita é o financeiro.
- Considerar receita efetivamente reconhecida no período.
- Receita contratada e receita realizada são conceitos distintos.

## 5. Negócios ganhos

- A fonte conceitual do resultado comercial é o CRM.
- Apenas oportunidades efetivamente ganhas são contabilizadas.
- Oportunidades abertas, perdidas ou apenas criadas não compõem o indicador.

## 6. Ticket médio

Calcular:

```
Ticket médio = valor total contratado dos negócios ganhos / quantidade de negócios ganhos
```

Não utilizar receita reconhecida no cálculo do Ticket Médio.

## 7. Consistência de Produção

Calcular:

```
Consistência = meses com pelo menos um negócio que gerou receita / meses observáveis
```

Os meses observáveis são limitados à janela de avaliação e ao período em que o parceiro já fazia parte da rede.

A taxa absoluta de consistência deve permanecer disponível ao usuário. Para composição do Score, a taxa é convertida em percentil dentro da população elegível.

## 8. Faixas ABCD

As faixas representam posição relativa dentro da população elegível:

| Faixa | Distribuição |
|---|---|
| A | Top 20% |
| B | 20% seguintes |
| C | 30% seguintes |
| D | 30% inferiores |

Faixa não representa julgamento absoluto de qualidade do parceiro.

## 9. Ranking

- Ranking geral baseado no Score final.
- Apenas parceiros elegíveis participam.
- Parceiros com Score efetivamente igual compartilham a mesma posição.
- Não criar desempate artificial.
- Empates podem gerar posições subsequentes puladas.
- Rankings/posições relativas por dimensão também podem ser calculados para explicar a performance.
- O ranking é informação de posicionamento, não o elemento principal da avaliação.

## 10. Precisão

- Cálculos devem preservar precisão suficiente internamente.
- Arredondamento é uma decisão de apresentação.
- Valores que aparecem iguais após arredondamento não devem ser considerados empatados se os valores calculados forem diferentes.

## 11. Atividade comercial

Atividade comercial e performance financeira são conceitos distintos.

- **Inativo**: parceiro que já produziu anteriormente, mas está há 120 dias sem nenhum negócio ganho.
- A existência de receita proveniente de contratos antigos não mantém o parceiro comercialmente ativo.
- Parceiros inativos deixam de participar da população elegível enquanto permanecerem inativos.

## 12. Reativação

- Um parceiro inativo é reativado quando volta a possuir um negócio ganho.
- Retorna imediatamente à elegibilidade, desde que cumpra os demais critérios.
- Permanece sinalizado como Reativado durante 90 dias após a retomada.
- Após esse período, volta à condição normal de ativo.

## 13. Estados independentes

Não utilizar um único status para representar conceitos diferentes.

Manter conceitualmente separados:

- Situação cadastral.
- Atividade comercial: ativo, inativo ou reativado.
- Elegibilidade analítica: elegível, novo, sem produção ou dados inconsistentes.

## 14. Qualidade dos dados

Problemas de qualidade possuem dois níveis:

- **Crítico**: compromete identidade, atribuição da produção ou confiabilidade das métricas. Bloqueia Score, ABCD e ranking.
- **Alerta**: problema existente que não compromete materialmente o cálculo. Não bloqueia avaliação.

Todo bloqueio deve possuir motivo identificável e rastreável.

O Prisma não deve produzir classificação quando os dados necessários para sustentá-la não forem confiáveis.

## 15. Explicabilidade

A explicação do Score deve ser determinística.

Deve ser possível identificar:

- Dimensões que mais contribuíram positivamente.
- Dimensões que mais limitaram o resultado.
- Posição relativa em cada dimensão.
- Situação de consistência.

IA não determina a justificativa da classificação. Futuramente pode ser utilizada apenas como camada de linguagem sobre fatos previamente calculados pelo motor analítico.

## 16. Parametrização

Parâmetros dependentes do contexto comercial não devem ficar fixos na lógica.

Parâmetros iniciais da V1 incluem:

- Parceiro novo: 90 dias.
- Inatividade: 120 dias.
- Período de sinalização como reativado: 90 dias.
- Janela de avaliação: 12 meses.
- Pesos do Score: 45/25/15/15.
- Distribuição ABCD: 20/20/30/30.

A metodologia define como avaliar. Os parâmetros adaptam essa metodologia ao contexto da operação.

Nem toda regra é parametrizável. Princípios estruturais, como a separação entre resultado comercial e receita realizada ou a exigência de elegibilidade para participar do Score, pertencem à metodologia.

## 17. Versionamento

Alterações de regras ou parâmetros não devem sobrescrever silenciosamente configurações anteriores.

Separar conceitualmente:

- **Versão da metodologia**: alterações na lógica estrutural de avaliação.
- **Versão da configuração**: alterações nos parâmetros da metodologia.

Cada configuração deve possuir vigência identificável.

Resultados analíticos devem manter referência à metodologia e configuração utilizadas em seu cálculo.

Alterações futuras não devem modificar silenciosamente a interpretação histórica de resultados já produzidos.

**Princípio**: todo resultado do Prisma deve ser reproduzível a partir dos dados, metodologia e configuração vigentes no momento do cálculo.

## 18. Princípios metodológicos da V1

- Performance é relativa à população elegível.
- Métrica absoluta e posição relativa são informações complementares.
- Ausência de informação confiável não equivale a baixa performance.
- Atividade comercial não é determinada por receita financeira residual.
- Classificação deve ser explicável e reproduzível.
- Regras contextuais devem ser parametrizáveis.
- Histórico não deve ser reinterpretado silenciosamente após mudança de metodologia.
