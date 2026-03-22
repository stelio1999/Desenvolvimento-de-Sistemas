# SGAA - Work Breakdown Structure (WBS)

## 📊 Estrutura de Divisão do Trabalho

## 1.0 Planeamento (Semana 1)

### 1.1 Definição de requisitos
**1.1.1 Levantamento de necessidades** - Realizar entrevistas com stakeholders para identificar as necessidades do negócio, mapear os processos atuais de gestão de água e documentar os fluxos de trabalho existentes. Entregável: Relatório de necessidades validado.

**1.1.2 Validação com stakeholders** - Apresentar os requisitos levantados para aprovação com a direcção, gestores e utilizadores finais, recolhendo feedback e ajustando conforme necessário. Entregável: Requisitos validados e assinados.

**1.1.3 Documentação dos requisitos** - Elaborar a documentação formal dos requisitos funcionais e não-funcionais, incluindo casos de uso e critérios de aceitação. Entregável: Documento de requisitos (RF e RNF).

### 1.2 Criação do Product Backlog
**1.2.1 User Stories** - Criar as histórias de utilizador baseadas nos requisitos validados, seguindo o formato "Como [perfil], quero [acção], para [benefício]". Entregável: Product Backlog inicial com 20 User Stories.

**1.2.2 Critérios de aceitação** - Definir critérios de aceitação claros e testáveis para cada User Story, garantindo que o desenvolvimento possa ser validado adequadamente. Entregável: Cada User Story com 3-5 critérios de aceitação.

