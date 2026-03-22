# SGAA - Arquitectura do Sistema

## 📐 1. VISÃO GERAL DA ARQUITECTURA

O SGAA (Sistema de Gestão de Abastecimento de Água) foi concebido seguindo uma arquitectura moderna, escalável e segura, baseada no padrão **MVC (Model-View-Controller)** combinado com **API RESTful** para o backend e **SPA (Single Page Application)** para o frontend.

### Diagrama de Alto Nível

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              CLIENTES                                       │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │   Desktop    │  │   Tablet     │  │   Mobile     │  │   API Client │     │
│  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘     │
└─────────────────────────────────────┬───────────────────────────────────────┘
                                      │ HTTPS / TLS 1.3
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                           REVERSE PROXY (Nginx)                             │
│                    Balanceamento de carga, SSL termination                  │
└─────────────────────────────────────┬───────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         FRONTEND - REACT SPA                                │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │  Vite Build Tool │ TypeScript │ TailwindCSS │ Framer Motion         │    │
│  │  React Router │ React Hook Form │ Axios │ i18next                   │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
└─────────────────────────────────────┬───────────────────────────────────────┘
                                      │ API REST (JSON)
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         BACKEND - LARAVEL 12                                │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                    API RESTful (Laravel Sanctum)                    │    │
│  ├─────────────────────────────────────────────────────────────────────┤    │
│  │  Controllers │ Models │ Services │ Middleware │ Policies            │    │
│  ├─────────────────────────────────────────────────────────────────────┤    │
│  │                    Business Logic Layer                             │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
└─────────────────────────────────────┬───────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         DATA LAYER                                          │
│  ┌──────────────────────┐  ┌──────────────────────┐  ┌──────────────────┐   │
│  │     MySQL 8.0        │  │       Redis          │  │   File Storage   │   │
│  │   (Dados principais) │  │   (Cache/Sessions)   │  │    (Uploads)     │   │
│  └──────────────────────┘  └──────────────────────┘  └──────────────────┘   │
└─────────────────────────────────────────────────────────────────────────────┘
                                      │
                                      ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         EXTERNAL SERVICES                                   │
│  ┌──────────────────────┐  ┌──────────────────────┐  ┌──────────────────┐   │
│  │   OpenStreetMap      │  │      SMTP Server     │  │   OSRM Router    │   │
│  │   (Mapas)            │  │    (Emails)          │  │   (Rotas)        │   │
│  └──────────────────────┘  └──────────────────────┘  └──────────────────┘   │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🎯 2. REQUISITOS FUNCIONAIS PRINCIPAIS DO MVP

| ID | Requisito | Descrição | Critério de Aceitação |
|----|-----------|-----------|----------------------|
| **RF01** | Autenticação multi-nível | O sistema deve permitir login por email ou telefone, com perfis SuperAdmin, Admin e Cliente, cada um com permissões específicas. | 100% dos acessos autenticados; perfis com permissões distintas; logs de tentativas de login. |
| **RF02** | Gestão de vistorias com geolocalização | O sistema deve permitir que o Admin registe leituras de contador, calcule consumo automaticamente e actualize marcadores no mapa (vermelho/verde). | Registro de vistoria em < 2 minutos; consumo calculado com precisão; marcador actualizado em tempo real. |
| **RF03** | Facturação automática | O sistema deve gerar factura automaticamente após vistoria, aplicando regras de taxa mínima e taxa adicional, com cálculo de multa após vencimento. | Geração de factura em < 1 segundo; cálculo do valor 100% preciso; histórico completo disponível. |

---

## 🏛️ 3. PADRÃO ARQUITECTÓNICO ESCOLHIDO

### MVC (Model-View-Controller) + API RESTful

O SGAA adopta uma arquitectura **MVC** no backend, combinada com uma **API RESTful** que serve dados para o frontend SPA. Esta abordagem oferece:

| Benefício | Descrição |
|-----------|-----------|
| **Separação de Responsabilidades** | Model (dados), View (interface), Controller (lógica) organizados de forma clara |
| **Reutilização de Código** | A mesma API pode servir múltiplos clientes (web, mobile futuro) |
| **Testabilidade** | Camadas isoladas permitem testes unitários e de integração focados |
| **Manutenibilidade** | Código organizado facilita correções e evoluções |

### Justificativa da Escolha

1. **Escalabilidade**: A separação entre frontend e backend permite escalar cada camada independentemente
2. **Flexibilidade**: A API RESTful facilita futuras integrações (app mobile, sistemas externos)
3. **Segurança**: A camada de middleware e policies garante controlo de acesso granular
4. **Performance**: Cache distribuído (Redis) e otimizações de query garantem respostas rápidas

---

## 🛠️ 4. STACK TECNOLÓGICA COMPLETA

### 4.1 Backend

