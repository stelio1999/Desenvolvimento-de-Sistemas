# SGAA - Cronograma do Projeto

## 📅 Linha do Tempo - 8 Semanas

| Semana | Período | Sprint | Marcos | Entregas |
|--------|---------|--------|--------|----------|
| **Semana 1** | 01/03 - 07/03 | Sprint 1 | Kick-off e Planeamento | • Product Backlog validado<br>• Arquitectura técnica definida<br>• Ambiente configurado |
| **Semana 2** | 08/03 - 14/03 | Sprint 1 | Base do Sistema | • Autenticação multi-nível<br>• CRUD Utilizadores<br>• Recuperação de senha<br>• Perfil do utilizador |
| **Semana 3** | 15/03 - 21/03 | Sprint 2 | Gestão de Clientes | • CRUD Clientes<br>• Gestão de Contadores<br>• Mapa interactivo<br>• Marcadores de clientes |
| **Semana 4** | 22/03 - 28/03 | Sprint 2 | Mapas e Localizações | • Busca por endereço<br>• Marcação manual<br>• Filtros no mapa<br>• Validação geográfica |
| **Semana 5** | 29/03 - 04/04 | Sprint 3 | Vistorias e Facturação | • Registo de leituras<br>• Cálculo de consumo<br>• Geração de facturas<br>• Configuração de taxas |
| **Semana 6** | 05/04 - 11/04 | Sprint 3 | Rotas e Optimização | • Traçado de rota optimizada<br>• Cálculo de distância<br>• Actualização de status<br>• Histórico de vistorias |
| **Semana 7** | 12/04 - 18/04 | Sprint 4 | Pagamentos e Cliente | • Confirmação de pagamentos<br>• Portal do cliente<br>• Mapa da secretaria<br>• Multi-idioma e tema |
| **Semana 8** | 19/04 - 25/04 | Sprint 4 | Finalização e Deploy | • Relatórios<br>• Testes completos<br>• Documentação<br>• Deploy em produção |

---

## 🎯 Marcos Principais (Milestones)

| ID | Marco | Data | Descrição | Critério de Aceitação |
|----|-------|------|-----------|----------------------|
| **M1** | Kick-off | 01/03 | Início oficial do projecto | • Backlog validado<br>• Ambiente configurado |
| **M2** | Base do Sistema | 14/03 | Autenticação e utilizadores funcionais | • Login/Logout funcional<br>• Recuperação de senha<br>• CRUD de Admins |
| **M3** | Clientes e Mapas | 28/03 | Cadastro e geolocalização completos | • 50 clientes cadastrados<br>• Marcadores no mapa<br>• Busca funcional |
| **M4** | Vistorias | 11/04 | Ciclo completo de vistoria | • Leitura registada<br>• Consumo calculado<br>• Factura gerada |
| **M5** | Portal do Cliente | 18/04 | Funcionalidades para cliente | • Facturas visíveis<br>• Download PDF<br>• Mapa da secretaria |
| **M6** | Sistema Completo | 25/04 | Todas as funcionalidades entregues | • Relatórios gerados<br>• Testes aprovados<br>• Documentação entregue |
| **M7** | Go-Live | 28/04 | Sistema em produção | • Deploy realizado<br>• Backup configurado<br>• Treinamento concluído |

---

## 📊 Dependências

| Dependência | Descrição | Impacto | Mitigação |
|-------------|-----------|---------|-----------|
| **D01** | Aprovação de requisitos | Atraso no início | Reunião de alinhamento na Semana 0 |
| **D02** | Disponibilidade | Capacidade reduzida | Buffer de 15% no cronograma |
| **D03** | Servidor de produção | Deploy atrasado | Ambiente de staging desde Semana 2 |
| **D04** | API de mapas | Funcionalidade comprometida | Fallback para coordenadas manuais |
| **D05** | Serviço de email | Recuperação de senha | Configuração SMTP na Semana 1 |

---

## 🕐 Cronograma Detalhado - Sprint 1 (Semana 1-2)

