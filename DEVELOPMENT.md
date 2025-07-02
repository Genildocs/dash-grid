# 🛠️ Guia de Desenvolvimento

Este documento fornece informações detalhadas para desenvolvedores que desejam contribuir ou personalizar o Advanced CSS Grid Dashboard.

## 📋 Pré-requisitos

- Navegador moderno com suporte a CSS Grid
- Servidor web local (Python, Node.js, PHP, etc.)
- Editor de código com suporte a HTML/CSS/JS
- Conhecimento básico de CSS Grid e JavaScript ES6+

## 🏗️ Arquitetura do Projeto

### **Estrutura de Arquivos**
```
dash-grid/
├── index.html          # Aplicação principal (SPA)
├── manifest.json       # Configuração PWA
├── sw.js              # Service Worker
├── README.md          # Documentação principal
├── LICENSE            # Licença MIT
├── DEVELOPMENT.md     # Este arquivo
└── article-medium.md  # Artigo técnico
```

### **Arquitetura CSS**
```css
/* Hierarquia de estilos */
:root                   # Variáveis globais e temas
body                    # Configurações base
.dashboard-grid         # Layout principal (CSS Grid)
├── .header            # Cabeçalho fixo
├── .sidebar           # Navegação lateral
└── .main-content      # Área de conteúdo
    └── .content-grid  # Grid de widgets (nested)
        └── .widget    # Componentes individuais
```

### **Arquitetura JavaScript**
```javascript
class DashboardApp {
  constructor()          # Inicialização
  init()                # Setup principal
  ├── initTheme()       # Sistema de temas
  ├── initEventListeners() # Event handlers
  ├── initCharts()      # Configuração Chart.js
  ├── loadData()        # Carregamento de dados
  └── initPWA()         # Funcionalidades PWA
}
```

## 🎨 Sistema de Design

### **Variáveis CSS**
```css
:root {
  /* Cores principais */
  --primary-color: #2563eb;
  --secondary-color: #1e40af;
  --success-color: #10b981;
  --danger-color: #ef4444;
  
  /* Layout */
  --sidebar-width: 280px;
  --header-height: 70px;
  --content-gap: 1.5rem;
  
  /* Transições */
  --transition-fast: 0.15s ease;
  --transition-normal: 0.3s ease;
}
```

### **Tema Escuro**
```css
[data-theme="dark"] {
  --text-primary: #f9fafb;
  --bg-primary: #1f2937;
  --border-color: #374151;
}
```

## 📊 Sistema de Dados

### **Estrutura de Dados Mock**
```javascript
const mockData = {
  // Widgets KPI
  revenue: { value: 47521, change: "+12.5", trend: "up" },
  users: { value: 2847, change: "+3.2", trend: "up" },
  
  // Dados de gráficos
  chartData: {
    revenue: [40000, 42000, 45000, ...], // Array de 30 dias
    labels: ["Jan 1", "Jan 2", "Jan 3", ...]
  },
  
  // Dados de tabela
  products: [
    { name: "Premium", sales: 2847, revenue: 23450, growth: "12.5" }
  ]
};
```

### **API Mock Simulation**
```javascript
async fetchMockData() {
  // Simula delay de API
  await new Promise(resolve => setTimeout(resolve, 1000));
  
  // Gera dados dinâmicos
  return {
    revenue: {
      value: 47521 + Math.floor(Math.random() * 10000),
      change: (Math.random() * 20 - 10).toFixed(1)
    }
  };
}
```

## 📈 Sistema de Gráficos

### **Chart.js Configuration**
```javascript
// Gráfico de linha responsivo
const lineChart = new Chart(ctx, {
  type: 'line',
  data: { labels: [], datasets: [{}] },
  options: {
    responsive: true,
    maintainAspectRatio: false,
    plugins: { legend: { display: false } }
  }
});
```

### **Adaptação de Tema**
```javascript
updateChartsTheme() {
  const isDark = this.theme === 'dark';
  
  Object.values(this.charts).forEach(chart => {
    chart.options.scales.x.ticks.color = isDark ? '#d1d5db' : '#6b7280';
    chart.update();
  });
}
```

## 🔧 Personalização

### **Adicionando Novos Widgets**

