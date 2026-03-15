# Análise de Riscos - Monitora Wuaze

## Matriz de Probabilidade e Impacto
- **Probabilidade:** (B) Baixa, (M) Média, (A) Alta
- **Impacto:** (B) Baixo, (M) Médio, (A) Alto

| ID | Risco | Descrição | Probabilidade | Impacto | Mitigação / Plano de Ação |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **R01** | **Mudanças na Política da Google Play** | O Google pode alterar políticas de privacidade, dificultando a publicação ou funcionamento do app. | M | A | Manter-se atualizado com as políticas. Desenvolver o app de forma modular para adaptar rapidamente a novas regras. Distribuir inicialmente por download direto (APK). |
| **R02** | **Dificuldades Técnicas com Android** | A implementação do modo invisível e monitorização em background pode ser complexa e variar entre versões/fabricantes. | A | A | Pesquisa aprofundada, prototipagem antecipada. Utilizar permissões adequadas e justificar a necessidade. Testar em diversos dispositivos e versões. |
| **R03** | **Baixa Adesão de Utilizadores** | O produto pode não atingir o público esperado devido a falta de divulgação ou desconfiança. | M | A | Criar campanhas de marketing focadas em segurança. Oferecer um período de teste gratuito. Coletar feedback e melhorar continuamente. |
| **R04** | **Questões Legais e de Privacidade** | A monitorização de menores pode levantar questões legais se não for implementada com o devido consentimento. | M | A | Incluir termos de uso claros que transfiram a responsabilidade do consentimento para o parente. Garantir que o uso é para menores sob tutela. Consultar um advogado. |
| **R05** | **Concorrência com Soluções Gratuitas** | Existem aplicações gratuitas que oferecem funcionalidades semelhantes, como o Google Family Link. | A | M | Diferenciar-se pelo preço acessível em MZN, suporte local e funcionalidades mais invasivas (teclado, SMS) que os concorrentes gratuitos não oferecem. |
| **R06** | **Falhas de Segurança e Vazamento de Dados** | Dados sensíveis de crianças podem ser expostos devido a falhas de segurança. | B | A | Implementar boas práticas de segurança (bcrypt, HTTPS, criptografia). Realizar testes de penetração. Manter backups regulares. Seguir a LGPD local. |
| **R07** | **Dependência de Serviços Gratuitos** | O projeto depende de Firebase e OpenStreetMap, que podem alterar seus modelos de preços ou termos de uso. | M | M | Acompanhar anúncios das plataformas. Ter um plano de contingência para migrar para alternativas se necessário (ex: servidor próprio de mapas). |
| **R08** | **Disponibilidade do Desenvolvedor** | Por ser um projeto de uma só pessoa (Stélio), atrasos podem ocorrer por motivos pessoais ou sobrecarga. | M | M | Utilizar a metodologia Scrum para gerir o tempo de forma eficiente. Priorizar o backlog para garantir entrega do mínimo produto viável (MVP) dentro do prazo. |
| **R09** | **Consumo Elevado de Bateria** | O app pode ser identificado como consumidor excessivo de bateria, levando o sistema operativo a encerrá-lo. | M | A | Otimizar o envio de localização (usar movimento significativo). Utilizar workers eficientes. Testar exaustivamente o consumo. |
