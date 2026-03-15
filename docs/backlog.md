# Backlog do Produto - Monitora Wuaze

**Prioridades (MoSCoW):** Must Have, Should Have, Could Have, Won't Have
**Estimativa de Complexidade:** (S) Simples, (M) Média, (C) Complexa

## Must Have (Prioridade Alta)

| ID | User Story | Critérios de Aceitação | Complexidade |
| :--- | :--- | :--- | :--- |
| **US01** | Como encarregado de educação, quero registrar-me no sistema com meu email e telefone para poder aceder à plataforma. | • Formulário com nome, email, telefone e senha.<br>• Email único no sistema.<br>• Senha com mínimo 8 caracteres.<br>• Telefone moçambicano válido.<br>• Envio de email de confirmação. | M |
| **US02** | Como utilizador, quero fazer login com email e senha para aceder às minhas informações. | • Validação de credenciais.<br>• Mensagem de erro clara.<br>• Opção "Lembrar-me".<br>• Redirecionamento por perfil (admin/parente).<br>• Bloqueio temporário após 5 tentativas falhadas. | S |
| **US03** | Como parente, quero cadastrar os dados dos meus filhos para começar a monitorizá-los. | • Formulário com nome, data de nascimento, género, escola e classe.<br>• Validação de idade (menor de 18 anos).<br>• Permitir cadastrar múltiplas crianças.<br>• Listagem das crianças cadastradas. | M |
| **US04** | Como parente, quero gerar um código único para cada criança para poder instalar o app no telemóvel dela. | • Código com formato XXXX-XXXX.<br>• Expiração em 24 horas.<br>• Não gerar código para criança com app ativo.<br>• Opção de copiar o código. | S |
| **US05** | Como sistema, quero validar o código inserido no app móvel para garantir que apenas dispositivos autorizados são monitorizados. | • App envia código, IMEI e modelo.<br>• Verificar validade e expiração do código.<br>• Registrar IMEI do dispositivo.<br>• Retornar resposta JSON com sucesso/erro. | M |
| **US06** | Como sistema, quero recolher a localização do dispositivo a cada 30 segundos para permitir o acompanhamento em tempo real. | • Guardar localização apenas se houver movimento > 120m.<br>• Armazenamento offline quando sem internet.<br>• Enviar para o Firebase quando houver conexão.<br>• Incluir latitude, longitude, precisão, velocidade e altitude. | C |
| **US07** | Como parente, quero ver um dashboard com as informações resumidas dos meus filhos para acompanhar rapidamente o estado de cada um. | • Lista de crianças com nome e idade.<br>• Indicador de online/offline.<br>• Nível de bateria.<br>• Última localização.<br>• Botões de acesso rápido para detalhes. | M |
| **US08** | Como parente, quero ver a localização atual do meu filho num mapa para saber onde ele está. | • Mapa interativo com OpenStreetMap.<br>• Marcador da localização atual.<br>• Popup com hora, bateria e precisão.<br>• Opção de centralizar e zoom. | M |

## Should Have (Prioridade Média)

| ID | User Story | Critérios de Aceitação | Complexidade |
| :--- | :--- | :--- | :--- |
| **US09** | Como parente, quero ver o histórico de localizações do meu filho para saber onde ele esteve durante o dia. | • Listagem das últimas 50 localizações.<br>• Filtro por data.<br>• Visualização em lista e mapa.<br>• Informação de data, hora e endereço aproximado. | M |
| **US10** | Como parente, quero ver as mensagens SMS do telemóvel do meu filho para saber com quem ele comunica. | • Listagem de SMS recebidos e enviados.<br>• Identificação do contacto.<br>• Data e hora da mensagem.<br>• Visualização do conteúdo completo.<br>• Opção de exportar para CSV. | C |
| **US11** | Como parente, quero ver o histórico de chamadas do telemóvel do meu filho para saber com quem ele fala. | • Listagem de chamadas recebidas, efetuadas e perdidas.<br>• Identificação do contacto.<br>• Duração da chamada.<br>• Data e hora.<br>• Filtro por tipo de chamada. | M |
| **US12** | Como parente, quero ver a lista de contactos do telemóvel do meu filho para saber quem são as pessoas com quem ele se relaciona. | • Listagem de contactos com nome e número.<br>• Contagem total de contactos.<br>• Pesquisa por nome ou número.<br>• Identificação de números duplicados. | M |
| **US13** | Como administrador, quero um dashboard com estatísticas gerais do sistema para monitorizar o crescimento da plataforma. | • Total de parentes registados.<br>• Total de crianças monitorizadas.<br>• Total de pagamentos do mês.<br>• Gráficos de crescimento.<br>• Lista de últimas atividades. | M |
| **US14** | Como administrador, quero gerir os pagamentos mensais dos parentes para controlar as assinaturas ativas. | • Listagem de pagamentos por parente.<br>• Filtro por mês, ano e status.<br>• Confirmação manual de pagamentos.<br>• Upload de comprovativos.<br>• Notificação por email. | C |

## Could Have (Prioridade Baixa)

| ID | User Story | Critérios de Aceitação | Complexidade |
| :--- | :--- | :--- | :--- |
| **US15** | Como parente, quero monitorizar o que meu filho digita em aplicativos como WhatsApp para garantir que não está em risco. | • Captura de textos completos (após envio).<br>• Identificação do aplicativo utilizado.<br>• Data e hora da digitação.<br>• Listagem por aplicativo.<br>• Prevenção de duplicatas. | C |
