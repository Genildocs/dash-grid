# 📊 Advanced CSS Grid Dashboard

Um dashboard moderno e profissional construído com CSS Grid avançado, dados dinâmicos, gráficos interativos e funcionalidades PWA completas.

![Dashboard Preview](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![CSS Grid](https://img.shields.io/badge/CSS-Grid%20Layout-blue)
![PWA](https://img.shields.io/badge/PWA-Ready-purple)
![Chart.js](https://img.shields.io/badge/Charts-Chart.js-orange)

> **🌍 Languages:** [Português](README.md) | [English](README-en.md)
>
> **📖 Articles:** [Tutorial PT](article-medium.md) | [Tutorial EN](article-medium-en.md)
>
> **🛠️ Development:** [Guide PT](DEVELOPMENT.md) | [Guide EN](DEVELOPMENT-en.md)

## ✨ Características Principais

### 🎯 **Layout CSS Grid Avançado**
- **Named Areas Strategy** - Layout semântico e maintível
- **Nested Grid Architecture** - Grids aninhados para organização
- **Progressive Enhancement** - Compatibilidade e performance
- **Responsive Design** - Mobile-first com breakpoints inteligentes

### 📈 **Dados Dinâmicos e Visualizações**
- **6 Widgets KPI** com atualizações em tempo real
- **3 Tipos de Gráficos** (linha, rosca, barras) com Chart.js
- **API Mock** simulando dados reais
- **Tabela de Produtos** com dados dinâmicos

### 🌙 **Sistema de Temas**
- **Modo Claro/Escuro** com toggle animado
- **Persistência** via localStorage
- **Transições suaves** entre temas
- **Gráficos adaptativos** que mudam cores automaticamente

### 📱 **PWA Completo**
- **Service Worker** com cache inteligente
- **Instalável** como app nativo
- **Offline Support** com indicadores visuais
- **Notificações** de atualização automáticas

## 🚀 Demo Online

Acesse a demonstração: [Dashboard Demo](https://seu-dominio.com/dash-grid)

## 📦 Instalação

### Opção 1: Servidor Local
```bash
# Clone o repositório
git clone https://github.com/seu-usuario/dash-grid.git

# Entre no diretório
cd dash-grid

# Inicie um servidor local
python3 -m http.server 8000
# ou
npx serve .
# ou
php -S localhost:8000

# Acesse http://localhost:8000
```

### Opção 2: Deploy Direto
Faça upload dos arquivos para qualquer servidor web. Não requer backend.

## 🏗️ Estrutura do Projeto

```
dash-grid/
├── index.html          # Dashboard principal
├── manifest.json       # Configuração PWA
├── sw.js              # Service Worker
├── README.md          # Documentação (PT)
├── README-en.md       # Documentação (EN)
├── LICENSE            # Licença MIT
├── DEVELOPMENT.md     # Guia de desenvolvimento (PT)
├── DEVELOPMENT-en.md  # Guia de desenvolvimento (EN)
├── article-medium.md  # Artigo técnico (PT)
└── article-medium-en.md # Artigo técnico (EN)
```

## 🎨 Widgets Disponíveis

| Widget | Descrição | Tipo |
|--------|-----------|------|
| **Revenue** | Receita total com tendência | KPI |
| **Active Users** | Usuários ativos | KPI |
| **Orders** | Pedidos realizados | KPI |
| **Conversion Rate** | Taxa de conversão | KPI |
| **Performance Score** | Score de performance | KPI |
| **Bounce Rate** | Taxa de rejeição | KPI |
| **Revenue Overview** | Gráfico temporal 30 dias | Chart |
| **Traffic Sources** | Distribuição por canal | Chart |
| **Sales Trend** | Vendas mensais | Chart |
| **Top Products** | Tabela de produtos | Table |
| **Recent Activity** | Feed de atividades | List |

## 🛠️ Tecnologias Utilizadas

- **HTML5** - Estrutura semântica
- **CSS3** - Grid Layout, Custom Properties, Animations
- **JavaScript ES6+** - Classes, Async/Await, Modules
- **Chart.js** - Gráficos interativos
- **Service Worker API** - Cache e offline support
- **Web App Manifest** - PWA features

## 📱 Funcionalidades PWA

### ✅ **Instalação**
- Prompt automático de instalação
- Ícones adaptativos para diferentes plataformas
- Splash screen personalizada

### ✅ **Offline Support**
- Cache de recursos estáticos
- Estratégias de cache inteligentes
- Indicador visual de status offline

### ✅ **Performance**
- Cache first para recursos estáticos
- Network first para dados dinâmicos
- Stale while revalidate para conteúdo

## 🎯 Casos de Uso

### **Dashboards Empresariais**
- Analytics de vendas
- Métricas de performance
- Relatórios executivos

### **Aplicações SaaS**
- Painéis de controle
- Dashboards de usuário
- Métricas de produto

### **Projetos Educacionais**
- Exemplo de CSS Grid avançado
- Implementação PWA
- Boas práticas de frontend

## 🔧 Personalização

### **Cores e Temas**
```css
:root {
  --primary-color: #2563eb;
  --secondary-color: #1e40af;
  --success-color: #10b981;
  --danger-color: #ef4444;
}
```

### **Layout Responsivo**
```css
.dashboard-grid {
  grid-template-columns: var(--sidebar-width) 1fr;
  grid-template-areas:
    'sidebar header'
    'sidebar main';
}
```

### **Novos Widgets**
```javascript
// Adicione novos widgets no array de dados
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

## 🤝 Contribuição

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📝 Roadmap

- [ ] **Integração com APIs reais**
- [ ] **Mais tipos de gráficos** (scatter, radar, etc.)
- [ ] **Filtros e períodos** personalizáveis
- [ ] **Exportação de dados** (PDF, Excel)
- [ ] **Notificações push** em tempo real
- [ ] **Temas personalizáveis** pelo usuário

## 📄 Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

## 👨‍💻 Autor

- GitHub: [@Genildocs](https://github.com/Genildocs)
- LinkedIn: [genildo-cerqueira](https://www.linkedin.com/in/genildo-cerqueira-91888786/)
- Email: genildocs@gmail.com

## 🙏 Agradecimentos

- [Chart.js](https://www.chartjs.org/) - Biblioteca de gráficos
- [CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout) - Layout system
- [PWA](https://web.dev/progressive-web-apps/) - Progressive Web Apps
- Comunidade open source

---

⭐ **Se este projeto foi útil, considere dar uma estrela!**
