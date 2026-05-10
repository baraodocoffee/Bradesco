# Skill: Design System — Invista com o Barão

Base de referência visual para todos os projetos do site **invistacomobarao**.
Identidade própria: dark, elegante, sofisticado. Público-alvo: investidores PF com patrimônio relevante.

---

## Identidade Visual

### Paleta de Cores

```css
:root {
  /* Primária — Gold */
  --gold:           #C9A84C;
  --gold-light:     rgba(201,168,76,0.15);
  --gold-border:    rgba(201,168,76,0.35);

  /* Fundos */
  --bg-deep:        #0D0A05;  /* fundo de página */
  --bg-dark:        #080502;  /* overlay, cards escuros */
  --bg-card:        rgba(255,255,255,0.04); /* cards sobre fundo escuro */
  --bg-card-hover:  rgba(255,255,255,0.07);

  /* Texto */
  --cream:          #F5E6C8;  /* texto principal */
  --cream-muted:    rgba(245,230,200,0.6);  /* texto secundário */
  --cream-faint:    rgba(245,230,200,0.35); /* texto auxiliar/placeholder */

  /* Bordas */
  --border:         rgba(245,230,200,0.10);
  --border-gold:    rgba(201,168,76,0.35);

  /* Status */
  --green:          #4CAF7D;
  --green-light:    rgba(76,175,125,0.15);
  --yellow:         #D4A017;
  --yellow-light:   rgba(212,160,23,0.15);
  --red:            #C0392B;
  --red-light:      rgba(192,57,43,0.15);
}
```

