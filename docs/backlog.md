# SGAA - Product Backlog

## 📊 Visão Geral

| Métrica | Valor |
|---------|-------|
| **Total de User Stories** | 20 |
| **Must Have (MVP)** | 12 |
| **Should Have** | 5 |
| **Could Have** | 3 |
| **Won't Have (v1.0)** | 0 |
| **Total Pontos de Estimativa** | 65 |

---

## 🎯 User Stories

| ID | USER STORY | Critérios de Aceitação | Prioridade | Estimativa |
|----|------------|------------------------|------------|------------|
| **US01** | Como utilizador, quero fazer login com email ou telefone e senha, para aceder ao sistema | 1. Login aceita email ou telefone válido<br>2. Senha com mínimo 8 caracteres<br>3. Mensagem de erro clara para credenciais inválidas<br>4. Redirecionamento correto baseado no perfil<br>5. Conta inativa exibe mensagem apropriada | **Must** | M (3) |
| **US02** | Como utilizador, quero recuperar minha senha através do email, para redefinir acesso | 1. Link de recuperação enviado por email<br>2. Token válido por 60 minutos<br>3. Redefinição exige confirmação da nova senha<br>4. Senha nova segue política de complexidade<br>5. Notificação por email após alteração | **Must** | M (3) |
| **US03** | Como SuperAdmin, quero criar novos utilizadores (Admins), para delegar responsabilidades | 1. Campos obrigatórios: nome, email, telefone, senha<br>2. Validação de email e telefone únicos<br>3. Definição do perfil (Admin apenas)<br>4. Opção de activar/desactivar utilizador<br>5. Senha temporária gerada e enviada por email | **Must** | M (3) |
| **US04** | Como Admin, quero cadastrar novos clientes com dados completos, para registar no sistema | 1. Campos: nome completo, email, telefone, nacionalidade, NUIT, endereço, nº contrato<br>2. Validação de unicidade de NUIT e contrato<br>3. Registo automático de utilizador associado<br>4. Opção de marcar localização no mapa<br>5. Criar contador com leitura inicial | **Must** | C (5) |
| **US05** | Como Admin, quero marcar a localização do cliente no mapa, para georreferenciar residências | 1. Mapa interativo com OpenStreetMap<br>2. Busca por endereço/bairro/avenida<br>3. Marcação manual arrastando marcador<br>4. Salvamento automático das coordenadas<br>5. Validação de que o marcador está dentro de Moçambique | **Must** | C (5) |
| **US06** | Como Admin, quero realizar vistorias e registar leituras do contador, para calcular consumo | 1. Seleção do cliente por nome ou mapa<br>2. Exibição da leitura anterior automaticamente<br>3. Campo para leitura actual<br>4. Cálculo automático do consumo<br>5. Geração automática de factura após confirmação | **Must** | C (5) |
| **US07** | Como Admin, quero que o sistema calcule automaticamente o valor da factura, para facilitar cobrança | 1. Consumo <= consumo mínimo: cobrar taxa mínima<br>2. Consumo > consumo mínimo: taxa mínima + (excedente × taxa adicional)<br>3. Aplicação de multa após X dias de vencimento<br>4. Cálculo em tempo real durante vistoria<br>5. Exibição do valor calculado antes da confirmação | **Must** | M (3) |
| **US08** | Como Admin, quero ver todos os clientes no mapa, para planificar vistorias | 1. Marcadores coloridos: vermelho = não visitado, verde = visitado<br>2. Pop-up com informações do cliente ao clicar<br>3. Filtro por status de visita<br>4. Filtro por bairro/zona<br>5. Zoom automático para área de concentração | **Must** | M (3) |
| **US09** | Como Admin, quero traçar rota optimizada para vistorias, para reduzir tempo de deslocamento | 1. Botão "Calcular Rotas" para pontos não visitados<br>2. Exibição da ordem optimizada de visita<br>3. Visualização da rota no mapa<br>4. Distância total e tempo estimado<br>5. Opção de salvar rota para referência | **Should** | C (5) |
| **US10** | Como Admin, quero que o marcador mude de cor após vistoria, para saber quais casas já visitei | 1. Marcador muda de vermelho para verde automaticamente<br>2. Actualização em tempo real no mapa<br>3. Registo da data/hora da última visita<br>4. Histórico de visitas disponível<br>5. Indicador de quantas visitas realizadas | **Must** | S (1) |
| **US11** | Como Admin, quero configurar taxas e multas, para definir política de cobrança | 1. Configuração de: consumo mínimo (m³), taxa mínima (MT), taxa adicional (MT/m³)<br>2. Configuração de: percentagem de multa (%), dias para aplicar multa<br>3. Validação de campos numéricos positivos<br>4. Opção de activar/desactivar taxas<br>5. Histórico de alterações | **Should** | M (3) |
| **US12** | Como Admin, quero confirmar pagamentos, para actualizar status de facturas | 1. Lista de pagamentos pendentes<br>2. Campo para referência/código de confirmação<br>3. Botão "Confirmar" que carimba a factura<br>4. Registo do nome do operário e data<br>5. Emissão automática de recibo | **Must** | M (3) |
| **US13** | Como Cliente, quero ver minhas facturas e consumos, para acompanhar despesas | 1. Lista de facturas com data, valor e status<br>2. Filtro por período (mês/ano)<br>3. Download de factura em PDF<br>4. Gráfico de consumo mensal<br>5. Detalhamento dos valores (taxas, multas) | **Must** | M (3) |
| **US14** | Como Cliente, quero ver a localização da secretaria no mapa, para me dirigir ao escritório | 1. Mapa com marcador da secretaria<br>2. Detecção automática da localização do utilizador<br>3. Traçado da rota mais próxima<br>4. Destacar a rota a vermelho<br>55. Instruções passo-a-passo | **Should** | M (3) |
| **US15** | Como utilizador, quero alterar idioma e tema, para personalizar experiência | 1. Alternância entre 7 idiomas<br>2. Persistência da escolha do idioma<br>3. Alternância entre tema claro/escuro<br>4. Persistência do tema<br>5. Tradução de todas as interfaces | **Should** | M (3) |
| **US16** | Como utilizador, quero editar meu perfil, para manter dados actualizados | 1. Edição de nome, email, telefone<br>2. Upload de foto de perfil<br>3. Alteração de senha com confirmação<br>4. Validação de dados únicos<br>5. Visualização de sessões activas | **Must** | M (3) |
| **US17** | Como Admin, quero gerar relatórios, para análise de desempenho | 1. Relatório financeiro: receitas, pagamentos, inadimplência<br>2. Relatório de consumo: total, médio, por bairro<br>3. Relatório operacional: vistorias, desempenho por inspector<br>4. Exportação em PDF, Excel e CSV<br>5. Filtro por período (data inicial/final) | **Could** | C (5) |
| **US18** | Como SuperAdmin, quero visualizar logs do sistema, para auditoria | 1. Lista de actividades dos utilizadores<br>2. Filtro por utilizador, data, acção<br>3. Detalhamento do IP e user agent<br>4. Exportação de logs<br>5. Retenção de 90 dias | **Could** | M (3) |
| **US19** | Como Admin, quero publicar comunicados, para informar clientes | 1. Editor de texto para conteúdo<br>2. Categorias: geral, importante, emergência<br>3. Agendamento de publicação<br>4. Visualização na página inicial e portal<br>5. Destaque visual para importantes | **Should** | M (3) |
| **US20** | Como utilizador, quero receber notificações, para não perder prazos | 1. Notificações de vencimento de factura<br>2. Notificações de confirmação de pagamento<br>3. Centro de notificações<br>4. Marcação como lida<br>5. Indicador de não lidas | **Could** | M (3) |

