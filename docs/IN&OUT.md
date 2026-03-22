# SGAA - Escopo do Projeto (IN & OUT)

## 📌 Escopo do Projeto (IN)

### 1. Autenticação e Segurança
- [x] Login por email ou número de telefone com senha
- [x] Recuperação de senha via email com link seguro (token válido por 60 minutos)
- [x] Três níveis de acesso: SuperAdmin, Admin, Cliente
- [x] Middleware para controlo de permissões por rota
- [x] Protecção contra SQL Injection, XSS e CSRF
- [x] Logout com invalidação de token

### 2. Gestão de Utilizadores
- [x] SuperAdmin pode criar, editar, activar/desactivar e eliminar Admins
- [x] Validação de unicidade de email e telefone
- [x] Geração de senha temporária enviada por email

### 3. Gestão de Clientes
- [x] Cadastro completo de clientes com: nome, email, telefone, nacionalidade, NUIT, endereço, contrato
- [x] Edição de dados do cliente
- [x] Activação/desactivação de cliente
- [x] Histórico completo do cliente (facturas, pagamentos, vistorias)
- [x] Validação de unicidade de NUIT e número de contrato

### 4. Gestão de Contadores de Água
- [x] Registo de número do contador
- [x] Registo de leitura inicial
- [x] Histórico de leituras
- [x] Data de instalação
- [x] Status de activação do contador

### 5. Geolocalização e Mapas
- [x] Marcação de residências no mapa OpenStreetMap
- [x] Busca por endereço, bairro, avenida, município
- [x] Visualização de todos os clientes com marcadores coloridos (vermelho = não visitado, verde = visitado)
- [x] Pop-up com informações do cliente ao clicar no marcador
- [x] Traçado de rota optimizada para vistorias
- [x] Exibição de distância total e tempo estimado
- [x] Mapa da secretaria mais próxima para clientes
- [x] Rota desde localização actual do cliente até à secretaria

### 6. Vistorias Técnicas
- [x] Seleção de cliente por nome ou mapa
- [x] Visualização da leitura anterior automaticamente
- [x] Registo da leitura actual
- [x] Cálculo automático do consumo (diferença entre leituras)
- [x] Upload de fotos da vistoria
- [x] Campo para observações
- [x] Registo de condição do contador (bom, com defeito, danificado)
- [x] Actualização automática do marcador para verde após vistoria
- [x] Histórico de vistorias por cliente

### 7. Facturação
- [x] Geração automática de factura após vistoria
- [x] Cálculo: consumo ≤ mínimo → taxa mínima
- [x] Cálculo: consumo > mínimo → taxa mínima + (excedente × taxa adicional)
- [x] Aplicação de multa após dias configurados
- [x] Número de factura sequencial único
- [x] Data de emissão e vencimento
- [x] Status da factura (pendente, pago, vencido, cancelado, parcial)
- [x] Emissão de PDF da factura

### 8. Gestão de Taxas e Multas
- [x] Configuração de consumo mínimo (m³)
- [x] Configuração de taxa mínima (MT)
- [x] Configuração de taxa adicional por m³ excedente (MT)
- [x] Configuração de percentagem de multa (%)
- [x] Configuração de dias para início da multa
- [x] Histórico de alterações de taxas

### 9. Gestão de Pagamentos
- [x] Registo de pagamentos com valor e método
- [x] Múltiplos métodos: dinheiro, transferência bancária, dinheiro móvel, cartão, cheque
- [x] Confirmação manual de pagamentos pelo Admin
- [x] Registo do nome do operário e data
- [x] Emissão de recibo com número de confirmação
- [x] Atualização automática do status da factura
- [x] Histórico de pagamentos por cliente

### 10. Portal do Cliente
- [x] Visualização de todas as facturas
- [x] Download de facturas em PDF
- [x] Gráfico de consumo mensal
- [x] Histórico de pagamentos
- [x] Mapa da secretaria com rota
- [x] Detalhamento de valores (taxas, multas)

### 11. Gestão de Comunicados
- [x] Criação, edição e remoção de comunicados
- [x] Título, conteúdo, categoria (geral, importante, emergência)
- [x] Publicação agendada
- [x] Visualização na página inicial e portal do cliente
- [x] Destaque para comunicados importantes