### Uso das Cores
- **Gold:** ações primárias, destaques, títulos em itálico, bordas de destaque, badges
- **Cream:** todo texto principal — nunca branco puro (#FFF)
- **Cream-muted:** textos secundários, subtítulos, descrições
- **Verde:** rentabilidade positiva, acima da meta, isento de IR
- **Amarelo:** resultado próximo da meta (75–99%), atenção
- **Vermelho:** queda, abaixo da meta, tributado com desvantagem
- **Fundo:** sempre `--bg-deep`; cards com `--bg-card` + borda `--border`

---

## Tipografia

### Fontes
```html
<!-- Sempre importar ambas -->
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet"/>
```

| Uso | Fonte | Peso |
|---|---|---|
| Títulos, headings, marca | Playfair Display | 700 |
| Subtítulos elegantes | Playfair Display italic | 400 italic |
| Corpo de texto | Inter | 400 |
| Labels, dados, tabelas | Inter | 500–600 |
| Badges, caps | Inter | 500 |

### Escala Tipográfica

```css
body        { font-family: 'Inter', sans-serif; font-size: 16px; line-height: 1.7; color: var(--cream-muted); background: var(--bg-deep); }
h1          { font-family: 'Playfair Display', serif; font-size: clamp(32px,5vw,64px); font-weight: 700; color: var(--cream); }
h2          { font-family: 'Playfair Display', serif; font-size: clamp(22px,3vw,36px); font-weight: 700; color: var(--cream); }
h3          { font-family: 'Playfair Display', serif; font-size: 20px; font-weight: 400; font-style: italic; color: var(--cream); }
.label-caps { font-family: 'Inter'; font-size: 11px; font-weight: 500; text-transform: uppercase; letter-spacing: 0.22em; color: var(--gold); }
.data-lg    { font-family: 'Inter'; font-size: 32px; font-weight: 600; color: var(--cream); }
.data-md    { font-family: 'Inter'; font-size: 22px; font-weight: 600; color: var(--cream); }

/* Gold italic — elemento de marca */
em, .brand-em { font-style: italic; color: var(--gold); }
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
--space-2xl:  80px

/* Border radius */
--radius-sm:  8px    /* badges, botões pequenos */
--radius-md:  12px   /* cards, inputs */
--radius-lg:  20px   /* modais, painéis */
```

---

## Elementos de Identidade

### Divisor Gold (substitui barra de identidade)

```html
<div class="divider-gold">
  <div class="divider-line"></div>
  <div class="divider-diamond"></div>
  <div class="divider-line"></div>
</div>
```

```css
.divider-gold        { display:flex; align-items:center; gap:16px; width:min(320px,80vw); margin:32px auto; }
.divider-line        { flex:1; height:1px; background:var(--border-gold); }
.divider-diamond     { width:8px; height:8px; border:1px solid var(--gold); transform:rotate(45deg); flex-shrink:0; opacity:.7; }
```

### Badge "Em breve" / status

```html
<div class="badge-status">
  <span class="badge-dot"></span>
  Em breve
</div>
```

```css
.badge-status {
  display:inline-flex; align-items:center; gap:8px;
  font-size:11px; font-weight:500; letter-spacing:.28em; text-transform:uppercase;
  color:var(--gold); border:1px solid var(--border-gold);
  border-radius:40px; padding:6px 18px;
  backdrop-filter:blur(4px);
}
.badge-dot { width:6px; height:6px; border-radius:50%; background:var(--gold); animation:pulse 2s ease-in-out infinite; }
@keyframes pulse { 0%,100%{opacity:1;transform:scale(1);} 50%{opacity:.4;transform:scale(.8);} }
```

---

## Componentes

### Card de Indicador

```html
<div class="indicador-card [destaque]">
  <div class="label-caps">CDI</div>
  <div class="valor">14,65% <span>a.a.</span></div>
</div>
```

```css
.indicador-card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: 20px 24px;
  backdrop-filter: blur(8px);
}
.indicador-card.destaque {
  border-color: var(--gold-border);
  background: var(--gold-light);
}
.indicador-card .valor      { font-size: 26px; font-weight: 600; color: var(--cream); }
.indicador-card .valor span { font-size: 13px; font-weight: 400; color: var(--cream-muted); }
```

---

### Card de Produto

**Estados:**
- `destaque-card` — rentabilidade ≥ meta (borda gold/verde)
- `alerta-card` — rentabilidade próxima da meta (borda yellow)
- padrão — neutro

```css
.produto-card          { background: var(--bg-card); border: 1px solid var(--border); border-radius: var(--radius-md); padding: 20px 24px; }
.produto-card.destaque-card { border-color: var(--green); background: var(--green-light); }
.produto-card.alerta-card   { border-color: var(--yellow); background: var(--yellow-light); }
```

---

### Badges de Produto

```html
<span class="badge badge-isento">Isento IR</span>
<span class="badge badge-tributado">IR 15%</span>
<span class="badge badge-atencao">Atenção</span>
```

```css
.badge          { font-size:11px; font-weight:500; padding:3px 10px; border-radius:20px; text-transform:uppercase; letter-spacing:.08em; font-family:'Inter'; }
.badge-isento   { background:var(--green-light); color:var(--green); border:1px solid var(--green); }
.badge-tributado{ background:var(--bg-card); color:var(--cream-muted); border:1px solid var(--border); }
.badge-atencao  { background:var(--yellow-light); color:var(--yellow); border:1px solid var(--yellow); }
```

---

### Seletor de Perfil

```css
.perfil-btn {
  padding: 10px 22px; border-radius: 8px;
  border: 1px solid var(--border); background: var(--bg-card);
  font-size: 14px; font-weight: 500; color: var(--cream-muted);
  font-family: 'Inter', sans-serif; cursor: pointer;
  transition: all 0.2s ease;
}
.perfil-btn:hover  { border-color: var(--gold); color: var(--gold); }
.perfil-btn.active { background: var(--gold-light); border-color: var(--gold); color: var(--gold); }
```

---

### Barra de Progresso com Marcador de Meta

```css
.barra-bg           { height:8px; background:var(--border); border-radius:99px; overflow:hidden; position:relative; }
.barra-fill         { height:100%; border-radius:99px; transition:width 0.4s ease; }
.barra-fill.verde   { background:var(--green); }
.barra-fill.amarelo { background:var(--yellow); }
.barra-fill.cinza   { background:var(--cream-faint); }
.meta-marker        { position:absolute; top:0; width:2px; height:100%; background:var(--gold); opacity:.8; }
```

---

### Botão Primário

```html
<button class="btn-primary">Ver ferramentas</button>
```

```css
.btn-primary {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 14px 32px; border-radius: var(--radius-sm);
  background: var(--gold); color: var(--bg-deep);
  font-family: 'Inter', sans-serif; font-size: 14px; font-weight: 600;
  letter-spacing: 0.05em; text-transform: uppercase;
  border: none; cursor: pointer;
  transition: opacity 0.2s ease;
}
.btn-primary:hover { opacity: 0.85; }

.btn-outline {
  background: transparent;
  border: 1px solid var(--border-gold);
  color: var(--gold);
}
.btn-outline:hover { background: var(--gold-light); }
```

---

### Gráfico de Rentabilidade Temporal

**Biblioteca:** Chart.js (vanilla)

**Comportamento:**
- Seletor de período: **1 / 2 / 3 / 5 / 10 anos**
- Curvas por produto, calculadas mês a mês via juros compostos
- Linha tracejada gold: meta de retorno do perfil
- Input de valor inicial (default: R$ 10.000)

**Regras de cálculo:**
- CDI/SELIC: capitalização diária em dias úteis (252 du/ano)
- Poupança: 0,5% + TR (0,131%) = 0,631% a.m.
- IR em **dias corridos**: ≤180dc → 22,5% | 181–360 → 20% | 361–720 → 17,5% | >720 → 15%
- Tesouro Selic: descontar 0,20% a.a. de custódia antes do IR

**Estilo visual (dark theme):**
- Fundo do canvas: transparente sobre `--bg-deep`
- Grid lines: `rgba(245,230,200,0.06)`
- Linhas: verde para isentos, gold para benchmarks, cinza para tributados fracos
- Linha da meta: gold tracejada, mais fina
- Tooltip: fundo `#1A1508`, borda `--border-gold`, texto `--cream`

---

### Nota de Rodapé

```html
<div class="nota">
  Simulação com fins informativos. Não constitui oferta ou recomendação de investimento.
  Rentabilidade passada não garante rentabilidade futura.
</div>
```

```css
.nota {
  padding: 16px 20px;
  background: var(--bg-card);
  border-radius: var(--radius-sm);
  border-left: 3px solid var(--border-gold);
  font-size: 12px; color: var(--cream-faint); line-height: 1.7;
}
```

---

## Responsividade

```css
@media (max-width: 640px) {
  .container { padding: 0 16px; }
  h1 { font-size: 32px; }
  /* Grid de indicadores: 1 coluna */
  /* Seletor de perfil: flex-wrap */
  /* Tabelas: scroll horizontal */
}
```

---

## Alertas de UX

- Fonte base mínima: **16px** — nunca abaixo disso
- Contraste: texto `--cream` sempre sobre fundo escuro — nunca cinza claro sobre escuro
- Valores monetários em destaque visual (tamanho e cor gold ou cream)
- Tooltips acessíveis — nunca esconder informação crítica só em hover mobile
- Preferir barras visuais e gráficos a tabelas densas
- `backdrop-filter: blur()` em cards para profundidade — verificar fallback em Safari