**1.2.3 Priorização MoSCoW** - Aplicar a técnica MoSCoW (Must have, Should have, Could have, Won't have) para priorizar as User Stories e definir o escopo do MVP. Entregável: Backlog priorizado.

### 1.3 Definição de arquitectura técnica
**1.3.1 Stack tecnológico** - Definir as tecnologias a serem utilizadas no backend (Laravel 12, MySQL, Redis), frontend (React, TypeScript, TailwindCSS) e infraestrutura (Nginx, Docker). Entregável: Documento de stack tecnológico.

**1.3.2 Arquitectura de dados** - Modelar as entidades do sistema, seus relacionamentos e definir a estrutura do banco de dados com 16 tabelas principais. Entregável: Diagrama ER e dicionário de dados.

**1.3.3 Diagramas de sequência** - Elaborar diagramas de sequência para os fluxos críticos: autenticação, vistoria, facturação e pagamento. Entregável: Diagramas de sequência validados.

### 1.4 Configuração do ambiente de desenvolvimento
**1.4.1 Repositório Git** - Criar repositório no GitHub, definir estrutura de branches (main, develop, feature/*) e configurar protecções para a branch principal. Entregável: Repositório configurado.

**1.4.2 Ambiente local (Docker/Laravel Sail)** - Configurar ambiente de desenvolvimento utilizando Docker e Laravel Sail para garantir consistência entre a equipa. Entregável: Ambiente funcional para todos os desenvolvedores.

**1.4.3 Ambiente de staging** - Provisionar ambiente de staging para testes e validação antes do deploy em produção. Entregável: Ambiente de staging acessível.

---

## 2.0 Backend - API (Semana 1-4)

### 2.1 Autenticação e Autorização
**2.1.1 Login/Logout (email/telefone)** - Implementar endpoint de autenticação que aceite email ou número de telefone combinado com senha, gerando token de acesso via Laravel Sanctum. Entregável: Endpoints /api/v1/login e /api/v1/logout.

**2.1.2 Recuperação de senha via email** - Implementar fluxo de recuperação de senha com envio de link por email, token válido por 60 minutos e formulário de redefinição. Entregável: Endpoints /api/v1/forgot-password e /api/v1/reset-password.

**2.1.3 Gestão de tokens (Sanctum)** - Configurar gerenciamento de tokens de acesso com expiração, revogação e capacidade de múltiplos tokens por utilizador. Entregável: Tokens com expiração configurada.

**2.1.4 Middleware de permissões (SuperAdmin, Admin, Client)** - Implementar middleware para verificação de perfil de utilizador, garantindo que cada endpoint seja acessível apenas pelo perfil autorizado. Entregável: Middlewares `role:super_admin`, `role:admin`, `role:client`.

### 2.2 Gestão de Utilizadores
**2.2.1 CRUD de Utilizadores (SuperAdmin)** - Implementar endpoints para criação, leitura, actualização e exclusão de utilizadores com perfil Admin, incluindo listagem paginada. Entregável: Endpoints /api/v1/admin/users.

**2.2.2 Validação de unicidade (email/telefone)** - Implementar validação no backend garantindo que email e telefone sejam únicos no sistema. Entregável: Validações com mensagens de erro claras.

**2.2.3 Geração de senha temporária** - Implementar geração de senha temporária e envio por email quando um novo Admin é criado. Entregável: Senha temporária enviada automaticamente.

### 2.3 Gestão de Clientes
**2.3.1 CRUD de Clientes** - Implementar endpoints para gestão completa de clientes, incluindo cadastro com todos os campos obrigatórios (nome, email, telefone, nacionalidade, NUIT, endereço, contrato). Entregável: Endpoints /api/v1/admin/clients.

**2.3.2 Validação de NUIT e contrato** - Implementar validações garantindo que NUIT e número de contrato sejam únicos no sistema. Entregável: Mensagens de erro para NUIT ou contrato duplicado.

**2.3.3 Histórico do cliente** - Implementar endpoints para consulta do histórico completo do cliente: facturas, pagamentos e vistorias. Entregável: Endpoints /api/v1/admin/clients/{id}/history.

### 2.4 Gestão de Contadores de Água
**2.4.1 CRUD de Contadores** - Implementar endpoints para gestão de contadores associados a cada cliente, com número do contador, data de instalação e status. Entregável: Endpoints /api/v1/admin/water-meters.

**2.4.2 Registo de leituras** - Implementar endpoint para registo de leituras com validação de que a leitura não é inferior à anterior. Entregável: Leitura registada com timestamp.

**2.4.3 Histórico de leituras** - Implementar endpoint para consulta do histórico de leituras por cliente, ordenado por data. Entregável: Histórico paginado.

### 2.5 Gestão de Localizações
**2.5.1 CRUD de Localizações** - Implementar endpoints para armazenar coordenadas geográficas (latitude, longitude) associadas a cada cliente. Entregável: Endpoints /api/v1/admin/locations.

**2.5.2 Validação de coordenadas** - Implementar validação garantindo que as coordenadas estejam dentro do território de Moçambique. Entregável: Validação geográfica implementada.

**2.5.3 Geocodificação reversa** - Implementar serviço para obter endereço a partir de coordenadas utilizando API Nominatim do OpenStreetMap. Entregável: Endereço preenchido automaticamente.

### 2.6 Vistorias e Facturação
**2.6.1 CRUD de Vistorias** - Implementar endpoints para registo de vistorias com campos: cliente, leitura anterior, leitura actual, consumo, observações, fotos, condição do contador. Entregável: Endpoints /api/v1/admin/inspections.

**2.6.2 Cálculo de Consumo** - Implementar lógica para calcular consumo em metros cúbicos pela diferença entre leitura actual e anterior. Entregável: Consumo calculado automaticamente.

**2.6.3 Cálculo de Factura (taxas/multas)** - Implementar serviço de cálculo que aplica as taxas configuradas: consumo <= mínimo cobra taxa mínima; consumo > mínimo cobra taxa mínima + adicional por excedente; aplicação de multa após vencimento. Entregável: Valor da factura calculado.

**2.6.4 Geração de PDF (DomPDF)** - Implementar geração de PDF para facturas, contendo dados da empresa, cliente, detalhes do consumo, cálculo dos valores e código de barras. Entregável: PDF com layout padronizado.

**2.6.5 Upload de fotos da vistoria** - Implementar endpoint para upload de múltiplas fotos durante a vistoria, com validação de tipo e tamanho. Entregável: Fotos armazenadas e associadas à vistoria.

### 2.7 Pagamentos
**2.7.1 CRUD de Pagamentos** - Implementar endpoints para registo de pagamentos com campos: cliente, factura, valor, método de pagamento, referência. Entregável: Endpoints /api/v1/admin/payments.

**2.7.2 Confirmação de Pagamentos** - Implementar endpoint para confirmação manual de pagamentos pelo Admin, com registo do nome do operário e data. Entregável: Pagamento confirmado e status da factura actualizado.

**2.7.3 Emissão de recibos** - Implementar geração de recibo com número de confirmação único, dados do pagamento e assinatura digital do operário. Entregável: Recibo em PDF.

**2.7.4 Atualização de status da factura** - Implementar lógica para atualizar o status da factura para "pago" quando o valor total for quitado, ou "parcial" quando houver pagamento incompleto. Entregável: Status actualizado automaticamente.

### 2.8 Configurações
**2.8.1 CRUD de Taxas** - Implementar endpoints para gestão de taxas: consumo mínimo, taxa mínima, taxa adicional por m³, percentagem de multa, dias para multa. Entregável: Endpoints /api/v1/admin/rates.

**2.8.2 CRUD de Comunicados** - Implementar endpoints para gestão de comunicados com título, conteúdo, categoria, agendamento de publicação e destaque. Entregável: Endpoints /api/v1/admin/announcements.

**2.8.3 Configurações do sistema** - Implementar endpoints para configurações gerais: dados da empresa, fuso horário, formato de data, moeda. Entregável: Endpoints /api/v1/admin/settings.

**2.8.4 Logs de auditoria** - Implementar registo de todas as acções dos utilizadores: quem, quando, qual acção, endereço IP. Entregável: Tabela activity_log populada.

### 2.9 Relatórios
**2.9.1 Relatório Financeiro** - Implementar endpoint que consolida dados financeiros: total facturado, total recebido, total pendente, inadimplência, com filtro por período. Entregável: Endpoint /api/v1/admin/reports/financial.

**2.9.2 Relatório de Consumo** - Implementar endpoint com dados de consumo: total, médio, por cliente, por bairro, com filtro por período. Entregável: Endpoint /api/v1/admin/reports/consumption.

**2.9.3 Relatório Operacional** - Implementar endpoint com dados operacionais: total de vistorias, desempenho por técnico, condição dos contadores, com filtro por período. Entregável: Endpoint /api/v1/admin/reports/operational.

**2.9.4 Exportação PDF** - Implementar exportação de relatórios em formato PDF com layout adequado para impressão. Entregável: PDF gerado.

**2.9.5 Exportação Excel** - Implementar exportação de relatórios em formato Excel utilizando Laravel Excel. Entregável: Arquivo XLSX gerado.

**2.9.6 Exportação CSV** - Implementar exportação de relatórios em formato CSV para análise em outras ferramentas. Entregável: Arquivo CSV gerado.

---

## 3.0 Frontend - React/TypeScript (Semana 2-7)

### 3.1 Componentes Base
**3.1.1 Sistema de Autenticação** - Implementar páginas de login, registro e recuperação de senha, com validação de formulários e integração com API. Entregável: Componentes Login, Register, ForgotPassword.

**3.1.2 Layout Responsivo** - Implementar layout base responsivo utilizando TailwindCSS, com adaptação para mobile, tablet e desktop. Entregável: Layout funcional em todos os breakpoints.

**3.1.3 Sidebar e Menu** - Implementar menu lateral com navegação baseada no perfil do utilizador, colapsável em mobile. Entregável: Sidebar com links dinâmicos.

**3.1.4 Header com notificações** - Implementar cabeçalho com indicador de notificações, seletor de idioma e tema, e menu do utilizador. Entregável: Header funcional.

**3.1.5 Internacionalização (i18n)** - Implementar sistema de tradução com suporte a 7 idiomas, persistência da escolha e lazy loading dos arquivos. Entregável: i18n configurado.

**3.1.6 Tema Claro/Escuro** - Implementar alternância entre tema claro e escuro com persistência via localStorage. Entregável: Toggle de tema funcional.

**3.1.7 Skeleton Loading** - Implementar componentes de skeleton loading para melhor experiência durante carregamento de dados. Entregável: Skeletons em todas as listas e cards.

### 3.2 Portal do Administrador
**3.2.1 Dashboard com Estatísticas** - Implementar dashboard com cards de estatísticas (clientes, facturas, pagamentos) e gráficos de consumo e receita. Entregável: Página /admin/dashboard.

**3.2.2 Gestão de Utilizadores** - Implementar CRUD de utilizadores com DataTable, formulários de criação/edição e confirmação de exclusão. Entregável: Páginas /admin/users.

**3.2.3 Gestão de Clientes** - Implementar CRUD de clientes com DataTable, formulário completo e busca por nome/contrato. Entregável: Páginas /admin/clients.

**3.2.4 Mapa de Clientes** - Implementar mapa interactivo com marcadores coloridos (vermelho/verde), pop-up com informações e filtros por status e bairro. Entregável: Página /admin/map.

**3.2.5 Vistorias (com mapa)** - Implementar página de vistoria com seleção de cliente, registo de leitura, cálculo automático e actualização do marcador. Entregável: Página /admin/inspections/create.

**3.2.6 Gestão de Facturas** - Implementar listagem de facturas com DataTable, visualização detalhada e download em PDF. Entregável: Páginas /admin/invoices.

**3.2.7 Gestão de Pagamentos** - Implementar listagem de pagamentos, confirmação manual de pagamentos e emissão de recibos. Entregável: Páginas /admin/payments.

**3.2.8 Gestão de Comunicados** - Implementar CRUD de comunicados com editor de texto, categorias e agendamento de publicação. Entregável: Páginas /admin/announcements.

**3.2.9 Gestão de Taxas** - Implementar formulário para configuração de taxas e multas, com histórico de alterações. Entregável: Páginas /admin/rates.

**3.2.10 Relatórios e Exportações** - Implementar interface para geração de relatórios com filtros de data e botões de exportação. Entregável: Páginas /admin/reports.

**3.2.11 Configurações do Sistema** - Implementar interface para configurações da empresa, notificações e segurança. Entregável: Páginas /admin/settings.

**3.2.12 Logs de Auditoria** - Implementar visualização de logs com filtros por utilizador, data e tipo de acção. Entregável: Páginas /admin/audit.

### 3.3 Portal do Cliente
**3.3.1 Dashboard Pessoal** - Implementar dashboard com resumo de facturas pendentes, consumo actual e último pagamento. Entregável: Página /client/dashboard.

**3.3.2 Minhas Facturas** - Implementar listagem de facturas com download em PDF e visualização detalhada. Entregável: Página /client/invoices.

**3.3.3 Meus Pagamentos** - Implementar listagem de pagamentos realizados com detalhes de data, valor e status. Entregável: Página /client/payments.

**3.3.4 Histórico de Consumo** - Implementar gráfico de consumo mensal e tabela com histórico completo. Entregável: Página /client/history.

**3.3.5 Mapa do Escritório** - Implementar mapa com localização da secretaria, detecção da posição do utilizador e traçado de rota. Entregável: Página /client/map.

**3.3.6 Perfil** - Implementar edição de dados pessoais, alteração de senha e upload de foto de perfil. Entregável: Página /client/profile.

### 3.4 Página Inicial (Welcome)
**3.4.1 Hero Section com Animação** - Implementar seção principal com título, subtítulo, botões de CTA e animação de entrada. Entregável: Hero animado.

**3.4.2 Estatísticas do Sistema** - Implementar seção com estatísticas reais (total de clientes, consumo mensal, etc) carregadas via API. Entregável: Cards de estatísticas.

**3.4.3 Lista de Comunicados** - Implementar seção com últimos comunicados publicados, ordenados por data. Entregável: Lista de comunicados.

**3.4.4 Features e Benefícios** - Implementar seção com os principais benefícios do sistema e como ele ajuda clientes e administradores. Entregável: Grid de features.

### 3.5 Componentes Comuns
**3.5.1 DataTables com i18n** - Implementar componente reutilizável de DataTable com busca, ordenação, paginação e suporte a múltiplos idiomas. Entregável: Componente DataTable.

**3.5.2 Mapas (OpenStreetMap + Leaflet)** - Implementar componente de mapa com marcadores, pop-ups, geolocalização e traçado de rotas. Entregável: Componente Map.

**3.5.3 Notificações Toast** - Implementar sistema de notificações toast para feedback de acções (sucesso, erro, aviso). Entregável: Componente Toast.

**3.5.4 Modais e Formulários** - Implementar componentes de modal e formulários reutilizáveis com validação. Entregável: Componentes Modal e Form.

**3.5.5 Gráficos (Recharts)** - Implementar componentes de gráficos reutilizáveis para visualização de dados. Entregável: Componentes de gráficos.

**3.5.6 Componentes de UI reutilizáveis** - Implementar biblioteca de componentes: botões, cards, inputs, selects, badges. Entregável: Storybook ou documentação de componentes.

---

## 4.0 Base de Dados (Semana 1-2)

### 4.1 Modelagem de Dados
**4.1.1 Diagrama ER** - Elaborar diagrama entidade-relacionamento com todas as 16 tabelas e seus relacionamentos. Entregável: Diagrama ER validado.

**4.1.2 Definição de relacionamentos** - Definir os relacionamentos entre as tabelas (1:N, N:N) e as constraints de integridade referencial. Entregável: Documento de relacionamentos.

### 4.2 Migrações (16 tabelas)
**4.2.1 users** - Criar migração para tabela de utilizadores com campos: id, name, email, phone, password, role, is_active, timestamps. Entregável: Migração users.

**4.2.2 clients** - Criar migração para tabela de clientes com campos: id, user_id, contract_number, full_name, phone, email, nationality, nuit, address, is_active. Entregável: Migração clients.

**4.2.3 water_meters** - Criar migração para tabela de contadores com campos: id, client_id, meter_number, last_reading, last_reading_date, installation_date, is_active. Entregável: Migração water_meters.

**4.2.4 announcements** - Criar migração para tabela de comunicados com campos: id, title, content, is_published, published_at, created_by. Entregável: Migração announcements.

**4.2.5 rates** - Criar migração para tabela de taxas com campos: id, name, minimum_consumption, minimum_fee, additional_fee_per_m3, late_fee_percentage, late_fee_days, is_active. Entregável: Migração rates.

**4.2.6 inspections** - Criar migração para tabela de vistorias com campos: id, client_id, water_meter_id, inspector_id, previous_reading, current_reading, consumption, notes, status, inspection_date. Entregável: Migração inspections.

**4.2.7 invoices** - Criar migração para tabela de facturas com campos: id, client_id, invoice_number, previous_reading, current_reading, consumption, minimum_fee, additional_fee, late_fee, total_amount, due_date, status, issued_by. Entregável: Migração invoices.

**4.2.8 payments** - Criar migração para tabela de pagamentos com campos: id, client_id, invoice_id, amount, payment_method, reference, status, payment_date, confirmed_by, confirmed_at. Entregável: Migração payments.

**4.2.9 locations** - Criar migração para tabela de localizações com campos: id, client_id, latitude, longitude, address, neighborhood, city, province, is_visited, last_visited_at. Entregável: Migração locations.

**4.2.10 office_locations** - Criar migração para tabela de escritórios com campos: id, name, address, latitude, longitude, phone, email, opening_hours, is_active. Entregável: Migração office_locations.

**4.2.11 media** - Criar migração para tabela de mídia com campos: id, mediable_type, mediable_id, path, type, uploaded_by. Entregável: Migração media.

**4.2.12 notifications** - Criar migração para tabela de notificações (Laravel padrão). Entregável: Migração notifications.

**4.2.13 activity_log** - Criar migração para tabela de logs de actividade com campos: id, log_name, description, subject_type, subject_id, causer_type, causer_id, properties. Entregável: Migração activity_log.

**4.2.14 jobs** - Criar migração para tabela de jobs (Laravel padrão). Entregável: Migração jobs.

**4.2.15 failed_jobs** - Criar migração para tabela de jobs falhados (Laravel padrão). Entregável: Migração failed_jobs.

**4.2.16 cache** - Criar migração para tabela de cache (Laravel padrão). Entregável: Migração cache.

### 4.3 Seeders
**4.3.1 UserSeeder (SuperAdmin, Admin, Clientes)** - Criar seeder que popula dados iniciais: SuperAdmin, Admin e 10 clientes de exemplo. Entregável: Dados de teste carregados.

**4.3.2 RateSeeder (taxas padrão)** - Criar seeder com taxas padrão: consumo mínimo 5m³, taxa mínima 275 MT, taxa adicional 50 MT, multa 10% após 10 dias. Entregável: Taxas carregadas.

### 4.4 Índices e Otimização
**4.4.1 Índices para consultas frequentes** - Criar índices para campos frequentemente consultados: email, phone, contract_number, status, created_at. Entregável: Índices criados.

**4.4.2 Otimização de queries** - Revisar e otimizar queries complexas, especialmente para relatórios e consultas com joins. Entregável: Queries optimizadas.

---

## 5.0 Testes (Semana 4-8)

### 5.1 Testes Unitários (PHPUnit)
**5.1.1 Testes de Modelos** - Criar testes unitários para os modelos Eloquent, validando relacionamentos e atributos. Entregável: Testes para todos os modelos.

**5.1.2 Testes de Controllers** - Criar testes unitários para os controllers, validando respostas e status HTTP. Entregável: Testes para controllers principais.

**5.1.3 Testes de Serviços** - Criar testes unitários para a camada de serviços, especialmente cálculo de facturas e taxas. Entregável: Testes para InvoiceCalculationService.

### 5.2 Testes de Integração
**5.2.1 Fluxos de autenticação** - Criar testes de integração para login, registro, recuperação de senha e logout. Entregável: Testes de autenticação.

**5.2.2 Fluxos de vistoria** - Criar testes de integração para o ciclo completo de vistoria: seleção de cliente, registo de leitura, cálculo de consumo, geração de factura. Entregável: Testes de vistoria.

**5.2.3 Fluxos de pagamento** - Criar testes de integração para registro e confirmação de pagamentos. Entregável: Testes de pagamento.

### 5.3 Testes End-to-End (Cypress)
**5.3.1 Cenários de login** - Criar testes E2E para login bem-sucedido, falha de credenciais e recuperação de senha. Entregável: Testes de login.

**5.3.2 Cadastro de cliente** - Criar testes E2E para cadastro de cliente, validação de campos e confirmação. Entregável: Testes de cadastro.

**5.3.3 Vistoria completa** - Criar testes E2E para o fluxo completo de vistoria: navegação, seleção, leitura, geração de factura. Entregável: Testes de vistoria.

### 5.4 Testes de Aceitação
**5.4.1 Validação com stakeholders** - Realizar sessões de validação com stakeholders para verificar se os requisitos foram atendidos. Entregável: Relatório de validação.

**5.4.2 Testes de usabilidade** - Realizar testes de usabilidade com utilizadores reais para identificar melhorias na interface. Entregável: Relatório de usabilidade.

---

## 6.0 Documentação (Semana 7-8)

### 6.1 Documentação Técnica
**6.1.1 README.md** - Criar documentação principal do projeto com visão geral, instalação, configuração e execução. Entregável: README.md completo.

**6.1.2 Guia de instalação** - Criar guia detalhado de instalação para desenvolvimento e produção. Entregável: INSTALL.md.

**6.1.3 Guia de deploy** - Criar guia de deploy em servidores Linux com Nginx e Supervisor. Entregável: DEPLOY.md.

**6.1.4 Código comentado** - Revisar e adicionar comentários em métodos complexos e pontos críticos do código. Entregável: Código documentado.

### 6.2 Guia do Utilizador
**6.2.1 Manual do SuperAdmin** - Criar manual completo para SuperAdmin: gestão de utilizadores, configurações, auditoria. Entregável: PDF manual.

**6.2.2 Manual do Admin** - Criar manual para Admin: gestão de clientes, vistorias, facturas, pagamentos. Entregável: PDF manual.

**6.2.3 Manual do Cliente** - Criar manual para cliente: acesso ao portal, visualização de facturas, pagamentos, mapa. Entregável: PDF manual.

### 6.3 API Documentation (Swagger)
**6.3.1 Endpoints de autenticação** - Documentar todos os endpoints de autenticação com exemplos de requisição e resposta. Entregável: Documentação Swagger.

**6.3.2 Endpoints de admin** - Documentar todos os endpoints administrativos com autenticação e permissões. Entregável: Documentação Swagger.

**6.3.3 Endpoints de cliente** - Documentar todos os endpoints do portal do cliente. Entregável: Documentação Swagger.

### 6.4 Deploy Guide
**6.4.1 Requisitos de servidor** - Listar requisitos de servidor: PHP versão, extensões, banco de dados, recursos. Entregável: Checklist de requisitos.

**6.4.2 Configuração Nginx/Apache** - Fornecer configurações de exemplo para Nginx e Apache. Entregável: Arquivos de configuração.

**6.4.3 Configuração de backup** - Fornecer scripts e configurações para backup automático do banco de dados e arquivos. Entregável: Scripts de backup.

---

## 7.0 Implantação (Semana 8)

### 7.1 Configuração do Servidor
**7.1.1 Provisionamento** - Provisionar servidor de produção com sistema operacional, atualizações de segurança e dependências. Entregável: Servidor provisionado.

**7.1.2 Instalação de dependências** - Instalar PHP, Composer, Node, MySQL, Nginx, Supervisor e Redis. Entregável: Dependências instaladas.

**7.1.3 Configuração de firewall** - Configurar firewall permitindo apenas portas 22 (SSH), 80 (HTTP), 443 (HTTPS). Entregável: Firewall configurado.

### 7.2 Deploy da Aplicação
**7.2.1 Deploy do código** - Realizar deploy do código fonte no servidor de produção a partir do repositório. Entregável: Código em produção.

**7.2.2 Migrações em produção** - Executar migrações e seeders no banco de dados de produção. Entregável: Banco de dados populado.

**7.2.3 Otimização (cache)** - Executar comandos de otimização: config:cache, route:cache, view:cache. Entregável: Cache configurado.

### 7.3 Configuração de Backup
**7.3.1 Backup de banco de dados** - Configurar backup diário do banco de dados com retenção de 30 dias. Entregável: Script de backup.

**7.3.2 Backup de arquivos** - Configurar backup dos arquivos de upload e logs. Entregável: Backup configurado.

**7.3.3 Teste de restauração** - Realizar teste de restauração dos backups para validar integridade. Entregável: Teste documentado.

### 7.4 Treinamento de Utilizadores
**7.4.1 Treinamento SuperAdmin** - Realizar treinamento com SuperAdmin sobre gestão de utilizadores, configurações e auditoria. Entregável: Treinamento concluído.

**7.4.2 Treinamento Admins** - Realizar treinamento com Admins sobre gestão de clientes, vistorias, facturas e pagamentos. Entregável: Treinamento concluído.

**7.4.3 Material de apoio** - Fornecer material de apoio: manuais em PDF, vídeos tutoriais, FAQ. Entregável: Material entregue.











---

## 📊 Pacotes de Trabalho por Sprint

### Sprint 1 (Semana 1-2) - 12 pontos

| ID | Pacote | Estimativa | Responsável |
|----|--------|------------|-------------|
| 1.0 | Planeamento | 2d | Todos |
| 2.1 | Autenticação | 3d | Backend |
| 2.2 | Gestão de Utilizadores | 3d | Backend |
| 3.1 | Componentes Base | 4d | Frontend |
| 4.0 | Base de Dados | 2d | Backend |

### Sprint 2 (Semana 3-4) - 14 pontos

| ID | Pacote | Estimativa | Responsável |
|----|--------|------------|-------------|
| 2.3 | Gestão de Clientes | 3d | Backend |
| 2.4 | Gestão de Contadores | 2d | Backend |
| 2.5 | Gestão de Localizações | 2d | Backend |
| 3.2.1-3 | Admin - Clientes | 4d | Frontend |
| 3.5.2 | Mapas | 3d | Frontend |

### Sprint 3 (Semana 5-6) - 16 pontos

| ID | Pacote | Estimativa | Responsável |
|----|--------|------------|-------------|
| 2.6 | Vistorias e Facturação | 5d | Backend |
| 2.7 | Pagamentos | 3d | Backend |
| 2.8.1 | Configuração de Taxas | 2d | Backend |
| 3.2.4-7 | Admin - Vistorias/Facturas | 4d | Frontend |
| 3.5.1 | DataTables | 2d | Frontend |

### Sprint 4 (Semana 7-8) - 26 pontos

| ID | Pacote | Estimativa | Responsável |
|----|--------|------------|-------------|
| 2.8.2 | Comunicados | 2d | Backend |
| 2.9 | Relatórios | 4d | Backend |
| 3.2.8-12 | Admin - Configurações/Relatórios | 4d | Frontend |
| 3.3 | Portal do Cliente | 4d | Frontend |
| 3.4 | Página Inicial | 2d | Frontend |
| 5.0 | Testes | 4d | QA |
| 6.0 | Documentação | 3d | Tech Lead |
| 7.0 | Implantação | 3d | DevOps |
