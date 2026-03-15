# Desenvolvimento-de-Sistemas
# 📱 App de Monitorizacao - Sistema de Monitoria Parental

## Sobre o Projeto

O **App de Monitorizacao** é uma solução tecnológica desenvolvida inteiramente para ajudar pais e encarregados de educação a monitorarem a segurança de seus filhos menores de idade. O sistema permite acompanhar em tempo real a localização da criança, visualizar histórico de chamadas, SMS, contatos e muito mais.

> "Tecnologia para tranquilidade familiar"

## 🏗️ Estrutura do Projeto

O projeto é dividido em duas partes principais:

```
📦 App Espião Moçambicano
├── 📱 App Android (Kotlin) - Instalado no celular da criança
└── 🌐 Web Platform (Laravel 10) - Acessado pelos pais
```

### 📱 **App Android (Kotlin)**

O aplicativo roda em **background** de forma invisível e coleta:
- 📍 Localização em tempo real (apenas quando há movimento > 120m)
- 📨 Mensagens SMS (cada mensagem uma única vez)
- 📞 Histórico de chamadas (cada chamada uma única vez)
- 👥 Lista de contatos (apenas novos contatos)
- ℹ️ Informações do dispositivo (modelo, operadora, bateria, IMEI)
- ⌨️ Monitor de teclado (em apps específicos, apenas textos completos)

**Características:**
- ✅ Funciona offline (armazena localmente e sincroniza quando há internet)
- ✅ Bateria otimizada (só envia localização se houver movimento significativo)
- ✅ Sem duplicatas (cada dado é enviado uma única vez)
- ✅ Inicia automaticamente com o dispositivo
- ✅ Todas as permissões na instalação

### 🌐 **Web Platform**

Plataforma web para os pais monitorarem:
- 📊 Dashboard com estatísticas em tempo real
- 🗺️ Mapa interativo com OpenStreetMap
- 📱 Lista de dispositivos associados
- 📨 Visualização de SMS e chamadas
- 👥 Lista de contatos do celular
- ℹ️ Informações detalhadas do dispositivo
- 💳 Gestão de pagamentos mensais
- 👤 Dois níveis de acesso (Admin e Parente)

## 🚀 **Funcionalidades Principais**

### Para os Pais:
- ✅ Ver localização em tempo real da criança
- ✅ Saber se a criança está com internet ligada
- ✅ Visualizar nível de bateria do celular
- ✅ Acessar histórico de chamadas e SMS
- ✅ Ver lista completa de contatos
- ✅ Informações do dispositivo (modelo, operadora, IMEI)
- ✅ Receber alertas de movimentação
- ✅ Histórico de todas as localizações

### Para o Administrador:
- ✅ Gerir todos os parentes e crianças
- ✅ Controlar pagamentos mensais
- ✅ Visualizar estatísticas do sistema
- ✅ Sincronizar dados com Firebase
- ✅ Gerir dispositivos ativos

## 🛠️ **Tecnologias Utilizadas**

### **Backend (Laravel 10):**
- Laravel 10
- MySQL
- Firebase Cloud Firestore
- OpenStreetMap (Nominatim + Overpass API)
- Bootstrap 5
- jQuery & AJAX
- DataTables

### **App Android (Kotlin):**
- Kotlin
- Firebase Firestore
- Retrofit (API)
- Google Play Services (Location)
- Coroutines
- WorkManager
- Accessibility Service (teclado)

## 📊 **Principais Características Técnicas**

### **Sem Duplicatas:**
- Cada SMS é enviado **uma única vez**
- Cada chamada é enviada **uma única vez**
- Contatos são enviados apenas **na primeira execução** e quando **novos** são adicionados
- Localização só é enviada quando há **movimento > 120m**

### **Otimização de Bateria:**
- Localização só é registrada com mudança significativa
- Dados são enviados apenas quando há conexão
- Sincronização inteligente apenas de dados novos

### **Offline First:**
- Todos os dados são armazenados localmente
- Sincronização automática quando a internet está disponível
- Zero perda de dados

## 🔒 **Privacidade e Segurança**

- ✅ Código único por dispositivo
- ✅ Dados encriptados
- ✅ Acesso apenas do responsável legal
- ✅ Conformidade com leis moçambicanas
- ✅ Uso exclusivo para menores de idade

## 📱 **Como Funciona**

1. **Registo:** O pai cria conta na plataforma web
2. **Adicionar Criança:** Cadastra os dados da criança
3. **Gerar Código:** Sistema gera código único
4. **Instalar App:** Baixa e instala o APK no celular da criança
5. **Ativar:** Insere o código no app (apenas uma vez)
6. **Monitorar:** Acompanha tudo pela web



Este projeto foi desenvolvido para atender às necessidades das famílias moçambicanas, considerando:
- 📱 Operadoras locais (Mcel, Vodacom, Movitel)
- 🗺️ Mapas com dados de Moçambique
- 💳 Pagamentos em Meticais (MZN)
- 🇲🇿 Interface em português de Moçambique

## 📄 **Licença**

Este projeto é proprietário e de uso controlado. Todos os direitos reservados.

---

## ⚙️ **Comandos Rápidos (Laravel)**

```bash
# Instalar dependências
composer install
npm install

# Configurar ambiente
cp .env.example .env
php artisan key:generate

# Migrações
php artisan migrate
php artisan db:seed

# Sincronizar Firebase
php artisan firebase:sincronizar

# Verificar dados
php artisan firebase:verificar

# Iniciar servidor
php artisan serve
```

## 📲 **Build do App Android**

```bash
# Limpar e compilar
./gradlew clean
./gradlew assembleRelease

# APK gerado em:
app/build/outputs/apk/release/app-release.apk
```
