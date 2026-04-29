# Skill: Parâmetros e Benchmarks de Investimentos

Base de referência para projetos de planejamento financeiro e comparativos de investimentos.
Contexto: uso interno por especialistas do Bradesco e atendimento a clientes investidores PF.

---

## Indicadores Macroeconômicos

| Indicador | Valor |
|---|---|
| SELIC | 14,75% a.a. |
| CDI | 14,65% a.a. (SELIC - 0,10%) |
| IPCA projetado (premissa padrão) | 5,00% a.a. |
| TR (premissa conservadora) | 0,131% a.m. |

---

## Convenções de Capitalização

### CDI / SELIC
- Capitalização **diária em dias úteis (du)**
- Convenção: **252 du/ano | 21 du/mês**
- Taxa diária: `(1 + taxa anual)^(1/252) - 1`
- CDI diário atual: ~0,05466% a.d.
- CDI mensal atual (21 du): ~1,1538% a.m.

### Poupança
- Capitalização **mensal em dias corridos** (data de aniversário)
- Rendimento mensal: **0,5% + TR**
- Premissa TR: **0,131% a.m.** (média conservadora 2022–2026)
- Rendimento mensal efetivo: **0,631% a.m.**
- Equivalente anual: **~7,82% a.a.**
- Sempre calcular juros compostos mês a mês — nunca converter diretamente para taxa anual sem respeitar a capitalização mensal

---

## Perfis de Investimento

| Perfil | Retorno Real (acima do IPCA) | Retorno Nominal Alvo* |
|---|---|---|
| Conservador | 4% a.a. | ~9,2% a.a. |
| Moderado | 6% a.a. | ~11,3% a.a. |
| Arrojado | 8% a.a. | ~13,4% a.a. |

*Cálculo pela fórmula de Fisher: `(1 + real) × (1 + IPCA) - 1`

---

## Horizontes Temporais

| Horizonte | Prazo |
|---|---|
| Curto prazo | Até 1 ano |
| Médio prazo | 1 a 5 anos |
| Longo prazo | Acima de 5 anos |

---

## Tributação — Renda Fixa

### IR (Imposto de Renda)
Regressivo em **dias corridos** — atenção: 720 dias corridos ≠ 2 anos.

| Prazo (dias corridos) | Alíquota IR |
|---|---|
| Até 180 dias | 22,5% |
| 181 a 360 dias | 20,0% |
| 361 a 720 dias | 17,5% |
| Acima de 720 dias | 15,0% |

**Isentos de IR para PF:** LCI, LCA, CRI, CRA, Debêntures incentivadas

### IOF
- Regressivo nos primeiros 30 dias (zerado a partir do 31º dia)
- **Sem IOF:** CRI, CRA, Debêntures (crédito privado) e LCA

---

## Prazos Mínimos

| Produto | Prazo mínimo (PF) |
|---|---|
| LCI | 9 meses |
| LCA | 12 meses |

---

## FGC — Fundo Garantidor de Créditos

- Limite por CPF por instituição: **R$ 250.000**
- Teto total por CPF: **R$ 1.000.000** (renovável a cada 4 anos)

**Cobertos pelo FGC:** CDB, LCI, LCA, Poupança, LC, LH

**Não cobertos:** CRI, CRA, Debêntures, Fundos de Investimento
**Tesouro Direto:** não tem FGC — garantia do Tesouro Nacional (risco soberano)

---

## Benchmark Comparativo de Produtos

### Produtos Bradesco

| Produto | Rentabilidade | Equiv. Anual Bruto | Equiv. Mensal Bruto | IR | IOF |
|---|---|---|---|---|---|
| Invest Fácil | 5% do CDI | ~0,73% a.a. | ~0,061% a.m. | Sim | Sim |
| CDB Baixa Automática | 50% do CDI | ~7,33% a.a. | ~0,577% a.m. | Sim | Sim |
| LCA DI | 87% do CDI | ~12,75% a.a. | ~1,004% a.m. | Não | Não |
| CDB DI | 100% do CDI | ~14,65% a.a. | ~1,154% a.m. | Sim | Sim |

### Referências de Mercado

| Produto | Rentabilidade | Equiv. Anual Bruto | Equiv. Mensal Bruto | IR | IOF | Custódia |
|---|---|---|---|---|---|---|
| Poupança | 0,5% a.m. + TR | ~7,82% a.a. | ~0,631% a.m. | Não | Não | Não |
| Tesouro Selic | ~100% SELIC | ~14,55% a.a.* | ~1,142% a.m.* | Sim | Não | 0,20% a.a. (B3) |

*Já descontada a taxa de custódia de 0,20% a.a. — sempre descontar antes de comparativos.
Tesouro Selic capitaliza diariamente em dias úteis (mesma convenção do CDI).

---

## Alertas para Modelos e Cálculos

- **IR em dias corridos:** 720 dias corridos ≠ 2 anos — erro comum em modelos
- **Poupança:** sempre usar capitalização mensal, nunca taxa anual direta
- **TR:** não é insignificante — usar premissa de 0,131% a.m.
- **Tesouro Direto:** sempre descontar 0,20% a.a. de custódia antes de comparar
- **LCA no secundário:** pode servir como liquidez mesmo sem ser produto de liquidez diária
- **Isenção vs tributado:** LCA DI a 87% CDI equivale a ~102,4% CDI bruto para prazo acima de 720 dias corridos (IR 15%)