1. **HTML Structure**
```html
<div class="widget fade-in" data-widget="new-metric">
  <div class="widget-header">
    <span class="widget-title">New Metric</span>
    <span>📊</span>
  </div>
  <div class="widget-value loading">0</div>
  <div class="widget-change positive">+0% from last month</div>
</div>
```

2. **JavaScript Data**
```javascript
// No fetchMockData()
newMetric: {
  value: 1234,
  change: "+5.2",
  trend: "up"
}
```

3. **CSS Styling** (opcional)
```css
[data-widget="new-metric"] {
  /* Estilos específicos */
}
```

### **Adicionando Novos Gráficos**

1. **Canvas Element**
```html
<canvas id="newChart" width="400" height="200"></canvas>
```

2. **Chart Creation**
```javascript
createNewChart() {
  const ctx = document.getElementById('newChart');
  this.charts.newChart = new Chart(ctx, {
    type: 'bar', // line, doughnut, bar, etc.
    data: { /* configuração */ },
    options: { /* opções */ }
  });
}
```

### **Modificando Layout Grid**

```css
/* Layout personalizado */
.dashboard-grid {
  grid-template-columns: 200px 1fr 300px; /* 3 colunas */
  grid-template-areas:
    'sidebar header notifications'
    'sidebar main aside';
}

/* Responsivo */
@media (max-width: 1024px) {
  .dashboard-grid {
    grid-template-columns: 1fr;
    grid-template-areas:
      'header'
      'sidebar'
      'main'
      'aside';
  }
}
```

## 🚀 PWA Development

### **Service Worker Strategies**

```javascript
// Cache First (recursos estáticos)
async function cacheFirst(request) {
  const cachedResponse = await caches.match(request);
  return cachedResponse || fetch(request);
}

// Network First (dados dinâmicos)
async function networkFirst(request) {
  try {
    const networkResponse = await fetch(request);
    // Cache para uso offline
    return networkResponse;
  } catch {
    return caches.match(request);
  }
}
```

### **Manifest Configuration**
```json
{
  "name": "Dashboard App",
  "short_name": "Dashboard",
  "start_url": "/",
  "display": "standalone",
  "theme_color": "#2563eb"
}
```

## 🧪 Testing

### **Manual Testing Checklist**

- [ ] **Layout responsivo** em diferentes tamanhos
- [ ] **Troca de tema** funciona corretamente
- [ ] **Gráficos** renderizam e são interativos
- [ ] **Dados** carregam e atualizam
- [ ] **PWA** instala corretamente
- [ ] **Offline** funciona com cache

### **Performance Testing**
```bash
# Lighthouse CLI
npm install -g lighthouse
lighthouse http://localhost:8000 --view

# Ou use DevTools > Lighthouse
```

## 🐛 Debugging

### **Common Issues**

1. **Gráficos não aparecem**
   - Verifique se Chart.js carregou
   - Confirme que o canvas existe no DOM
   - Verifique console para erros

2. **Service Worker não registra**
   - Deve ser servido via HTTPS ou localhost
   - Verifique console para erros
   - Use DevTools > Application > Service Workers

3. **Tema não persiste**
   - Verifique localStorage no DevTools
   - Confirme que initTheme() é chamado

### **Debug Tools**
```javascript
// Debug mode
const DEBUG = true;

if (DEBUG) {
  console.log('Dashboard data:', this.data);
  console.log('Charts:', this.charts);
  console.log('Theme:', this.theme);
}
```

## 📦 Build Process

### **Development Server**
```bash
# Python
python3 -m http.server 8000

# Node.js
npx serve . -p 8000

# PHP
php -S localhost:8000
```

### **Production Deployment**
1. **Minify CSS/JS** (opcional)
2. **Optimize images** (se houver)
3. **Configure HTTPS** (necessário para PWA)
4. **Test PWA features** em produção

## 🤝 Contributing Guidelines

1. **Fork** o repositório
2. **Create branch** com nome descritivo
3. **Follow** padrões de código existentes
4. **Test** suas mudanças
5. **Document** novas funcionalidades
6. **Submit** pull request com descrição clara

### **Code Style**
- Use **2 spaces** para indentação
- **Semicolons** obrigatórios em JavaScript
- **BEM methodology** para classes CSS quando aplicável
- **Comentários** em português para este projeto

---

**Happy Coding!** 🚀
