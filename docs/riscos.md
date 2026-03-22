# SGAA - Matriz de Riscos

## 📊 Visão Geral

| Métrica | Valor |
|---------|-------|
| **Total de Riscos Identificados** | 15 |
| **Riscos Críticos (Prioridade Alta)** | 6 |
| **Riscos Médios** | 6 |
| **Riscos Baixos** | 3 |
| **Riscos Mitigados** | 12 |
| **Riscos Aceitos** | 3 |

---

## 🎯 Matriz de Riscos

| ID | Risco | Probabilidade | Impacto | Prioridade | Mitigação | Responsável |
|----|-------|---------------|---------|------------|-----------|-------------|
| **R01** | Atraso na entrega por requisitos mal definidos | Média (3) | Alto (4) | **Alta** | • Reuniões semanais com stakeholders<br>• Protótipos validados antes do desenvolvimento<br>• Buffer de contingência de 15% | Product Owner |
| **R02** | Mudanças frequentes de requisitos | Média (3) | Médio (3) | **Média** | • Processo formal de mudança<br>• Impacto avaliado antes de aprovar<br>• Priorização com Product Owner | Scrum Master |
| **R03** | Problemas de desempenho com muitos dados | Baixa (2) | Alto (4) | **Alta** | • Testes de carga desde o início<br>• Índices optimizados<br>• Cache implementado (Redis)<br>• Paginação em todas as listas | Tech Lead |
| **R04** | Falha na integração do mapa OpenStreetMap | Baixa (2) | Médio (3) | **Média** | • Fallback para coordenadas manuais<br>• Cache de mapas offline<br>• Alternativa com Leaflet local | Frontend |
| **R05** | Segurança de dados comprometida | Baixa (2) | Crítico (5) | **Alta** | • Validação server-side<br>• Prepared statements (SQL injection)<br>• CSRF tokens<br>• Auditoria de segurança<br>• Hash de senhas (bcrypt) | Tech Lead |
| **R06** | Rotatividade da equipa de desenvolvimento | Baixa (2) | Médio (3) | **Média** | • Documentação detalhada<br>• Code reviews regulares<br>• Pair programming<br>• Conhecimento distribuído | Scrum Master |
| **R07** | Problemas com servidor/hospedagem | Baixa (2) | Alto (4) | **Alta** | • Backup diário<br>• Ambiente de staging<br>• Plano de contingência para downtime<br>• Monitorização 24/7 | DevOps |
| **R08** | Resistência dos utilizadores à mudança | Média (3) | Médio (3) | **Média** | • Treinamento antecipado<br>• Documentação clara<br>• Suporte pós-implantação<br>• Programa de pilotos | Product Owner |
| **R09** | Erros de cálculo de facturas | Baixa (2) | Crítico (5) | **Alta** | • Testes unitários com cenários variados<br>• Validação manual em homologação<br>• Histórico de cálculos para auditoria<br>• Logs detalhados | Backend |
| **R10** | Falha na integração com serviços de pagamento | Baixa (2) | Médio (3) | **Média** | • Múltiplos métodos de pagamento<br>• Confirmação manual disponível<br>• Logs detalhados de transações | Backend |
| **R11** | Vazamento de dados sensíveis | Baixa (2) | Crítico (5) | **Alta** | • Criptografia em trânsito (HTTPS)<br>• Dados sensíveis mascarados<br>• Controlo de acesso rigoroso<br>• Auditoria de segurança | Tech Lead |
| **R12** | Indisponibilidade do sistema | Baixa (2) | Alto (4) | **Alta** | • Arquitectura escalável<br>• Balanceamento de carga<br>• Monitorização proactiva<br>• Plano de recuperação | DevOps |
| **R13** | Dificuldade de aprendizagem dos utilizadores | Média (3) | Baixo (2) | **Baixa** | • Interface intuitiva<br>• Tooltips e guias<br>• Vídeos tutoriais<br>• Suporte por chat | Frontend |
| **R14** | Conformidade legal não atendida | Baixa (2) | Alto (4) | **Alta** | • Consultoria jurídica<br>• Termos de uso claros<br>• Consentimento explícito<br>• Política de privacidade | Product Owner |
| **R15** | Orçamento excedido | Baixa (2) | Médio (3) | **Média** | • Monitorização de custos<br>• Aprovação prévia de aquisições<br>• Uso de ferramentas open-source | Scrum Master |

---

## 📈 Plano de Ação por Risco

### R01 - Atraso na entrega por requisitos mal definidos
- **Ação Preventiva:** Reuniões de refinamento de backlog semanais
- **Ação Corretiva:** Replaneamento do sprint, remoção de histórias de baixa prioridade
- **Responsável:** Product Owner
- **Prazo:** Contínuo

### R03 - Problemas de desempenho com muitos dados
- **Ação Preventiva:** Testes de carga com 10.000 registos na Semana 3
- **Ação Corretiva:** Otimização de queries, adição de índices, implementação de cache
- **Responsável:** Tech Lead
- **Prazo:** Semana 4

### R05 - Segurança de dados comprometida
- **Ação Preventiva:** Auditoria de segurança na Semana 2, revisão de código focada em segurança
- **Ação Corretiva:** Patch de segurança imediato, notificação de incidente
- **Responsável:** Tech Lead
- **Prazo:** Contínuo

### R07 - Problemas com servidor/hospedagem
- **Ação Preventiva:** Ambiente de staging idêntico à produção, backups diários
- **Ação Corretiva:** Plano de contingência com rollback em 30 minutos
- **Responsável:** DevOps
- **Prazo:** Semana 1

### R09 - Erros de cálculo de facturas
- **Ação Preventiva:** Testes unitários com 50+ cenários de consumo
- **Ação Corretiva:** Correção imediata, reemissão de facturas afectadas
- **Responsável:** Backend
- **Prazo:** Semana 5

### R14 - Conformidade legal não atendida
- **Ação Preventiva:** Validação jurídica dos termos e políticas na Semana 1
- **Ação Corretiva:** Atualização dos documentos legais
- **Responsável:** Product Owner
- **Prazo:** Semana 1

---

## 🔄 Ciclo de Gestão de Riscos

1. **Identificação** - Reunião semanal de identificação de novos riscos
2. **Análise** - Avaliação de probabilidade e impacto
3. **Priorização** - Classificação por prioridade
4. **Mitigação** - Definição e implementação de ações
5. **Monitoramento** - Acompanhamento contínuo
6. **Revisão** - Atualização da matriz semanalmente