### 12. Relatórios Gerenciais
- [x] Relatório Financeiro: total facturado, recebido, pendente, inadimplência
- [x] Relatório de Consumo: total, médio, por bairro
- [x] Relatório Operacional: vistorias, desempenho por técnico, condição dos contadores
- [x] Filtro por período (data inicial e final)
- [x] Exportação em PDF, Excel e CSV

### 13. Perfil do Utilizador
- [x] Edição de dados pessoais
- [x] Alteração de senha com confirmação
- [x] Upload de foto de perfil
- [x] Visualização de sessões activas
- [x] Encerramento de sessões remotas

### 14. Internacionalização
- [x] Português de Moçambique (padrão)
- [x] Português do Brasil
- [x] Português de Portugal
- [x] Inglês
- [x] Chinês Mandarim
- [x] Árabe
- [x] Russo
- [x] Persistência da escolha do idioma

### 15. Interface e Experiência
- [x] Tema claro/escuro com persistência
- [x] Design responsivo (mobile-first)
- [x] Skeleton loading durante carregamento
- [x] Animações suaves (Framer Motion)
- [x] Feedback visual para todas as acções
- [x] DataTables com busca e paginação
- [x] Gráficos interativos (Recharts)

### 16. Notificações
- [x] Centro de notificações
- [x] Notificações de vencimento de factura
- [x] Notificações de confirmação de pagamento
- [x] Notificações de novos comunicados
- [x] Marcação de notificações como lidas

### 17. Auditoria
- [x] Registo de actividades dos utilizadores
- [x] Logs de tentativas de login
- [x] Histórico de alterações em dados críticos

### 18. Segurança e Backup
- [x] Backup automático diário
- [x] Restauração de backup
- [x] Retenção de 30 dias

---

## ❌ Fora do Escopo (OUT)

### Versão 1.0 (MVP) - Excluído
| Item | Motivo |
|------|--------|
| Aplicativo mobile nativo | Planeado para versão 2.0 |
| Integração com pagamentos online (API bancária) | Complexidade e dependências externas |
| Notificações push (Firebase) | Versão 2.0 |
| Leitura automática de contadores (IoT) | Versão 3.0 |
| Faturação electrónica  | Dependência de API externa |
| Múltiplas empresas (multi-tenancy) | Não previsto no escopo actual |
| Integração com SMS Gateway | Versão 2.0 |
| Chat online para suporte | Versão 2.0 |
| Reconhecimento facial para login | Não previsto |

### Funcionalidades Não Incluídas
| Categoria | Funcionalidade |
|-----------|----------------|
| **Hardware** | Leitura automática de contadores, sensores de vazamento |
| **Integrações** | ERP, sistemas contabilísticos, plataformas de pagamento externas |
| **Mobile** | Aplicativos iOS/Android nativos |
| **Marketing** | Campanhas de email marketing, SMS marketing |
| **Suporte** | Chat online, ticket de suporte |
| **Documentos** | Assinatura digital de contratos |
| **Workflow** | Aprovações em múltiplos níveis |

### Restrições Técnicas
| Restrição | Descrição |
|-----------|-----------|
| **Ambiente** | Apenas web (não há aplicativo desktop) |
| **Navegadores** | Suporte apenas às 2 versões mais recentes |
| **Offline** | Não suporta modo offline |
| **Escala** | Limitado a 100.000 clientes activos |
| **Backup** | Manual ou agendado, não em tempo real |

---

## 📊 Prioridades para o MVP

| Prioridade | Funcionalidades Incluídas |
|------------|---------------------------|
| **Must Have** | Autenticação, gestão de clientes, vistorias, facturação, pagamentos |
| **Should Have** | Mapas, rotas optimizadas, portal do cliente, relatórios básicos |
| **Could Have** | Multi-idioma completo, tema escuro, notificações push |
| **Won't Have** | Integrações externas, app mobile, IoT |

---

## ✅ Critérios de Aceitação do Escopo

1. **Todas as funcionalidades listadas em IN devem ser entregues**
2. **Nenhuma funcionalidade listada em OUT será entregue na versão 1.0**
3. **Alterações de escopo requerem aprovação formal do Product Owner**
4. **Documentação de alterações mantida no changelog**

