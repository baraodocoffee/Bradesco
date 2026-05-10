# Skill: Design System — Invista com o Barão

Base de referência visual para todos os projetos do site **invistacomobarao**.
Identidade: dark/gold elegante com suporte a modo claro. Público-alvo: investidores PF com patrimônio relevante.

---

## Identidade Visual

### Paleta de Cores

```css
:root {
  /* Primária — Gold */
  --gold:           #C9A84C;
  --gold-light:     rgba(201,168,76,0.12);
  --gold-border:    rgba(201,168,76,0.35);

  /* Fundos */
  --bg-deep:        #0D0A05;
  --bg-dark:        #080502;
  --bg-card:        rgba(255,255,255,0.04);
  --bg-card-hover:  rgba(255,255,255,0.07);

  /* Texto */
  --cream:          #F5E6C8;
  --cream-muted:    rgba(245,230,200,0.6);
  --cream-faint:    rgba(245,230,200,0.35);

  /* Bordas */
  --border:         rgba(245,230,200,0.10);
  --border-gold:    rgba(201,168,76,0.35);

  /* Status */
  --green:          #4CAF7D;
  --green-light:    rgba(76,175,125,0.12);
  --yellow:         #D4A017;
  --yellow-light:   rgba(212,160,23,0.12);
  --blue:           #5B8FD4;
  --blue-light:     rgba(91,143,212,0.12);
  --red:            #C0392B;
  --red-light:      rgba(192,57,43,0.12);
}
```

### Modo Claro — override em `body.light`

```css
body.light {
  --bg-deep:        #F5EFE3;
  --bg-dark:        #EDE4D3;
  --bg-card:        rgba(255,255,255,0.75);
  --bg-card-hover:  rgba(255,255,255,0.95);
  --cream:          #2A1F0A;
  --cream-muted:    rgba(42,31,10,0.72);
  --cream-faint:    rgba(42,31,10,0.45);
  --border:         rgba(42,31,10,0.12);
  --border-gold:    rgba(201,168,76,0.5);
  --green:          #1A7F4B;
  --green-light:    rgba(26,127,75,0.10);
  --yellow:         #A06800;
  --yellow-light:   rgba(160,104,0,0.10);
  --blue:           #1A5FA5;
  --blue-light:     rgba(26,95,165,0.10);
}
```