| Componente | Tecnologia | Versão | Justificativa |
|------------|------------|--------|---------------|
| **Linguagem** | PHP | 8.2+ | Maturidade, ecossistema robusto, desempenho optimizado |
| **Framework** | Laravel | 12.x | Eloquent ORM, segurança integrada, comunidade activa, ferramentas built-in |
| **Autenticação** | Laravel Sanctum | - | Tokens API simples e seguros, suporte a SPA |
| **Base de Dados** | MySQL | 8.0+ | ACID compliant, índices espaciais para geolocalização, estabilidade |
| **Cache** | Redis | 7.0+ | Performance em cache de queries e sessões, suporte a filas |
| **Queue** | Redis/Database | - | Processamento assíncrono de tarefas (emails, relatórios) |
| **PDF** | DomPDF / Laravel PDF | - | Geração de facturas e relatórios em PDF |
| **Excel** | Laravel Excel | - | Exportação de relatórios em Excel/CSV |
| **Logs** | Monolog | - | Logs estruturados, integração com serviços externos |

### 4.2 Frontend

| Componente | Tecnologia | Versão | Justificativa |
|------------|------------|--------|---------------|
| **Linguagem** | TypeScript | 5.x | Type safety, melhor experiência de desenvolvimento, código mais robusto |
| **Framework** | React | 18.x | Componentização, ecossistema maduro, performance, comunidade activa |
| **Build Tool** | Vite | 5.x | Build rápido, hot module replacement, optimizações out-of-the-box |
| **Estilização** | TailwindCSS | 3.x | Utility-first, design responsivo eficiente, customização fácil |
| **UI Components** | Headless UI | 1.7+ | Acessível, sem estilos pré-definidos, integração perfeita com Tailwind |
| **Ícones** | Heroicons | 2.x | Conjunto completo, SVG, customizáveis |
| **Mapas** | Leaflet + React-Leaflet | 1.9+ | OpenStreetMap, leve, sem custos de licenciamento |
| **Rotas** | React Router DOM | 6.x | Navegação declarativa, code splitting, lazy loading |
| **Estado Global** | Redux Toolkit | 2.x | Gerenciamento de estado previsível, devtools, middleware |
| **Formulários** | React Hook Form | 7.48+ | Performance, validação integrada, reduz re-renders |
| **HTTP Client** | Axios | 1.6+ | Interceptors, CSRF protection, fácil configuração |
| **Animações** | Framer Motion | 10.x | Animações fluidas, API declarativa, performance |
| **Gráficos** | Recharts | 2.10+ | Componentes React, SVG, responsivo |
| **Tabelas** | DataTables.net | 2.0+ | Busca, ordenação, paginação, i18n |
| **Notificações** | React Toastify | 9.1+ | Toast notifications customizáveis, não intrusivas |
| **Internacionalização** | i18next + react-i18next | 23.x | Traduções dinâmicas, suporte a 7 idiomas, lazy loading |
| **Data Manipulation** | date-fns | 3.x | Leve, modular, manipulação de datas eficiente |

### 4.3 Infraestrutura

| Componente | Tecnologia | Justificativa |
|------------|------------|---------------|
| **Servidor Web** | Nginx | Performance, baixo consumo de recursos, configuração flexível |
| **Process Manager** | Supervisor | Garantia de execução contínua de workers e queues |
| **Containerização** | Docker | Ambientes consistentes, facilidade de deploy |
| **Versionamento** | Git + GitHub | Controle de versão, colaboração, CI/CD |
| **CI/CD** | GitHub Actions | Automação de testes e deploys |
| **Monitorização** | Sentry + Laravel Telescope | Erros em tempo real, debugging, performance monitoring |
| **Backup** | mysqldump + cron | Backup automático diário, retenção de 30 dias |

---

## 📁 5. ESTRUTURA DE DIRETÓRIOS

```
sgaa/
├── app/
│   ├── Console/              # Comandos Artisan
│   ├── Exceptions/           # Tratamento de exceções
│   ├── Http/
│   │   ├── Controllers/      # Controladores da aplicação
│   │   │   ├── Api/          # API Controllers
│   │   │   ├── Auth/         # Autenticação
│   │   │   ├── Admin/        # Admin Controllers
│   │   │   └── Client/       # Client Controllers
│   │   ├── Middleware/       # Middleware personalizados
│   │   └── Kernel.php        # Configuração de middleware
│   ├── Models/               # Eloquent Models (15+)
│   ├── Policies/             # Políticas de autorização
│   ├── Services/             # Camada de serviços
│   └── Providers/            # Service Providers
│
├── database/
│   ├── migrations/           # 16 migrações
│   ├── seeders/              # Seeders (UserSeeder, RateSeeder)
│   └── factories/            # Factories para testes
│
├── resources/
│   ├── js/
│   │   ├── components/       # React Components
│   │   │   ├── common/       # Componentes reutilizáveis
│   │   │   ├── admin/        # Admin Components
│   │   │   ├── client/       # Client Components
│   │   │   └── welcome/      # Welcome Page Components
│   │   ├── hooks/            # Custom React Hooks
│   │   ├── i18n/             # Arquivos de tradução (7 idiomas)
│   │   ├── pages/            # Page Components
│   │   ├── store/            # Redux store
│   │   ├── types/            # TypeScript definitions
│   │   └── app.tsx           # Ponto de entrada React
│   ├── css/
│   │   └── app.css           # Estilos Tailwind
│   └── views/
│       └── spa.blade.php     # Template principal
│
├── routes/
│   ├── web.php               # Rotas web (SPA)
│   ├── api.php               # Rotas API (RESTful)
│   └── console.php           # Comandos Artisan
│
├── tests/                    # Testes automatizados
├── public/                   # Assets compilados
├── storage/                  # Uploads, logs, cache
├── .env.example              # Configuração de ambiente
├── composer.json             # Dependências PHP
├── package.json              # Dependências Node
├── tsconfig.json             # Configuração TypeScript
├── tailwind.config.js        # Configuração Tailwind
├── vite.config.js            # Configuração Vite
└── README.md                 # Documentação
```

