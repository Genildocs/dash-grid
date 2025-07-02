# 🛠️ Development Guide

This document provides detailed information for developers who want to contribute or customize the Advanced CSS Grid Dashboard.

## 📋 Prerequisites

- Modern browser with CSS Grid support
- Local web server (Python, Node.js, PHP, etc.)
- Code editor with HTML/CSS/JS support
- Basic knowledge of CSS Grid and JavaScript ES6+

## 🏗️ Project Architecture

### **File Structure**
```
dash-grid/
├── index.html          # Main application (SPA)
├── manifest.json       # PWA configuration
├── sw.js              # Service Worker
├── README.md          # Main documentation (PT)
├── README-en.md       # Main documentation (EN)
├── LICENSE            # MIT License
├── DEVELOPMENT.md     # Development guide (PT)
├── DEVELOPMENT-en.md  # This file
├── article-medium.md  # Technical article (PT)
└── article-medium-en.md # Technical article (EN)
```

### **CSS Architecture**
```css
/* Style hierarchy */
:root                   # Global variables and themes
body                    # Base configurations
.dashboard-grid         # Main layout (CSS Grid)
├── .header            # Fixed header
├── .sidebar           # Side navigation
└── .main-content      # Content area
    └── .content-grid  # Widget grid (nested)
        └── .widget    # Individual components
```

### **JavaScript Architecture**
```javascript
class DashboardApp {
  constructor()          # Initialization
  init()                # Main setup
  ├── initTheme()       # Theme system
  ├── initEventListeners() # Event handlers
  ├── initCharts()      # Chart.js configuration
  ├── loadData()        # Data loading
  └── initPWA()         # PWA features
}
```

## 🎨 Design System

### **CSS Variables**
```css
:root {
  /* Main colors */
  --primary-color: #2563eb;
  --secondary-color: #1e40af;
  --success-color: #10b981;
  --danger-color: #ef4444;
  
  /* Layout */
  --sidebar-width: 280px;
  --header-height: 70px;
  --content-gap: 1.5rem;
  
  /* Transitions */
  --transition-fast: 0.15s ease;
  --transition-normal: 0.3s ease;
}
```

### **Dark Theme**
```css
[data-theme="dark"] {
  --text-primary: #f9fafb;
  --bg-primary: #1f2937;
  --border-color: #374151;
}
```

## 📊 Data System

### **Mock Data Structure**
```javascript
const mockData = {
  // KPI Widgets
  revenue: { value: 47521, change: "+12.5", trend: "up" },
  users: { value: 2847, change: "+3.2", trend: "up" },
  
  // Chart data
  chartData: {
    revenue: [40000, 42000, 45000, ...], // 30-day array
    labels: ["Jan 1", "Jan 2", "Jan 3", ...]
  },
  
  // Table data
  products: [
    { name: "Premium", sales: 2847, revenue: 23450, growth: "12.5" }
  ]
};
```

### **API Mock Simulation**
```javascript
async fetchMockData() {
  // Simulates API delay
  await new Promise(resolve => setTimeout(resolve, 1000));
  
  // Generates dynamic data
  return {
    revenue: {
      value: 47521 + Math.floor(Math.random() * 10000),
      change: (Math.random() * 20 - 10).toFixed(1)
    }
  };
}
```

## 📈 Chart System

### **Chart.js Configuration**
```javascript
// Responsive line chart
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

### **Theme Adaptation**
```javascript
updateChartsTheme() {
  const isDark = this.theme === 'dark';
  
  Object.values(this.charts).forEach(chart => {
    chart.options.scales.x.ticks.color = isDark ? '#d1d5db' : '#6b7280';
    chart.update();
  });
}
```

## 🔧 Customization

### **Adding New Widgets**

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
// In fetchMockData()
newMetric: {
  value: 1234,
  change: "+5.2",
  trend: "up"
}
```

3. **CSS Styling** (optional)
```css
[data-widget="new-metric"] {
  /* Specific styles */
}
```

### **Adding New Charts**

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
    data: { /* configuration */ },
    options: { /* options */ }
  });
}
```

### **Modifying Grid Layout**

```css
/* Custom layout */
.dashboard-grid {
  grid-template-columns: 200px 1fr 300px; /* 3 columns */
  grid-template-areas:
    'sidebar header notifications'
    'sidebar main aside';
}

/* Responsive */
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
// Cache First (static resources)
async function cacheFirst(request) {
  const cachedResponse = await caches.match(request);
  return cachedResponse || fetch(request);
}

// Network First (dynamic data)
async function networkFirst(request) {
  try {
    const networkResponse = await fetch(request);
    // Cache for offline use
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

- [ ] **Responsive layout** on different sizes
- [ ] **Theme switching** works correctly
- [ ] **Charts** render and are interactive
- [ ] **Data** loads and updates
- [ ] **PWA** installs correctly
- [ ] **Offline** works with cache

### **Performance Testing**
```bash
# Lighthouse CLI
npm install -g lighthouse
lighthouse http://localhost:8000 --view

# Or use DevTools > Lighthouse
```

## 🐛 Debugging

### **Common Issues**

1. **Charts don't appear**
   - Check if Chart.js loaded
   - Confirm canvas exists in DOM
   - Check console for errors

2. **Service Worker doesn't register**
   - Must be served via HTTPS or localhost
   - Check console for errors
   - Use DevTools > Application > Service Workers

3. **Theme doesn't persist**
   - Check localStorage in DevTools
   - Confirm initTheme() is called

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
1. **Minify CSS/JS** (optional)
2. **Optimize images** (if any)
3. **Configure HTTPS** (required for PWA)
4. **Test PWA features** in production

## 🤝 Contributing Guidelines

1. **Fork** the repository
2. **Create branch** with descriptive name
3. **Follow** existing code patterns
4. **Test** your changes
5. **Document** new features
6. **Submit** pull request with clear description

### **Code Style**
- Use **2 spaces** for indentation
- **Semicolons** required in JavaScript
- **BEM methodology** for CSS classes when applicable
- **Comments** in English for international collaboration

### **Commit Messages**
```bash
# Format: type(scope): description
feat(widgets): add new performance widget
fix(charts): resolve theme switching bug
docs(readme): update installation instructions
style(css): improve responsive breakpoints
```

## 🌍 Internationalization

### **Adding New Languages**
1. Create `README-[lang].md`
2. Create `article-medium-[lang].md`
3. Update main README with language links
4. Consider creating `DEVELOPMENT-[lang].md`

### **Current Languages**
- 🇧🇷 Portuguese (PT) - Default
- 🇺🇸 English (EN) - Available

## 📚 Learning Resources

### **CSS Grid**
- [CSS Grid Complete Guide](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Grid by Example](https://gridbyexample.com/)
- [CSS Grid Garden](https://cssgridgarden.com/) - Interactive game

### **PWA Development**
- [PWA Guide by Google](https://web.dev/progressive-web-apps/)
- [Service Worker Cookbook](https://serviceworke.rs/)
- [PWA Builder](https://www.pwabuilder.com/)

### **Chart.js**
- [Chart.js Documentation](https://www.chartjs.org/docs/)
- [Chart.js Samples](https://www.chartjs.org/samples/)

---

**Happy Coding!** 🚀
