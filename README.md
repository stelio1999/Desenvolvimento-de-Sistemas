# SGAA - Sistema de Gestão de Abastecimento de Água

[![Laravel Version](https://img.shields.io/badge/Laravel-12.x-FF2D20?logo=laravel)](https://laravel.com)
[![React Version](https://img.shields.io/badge/React-18.x-61DAFB?logo=react)](https://reactjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript)](https://www.typescriptlang.org)
[![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3.x-06B6D4?logo=tailwindcss)](https://tailwindcss.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📋 Índice

- [Sobre o Projeto](#sobre-o-projeto)
- [Funcionalidades](#funcionalidades)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Pré-requisitos](#pré-requisitos)
- [Instalação](#instalação)
- [Configuração](#configuração)
- [Executando o Projeto](#executando-o-projeto)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Documentação da API](#documentação-da-api)
- [Testes](#testes)
- [Deploy](#deploy)
- [Contribuição](#contribuição)
- [Licença](#licença)
- [Contato](#contato)

---

## 🚀 Sobre o Projeto

O **SGAA (Sistema de Gestão de Abastecimento de Água)** é uma plataforma web completa desenvolvida para automatizar e otimizar a gestão do abastecimento de água em concessionárias e empresas do setor. O sistema permite o controlo eficiente de clientes, contadores de água, vistorias técnicas, facturação, pagamentos e comunicação com os utentes.

### 🎯 Objetivos

- Automatizar o processo de leitura de contadores e geração de facturas
- Reduzir o tempo de resposta nas vistorias técnicas
- Permitir o acompanhamento em tempo real das vistorias através de mapas interativos
- Facilitar o pagamento de facturas através de múltiplos canais
- Melhorar a comunicação entre a empresa e os clientes
- Garantir a segurança dos dados através de autenticação multi-nível

### 👥 Perfis de Utilizador

| Perfil | Descrição |
|--------|-----------|
| **SuperAdmin** | Acesso total ao sistema, gestão de administradores, configurações globais |
| **Admin** | Gestão de clientes, vistorias, facturas, pagamentos, comunicados |
| **Cliente** | Acesso às suas facturas, histórico de consumo, localização da secretaria |

---

## ✨ Funcionalidades

### 🔐 Autenticação e Segurança
- Login por email ou telefone
- Recuperação de senha via email
- Autenticação multi-nível (SuperAdmin, Admin, Cliente)
- Protecção contra SQL Injection, XSS e CSRF

### 👥 Gestão de Utilizadores e Clientes
- CRUD completo de utilizadores (SuperAdmin)
- Cadastro de clientes com dados completos
- Gestão de contadores de água
- Histórico de consumo por cliente

### 🗺️ Geolocalização e Mapas
- Marcação de residências no mapa (OpenStreetMap)
- Visualização de todos os clientes com marcadores coloridos
- Traçado de rota optimizada para vistorias
- Mapa do escritório mais próximo para clientes

### 🔧 Vistorias Técnicas
- Registo de leituras do contador
- Cálculo automático do consumo
- Upload de fotos da vistoria
- Actualização automática do status no mapa

### 📄 Facturação
- Cálculo automático baseado no consumo
- Configuração de taxas e multas
- Emissão de facturas em PDF
- Histórico completo de facturas

### 💰 Pagamentos
- Registo de pagamentos com múltiplos métodos
- Confirmação manual de pagamentos
- Emissão de recibos
- Histórico de pagamentos por cliente

### 📢 Comunicação
- Gestão de comunicados e avisos
- Notificações do sistema
- Portal do cliente com informações personalizadas

### 📊 Relatórios
- Relatório financeiro (receitas, pagamentos, inadimplência)
- Relatório de consumo (total, médio, por bairro)
- Relatório operacional (vistorias, desempenho)
- Exportação em PDF, Excel e CSV

### 🌐 Internacionalização
- Suporte a 7 idiomas:
  - Português (Moçambique)
  - Português (Brasil)
  - Português (Portugal)
  - English
  - 中文 (Chinês Mandarim)
  - العربية (Árabe)
  - Русский (Russo)

### 🎨 Interface
- Tema claro/escuro com persistência
- Design responsivo (mobile-first)
- Skeleton loading para melhor experiência
- Animações suaves com Framer Motion

---

## 🛠️ Tecnologias Utilizadas

### Backend
| Tecnologia | Versão | Descrição |
|------------|--------|-----------|
| PHP | 8.2+ | Linguagem de programação |
| Laravel | 12.x | Framework PHP |
| MySQL | 8.0+ | Banco de dados relacional |
| Laravel Sanctum | - | Autenticação API |
| DomPDF | - | Geração de PDF |
| Laravel Excel | - | Exportação de relatórios |

### Frontend
| Tecnologia | Versão | Descrição |
|------------|--------|-----------|
| React | 18.x | Biblioteca JavaScript |
| TypeScript | 5.x | Superset tipado do JavaScript |
| TailwindCSS | 3.x | Framework CSS |
| Vite | 5.x | Bundler e build tool |
| React Router | 6.x | Navegação |
| React Hook Form | - | Gerenciamento de formulários |
| Axios | - | Cliente HTTP |
| Framer Motion | - | Animações |
| Recharts | - | Gráficos e visualizações |
| Leaflet | - | Mapas interativos |
| DataTables | - | Tabelas com busca e paginação |
| i18next | - | Internacionalização |

### Ferramentas de Desenvolvimento
| Ferramenta | Descrição |
|------------|-----------|
| Git | Controle de versão |
| Composer | Gerenciador de dependências PHP |
| NPM | Gerenciador de dependências Node |
| PHPUnit | Testes unitários |
| ESLint | Linting JavaScript/TypeScript |
| Prettier | Formatação de código |

---

## 📋 Pré-requisitos

Antes de começar, certifique-se de ter instalado em sua máquina:

- [PHP](https://www.php.net/) >= 8.2
- [Composer](https://getcomposer.org/) >= 2.5
- [Node.js](https://nodejs.org/) >= 18.0
- [NPM](https://www.npmjs.com/) >= 9.0
- [MySQL](https://www.mysql.com/) >= 8.0 ou [MariaDB](https://mariadb.org/) >= 10.6
- [Git](https://git-scm.com/)

---

## 🔧 Instalação

### 1. Clonar o repositório

```bash
git clone https://github.com/seu-usuario/sgaa.git
cd sgaa

composer install
npm install
cp .env.example .env
php artisan key:generate

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=sgaa
DB_USERNAME=root
DB_PASSWORD=your_password

php artisan migrate --seed
npm run build
php artisan serve

sgaa/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Api/              # API Controllers
│   │   │   ├── Auth/             # Autenticação
│   │   │   ├── Admin/            # Admin Controllers
│   │   │   └── Client/           # Client Controllers
│   │   └── Middleware/           # Middleware personalizados
│   ├── Models/                   # Eloquent Models
│   └── Services/                 # Services Layer
│
├── database/
│   ├── migrations/               # Migrações do banco
│   └── seeders/                  # Seeders para dados iniciais
│
├── resources/
│   ├── js/
│   │   ├── components/           # React Components
│   │   │   ├── common/           # Componentes reutilizáveis
│   │   │   ├── admin/            # Admin Components
│   │   │   ├── client/           # Client Components
│   │   │   └── welcome/          # Welcome Page Components
│   │   ├── hooks/                # Custom Hooks
│   │   ├── i18n/                 # Arquivos de tradução
│   │   ├── pages/                # Page Components
│   │   ├── types/                # TypeScript definitions
│   │   └── app.tsx               # Ponto de entrada React
│   ├── css/
│   │   └── app.css               # Estilos principais
│   └── views/
│       └── spa.blade.php         # Template principal
│
├── routes/
│   ├── web.php                   # Rotas web
│   ├── api.php                   # Rotas API
│   └── console.php               # Comandos Artisan
│
├── public/
│   ├── css/
│   └── js/
│
├── tests/                        # Testes automatizados
├── .env.example                  # Exemplo de configuração
├── package.json                  # Dependências Node
├── composer.json                 # Dependências PHP
├── tailwind.config.js            # Configuração Tailwind
├── tsconfig.json                 # Configuração TypeScript
├── vite.config.js                # Configuração Vite
└── README.md                     # Documentação