---

## 🔄 6. FLUXOS DE DADOS PRINCIPAIS

### 6.1 Fluxo de Autenticação

```
┌────────┐     ┌──────────┐     ┌─────────────┐     ┌──────────┐
│ Client │───▶│  Login    │───▶│  Sanctum    │───▶│ Response │
│        │◀───│ Request   │◀───│  Token      │◀───│ + Token  │
└────────┘     └──────────┘     └─────────────┘     └──────────┘
```

### 6.2 Fluxo de Vistoria

```
┌──────────┐     ┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│ Select   │───▶│ Record      │────▶│ Calculate    │───▶│ Generate    │
│ Client   │     │ Reading     │     │ Consumption  │     │ Invoice     │
└──────────┘     └─────────────┘     └──────────────┘     └─────────────┘
       │                │                     │                    │
       ▼                ▼                     ▼                    ▼
┌──────────┐     ┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│ Update   │◀───│ Save        │◀────│ Apply        │◀───│ Calculate   │
│ Marker   │     │ Inspection  │     │ Rates        │     │ Total       │
└──────────┘     └─────────────┘     └──────────────┘     └─────────────┘
```

### 6.3 Fluxo de Pagamento

```
┌──────────┐     ┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│ Client   │───▶│ Register    │────▶│ Admin        │───▶│ Update      │
│ Payment  │     │ Payment     │     │ Confirmation │     │ Invoice     │
└──────────┘     └─────────────┘     └──────────────┘     └─────────────┘
       │                                   │                      │
       ▼                                   ▼                      ▼
┌──────────┐                       ┌─────────────┐     ┌─────────────┐
│ Receipt  │◀─────────────────────│ Generate    │◀────│ Emit        │
│ Generated│                       │ Receipt     │     │ Receipt     │
└──────────┘                       └─────────────┘     └─────────────┘
```

---

## 🔒 7. SEGURANÇA

### 7.1 Camadas de Segurança

| Camada | Medidas |
|--------|---------|
| **Rede** | HTTPS obrigatório, TLS 1.3, CORS configurado |
| **Aplicação** | CSRF tokens, Prepared statements (SQL injection), XSS sanitization, Rate limiting |
| **Autenticação** | Hash bcrypt, Sanctum tokens, 2FA (opcional), expiração de sessão |
| **Autorização** | Middleware por perfil, Policies, Gates |
| **Dados** | Dados sensíveis mascarados, logs sem informações críticas |

### 7.2 Políticas de Acesso

| Perfil | Permissões |
|--------|------------|
| **SuperAdmin** | Acesso total: gestão de Admins, logs, configurações globais |
| **Admin** | Gestão de clientes, vistorias, facturas, pagamentos, comunicados |
| **Cliente** | Apenas suas facturas, pagamentos, perfil, mapa da secretaria |

---

## 📊 8. PERFORMANCE E ESCALABILIDADE

| Componente | Estratégia |
|------------|------------|
| **Base de Dados** | Índices optimizados, paginação em listas, queries optimizadas |
| **Cache** | Redis para sessões, queries frequentes, rate limiting |
| **Frontend** | Code splitting, lazy loading, minificação de assets |
| **Assets** | CDN para bibliotecas estáticas, compressão gzip/brotli |
| **API** | Paginação, campos selecionáveis, rate limiting por IP/utilizador |

---

## ✅ 9. JUSTIFICATIVA DAS ESCOLHAS

| Escolha | Alternativa Considerada | Razão da Escolha |
|---------|------------------------|------------------|
| **Laravel vs Symfony** | Symfony | Laravel oferece maior produtividade, ecossistema mais acessível, curva de aprendizagem menor |
| **React vs Vue** | Vue | React tem ecossistema maior, TypeScript nativo, mercado mais aquecido |
| **TypeScript vs JavaScript** | JavaScript | TypeScript reduz bugs em tempo de desenvolvimento, melhor manutenção |
| **Tailwind vs Sass** | Sass | Tailwind acelera desenvolvimento, consistência de design, menor CSS final |
| **MySQL vs PostgreSQL** | PostgreSQL | MySQL mais familiar, amplo suporte em hospedagens, performance adequada |
| **OpenStreetMap vs Google Maps** | Google Maps | OpenStreetMap é gratuito, sem restrições de uso, dados colaborativos |
| **Sanctum vs Passport** | Passport | Sanctum é mais leve, suficiente para SPA, integração simples |
