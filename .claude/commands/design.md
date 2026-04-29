# Skill: Design System — Ferramentas de Planejamento Financeiro

Base de referência visual para todos os projetos web do repositório.
Identidade inspirada no Bradesco — sem uso de marca, logo ou nome oficial.
Público-alvo: clientes investidores PF, predominantemente 50+. Estilo: elegante, limpo, didático e visual.

---

## Identidade Visual

### Paleta de Cores

```css
:root {
  /* Primária — Bradesco */
  --red:          #CC1417;
  --red-dark:     #A50F11;
  --red-light:    #F9E5E5;

  /* Neutros */
  --gray-900:     #1A1A1A;  /* texto principal */
  --gray-700:     #3D3D3D;  /* texto secundário forte */
  --gray-500:     #6B6B6B;  /* texto auxiliar */
  --gray-200:     #E8E8E8;  /* bordas */
  --gray-100:     #F5F5F5;  /* fundo de página */
  --white:        #FFFFFF;  /* fundo de cards */

  /* Status — positivo */
  --green:        #1A7F4B;
  --green-light:  #E6F4ED;

  /* Status — atenção */
  --yellow:       #B97500;
  --yellow-light: #FFF4DC;
}
```

### Uso das Cores
- **Vermelho:** ações primárias, destaques, elementos ativos, barra de identidade no topo
- **Verde:** produto/resultado acima da meta, isento de IR, FGC coberto
- **Amarelo:** produto/resultado próximo da meta (75–99%), atenção
- **Cinza escuro:** todo texto principal — nunca usar preto puro (#000)
- **Fundo de página:** `--gray-100` | **Fundo de cards:** `--white`

---

## Tipografia

### Fontes
```html
<!-- Sempre importar ambas -->
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
```

| Uso | Fonte | Peso |
|---|---|---|
| Títulos, headings, UI | Plus Jakarta Sans | 600–700 |
| Subtítulos, labels | Plus Jakarta Sans | 500 |
| Corpo de texto | Inter | 400 |
| Tabelas, números, dados | Inter | 400–600 |
| Badges, labels pequenos | Inter | 600 |

### Escala Tipográfica

```css
/* Base: 17px — otimizado para público 50+ */
body        { font-family: 'Inter', sans-serif; font-size: 17px; line-height: 1.6; }
h1          { font-family: 'Plus Jakarta Sans', sans-serif; font-size: 30px; font-weight: 700; }
h2          { font-family: 'Plus Jakarta Sans', sans-serif; font-size: 22px; font-weight: 700; }
h3          { font-family: 'Plus Jakarta Sans', sans-serif; font-size: 18px; font-weight: 600; }
.label-caps { font-family: 'Inter'; font-size: 12px; font-weight: 600; text-transform: uppercase; letter-spacing: 0.08em; color: var(--gray-500); }
.data-lg    { font-family: 'Inter'; font-size: 28px; font-weight: 700; }
.data-md    { font-family: 'Inter'; font-size: 22px; font-weight: 700; }
```

---

## Espaçamento e Grid

```css
/* Grid principal */
.container  { max-width: 960px; margin: 0 auto; padding: 0 24px; }

/* Espaçamentos padrão */
--space-xs:   8px
--space-sm:   12px
--space-md:   20px
--space-lg:   32px
--space-xl:   48px

/* Border radius */
--radius-sm:  8px   /* badges, botões pequenos */
--radius-md:  12px  /* cards, inputs */
--radius-lg:  16px  /* modais, painéis */
```

---

## Barra de Identidade

Substitui o header com logo. Linha vermelha fina no topo da página — referência de identidade sem uso de marca.

```html
<div style="height:5px; background:#CC1417;"></div>
```

---

## Componentes

### Card de Indicador
Cards de métricas no topo (CDI, SELIC, IPCA, etc.)

```html
<div class="indicador-card [destaque]">
  <div class="label">CDI</div>
  <div class="valor">14,65% <span>a.a.</span></div>
</div>
```

```css
.indicador-card {
  background: var(--white);
  border-radius: 12px;
  padding: 20px 24px;
  border: 1px solid var(--gray-200);
  box-shadow: 0 1px 4px rgba(0,0,0,0.04);
}
.indicador-card.destaque {
  border-color: var(--red);
  background: var(--red-light);
}
.indicador-card .label { /* usar .label-caps */ }
.indicador-card .valor { font-size: 26px; font-weight: 700; }
.indicador-card .valor span { font-size: 14px; font-weight: 400; color: var(--gray-500); }
```

---

### Card de Produto
Exibe produto financeiro com barra de rentabilidade e marcador de meta.

**Estados:**
- `destaque-card` — rentabilidade ≥ meta (borda verde)
- `alerta-card` — rentabilidade muito abaixo (borda amarela)
- padrão — neutro

**Regras de cor da barra:**
- Verde → `liquido >= meta`
- Amarelo → `liquido >= meta * 0.75`
- Cinza → abaixo de 75% da meta

```css
.produto-card          { background: var(--white); border: 1px solid var(--gray-200); border-radius: 12px; padding: 20px 24px; }
.produto-card.destaque-card { border-color: var(--green); background: var(--green-light); }
.produto-card.alerta-card   { border-color: var(--yellow); background: var(--yellow-light); }
```

---

### Badges

```html
<span class="badge badge-isento">Isento IR</span>
<span class="badge badge-tributado">IR 15%</span>
<span class="badge badge-atencao">Atenção</span>
```

```css
.badge          { font-size: 11px; font-weight: 600; padding: 3px 8px; border-radius: 20px; text-transform: uppercase; letter-spacing: 0.05em; font-family: 'Inter'; }
.badge-isento   { background: var(--green-light); color: var(--green); border: 1px solid var(--green); }
.badge-tributado{ background: var(--gray-100); color: var(--gray-500); border: 1px solid var(--gray-200); }
.badge-atencao  { background: var(--yellow-light); color: var(--yellow); border: 1px solid var(--yellow); }
```

---

### Seletor de Perfil

```html
<button class="perfil-btn [active]">Conservador</button>
<button class="perfil-btn [active]">Moderado</button>
<button class="perfil-btn [active]">Arrojado</button>
```

```css
.perfil-btn {
  padding: 10px 22px; border-radius: 8px;
  border: 2px solid var(--gray-200); background: var(--white);
  font-size: 14px; font-weight: 600; color: var(--gray-500);
  font-family: 'Plus Jakarta Sans', sans-serif; cursor: pointer;
}
.perfil-btn:hover  { border-color: var(--red); color: var(--red); }
.perfil-btn.active { background: var(--red); border-color: var(--red); color: var(--white); }
```

---

### Barra de Progresso com Marcador de Meta

```html
<div class="barra-bg" style="position:relative">
  <div class="barra-fill verde" style="width: X%"></div>
  <div class="meta-marker" style="left: Y%"></div>
</div>
```

```css
.barra-bg        { height: 10px; background: var(--gray-200); border-radius: 99px; overflow: hidden; }
.barra-fill      { height: 100%; border-radius: 99px; transition: width 0.4s ease; }
.barra-fill.verde   { background: var(--green); }
.barra-fill.amarelo { background: #E8A000; }
.barra-fill.cinza   { background: var(--gray-500); }
.meta-marker     { position: absolute; top: 0; width: 2px; height: 100%; background: var(--red); opacity: 0.7; }
```

---

### Gráfico de Rentabilidade Temporal

Componente interativo de curvas de crescimento patrimonial por produto.

**Biblioteca:** Recharts (React) ou Chart.js (vanilla)

**Comportamento:**
- Seletor de período pelo usuário: **1 / 2 / 3 / 5 / 10 anos**
- Gráfico se ajusta dinamicamente ao período selecionado
- Curvas individuais por produto, calculadas mês a mês via juros compostos
- Linha tracejada vermelha: meta de retorno do perfil selecionado
- Input de valor inicial (default: R$ 10.000) para exibir R$ absolutos

**Regras críticas de cálculo:**
- CDI/SELIC: capitalização diária em dias úteis (252 du/ano, 21 du/mês)
- Poupança: capitalização mensal (0,5% + TR 0,131% = 0,631% a.m.)
- IR aplicado em **dias corridos** — não em anos:
  - Até 180 dc → 22,5%
  - 181–360 dc → 20,0%
  - 361–720 dc → 17,5%
  - Acima de 720 dc → 15,0% ← já válido antes de completar 2 anos
- Tesouro Selic: descontar 0,20% a.a. de custódia antes do IR

**Estilo visual:**
- Linha mais espessa para o produto em destaque (≥ meta)
- Paleta de linhas: verde para isentos, vermelho para tributados, cinza para benchmarks fracos
- Tooltip ao hover mostrando valor acumulado e rentabilidade no período

---

### Nota de Rodapé Padrão

Usar em todas as ferramentas com cálculo de rentabilidade:

```html
<div class="nota">
  Simulação com fins informativos. Não constitui oferta ou recomendação de investimento.
  Rentabilidade passada não garante rentabilidade futura.
</div>
```

```css
.nota {
  padding: 16px 20px; background: var(--white);
  border-radius: 10px; border-left: 4px solid var(--red);
  font-size: 13px; color: var(--gray-500); line-height: 1.6;
}
```

---

## Responsividade

```css
@media (max-width: 640px) {
  .container { padding: 0 16px; }
  /* Grid de indicadores: 1 coluna */
  /* Seletor de perfil: flex-wrap */
  /* Tabelas: scroll horizontal */
  /* Font-size h1: 24px */
}
```

---

## Alertas de UX para Público 50+

- Fonte base mínima: **17px** — nunca abaixo disso
- Contraste alto: texto principal sempre sobre fundo branco ou `--gray-100`
- Evitar informação densa sem hierarquia clara
- Valores monetários sempre em destaque visual (tamanho e peso)
- Tooltips e explicações acessíveis via hover/tap — nunca esconder informação crítica só em hover
- Preferir barras visuais e gráficos a tabelas densas quando possível
