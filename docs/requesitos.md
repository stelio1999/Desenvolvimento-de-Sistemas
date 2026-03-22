# SGAA - Requisitos do Sistema

## 📋 Índice

1. [Requisitos Funcionais](#requisitos-funcionais)
2. [Requisitos Não-Funcionais](#requisitos-não-funcionais)

---

## 1. Requisitos Funcionais (RF)

| ID | Requisito | Descrição |
|----|-----------|-----------|
| **RF01** | Autenticação de Utilizadores | O sistema deve permitir autenticação de utilizadores através de email ou número de telefone combinado com senha, validando as credenciais e concedendo acesso conforme o perfil atribuído (SuperAdmin, Admin ou Cliente). |
| **RF02** | Recuperação de Senha | O sistema deve disponibilizar funcionalidade de recuperação de senha mediante envio de link para o email do utilizador, com token válido por 60 minutos, e permitir a redefinição mediante confirmação da nova senha. |
| **RF03** | Gestão de Utilizadores por SuperAdmin | O sistema deve permitir que o SuperAdmin crie, edite, active, desactive e remova utilizadores com perfil Admin, validando a unicidade de email e número de telefone, e gerando senha temporária enviada por email. |
| **RF04** | Cadastro de Clientes por Admin | O sistema deve permitir que o Admin cadastre clientes informando: nome completo, email, telefone, nacionalidade, NUIT, endereço, número de contrato, número do contador e leitura inicial, validando a unicidade do NUIT, contrato e número do contador. |
| **RF05** | Gestão de Contadores de Água | O sistema deve manter registo de contadores associados a cada cliente, armazenando número do contador, leitura actual, data da última leitura, data de instalação e status de activação. |
| **RF06** | Georreferenciação de Clientes | O sistema deve permitir que o Admin marque a localização da residência do cliente em mapa interactivo OpenStreetMap, através de busca por endereço ou arrasto manual do marcador, registando as coordenadas geográficas. |
| **RF07** | Registo de Vistorias Técnicas | O sistema deve permitir que o Admin realize vistoria seleccionando o cliente, visualizando a leitura anterior, registando a leitura actual, calculando automaticamente o consumo (diferença entre leituras) e gerando a factura correspondente. |
| **RF08** | Cálculo Automático de Consumo | O sistema deve calcular o consumo em metros cúbicos pela diferença entre leitura actual e leitura anterior, exibindo o resultado imediatamente após o registo da nova leitura. |
| **RF09** | Emissão Automática de Facturas | O sistema deve gerar automaticamente factura após cada vistoria, aplicando as regras de cálculo: consumo igual ou inferior ao consumo mínimo cobra apenas a taxa mínima; consumo superior ao mínimo cobra taxa mínima acrescida de taxa adicional por cada metro cúbico excedente. |
| **RF10** | Aplicação de Multas | O sistema deve calcular e aplicar multa sobre facturas não pagas após o período de carência configurado, utilizando percentagem definida sobre o valor da factura. |
| **RF11** | Configuração de Taxas pelo Admin | O sistema deve permitir que o Admin configure: consumo mínimo em metros cúbicos, valor da taxa mínima em meticais, valor da taxa adicional por metro cúbico excedente, percentagem da multa sobre factura vencida e número de dias para início da cobrança de multa. |
| **RF12** | Visualização de Clientes em Mapa | O sistema deve exibir todos os clientes georreferenciados em mapa interactivo com marcadores coloridos: vermelho para clientes não visitados no período e verde para clientes já visitados, exibindo informações do cliente ao clicar no marcador. |
| **RF13** | Actualização de Status de Visita em Mapa | O sistema deve alterar automaticamente a cor do marcador de vermelho para verde assim que o Admin concluir uma vistoria na residência do cliente, registando a data e hora da visita. |
| **RF14** | Traçado de Rota Optimizada | O sistema deve permitir que o Admin calcule rota optimizada para visitar os clientes com marcadores vermelhos, exibindo a ordem de visita, a distância total e o tempo estimado de percurso. |
| **RF15** | Confirmação de Pagamentos pelo Admin | O sistema deve permitir que o Admin confirme pagamentos efectuados por clientes, registando o nome do operário responsável, a data do pagamento e emitindo recibo com número de confirmação. |
| **RF16** | Visualização de Facturas pelo Cliente | O sistema deve permitir que o cliente autenticado visualize todas as suas facturas, com detalhes de data de emissão, data de vencimento, consumo registado, valor total e status (pendente, pago, vencido). |
| **RF17** | Download de Factura em PDF pelo Cliente | O sistema deve disponibilizar funcionalidade para o cliente baixar qualquer factura no formato PDF, contendo os dados da empresa, dados do cliente, detalhes do consumo, cálculo dos valores e código de barras. |
| **RF18** | Visualização de Localização da Secretaria | O sistema deve exibir em mapa a localização da secretaria da empresa, detectar automaticamente a localização actual do cliente e traçar a rota mais curta desde o ponto de partida até à secretaria, destacando-a em vermelho. |
| **RF19** | Gestão de Comunicados pelo Admin | O sistema deve permitir que o Admin crie, edite, publique e remova comunicados, com título, conteúdo, categoria (geral, importante, emergência) e data de publicação. |
| **RF20** | Visualização de Comunicados | O sistema deve exibir comunicados publicados na página inicial e no portal do cliente, ordenados por data de publicação, com destaque para comunicados importantes. |
| **RF21** | Geração de Relatório Financeiro | O sistema deve gerar relatório financeiro consolidado com: total facturado, total recebido, total pendente, total em atraso e percentagem de inadimplência, com filtro por período. |
| **RF22** | Geração de Relatório de Consumo | O sistema deve gerar relatório de consumo com: consumo total, consumo médio por cliente, clientes atendidos e distribuição de consumo por bairro, com filtro por período. |
| **RF23** | Geração de Relatório Operacional | O sistema deve gerar relatório operacional com: total de vistorias realizadas, vistorias pendentes, desempenho por técnico e condição dos contadores, com filtro por período. |
| **RF24** | Exportação de Relatórios | O sistema deve permitir exportação de relatórios nos formatos PDF, Excel e CSV, com layout adequado para impressão e análise de dados. |
| **RF25** | Alteração de Idioma | O sistema deve permitir ao utilizador seleccionar o idioma de interface entre as opções: Português de Moçambique, Português do Brasil, Português de Portugal, Inglês, Chinês Mandarim, Árabe e Russo, persistindo a escolha para sessões futuras. |
| **RF26** | Alternância de Tema Visual | O sistema deve permitir ao utilizador alternar entre tema claro e tema escuro, persistindo a escolha para sessões futuras. |
| **RF27** | Edição de Perfil do Utilizador | O sistema deve permitir que qualquer utilizador autenticado edite seus dados pessoais (nome, email, telefone), altere sua senha com confirmação e faça upload de foto de perfil. |
| **RF28** | Gestão de Sessões Activas | O sistema deve permitir que o utilizador visualize todas as suas sessões activas e encerre sessões remotamente. |
| **RF29** | Notificações do Sistema | O sistema deve notificar o utilizador sobre eventos importantes como vencimento de factura, confirmação de pagamento e novos comunicados, através do centro de notificações. |
| **RF30** | Registo de Actividades | O sistema deve manter registo de actividades dos utilizadores (quem, quando, qual acção) para fins de auditoria. |

---

## 2. Requisitos Não-Funcionais (RNF)

| ID | Requisito | Descrição | Métrica de Aceitação |
|----|-----------|-----------|---------------------|
| **RNF01** | Tempo de Resposta | O sistema deve processar e apresentar os resultados de qualquer operação em tempo adequado à experiência do utilizador. | 95% das operações devem responder em até 3 segundos; operações complexas (relatórios) em até 10 segundos. |
| **RNF02** | Disponibilidade | O sistema deve estar acessível para utilização durante o horário comercial. | Disponibilidade mínima de 99% durante o horário de funcionamento (08:00 às 18:00). |
| **RNF03** | Capacidade de Concorrência | O sistema deve suportar múltiplos acessos simultâneos sem degradação significativa de desempenho. | Suportar até 100 utilizadores concorrentes com tempo de resposta inferior a 5 segundos. |
| **RNF04** | Segurança de Dados | O sistema deve proteger dados sensíveis contra acessos não autorizados e ataques comuns a aplicações web. | Senhas armazenadas com hash (bcrypt); protecção contra SQL Injection, XSS e CSRF; todas as validações implementadas no servidor. |
| **RNF05** | Auditoria de Acessos | O sistema deve registar todas as tentativas de acesso e acções críticas para rastreabilidade. | Logs devem conter identificador do utilizador, data/hora, endereço IP, acção executada e resultado. |
| **RNF06** | Integridade de Dados | O sistema deve garantir que operações que envolvem múltiplas tabelas sejam executadas completamente ou não sejam executadas. | Transacções devem ser atómicas, utilizando rollback automático em caso de falha. |
| **RNF07** | Escalabilidade Vertical | O sistema deve suportar crescimento no volume de dados sem necessidade de alteração na arquitectura. | Suportar cadastro de 100.000 clientes com manutenção do desempenho. |
| **RNF08** | Usabilidade | O sistema deve apresentar interface intuitiva, com padrões consistentes e acessível em dispositivos móveis. | Interface responsiva (mobile-first); navegação por menu lateral; feedback visual para todas as acções; skeleton loading durante carregamentos. |
| **RNF09** | Acessibilidade | O sistema deve ser acessível a utilizadores com necessidades especiais. | Conformidade com WCAG 2.1 nível AA; contraste adequado; navegação por teclado; suporte a leitores de tela. |
| **RNF10** | Compatibilidade com Navegadores | O sistema deve funcionar correctamente nos principais navegadores do mercado. | Suporte às duas versões mais recentes de Chrome, Firefox, Safari e Edge. |
| **RNF11** | Compatibilidade com Dispositivos | O sistema deve adaptar-se a diferentes tamanhos de ecrã. | Layout funcional em smartphones (320px), tablets (768px), notebooks (1024px) e desktops (1920px). |
| **RNF12** | Manutenibilidade | O código deve ser organizado, documentado e seguir padrões de boas práticas. | Código deve seguir PSR-12 (PHP) e padrões ESLint (JavaScript); documentação de API com Swagger; comentários em métodos complexos. |
| **RNF13** | Testabilidade | O sistema deve permitir execução de testes automatizados. | Cobertura mínima de testes unitários de 70%; testes de integração para fluxos críticos; testes end-to-end para autenticação e facturação. |
| **RNF14** | Portabilidade | O sistema deve poder ser instalado em diferentes ambientes sem modificações no código. | Configurações sensíveis gerenciadas por variáveis de ambiente; suporte a MySQL e MariaDB. |
| **RNF15** | Backup e Recuperação | O sistema deve garantir que dados possam ser recuperados em caso de falha. | Backup automático diário; retenção de 30 dias; procedimento documentado de recuperação. |
| **RNF16** | Internacionalização | O sistema deve suportar múltiplos idiomas sem necessidade de alteração no código-fonte. | Todas as strings na interface devem ser gerenciadas por arquivos de tradução; suporte a 7 idiomas completos. |
| **RNF17** | Monitorização | O sistema deve permitir monitorização de erros e desempenho. | Logs centralizados; registo de excepções com stack trace; alertas para erros críticos. |
| **RNF18** | Conformidade Legal | O sistema deve atender à legislação aplicável de protecção de dados. | Conformidade com a Lei de Protecção de Dados (Lei nº 8/2022, de 4 de Maio, Moçambique); consentimento explícito para coleta de dados pessoais. |
| **RNF19** | Consistência Visual | O sistema deve manter padrão visual consistente em todas as interfaces. | Utilização de design system com cores: branco, azul ciano, azul escuro, verde; ausência de gradientes; tipografia Inter; componentes padronizados. |
| **RNF20** | Eficiência de Recursos | O sistema deve utilizar recursos computacionais de forma optimizada. | Carregamento assíncrono de dados (AJAX); lazy loading de imagens; minificação de assets; cache de consultas frequentes. |