| Dia | Atividade | Responsável | Duração |
|-----|-----------|-------------|---------|
| **Dia 1** | Kick-off e alinhamento | Eu | 4h |
| **Dia 1** | Configuração do ambiente | DevOps | 4h |
| **Dia 2** | Definição da arquitectura | Tech Lead | 4h |
| **Dia 2** | Criação das migrações base | Backend | 4h |
| **Dia 3** | Implementação da autenticação | Backend | 6h |
| **Dia 3** | Testes unitários | QA | 2h |
| **Dia 4** | CRUD de utilizadores | Backend | 6h |
| **Dia 4** | Componentes de login | Frontend | 4h |
| **Dia 5** | Recuperação de senha | Backend | 4h |
| **Dia 5** | Página de perfil | Frontend | 4h |
| **Dia 6** | Middleware de permissões | Backend | 4h |
| **Dia 6** | Sidebar e navegação | Frontend | 4h |
| **Dia 7** | Testes de integração | QA | 4h |
| **Dia 7** | Revisão de código | Tech Lead | 2h |
| **Dia 8-10** | Buffer de contingência | - | - |

---

## 🕐 Cronograma Detalhado - Sprint 2 (Semana 3-4)

| Dia | Atividade | Responsável | Duração |
|-----|-----------|-------------|---------|
| **Dia 1** | Planeamento Sprint 2 | Eu | 2h |
| **Dia 1-2** | CRUD de clientes | Backend | 12h |
| **Dia 2-3** | Formulário de cliente | Frontend | 8h |
| **Dia 3** | Gestão de contadores | Backend | 4h |
| **Dia 4** | Integração OpenStreetMap | Frontend | 6h |
| **Dia 4-5** | Marcadores e pop-ups | Frontend | 8h |
| **Dia 5** | Busca geográfica | Frontend | 4h |
| **Dia 6** | Filtros no mapa | Frontend | 4h |
| **Dia 6-7** | Validação de coordenadas | Backend | 4h |
| **Dia 7** | Testes de integração | QA | 4h |
| **Dia 7** | Revisão de código | Tech Lead | 2h |
| **Dia 8-10** | Buffer de contingência | - | - |

---

## 🕐 Cronograma Detalhado - Sprint 3 (Semana 5-6)

| Dia | Atividade | Responsável | Duração |
|-----|-----------|-------------|---------|
| **Dia 1** | Planeamento Sprint 3 | Eu | 2h |
| **Dia 1-2** | Registo de vistorias | Backend | 12h |
| **Dia 2-3** | Interface de vistoria | Frontend | 8h |
| **Dia 3** | Cálculo de consumo | Backend | 4h |
| **Dia 4** | Geração de facturas | Backend | 6h |
| **Dia 4-5** | Visualização de facturas | Frontend | 6h |
| **Dia 5** | Configuração de taxas | Backend | 4h |
| **Dia 5-6** | Interface de taxas | Frontend | 4h |
| **Dia 6** | Traçado de rotas | Backend | 6h |
| **Dia 6-7** | Visualização de rotas | Frontend | 6h |
| **Dia 7** | Testes de integração | QA | 4h |
| **Dia 7** | Revisão de código | Tech Lead | 2h |
| **Dia 8-10** | Buffer de contingência | - | - |

---

## 🕐 Cronograma Detalhado - Sprint 4 (Semana 7-8)

| Dia | Atividade | Responsável | Duração |
|-----|-----------|-------------|---------|
| **Dia 1** | Planeamento Sprint 4 | Eu | 2h |
| **Dia 1-2** | Confirmação de pagamentos | Backend | 8h |
| **Dia 2-3** | Interface de pagamentos | Frontend | 8h |
| **Dia 3** | Portal do cliente | Frontend | 6h |
| **Dia 4** | Mapa da secretaria | Frontend | 6h |
| **Dia 4-5** | Multi-idioma (i18n) | Frontend | 8h |
| **Dia 5** | Tema claro/escuro | Frontend | 4h |
| **Dia 5-6** | Relatórios | Backend | 8h |
| **Dia 6-7** | Interface de relatórios | Frontend | 6h |
| **Dia 7** | Testes end-to-end | QA | 6h |
| **Dia 7** | Documentação | Tech Lead | 4h |
| **Dia 8** | Deploy em staging | DevOps | 4h |
| **Dia 8** | Treinamento de utilizadores | Product Owner | 4h |
| **Dia 8** | Deploy em produção | DevOps | 2h |
| **Dia 8-10** | Buffer de contingência | - | - |



---

## ⚠️ Riscos ao Cronograma

| Risco | Probabilidade | Impacto | Mitigação |
|-------|---------------|---------|-----------|
| Atraso na aprovação de requisitos | Média | Alto | Reuniões semanais de alinhamento |
| Falta de disponibilidade da equipa | Baixa | Médio | Buffer de contingência (4 dias) |
| Problemas técnicos não previstos | Média | Médio | Timebox para investigação |
| Mudanças de escopo | Média | Alto | Processo formal de mudança |
| Dependência de API externa | Baixa | Médio | Fallback implementado |

---