### Uso das Cores
- **Gold:** ações primárias, destaques, títulos em itálico, bordas de destaque, badges
- **Cream:** todo texto principal — nunca branco puro (#FFF)
- **Cream-muted:** textos secundários, subtítulos, descrições
- **Verde:** rentabilidade positiva, acima da meta, isento de IR, ciclos de queda de juros
- **Amarelo:** resultado próximo da meta (75–99%), atenção
- **Azul:** dados informativos neutros (juro real, métricas de contexto)
- **Vermelho/Gold:** destaque principal, taxa atual, dado de maior relevância
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
| Badges, caps, ctrl-label | Inter | 500 |

### Escala Tipográfica

```css
body        { font-family: 'Inter', sans-serif; font-size: 16px; line-height: 1.7; color: var(--cream-muted); background: var(--bg-deep); transition: background .3s, color .3s; }
h1          { font-family: 'Playfair Display', serif; font-size: clamp(32px,5vw,64px); font-weight: 700; color: var(--cream); }
h2          { font-family: 'Playfair Display', serif; font-size: clamp(22px,3vw,36px); font-weight: 700; color: var(--cream); }
h3          { font-family: 'Playfair Display', serif; font-size: 20px; font-weight: 400; font-style: italic; color: var(--cream); }
.label-caps { font-family: 'Inter'; font-size: 10px; font-weight: 500; text-transform: uppercase; letter-spacing: 0.22em; color: var(--gold); }
.data-lg    { font-family: 'Inter'; font-size: 28px; font-weight: 600; color: var(--cream); line-height: 1.1; }
.data-md    { font-family: 'Inter'; font-size: 22px; font-weight: 600; color: var(--cream); }

/* Gold italic — elemento de marca */
em, .brand-em { font-style: italic; color: var(--gold); }
```

---

## Espaçamento e Grid

```css
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

## Favicon SVG Inline

Padrão de favicon sem arquivo externo — inserir no `<head>`:

```html
<link rel="icon" type="image/svg+xml" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 32 32'><rect width='32' height='32' rx='6' fill='%230D0A05'/><text x='16' y='23' text-anchor='middle' font-family='Georgia,serif' font-size='22' font-weight='700' fill='%23C9A84C'>B</text></svg>"/>
```

---

## Hero Background com Overlay

Padrão para páginas com imagem de fundo. O overlay escurece no dark e clareia no light:

```html
<div class="hero-bg"></div>
<div class="hero-overlay"></div>
```

```css
.hero-bg {
  position: fixed; inset: 0; z-index: 0;
  background: url('hero.jpg') center center / cover no-repeat;
  transition: opacity .3s;
}
body.light .hero-bg { opacity: 0.18; }

.hero-overlay {
  position: fixed; inset: 0; z-index: 1;
  background: linear-gradient(to bottom, rgba(8,5,2,0.72) 0%, rgba(8,5,2,0.82) 50%, rgba(8,5,2,0.92) 100%);
  transition: background .3s;
}
body.light .hero-overlay {
  background: linear-gradient(to bottom, rgba(245,239,227,0.92) 0%, rgba(245,239,227,0.96) 50%, rgba(245,239,227,0.98) 100%);
}

/* Conteúdo acima das camadas fixas */
.page-header, .container { position: relative; z-index: 2; }
```

---

## Page Header Sticky

Header fixo no topo com título, subtítulo e navegação. Bege/dourado no modo claro:

```html
<div class="page-header">
  <div class="page-header-left">
    <h1>Título da Página</h1>
    <p id="page-subtitle">Descrição contextual</p>
  </div>
  <div style="display:flex;align-items:center;gap:12px;">
    <button class="theme-btn" id="theme-btn" onclick="toggleTheme()" title="Alternar tema">
      <span id="theme-label">Modo escuro</span>
      <span class="theme-btn-emoji" id="theme-icon">🌙</span>
    </button>
    <a href="../" class="nav-back">← Início</a>
  </div>
</div>
```

```css
.page-header {
  background: rgba(8,5,2,0.85);
  border-bottom: 1px solid var(--border);
  padding: 18px 24px;
  display: flex; align-items: center; justify-content: space-between;
  margin-bottom: 28px;
  backdrop-filter: blur(12px);
  position: sticky; top: 0; z-index: 10;
}
body.light .page-header {
  background: rgba(240,232,215,0.95);
  border-bottom-color: rgba(201,168,76,0.4);
}
.page-header-left h1 {
  font-family: 'Playfair Display', serif;
  font-size: 20px; font-weight: 700;
  color: var(--cream); letter-spacing: .01em;
}
.page-header-left p { font-size: 12px; color: var(--cream-faint); margin-top: 3px; letter-spacing: .02em; }

.nav-back {
  font-size: 12px; font-weight: 500;
  color: var(--cream-faint); text-decoration: none;
  display: flex; align-items: center; gap: 6px;
  letter-spacing: .05em; text-transform: uppercase;
  transition: color .15s;
}
.nav-back:hover { color: var(--gold); }
```

---

## Toggle Dark / Light Mode

### Botão

```css
.theme-btn {
  background: none; border: 1px solid var(--border-gold);
  color: var(--gold); border-radius: 8px; padding: 6px 14px;
  font-size: 13px; font-weight: 500; font-family: 'Inter', sans-serif;
  cursor: pointer; display: flex; align-items: center; gap: 6px;
  transition: all .15s; line-height: 1; letter-spacing: .01em;
}
.theme-btn:hover { background: var(--gold-light); }
.theme-btn-emoji { font-size: 15px; line-height: 1; }
```

### JavaScript — padrão completo

**Regra:** modo claro é o **default**. Dark fica salvo em `localStorage` quando escolhido.

```javascript
function setThemeUI(isLight) {
  document.getElementById('theme-label').textContent = isLight ? 'Modo escuro' : 'Modo claro';
  document.getElementById('theme-icon').textContent  = isLight ? '🌙' : '☀️';
}

function toggleTheme() {
  const isLight = document.body.classList.toggle('light');
  setThemeUI(isLight);
  localStorage.setItem('theme', isLight ? 'light' : 'dark');
  applyChartTheme(isLight); // só se houver Chart.js na página
}

function initTheme() {
  const saved = localStorage.getItem('theme');
  const isLight = saved !== 'dark'; // padrão: modo claro
  if (isLight) document.body.classList.add('light');
  setThemeUI(isLight);
  applyChartTheme(isLight); // só se houver Chart.js na página
}
```

---

## Elementos de Identidade

### Divisor Gold

```html
<div class="divider-gold">
  <div class="divider-line"></div>
  <div class="divider-diamond"></div>
  <div class="divider-line"></div>
</div>
```

```css
.divider-gold    { display:flex; align-items:center; gap:16px; width:min(320px,80vw); margin:32px auto; }
.divider-line    { flex:1; height:1px; background:var(--border-gold); }
.divider-diamond { width:8px; height:8px; border:1px solid var(--gold); transform:rotate(45deg); flex-shrink:0; opacity:.7; }
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

### Barra de Controles

```html
<div class="controls">
  <div class="ctrl-group">
    <span class="ctrl-label">Período</span>
    <button class="periodo-btn active" data-anos="0" onclick="setPeriodo(0)">Desde 2010</button>
    <button class="periodo-btn" data-anos="5" onclick="setPeriodo(5)">5 anos</button>
  </div>
  <div class="toggle-wrap">
    <span class="toggle-label">Exibir IPCA</span>
    <label class="toggle">
      <input type="checkbox" id="toggle-ipca" onchange="toggleIPCA()"/>
      <div class="toggle-track"></div>
      <div class="toggle-thumb"></div>
    </label>
  </div>
</div>
```

```css
.controls {
  background: var(--bg-card); border: 1px solid var(--border);
  border-radius: 12px; padding: 16px 22px; margin-bottom: 20px;
  display: flex; align-items: center; flex-wrap: wrap; gap: 16px;
  backdrop-filter: blur(8px);
}
.ctrl-group { display: flex; align-items: center; gap: 10px; }
.ctrl-label {
  font-size: 10px; font-weight: 500; color: var(--gold);
  font-family: 'Inter'; text-transform: uppercase; letter-spacing: .22em;
}
.periodo-btn {
  padding: 6px 16px; border-radius: 8px;
  border: 1px solid var(--border); background: transparent;
  font-size: 13px; font-weight: 500; color: var(--cream-muted);
  font-family: 'Inter', sans-serif; cursor: pointer; transition: all .15s;
}
.periodo-btn:hover  { border-color: var(--border-gold); color: var(--gold); }
.periodo-btn.active { background: var(--gold-light); border-color: var(--gold); color: var(--gold); }

.toggle-wrap  { display: flex; align-items: center; gap: 10px; margin-left: auto; }
.toggle-label { font-size: 13px; font-weight: 500; color: var(--cream-muted); font-family: 'Inter'; }
.toggle       { position: relative; width: 44px; height: 24px; cursor: pointer; }
.toggle input { opacity: 0; width: 0; height: 0; }
.toggle-track { position: absolute; inset: 0; background: var(--border); border-radius: 24px; transition: .2s; }
.toggle input:checked + .toggle-track { background: var(--border-gold); }
.toggle-thumb { position: absolute; top: 3px; left: 3px; width: 18px; height: 18px; background: var(--cream-faint); border-radius: 50%; transition: .2s; box-shadow: 0 1px 3px rgba(0,0,0,.4); }
.toggle input:checked ~ .toggle-thumb { left: 23px; background: var(--gold); }
```

---

### Card de Gráfico Chart.js

```html
<div class="chart-card">
  <div class="chart-header">
    <div class="chart-title">Título do Gráfico</div>
    <div class="legenda" id="legenda">
      <div class="leg-item"><div class="leg-selic"></div> SELIC</div>
    </div>
  </div>
  <div class="chart-wrap"><canvas id="chart"></canvas></div>
</div>
<div class="chart-footer">
  <span class="chart-fonte">Fonte: Banco Central do Brasil · IBGE</span>
  <button class="btn-pdf" id="btn-pdf" onclick="gerarPDF()">📄 Gerar PDF</button>
</div>
```

```css
.chart-card {
  background: var(--bg-card); border: 1px solid var(--border);
  border-radius: 14px; padding: 28px 24px 20px;
  margin-bottom: 12px; backdrop-filter: blur(8px);
}
.chart-header  { display: flex; align-items: flex-start; justify-content: space-between; margin-bottom: 20px; flex-wrap: wrap; gap: 12px; }
.chart-title   { font-family: 'Playfair Display', serif; font-size: 18px; font-weight: 700; color: var(--cream); }
.legenda       { display: flex; gap: 20px; flex-wrap: wrap; align-items: center; }
.leg-item      { display: flex; align-items: center; gap: 7px; font-size: 12px; font-weight: 500; color: var(--cream-muted); }
.leg-selic     { width: 28px; height: 3px; background: var(--gold); border-radius: 2px; }
.leg-ipca      { width: 28px; height: 0; border-top: 2.5px dashed var(--cream-muted); }
.chart-wrap    { position: relative; height: 380px; }
.chart-footer  { display: flex; align-items: center; justify-content: space-between; margin-top: 12px; margin-bottom: 28px; }
.chart-fonte   { font-size: 11px; color: var(--cream-faint); letter-spacing: .02em; }
```

#### Configuração Chart.js com suporte a dark/light

```javascript
const chart = new Chart(ctx, {
  type: 'line',
  data: { labels: [], datasets: [] },
  options: {
    responsive: true, maintainAspectRatio: false,
    interaction: { mode: 'index', intersect: false },
    plugins: {
      legend: { display: false },
      tooltip: {
        backgroundColor: '#1A1508',
        borderColor: 'rgba(201,168,76,0.35)', borderWidth: 1,
        titleColor: '#F5E6C8', bodyColor: 'rgba(245,230,200,0.6)',
        padding: 14, cornerRadius: 10,
        filter: item => item.parsed.y !== null,
        callbacks: {
          label(c) { return ` ${c.dataset.label}: ${c.parsed.y.toFixed(2).replace('.',',')}%`; }
        }
      }
    },
    scales: {
      x: {
        grid: { color: 'rgba(245,230,200,0.06)' },
        ticks: { font: { family: 'Inter', size: 11 }, color: 'rgba(245,230,200,0.35)', maxRotation: 0 }
      },
      y: {
        grid: { color: 'rgba(245,230,200,0.06)' },
        ticks: { font: { family: 'Inter', size: 12 }, color: 'rgba(245,230,200,0.35)' },
        min: 0
      }
    }
  }
});

// Atualiza cores do gráfico ao trocar tema
function applyChartTheme(isLight) {
  const gridColor = isLight ? 'rgba(42,31,10,0.08)' : 'rgba(245,230,200,0.06)';
  const tickColor = isLight ? 'rgba(42,31,10,0.5)'  : 'rgba(245,230,200,0.35)';

  chart.options.scales.x.grid.color  = gridColor;
  chart.options.scales.y.grid.color  = gridColor;
  chart.options.scales.x.ticks.color = tickColor;
  chart.options.scales.y.ticks.color = tickColor;

  // Linha secundária (ex: IPCA): cinza mais grossa no claro, cream translúcido no escuro
  if (chart.data.datasets[1]) {
    chart.data.datasets[1].borderColor = isLight ? 'rgba(90,85,80,0.75)' : 'rgba(245,230,200,0.5)';
    chart.data.datasets[1].borderWidth = isLight ? 3 : 2;
  }
  chart.update('none');
}

// Ao criar datasets, respeitar tema corrente
function buildDatasets() {
  const isLight = document.body.classList.contains('light');
  return [
    {
      label: 'SELIC',
      data: selicData,
      borderColor: '#C9A84C',
      backgroundColor: 'rgba(201,168,76,0.07)',
      borderWidth: 2.5, pointRadius: 0, pointHoverRadius: 4,
      fill: true, tension: 0.3,
    },
    {
      label: 'IPCA',
      data: ipcaData,
      borderColor: isLight ? 'rgba(90,85,80,0.75)' : 'rgba(245,230,200,0.5)',
      backgroundColor: 'transparent',
      borderWidth: isLight ? 3 : 2,
      borderDash: [6,3],
      pointRadius: 0, pointHoverRadius: 4,
      fill: false, tension: 0.3,
    }
  ];
}
```

---

### Insight Cards (grid de métricas)

**Estados de cor:** `vermelho` (gold), `verde`, `amarelo`, `azul` — neutro sem classe.

```html
<div class="insights-grid">
  <div class="insight-card vermelho">
    <div class="ic-label">SELIC Atual</div>
    <div class="ic-value">14,50%</div>
    <div class="ic-sub">Superior a 92% dos meses desde jan/2010</div>
  </div>
  <div class="insight-card verde">...</div>
  <div class="insight-card amarelo">...</div>
  <div class="insight-card azul">...</div>
  <div class="insight-card">...</div>
</div>
```

```css
.insights-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 14px; margin-bottom: 24px; }

.insight-card {
  background: var(--bg-card); border: 1px solid var(--border);
  border-radius: 12px; padding: 18px 20px;
  backdrop-filter: blur(8px); transition: background .15s;
}
.insight-card:hover { background: var(--bg-card-hover); }
.insight-card.vermelho { border-color: var(--border-gold); background: var(--gold-light); }
.insight-card.verde    { border-color: rgba(76,175,125,.35); background: var(--green-light); }
.insight-card.amarelo  { border-color: rgba(212,160,23,.35); background: var(--yellow-light); }
.insight-card.azul     { border-color: rgba(91,143,212,.35); background: var(--blue-light); }

.ic-label { font-size: 10px; font-weight: 500; text-transform: uppercase; letter-spacing: .18em; color: var(--cream-faint); font-family: 'Inter'; margin-bottom: 8px; }
.insight-card.vermelho .ic-label { color: var(--gold); }
.insight-card.verde    .ic-label { color: var(--green); }
.insight-card.amarelo  .ic-label { color: var(--yellow); }
.insight-card.azul     .ic-label { color: var(--blue); }

.ic-value { font-family: 'Inter'; font-size: 28px; font-weight: 600; color: var(--cream); line-height: 1.1; margin-bottom: 6px; }
.insight-card.vermelho .ic-value { color: var(--gold); }
.insight-card.verde    .ic-value { color: var(--green); }
.insight-card.amarelo  .ic-value { color: var(--yellow); }
.insight-card.azul     .ic-value { color: var(--blue); }

.ic-sub { font-size: 12px; color: var(--cream-faint); line-height: 1.6; }
```

---

### Card de Indicador (compacto)

```html
<div class="indicador-card destaque">
  <div class="label-caps">CDI</div>
  <div class="valor">14,65% <span>a.a.</span></div>
</div>
```

```css
.indicador-card { background: var(--bg-card); border: 1px solid var(--border); border-radius: 12px; padding: 20px 24px; backdrop-filter: blur(8px); }
.indicador-card.destaque { border-color: var(--border-gold); background: var(--gold-light); }
.indicador-card .valor      { font-size: 26px; font-weight: 600; color: var(--cream); }
.indicador-card .valor span { font-size: 13px; font-weight: 400; color: var(--cream-muted); }
```

---

### Card de Ciclos (linha colorida à esquerda)

```html
<div class="ciclos-card">
  <div class="ciclos-title">Ciclos de Política Monetária</div>
  <div class="ciclos-grid">
    <div class="ciclo-item alta">
      <div class="ciclo-tipo alta">Alta</div>
      <div class="ciclo-periodo">2021 → 2022</div>
      <div class="ciclo-detalhe">2,00% → 13,75% · +11,75 p.p.</div>
    </div>
    <div class="ciclo-item baixa">
      <div class="ciclo-tipo baixa">Queda</div>
      <div class="ciclo-periodo">2016 → 2020</div>
      <div class="ciclo-detalhe">14,25% → 2,00% · −12,25 p.p.</div>
    </div>
  </div>
</div>
```

```css
.ciclos-card {
  background: var(--bg-card); border: 1px solid var(--border);
  border-radius: 12px; padding: 22px 24px; margin-bottom: 20px; backdrop-filter: blur(8px);
}
.ciclos-title  { font-family: 'Playfair Display', serif; font-size: 16px; font-weight: 700; color: var(--cream); margin-bottom: 16px; }
.ciclos-grid   { display: grid; grid-template-columns: repeat(4,1fr); gap: 0; }
.ciclo-item    { padding: 14px 18px; border-left: 2px solid var(--border); }
.ciclo-item.alta  { border-left-color: var(--gold); }
.ciclo-item.baixa { border-left-color: var(--green); }
.ciclo-tipo    { font-size: 10px; font-weight: 500; text-transform: uppercase; letter-spacing: .14em; font-family: 'Inter'; margin-bottom: 4px; }
.ciclo-tipo.alta  { color: var(--gold); }
.ciclo-tipo.baixa { color: var(--green); }
.ciclo-periodo { font-size: 13px; font-weight: 600; color: var(--cream); margin-bottom: 2px; font-family: 'Inter'; }
.ciclo-detalhe { font-size: 11px; color: var(--cream-faint); }
```

---

### Card de Produto

```css
.produto-card             { background: var(--bg-card); border: 1px solid var(--border); border-radius: 12px; padding: 20px 24px; }
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
.badge           { font-size: 11px; font-weight: 500; padding: 3px 10px; border-radius: 20px; text-transform: uppercase; letter-spacing: .08em; font-family: 'Inter'; }
.badge-isento    { background: var(--green-light); color: var(--green); border: 1px solid var(--green); }
.badge-tributado { background: var(--bg-card); color: var(--cream-muted); border: 1px solid var(--border); }
.badge-atencao   { background: var(--yellow-light); color: var(--yellow); border: 1px solid var(--yellow); }
```

---

### Botões

```css
.btn-primary {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 14px 32px; border-radius: 8px;
  background: var(--gold); color: var(--bg-deep);
  font-family: 'Inter', sans-serif; font-size: 14px; font-weight: 600;
  letter-spacing: 0.05em; text-transform: uppercase;
  border: none; cursor: pointer; transition: opacity 0.2s ease;
}
.btn-primary:hover { opacity: 0.85; }

.btn-outline {
  background: transparent; border: 1px solid var(--border-gold); color: var(--gold);
}
.btn-outline:hover { background: var(--gold-light); }

/* Botão de ação secundária (ex: Gerar PDF) */
.btn-pdf {
  background: var(--gold); color: var(--bg-deep); border: none;
  font-family: 'Inter', sans-serif; font-size: 12px; font-weight: 600;
  padding: 8px 18px; border-radius: 8px; cursor: pointer;
  display: flex; align-items: center; gap: 6px;
  letter-spacing: .05em; text-transform: uppercase; transition: opacity .15s;
}
.btn-pdf:hover    { opacity: .85; }
.btn-pdf:disabled { opacity: .4; cursor: not-allowed; }
```

---

### Seletor de Perfil

```css
.perfil-btn {
  padding: 10px 22px; border-radius: 8px;
  border: 1px solid var(--border); background: var(--bg-card);
  font-size: 14px; font-weight: 500; color: var(--cream-muted);
  font-family: 'Inter', sans-serif; cursor: pointer; transition: all 0.2s ease;
}
.perfil-btn:hover  { border-color: var(--gold); color: var(--gold); }
.perfil-btn.active { background: var(--gold-light); border-color: var(--gold); color: var(--gold); }
```

---

### Barra de Progresso com Marcador de Meta

```css
.barra-bg           { height: 8px; background: var(--border); border-radius: 99px; overflow: hidden; position: relative; }
.barra-fill         { height: 100%; border-radius: 99px; transition: width 0.4s ease; }
.barra-fill.verde   { background: var(--green); }
.barra-fill.amarelo { background: var(--yellow); }
.barra-fill.cinza   { background: var(--cream-faint); }
.meta-marker        { position: absolute; top: 0; width: 2px; height: 100%; background: var(--gold); opacity: .8; }
```

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
  padding: 16px 20px; background: var(--bg-card);
  border-radius: 8px; border-left: 3px solid var(--border-gold);
  font-size: 12px; color: var(--cream-faint); line-height: 1.7;
  margin-bottom: 48px;
}
```

---

## Geração de PDF (html2canvas + jsPDF)

### Dependências
```html
<script src="https://cdn.jsdelivr.net/npm/html2canvas@1.4.1/dist/html2canvas.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/jspdf@2.5.1/dist/jspdf.umd.min.js"></script>
```

### Padrão completo

**Regras:**
- PDF sempre no tema claro — independente do tema ativo na página
- Forçar tema claro antes de capturar, restaurar depois no `finally`
- Forçar layout desktop (960px) antes de capturar, restaurar depois
- Todas as variáveis de DOM declaradas **fora** do `try` para ficarem acessíveis no `finally`

```javascript
async function gerarPDF() {
  const btn = document.getElementById('btn-pdf');
  const txtOriginal = btn.innerHTML;
  btn.innerHTML = 'Gerando...';
  btn.disabled = true;

  // Declaradas fora do try para ficarem acessíveis no finally
  const captureWidth = 960;
  const innerWidth   = captureWidth - 48;
  const container    = document.querySelector('.container');
  const chartWrap    = document.querySelector('.chart-wrap');
  const chartCard    = document.querySelector('.chart-card');
  const origContainerStyle = container.style.cssText;
  const origChartWrapStyle = chartWrap.style.cssText;
  const origChartCardStyle = chartCard.style.cssText;
  const eraEscuro = !document.body.classList.contains('light');

  try {
    // Força tema claro para a captura
    if (eraEscuro) {
      document.body.classList.add('light');
      setThemeUI(true);
      applyChartTheme(true);
    }

    // Força layout desktop
    container.style.cssText += ';width:' + captureWidth + 'px!important;max-width:none!important;';
    chartCard.style.cssText += ';width:' + captureWidth + 'px!important;overflow:visible!important;';
    chartWrap.style.cssText += ';width:' + innerWidth   + 'px!important;height:380px!important;overflow:visible!important;';
    chart.resize(innerWidth, 380);
    await new Promise(r => setTimeout(r, 400));

    // Cores do PDF (sempre claro)
    const pdfBgRGB  = [255, 252, 245];
    const pdfBgHex  = '#FFFCF5';
    const pdfTitle  = [42, 31, 10];
    const pdfSub    = [100, 85, 55];
    const pdfFooter = [120, 100, 65];

    const { jsPDF } = window.jspdf;
    const pdf = new jsPDF('p', 'mm', 'a4');
    const W = 210, H = 297, M = 15;
    const contentW = W - 2 * M;

    pdf.setFillColor(...pdfBgRGB);
    pdf.rect(0, 0, W, H, 'F');
    pdf.setFillColor(201, 168, 76);
    pdf.rect(0, 0, W, 4, 'F'); // linha gold no topo

    pdf.setFont('helvetica', 'bold');
    pdf.setFontSize(18);
    pdf.setTextColor(...pdfTitle);
    pdf.text('Título do Relatório', M, 18);

    pdf.setFont('helvetica', 'normal');
    pdf.setFontSize(10);
    pdf.setTextColor(...pdfSub);
    pdf.text('Subtítulo / descrição', M, 24);

    pdf.setFontSize(9);
    pdf.setTextColor(201, 168, 76);
    pdf.text(`Gerado em ${new Date().toLocaleDateString('pt-BR')}`, W - M, 18, { align: 'right' });

    pdf.setDrawColor(201, 168, 76);
    pdf.setLineWidth(0.3);
    pdf.line(M, 28, W - M, 28);

    let y = 32;
    const blocos = ['.chart-card', '.insights-grid', '.ciclos-card'];

    for (const sel of blocos) {
      const el = document.querySelector(sel);
      if (!el) continue;

      const canvas = await html2canvas(el, {
        scale: 2, useCORS: true,
        backgroundColor: pdfBgHex,
        logging: false, windowWidth: captureWidth,
      });

      const imgW = contentW;
      const imgH = canvas.height * imgW / canvas.width;

      if (y + imgH > H - 18) {
        pdf.addPage();
        pdf.setFillColor(...pdfBgRGB);
        pdf.rect(0, 0, W, H, 'F');
        y = M;
      }

      pdf.addImage(canvas.toDataURL('image/png'), 'PNG', M, y, imgW, imgH);
      y += imgH + 8;
    }

    // Rodapé em todas as páginas
    const totalPaginas = pdf.internal.getNumberOfPages();
    for (let i = 1; i <= totalPaginas; i++) {
      pdf.setPage(i);
      pdf.setFontSize(8);
      pdf.setTextColor(...pdfFooter);
      pdf.text(
        'Fonte: Banco Central do Brasil e IBGE  |  Simulação informativa, não constitui oferta ou recomendação de investimento.',
        M, H - 8
      );
      pdf.text(`Página ${i} de ${totalPaginas}`, W - M, H - 8, { align: 'right' });
    }

    pdf.save(`relatorio-${new Date().toISOString().slice(0,10)}.pdf`);

  } catch (err) {
    console.error('Erro ao gerar PDF:', err);
    alert('Erro ao gerar PDF. Detalhes no console.');
  } finally {
    // Restaura tema original
    if (eraEscuro) {
      document.body.classList.remove('light');
      setThemeUI(false);
      applyChartTheme(false);
    }
    // Restaura layout
    container.style.cssText = origContainerStyle;
    chartCard.style.cssText = origChartCardStyle;
    chartWrap.style.cssText = origChartWrapStyle;
    chart.resize();
    btn.innerHTML = txtOriginal;
    btn.disabled = false;
  }
}
```

---

## Responsividade

```css
@media (max-width: 640px) {
  .container    { padding: 0 16px; }
  h1            { font-size: 32px; }
  .insights-grid { grid-template-columns: 1fr 1fr; }
  .ciclos-grid  { grid-template-columns: 1fr 1fr; }
  .chart-wrap   { height: 260px; }
  .toggle-wrap  { margin-left: 0; }
  /* Tabelas: scroll horizontal */
}
```

---

## Alertas de UX

- Fonte base mínima: **16px** — nunca abaixo disso
- Contraste: texto `--cream` sempre sobre fundo escuro; `--cream` (dark) sobre bege no modo claro
- Valores monetários em destaque visual (tamanho e cor gold ou cream)
- Tooltips acessíveis — nunca esconder informação crítica só em hover mobile
- Preferir barras visuais e gráficos a tabelas densas
- `backdrop-filter: blur()` em cards para profundidade — verificar fallback em Safari
- Headers fixos (`position: sticky`) precisam de `z-index` explícito maior que o conteúdo
- PDF sempre gerado no tema claro — independente do tema ativo — forçar antes de capturar e restaurar no `finally`
- Modo claro é o **default** — dark salvo em `localStorage` apenas quando o usuário escolhe explicitamente