---

## 📈 Sprint Backlog

### Sprint 1 (Semana 1-2) - Base e Autenticação

| ID | User Story | Estimativa |
|----|------------|------------|
| US01 | Login com email/telefone | 3 |
| US02 | Recuperação de senha | 3 |
| US03 | Gestão de utilizadores (SuperAdmin) | 3 |
| US16 | Edição de perfil | 3 |
| **Total** | | **12** |

### Sprint 2 (Semana 3-4) - Clientes e Mapas

| ID | User Story | Estimativa |
|----|------------|------------|
| US04 | Cadastro de clientes | 5 |
| US05 | Marcação de localização no mapa | 5 |
| US08 | Visualização de clientes no mapa | 3 |
| US10 | Mudança de cor do marcador | 1 |
| **Total** | | **14** |

### Sprint 3 (Semana 5-6) - Vistorias e Facturação

| ID | User Story | Estimativa |
|----|------------|------------|
| US06 | Realização de vistorias | 5 |
| US07 | Cálculo automático de factura | 3 |
| US11 | Configuração de taxas | 3 |
| US09 | Traçado de rota optimizada | 5 |
| **Total** | | **16** |

### Sprint 4 (Semana 7) - Pagamentos e Finalização

| ID | User Story | Estimativa |
|----|------------|------------|
| US12 | Confirmação de pagamentos | 3 |
| US13 | Portal do cliente (facturas) | 3 |
| US14 | Mapa da secretaria com rota | 3 |
| US15 | Multi-idioma e tema | 3 |
| US17 | Relatórios gerenciais | 5 |
| US18 | Logs de auditoria | 3 |
| US19 | Comunicados | 3 |
| US20 | Notificações | 3 |
| **Total** | | **26** |

