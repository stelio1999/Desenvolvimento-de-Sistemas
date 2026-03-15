# Requisitos do Sistema - Monitora Wuaze

## 1. Requisitos Funcionais (RF)

| Código | Requisito | Descrição |
| :--- | :--- | :--- |
| RF01 | Autenticação | O sistema deve permitir que utilizadores (admin e parente) façam login com email e senha. |
| RF02 | Registo de Parentes | O sistema deve permitir o registo de novos parentes com nome, email, telefone e senha. |
| RF03 | Gestão de Crianças | O parente deve poder cadastrar, editar e remover crianças associadas à sua conta. |
| RF04 | Geração de Código Único | O sistema deve gerar um código único para associar o telemóvel da criança ao perfil. |
| RF05 | Validação de Código | O app móvel deve validar o código único com o servidor antes de iniciar a monitoria. |
| RF06 | Monitorização de Localização | O app deve recolher a localização do dispositivo e enviar para o servidor. |
| RF07 | Monitorização de SMS | O app deve recolher as mensagens SMS recebidas e enviadas. |
| RF08 | Monitorização de Chamadas | O app deve recolher o histórico de chamadas (recebidas, efetuadas e perdidas). |
| RF09 | Monitorização de Contactos | O app deve recolher a lista de contactos do dispositivo. |
| RF10 | Monitorização de Teclado | O app deve capturar textos digitados em aplicativos específicos. |
| RF11 | Dashboard Web | O sistema deve apresentar um dashboard com estatísticas e informações das crianças. |
| RF12 | Visualização em Mapa | O parente deve poder ver a localização da criança num mapa interativo. |
| RF13 | Histórico de Localizações | O sistema deve armazenar e permitir a visualização do histórico de localizações. |
| RF14 | Gestão de Pagamentos | O admin deve gerir os pagamentos mensais dos parentes. |
| RF15 | Notificações | O sistema deve notificar o parente quando a criança entra ou sai de zonas. |
| RF16 | Download do APK | O site deve disponibilizar o download da aplicação móvel (APK). |
| RF17 | Sincronização Offline | O app deve armazenar dados localmente quando não há internet e sincronizar quando houver conexão. |
| RF18 | Informações do Dispositivo | O app deve recolher modelo, versão Android, operadora e nível de bateria. |
| RF19 | Modo Invisível | O app deve funcionar em segundo plano sem ícone ou notificações visíveis. |

## 2. Requisitos Não Funcionais (RNF)

| Código | Requisito | Descrição |
| :--- | :--- | :--- |
| RNF01 | Segurança | As senhas devem ser armazenadas com hash (bcrypt) e os dados transmitidos com criptografia. |
| RNF02 | Disponibilidade | O sistema deve estar disponível 99.5% do tempo. |
| RNF03 | Performance | O tempo de resposta do sistema web deve ser inferior a 3 segundos. |
| RNF04 | Escalabilidade | O sistema deve suportar até 10.000 utilizadores simultâneos. |
| RNF05 | Usabilidade | A interface deve ser intuitiva, mesmo para utilizadores com pouca experiência. |
| RNF06 | Compatibilidade | O app deve funcionar em dispositivos Android a partir da versão 6.0 (API 23). |
| RNF07 | Consumo de Bateria | O app deve otimizar o consumo de bateria, enviando localizações apenas com movimento significativo. |
| RNF08 | Privacidade | Os dados das crianças só devem ser acessíveis pelos respetivos parentes. |
| RNF09 | Backup | O sistema deve realizar backup diário da base de dados. |
| RNF10 | Responsividade | O site deve ser totalmente responsivo para dispositivos móveis e tablets. |
| RNF11 | Armazenamento Local | O app deve limitar o armazenamento local a 100 registos por tipo. |
| RNF12 | Internacionalização | O sistema deve estar disponível em Português. |
