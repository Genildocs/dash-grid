# 📊 Advanced CSS Grid Dashboard

A modern and professional dashboard built with advanced CSS Grid, dynamic data, interactive charts, and complete PWA features.

![Dashboard Preview](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![CSS Grid](https://img.shields.io/badge/CSS-Grid%20Layout-blue)
![PWA](https://img.shields.io/badge/PWA-Ready-purple)
![Chart.js](https://img.shields.io/badge/Charts-Chart.js-orange)

> **🌍 Languages:** [Português](README.md) | [English](README-en.md)
>
> **📖 Articles:** [Tutorial PT](article-medium.md) | [Tutorial EN](article-medium-en.md)
>
> **🛠️ Development:** [Guide PT](DEVELOPMENT.md) | [Guide EN](DEVELOPMENT-en.md)

## ✨ Key Features

### 🎯 **Advanced CSS Grid Layout**
- **Named Areas Strategy** - Semantic and maintainable layout
- **Nested Grid Architecture** - Nested grids for organization
- **Progressive Enhancement** - Compatibility and performance
- **Responsive Design** - Mobile-first with intelligent breakpoints

### 📈 **Dynamic Data and Visualizations**
- **6 KPI Widgets** with real-time updates
- **3 Chart Types** (line, doughnut, bars) with Chart.js
- **Mock API** simulating real data
- **Dynamic Products Table** with live data

### 🌙 **Theme System**
- **Light/Dark Mode** with animated toggle
- **Persistence** via localStorage
- **Smooth transitions** between themes
- **Adaptive charts** that change colors automatically

### 📱 **Complete PWA**
- **Service Worker** with intelligent caching
- **Installable** as native app
- **Offline Support** with visual indicators
- **Automatic update** notifications

## 🚀 Online Demo

Access the demonstration: [Dashboard Demo](https://your-domain.com/dash-grid)

## 📦 Installation

### Option 1: Local Server
```bash
# Clone the repository
git clone https://github.com/your-username/dash-grid.git

# Enter directory
cd dash-grid

# Start local server
python3 -m http.server 8000
# or
npx serve .
# or
php -S localhost:8000

# Access http://localhost:8000
```

### Option 2: Direct Deploy
Upload files to any web server. No backend required.

## 🏗️ Project Structure

```
dash-grid/
├── index.html          # Main dashboard
├── manifest.json       # PWA configuration
├── sw.js              # Service Worker
├── README.md          # Documentation (PT)
├── README-en.md       # Documentation (EN)
├── LICENSE            # MIT License
├── DEVELOPMENT.md     # Development guide (PT)
├── DEVELOPMENT-en.md  # Development guide (EN)
├── article-medium.md  # Technical article (PT)
└── article-medium-en.md # Technical article (EN)
```

## 🎨 Available Widgets

| Widget | Description | Type |
|--------|-------------|------|
| **Revenue** | Total revenue with trend | KPI |
| **Active Users** | Active users | KPI |
| **Orders** | Orders placed | KPI |
| **Conversion Rate** | Conversion rate | KPI |
| **Performance Score** | Performance score | KPI |
| **Bounce Rate** | Bounce rate | KPI |
| **Revenue Overview** | 30-day timeline chart | Chart |
| **Traffic Sources** | Channel distribution | Chart |
| **Sales Trend** | Monthly sales | Chart |
| **Top Products** | Products table | Table |
| **Recent Activity** | Activity feed | List |

## 🛠️ Technologies Used

- **HTML5** - Semantic structure
- **CSS3** - Grid Layout, Custom Properties, Animations
- **JavaScript ES6+** - Classes, Async/Await, Modules
- **Chart.js** - Interactive charts
- **Service Worker API** - Cache and offline support
- **Web App Manifest** - PWA features

## 📱 PWA Features

### ✅ **Installation**
- Automatic installation prompt
- Adaptive icons for different platforms
- Custom splash screen

### ✅ **Offline Support**
- Static resource caching
- Intelligent cache strategies
- Visual offline status indicator

### ✅ **Performance**
- Cache first for static resources
- Network first for dynamic data
- Stale while revalidate for content

## 🎯 Use Cases

### **Enterprise Dashboards**
- Sales analytics
- Performance metrics
- Executive reports

### **SaaS Applications**
- Control panels
- User dashboards
- Product metrics

### **Educational Projects**
- Advanced CSS Grid example
- PWA implementation
- Frontend best practices

## 🔧 Customization

### **Colors and Themes**
```css
:root {
  --primary-color: #2563eb;
  --secondary-color: #1e40af;
  --success-color: #10b981;
  --danger-color: #ef4444;
}
```

### **Responsive Layout**
```css
.dashboard-grid {
  grid-template-columns: var(--sidebar-width) 1fr;
  grid-template-areas:
    'sidebar header'
    'sidebar main';
}
```

### **New Widgets**
```javascript
// Add new widgets to data array
const newWidget = {
  value: 1234,
  change: '+5.2',
  trend: 'up'
};
```

## 📊 Performance

- **Lighthouse Score**: 95+
- **First Contentful Paint**: < 1.5s
- **Largest Contentful Paint**: < 2.5s
- **Cumulative Layout Shift**: < 0.1

## 🤝 Contributing

1. Fork the project
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 Roadmap

- [ ] **Real API integration**
- [ ] **More chart types** (scatter, radar, etc.)
- [ ] **Custom filters and periods**
- [ ] **Data export** (PDF, Excel)
- [ ] **Real-time push notifications**
- [ ] **User-customizable themes**

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Your Name**
- GitHub: [@your-username](https://github.com/your-username)
- LinkedIn: [Your Profile](https://linkedin.com/in/your-profile)
- Email: your.email@example.com

## 🙏 Acknowledgments

- [Chart.js](https://www.chartjs.org/) - Chart library
- [CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout) - Layout system
- [PWA](https://web.dev/progressive-web-apps/) - Progressive Web Apps
- Open source community

---

⭐ **If this project was helpful, consider giving it a star!**
